---
title: "Problem with terminal after 18.04.03 update"
date: 2020-02-25
forum: Installation &amp; Upgrades
---

### Post by Roland_Msl on 2020-02-25
Before the update, it worked like expected.

perl server.pl
This runs a perl script, which opens Chrome. It is a client server system, where server.pl interacts with Chrome.
After the last update, there is this error message:



[5997:5997:0225/104747.693063:ERROR:sandbox_linux.cc(372)] InitializeSandbox() called with multiple threads in process gpu-process.

server.pl opens Chrome, but the window in Chrome remains empty.

---

### Post by CelticWarrior on 2020-02-27
The title you chose is misleading. It suggests a problem with the terminal itself but actually it's a script that used to work, now doesn't, and it happens to run in terminal, incidentally and besides the point.

We don't know your script or what it's supposed to do but the error message suggests something related to sandboxing. This may mean that the script needs to be rewritten for the new Chrome version.

---

