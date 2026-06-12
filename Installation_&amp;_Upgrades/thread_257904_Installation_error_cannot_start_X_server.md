---
title: "Installation error: cannot start X server"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by zuccs on 2006-09-15
hey,

I was attempting to dual boot xp/ubuntu and I have a brand new graphics card (albatron - nvidia geforce 7600) and cannot continue the ubuntu installation as I get a message similar to:

Cannot start X Server. And something about GDM also. 

I have done a lot of searching for it and cannot find a fix. I figure it is a problem with my new graphics card and does not have any drivers to suit it. I tried:

```
sudo apt-get install nvidia-glx
```

...but that did not fix it. I am currently running XP okay on my partioned hard drive, but the other half is a corrupted install of ubuntu 6.06.1

In another unrelated problem, I am also trying to run a SATA hdd as a secondary hdd. It is found in CMOS but windows (and possibly ubuntu?) refuses to show it? The disc I have with it does not boot on startup. It says not a system disk, please remove and continue. Any ideas with this one?

Thanks a lot for any help!
-zuccs

---

### Post by Paul41 on 2006-09-15
Try to run this to reset your xserver configuration to see if that helps.
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by zuccs on 2006-09-15
Ok I found a way to install Ubuntu.

I just had to select "Boot in Graphics Safe Mode", now it is all going.

I might have fixed the SATA problem too. Not sure yet.

---

