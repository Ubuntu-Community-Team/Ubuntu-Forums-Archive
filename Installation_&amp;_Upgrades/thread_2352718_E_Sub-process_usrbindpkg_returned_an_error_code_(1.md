---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-02-15
forum: Installation &amp; Upgrades
---

### Post by kleanuria on 2017-02-15
Hello!

So i tried to install github and shortly after starting the install it started giving me this error. 

Code:
```
Setting up runit (2.1.2-3ubuntu1) ...
start: Unable to connect to Upstart: Failed to connect to socket /com/ubuntu/upstart: Connection refused
dpkg: error processing package runit (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of git-daemon-run:
 git-daemon-run depends on runit; however:
  Package runit is not configured yet.

dpkg: error processing package git-daemon-run (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 runit
 git-daemon-run
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Been trying to fix for a day now figured I'd ask for help.

---

### Post by Perfect Storm on 2017-02-15
Try:
```
sudo dpkg --configure -a
sudo apt-get autoremove
sudo apt update
```

---

### Post by kleanuria on 2017-02-15
I just gave up about 5 minutes ago and reinstalled Ubuntu. It was just a VM so no big deal just wanted to figure out how to fix it but got a bit fed up with it. 
Thank you for trying to advise still!

---

