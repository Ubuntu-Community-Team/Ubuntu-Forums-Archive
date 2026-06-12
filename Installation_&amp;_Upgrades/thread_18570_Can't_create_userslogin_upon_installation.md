---
title: "Can't create users/login upon installation"
date: 2005-03-07
forum: Installation &amp; Upgrades
---

### Post by emtilt on 2005-03-07
I'm setting up a dual boot with Win2K, with two hard drives (Win2k on the master, Ubuntu on a slave). I am putting GRUB on the second hard drive and leaving the Windows Boot Manager intact, and just pointing it to GRUB. Did the initial installation smoothly, and then rebooted to finish the configuration of ubuntu. Everything went fine, until the part where you create a user account. I enter the information, but after entering the password I want, an error flashes by (too quick for me to read it). It keeps prompting me to create an account and this process repeats endlessly. If I quit the configuration and try to get into Ubuntu, I can't login. I have tried installing three times and have encountered this problem each time. Any idea whats going wrong?

---

### Post by hal8000 on 2005-03-07
[QUOTE=emtilt]I'm setting up a dual boot with Win2K, with two hard drives (Win2k on the master, Ubuntu on a slave). I am putting GRUB on the second hard drive and leaving the Windows Boot Manager intact, and just pointing it to GRUB. Did the initial installation smoothly, and then rebooted to finish the configuration of ubuntu. Everything went fine, until the part where you create a user account. I enter the information, but after entering the password I want, an error flashes by (too quick for me to read it). It keeps prompting me to create an account and this process repeats endlessly. If I quit the configuration and try to get into Ubuntu, I can't login. I have tried installing three times and have encountered this problem each time. Any idea whats going wrong?[/QUOTE]
 Just a thought, when you enter the password for your account, the characters are not echoed
to the screen. If you are unaware of this, this may be your mistake. I would try again, once created you can always alter your password from the terminal with the command passwd

---

### Post by emtilt on 2005-03-07
[QUOTE=hal8000]Just a thought, when you enter the password for your account, the characters are not echoed
to the screen. If you are unaware of this, this may be your mistake. I would try again, once created you can always alter your password from the terminal with the command passwd[/QUOTE]
Yes I am aware of that. The problem, I believe, is not at the login, but rather that the user acounts are not getting created in the first place, and because of this I can't get in. I am really eager to get this working, so any more advice from anyone will be much appreciated.

---

### Post by dewey on 2005-03-07
Many installation problems can be traced back to bad cds.  If you downloaded and burned the iso yourself, ensure the iso is intact, by comparing md5 checksums, also burn it at a 16x maximum speed, just to be on the safe side.  I've made many a coaster because of burning too fast.

---

### Post by oti on 2005-03-08
I had this exact problem, on one installation. Doing the installation again onto a freshly installed partition ( i was using ext3 in all cases ) worked fine. Make sure you are formatting your partition when you reinstall.

As someone else said it may be bad CD's, and mine just didn't read properly that one time.

---

### Post by emtilt on 2005-03-09
I reburned the CD, which passed all checks, and tried again. Repartitioned the drive and everything. Then I had the same problem again. Can't get past that part. I manage to get a glimpse of the errors returned after it asks for a password for the new user, and I *think* it says (where {user} is the user name that I entered in the previous step):

```

groupdel: group  {user} does not exist
chpasswd: line 1, unknown user {user}
chpasswd: error detected, changes ignored
``` 

Anyone got any advice? I'd really like to get this resolved.

---

### Post by emtilt on 2005-03-10
No ideas? I'm out of things to try, so I guess I'm just gonna have to give up on Ubuntu and go back to a different distro.

---

### Post by n64man120 on 2005-04-23
Bump for same exact problem!!!

---

### Post by Jemonster on 2005-11-30
I had the same problem, tried to reinstall twice from the same cd before I gave up and started hunting for info. I reburned at 16X and closed the disk. I deleted the partitions and just installed Kubuntu how it wanted to be installed. Works like a charm now!

---

