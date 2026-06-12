---
title: "Root Login Lost 2.6.26-2-686"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by ChrisRob300 on 2010-02-01
Hi

I have logged on  as chris; sudo su to get root access.  I have done:
apt-get update
apt-get upgrade

my previous versions of ubuntu have been removed from the grub menu.

I can not now log on as chris and sudo su to root from ssh.  It says I am missing from sudoers file.

Is there an easy way to fix as I can not access the master screen and will have to talk my wife through the changes required.

Chris

---

### Post by solar george on 2010-02-01
Ok, you can try (or rather get your wife) to reboot into single-user mode from the grub menu.

Then you should be given the option to access a root shell (not sure exactly what it would be called as i don't have a machine handy to test this on).

Then:
```
nano /etc/sudoers
```
add the following line to the end of the file
```
chris ALL=(ALL) ALL
```
I'm not sure if theres an easier way than this but i'm sure it will be possible to explain somehow.

---

