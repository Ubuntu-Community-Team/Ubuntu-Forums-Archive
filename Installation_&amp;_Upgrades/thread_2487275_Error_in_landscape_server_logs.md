---
title: "Error in landscape server logs"
date: 2023-05-29
forum: Installation &amp; Upgrades
---

### Post by and-ros-252525 on 2023-05-29
Hi,
I continuously get the following error in the lanscape server logs:



```
May 29 15:34:20 message-server-1 CRIT  #012Traceback (most recent call last):#012  File "/usr/lib/python3/dist-packages/txamqp/protocol.py", line 431, in authenticate#012    yield self.start(response, mechanism, locale)#012  File "/usr/lib/python3/dist-packages/txamqp/protocol.py", line 439, in start#012    yield self.started.wait()#012txamqp.client.Closed: [Failure instance: Traceback (failure with no frames): <class 'twisted.internet.error.ConnectionLost'>: Connection to the other side was lost in a non-clean fashion.#012]
```


Anyone can help me? what could be the problem that keeps generating this error?

Thanks in advance for the support.

---

