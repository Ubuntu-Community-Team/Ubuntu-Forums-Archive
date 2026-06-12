---
title: "Can't remove package on Ubuntu 16.04"
date: 2018-04-20
forum: Installation &amp; Upgrades
---

### Post by adhdluke on 2018-04-20
I installed amavisd-new-postfix while checking out all the ClamAV stuff in Synaptic. It didn't seem to install successfully, although everything says it's installed. Everything (apt, Synaptic, etc) comes up with an error whenever I try to remove it. sudo apt remove doesn't work, sudo dpkg --remove --force-remove-reinstreq doesn't work either, nothing works. What makes it really annoying is every single time I try to install new packages or upgrade existing packages, I ALSO GET THE ERROR. Whenever I do get the error it stops whatever the command was doing and I'm winding up unable to install some things. I couldn't install gnumeric with apt, for example.
Error after running "sudo dpkg --remove --force-remove-reinstreq amavisd-new-postfix"
```
(Reading database ... 232394 files and directories currently installed.)
Removing amavisd-new-postfix (1:2.10.1-2ubuntu1) ...
postfix.service is not active, cannot reload.
invoke-rc.d: initscript postfix, action "reload" failed.
dpkg: error processing package amavisd-new-postfix (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 amavisd-new-postfix

```

---

### Post by T.J. on 2018-04-20
I'm sorry, I can't help you with a detailed dissection of the problem presently.  Redoing OSes (Windows 10 blah). Have you checked your logs for an explanation of the exit code?

There are ways to force fix this issue, but I do not want to resort to them unless we absolutely have to.

---

### Post by adhdluke on 2018-04-22
I'm not sure how to check the logs for that, my experience with Linux isn't great yet.

---

