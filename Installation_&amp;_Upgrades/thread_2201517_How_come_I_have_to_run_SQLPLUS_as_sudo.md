---
title: "How come I have to run SQLPLUS as sudo?"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by robertzito on 2014-01-24
I have two different machines running Ubuntu 13.10 and just installed Oracles Instant Client on both. On my 32bit machine no problem went through it step by step runs fine.

But on my 64bit machine if I run the sqlplus64 command, I get the following error:

Error 46 initializing SQL*Plus
HTTP proxy setting has incorrect value
SP2-1502: The HTTP proxy server specified by http_proxy is not accessible

But if I run sudo sqlplus64 it connects with no problem!!! Where do the permission issues sit, with oracle or is it something with http_proxy? Either way how can I correct this issue.

---

### Post by robertzito on 2014-01-24
Not sure why by I had to set my proxy as below and works fine now:

export http_proxy=

---

