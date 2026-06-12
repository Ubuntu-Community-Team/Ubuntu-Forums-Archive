---
title: "running apt-get with no encryption"
date: 2013-07-09
forum: Installation &amp; Upgrades
---

### Post by floobit on 2013-07-09
I have an odd problem.  I run an Ubuntu vm at work.  Recently, our security team locked down the firewall such that denies most encrypted connections to outside websites.  This includes archive.ubuntu.com.  I don't think I can convince them to whitelist this site, so is there a way to do updates so that connections to repositories do not depend on any encrypted handshake?  I tried --allow-unauthenticated, but apt-get still hangs when connecting to archive.ubuntu.com.  Any ideas?  Ideally, I'd also like to play around with the new mind xfce 15, but in the install process, it also wants to connect to archive.ubuntu.com.  Am I sunk?

---

### Post by duanedesign on 2013-07-09
Hope maybe this will help you solve your issue. [http://askubuntu.com/questions/53146/how-do-i-get-add-apt-repository-to-work-through-a-proxy](http://askubuntu.com/questions/53146/how-do-i-get-add-apt-repository-to-work-through-a-proxy)

---

### Post by floobit on 2013-07-10
Thanks for the quick reply.  Unfortunately, the problem is not with https or any of the standard ssl useage - they just man in the middle that, and decrypt it on the fly.  As evidence, I can get to any https no problem.  I believe the issue is with some of the gpg keys that ubuntu has pre-stored in order to verify that the repositor server is not being impersonated.  Because the key is pre-stored, the connection is encrypted from the get-go, and the filter has no way of knowing the key to decrypt with.

---

