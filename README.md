# Methods
Possible methods to get the internet in restricted network


## Cellhack 
Brute `Host:` http header.  
You can use this url for this `http://151.236.217.13/ok`  
This url always returns `200` so we can use it to check redirects.  

It returns `You find the hole` plaintext response.  

```
$ curl -H "Host: blabla.com" http://151.236.217.13/ok
You find the hole
```

### Bypass the http cache
Some ISP's may cache http traffic.  
To check this we can add random data to request and server will retutrn it in response  
```
$ curl -H "Host: blabla.com" http://151.236.217.13/ok?cachedornot123
You find the hole
cachedornot123

```

### Check for scripts injection
Some IPS's may inject javascript in http page. 
We can check this by calculating checksum of response

```
$ curl -H "Host: blabla.com" http://151.236.217.13/ok?someshit | md5sum
e355a7c941287bf3d924cff1ab8fab13
```

## Find gateway in LAN and other networks
Some hosts in LAN may allow forwarding.  Lets scan it to find hidden gateways  
IPS may allow forwarding to some local networks, so additional networks may be possible to add via option  
https://github.com/pentestmonkey/gateway-finder

## Find proxies
Scan LAN for 8080, 80, 1080, 3128 and so on for proxies

## 53 port 
Test raw connection from/to 53 TCP/UDP port

## Firewall misconfiguration
How to expoit?




