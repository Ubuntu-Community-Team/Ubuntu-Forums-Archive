---
title: "Landscape on prem registering clients fails"
date: 2016-10-28
forum: Installation &amp; Upgrades
---

### Post by weathercloud on 2016-10-28
Having issues with On Prem Landscape deployment. I deployed this on a Digital Ocean droplet and the install went fine. However I just keep getting a time out when I try and register my client. As per other instructions I copied the cert over but still it seems to have an issue. I am able to connect to the host without issue. I am using Ubuntu 16.04 droplet on Digital Ocean. 

Error from the client:
```
[COLOR=#000000]HTTPCodeError: Server returned HTTP code 404[/COLOR]2016-10-25 12:22:36,538 INFO     [MainThread] Message exchange failed.
2016-10-25 12:22:36,539 INFO     [MainThread] Message exchange completed in 0.27s.
2016-10-25 12:23:36,544 INFO     [MainThread] Queueing message to register with account 'standalone' without a password.
2016-10-25 12:23:36,546 INFO     [MainThread] Starting urgent message exchange with http://landscape.myhost.com:8080/message-system.
2016-10-25 12:23:36,624 ERROR    [PoolThread-twisted.internet.reactor-1] Error contacting the server at http://landscape.myhost.com:8080/message-system.
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/landscape/broker/transport.py", line 71, in exchange
    message_api)
  File "/usr/lib/python2.7/dist-packages/landscape/broker/transport.py", line 45, in _curl
    headers=headers, cainfo=self._pubkey, curl=curl))
  File "/usr/lib/python2.7/dist-packages/landscape/lib/fetch.py", line 115, in fetch
    raise HTTPCodeError(http_code, body)
HTTPCodeError: Server returned HTTP code 404
2016-10-25 12:23:36,625 INFO     [MainThread] Message exchange failed. [COLOR=#000000]2016-10-25 12:23:36,625 INFO     [MainThread] Message exchange completed in 0.08s[/COLOR]
```

I copied the cert [COLOR=#000000]from /etc/ssl/certs/landscape_server_ca.crt  to client @ /etc/landscape/server.pem

[/COLOR]I update the client confit:

```
[COLOR=#000000][client][/COLOR]log_level = info
url = http://landscape.myhost.com:8080/message-system
ping_url = http://landscape.myhost.com:8080/pin
data_path = /var/lib/landscape/client
include_manager_plugins = ScriptExecution
computer_title = My Web Server
account_name = standalone [COLOR=#000000]ssl_public_key = /etc/landscape/server.pem[/COLOR]
```

---

### Post by weathercloud on 2016-10-28
I uploaded the server side error here! I purposely edited out hostnames and IPs but have confirmed everything is correct. I checked to make sure the cert signed with the correct hostname and that all the IPs are correct.  

Let me know if you guys have any ideas.

---

### Post by weathercloud on 2016-11-03
Still having this issue. Any ideas?

---

