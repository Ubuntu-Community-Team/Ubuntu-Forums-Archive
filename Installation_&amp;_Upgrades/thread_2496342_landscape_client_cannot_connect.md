---
title: "landscape client cannot connect"
date: 2024-03-24
forum: Installation &amp; Upgrades
---

### Post by zhex900 on 2024-03-24
I have landscape self hosted running on Ubuntu 22.04. I can't get the landscape client connect. The landscape client is installed in Ubuntu Core as a snap.

What should I do?

sudo cp /etc/ssl/certs/landscape_server.pem ~/server.pem

in ubuntu core

sudo landscape-client.config --account-name standalone --url [https://ubuntu/message-system](https://ubuntu/message-system) --ping-url [http://ubuntu/ping](http://ubuntu/ping) --computer-title "node-0" --ssl-public-key ./server.pem

```
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:21:48,513 INFO     [MainThread] This machine does not appear to be a Swift machine. Deactivating plugin.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:13,040 INFO     [MainThread] This machine does not appear to be a Ceph machine. Deactivating plugin.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:35,882 INFO     [MainThread] Got notification of impending exchange. Notifying all plugins.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:35,883 INFO     [MainThread] Got notification of impending exchange. Notifying all plugins.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:45,996 INFO     [MainThread] Queueing message to register with account 'standalone' without a password.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:46,078 INFO     [MainThread] Starting urgent message exchange with [https://ubuntu/message-system](https://ubuntu/message-system).
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:46,409 ERROR    [PoolThread-twisted.internet.reactor-0] Error contacting the server at [https://ubuntu/message-system](https://ubuntu/message-system).
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: Traceback (most recent call last):
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:   File "/snap/landscape-client/135/usr/lib/python3.10/site-packages/landscape/lib/fetch.py", line 127, in fetch
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:     curl.perform()
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: pycurl.error: (77, '')
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: During handling of the above exception, another exception occurred:
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: Traceback (most recent call last):
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:   File "/snap/landscape-client/135/usr/lib/python3.10/site-packages/landscape/client/broker/transport.py", line 98, in exchange
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:     curly, data = self._curl(
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:   File "/snap/landscape-client/135/usr/lib/python3.10/site-packages/landscape/client/broker/transport.py", line 60, in _curl
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:     fetch(
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:   File "/snap/landscape-client/135/usr/lib/python3.10/site-packages/landscape/lib/fetch.py", line 129, in fetch
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]:     raise PyCurlError(e.args[0], e.args[1])
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: landscape.lib.fetch.PyCurlError: Error 77:
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:46,489 INFO     [MainThread] Message exchange failed.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:22:46,497 INFO     [MainThread] Message exchange completed in 0.42s.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:23:36,516 INFO     [MainThread] Got notification of impending exchange. Notifying all plugins.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:23:36,516 INFO     [MainThread] Got notification of impending exchange. Notifying all plugins.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:23:46,528 INFO     [MainThread] Queueing message to register with account 'standalone' without a password.
2024-03-24T23:23:46Z landscape-client.landscape-client[1896]: 2024-03-24 23:23:46,549 INFO     [MainThread] Starting urgent message exchange with [https://ubuntu/message-system](https://ubuntu/message-system).

```

---

### Post by tommid1102 on 2024-07-08
Hi,

have a look at the file permissions of the certificate. Client must be able to read it. At least that solved it for me.

regards. Thomas

---

