---
title: "not cleanly ununmounted???"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by Saponsky09 on 2007-08-17
I'm getting this message every time I try to boot Ubuntu: 
> fsck 1.40-WIP (14-Nov-2006)
/dev/sdb1 was not cleanly unmounted, check forced.
Then it starts checking my disk but it stops at 74.6% and nothing more seems to happen, I waited a while but nothing.  Last time I couldn't unmount sdb1 propertly because I was using my LiveCD to edit some files but the CD has never let me reboot propertly so that's why I thinkk I get this message, is there any way to get pass this message? Or any way to solve this? Thanks in advance for your help!

---

### Post by Pumalite on 2007-08-17
I'm afraid you might have files corrupted. Use Rescue CD to check your system and hard drive: [http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by Saponsky09 on 2007-08-17
I did a little research and find out that the problem is that when you rebuild the file system is marked as "dirty" and fsck runs at every boot so you have to run a command to fix it.
The post says that this command is:> rdev -R/zImage 1
I'm not sure if this works but I'll try it anyways.

---

### Post by Pumalite on 2007-08-17
Let us know how it goes.

---

