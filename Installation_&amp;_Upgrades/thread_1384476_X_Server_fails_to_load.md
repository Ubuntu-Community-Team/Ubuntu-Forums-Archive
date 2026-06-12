---
title: "X Server fails to load"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by tevang on 2010-01-18
I had a dual boot Kubuntu 9.04 - FC 11 and decided to upgrade to Kubuntu 9.10. Recalling that I had issues with my ATI card drivers when I installed Kubuntu8.10 on my laptop, I decided to install the latest ATI Catalyst drivers. After the installation was complete I received a message warning me that if the X server fails to load I should run "aticonfig --initial -f". Indeed the X Server didn't load (after I logged in the screen flushed and went black). So I reinstalled Kubuntu 8.10 from a CD I without formating the respective partition. But the problem perists, X server fails to load. Even worse my menu.lst file has been changed and I can't boot FC11. Please help me rescue my system!!!!!!

---

### Post by kseise on 2010-01-18
Don't panic.  Can you plug your monitor into your onboard graphics port?  If so, you should be able to get into the recovery mode.  Once you are in, try this:
```

cd /opt/X11
mv xorg.conf xorg.conf.bad
init 6

```

Once it reboots, the system will generate a new xorg.conf and you should be back to square one.  You can also use a live CD to get in and make the same changes.  Use mv instead of deleting the file.  If that makes it worse, you can use mv to move it back like this:
```
mv xorg.conf.bad xorg.conf
```

---

### Post by tevang on 2010-01-18
I selected the recovery mode at GRUB Menu on startup. /opt/ directory is empty but there is a /etc/X11/xorg.conf which is renamed. That didn't make any difference, I get up to the login menu and when I log in the screen flashes and turned black!

---

### Post by kseise on 2010-01-18
My bad.  You are right.  Follow my instructions in /etc/X11 instead.  I had the wrong directory.  Even if there is a renamed file, follow my instructions and let us know how you make out.

---

### Post by tevang on 2010-01-18
I already did that with no result (typo: "I renamed" instead of "is renamed").

---

### Post by tevang on 2010-01-19
???

---

### Post by tevang on 2010-01-19
Anyone please???????????

---

### Post by kseise on 2010-01-20
OK, try this from the recovery console.

```
sudo dpkg-reconfigure xserver-xorg
```
Then reboot and tell me if that worked.  

Sorry for the delay, I wasn't notified that you had replied.  Sometimes I hate computers.

---

### Post by tevang on 2010-01-22
No it didn't work.

---

