---
title: "boot loop on 15.10 after upgrade"
date: 2016-08-30
forum: Installation &amp; Upgrades
---

### Post by Megan_Adams on 2016-08-30
I finally did an upgrade after ignoring it for months. 
It asked me if I wanted to turn off secure boot and I did. Now I am stuck in a boot loop. 

I get a terminal with alt cntl f1


My /var/log/gpu-manager.log reports that nvidia is not loaded. neither is nouveau. 

What should I print out here?

---

### Post by Megan_Adams on 2016-08-30
This worked for me:
[http://askubuntu.com/posts/481620/revisions](http://askubuntu.com/posts/481620/revisions)

But first I had to disable UEFI secure boot. 

Also I had a lightdm problem and did this:
[https://www.computersnyou.com/4947/](https://www.computersnyou.com/4947/)

---

