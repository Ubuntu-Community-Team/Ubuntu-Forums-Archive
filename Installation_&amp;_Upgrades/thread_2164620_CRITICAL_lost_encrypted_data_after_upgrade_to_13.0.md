---
title: "CRITICAL: lost encrypted data after upgrade to 13.04"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by madhusudana y n on 2013-08-01
Hi,

I was using ubuntu 12.04. my laptop hard disk size is 500GB. Of that, my first partition /dev/sda1 was of 20gb, /dev/sda2 was of 8gb and /dev/sda3 was rest of the disk.  Root(/) was mounted on sda1, and my home was mounted on sda3. 
I had encrypted the home directory, i.e sda3.

I tried upgrading to xubuntu 13.04 with live USB. Initially it asked if i want to install side by side or erase and install or something else. I chose erase and install hoping it would erase only sda1. But looks like it has erased whole disk.
Now  I have gone forward and installed fresh xubuntu. I want to recover my home directory data.

Is there any possible way of doing it?

pls pls help me.

---

### Post by lukeiamyourfather on 2013-08-01
Basically the data is gone. Some of it might be recoverable using utilities like scalpel but there's no silver bullet to just bring everything back. If the data is that important take it to a recovery specialist and have them do it, also know everything you do even browsing the internet could potentially be overwriting the old data.

---

### Post by madhusudana y n on 2013-08-01
Okay ... with some googling, I am trying testdisk. Next plan is to try photorec. Along with that, i will try scalpel also. The data is not something so important to take it to specialist, but it had all my personal photos, documents etc.

---

### Post by lukeiamyourfather on 2013-08-02
Good luck with it, also establish a backup routine starting now. Duplicity is pretty cool or if you like to do things from the terminal checkout the rsync command and cron.

---

