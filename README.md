# Introduction
An example of using workflow dispatch for creating virtual machines in Azure.

To invoke, use the following as an example.

```
$auth="<Enter your personal access token here>"
$headers = @{"Accept"="application/vnd.github.v3+json"; "Authorization"="token $auth"}
$payload = @{ "ref"="refs/heads/dev"; "inputs" =@{ "vmSku"="Standard_B2ms"; "vmCount"=3; } }
$body = $payload | ConvertTo-Json
$uri="https://api.github.com/repos/seekdavidlee/az-vm-workflow-dispatch/actions/workflows/app.yml/dispatches"
Invoke-WebRequest -Uri $uri -Headers $headers -UseBasicParsing -Body $body -Method POST
```

More information can be found on https://docs.github.com/en/rest/reference/actions#create-a-workflow-dispatch-event.
