---
title: "reinstall XP without affecting ubuntu"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by homer1976 on 2007-01-08
Hi

I have a duel boot (XP/UBUNTU/GRUB loader) machine.  I would like to reinstall my XP partition but I don't want to lose the bootloader as it will lock me out of ubuntu.

Does anyone know of a decent way to reinstall XP without losing my precious ubuntu?

TIA

Homer

---

### Post by meng on 2007-01-08
Can't be done, you just have to reinstall grub after installing windows.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by orb9220 on 2007-01-08
When xp installs it overwrites the mbr which the grub resides. After installing xp you will have to
restore the grub. [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

---

### Post by ajgreeny on 2007-01-08
Interestingly enough, I installed windowsXP over an existing install of windowsXP, without reformatting or anything, just to get back some system files that had been lost.  I was expecting to have to reinstall grub after doing that, but it wasn't needed, grub was still in place and worked straight away.  You , of course, may need to start again from scratch, which will remove grub, but itmis so easy to get it back with just a few commands in the terminal of a live CD, doesn't even have to be ubuntu live CD, any linux will do it, I used puppy, as it boots in a much shorter time than ubuntu or most full size live linux distros.

Boot into the (ubuntu) live CD
open a terminal and run :

sudo grub  (in puppy linux just "grub")

then:

find /boot/grub/stage1

replace the question marks in the following command with the output of the last command :

root (hd?,?)  If you have more than one linux install, use the one that you want the grub to run from.

[like : root (hd0,1) ,probably]
then:

setup (hd0)

and

quit

Reboot

---

### Post by orb9220 on 2007-01-09
> Interestingly enough, I installed windowsXP over an existing install of windowsXP, without reformatting or anything, just to get back some system files that had been lost. I was expecting to have to reinstall grub after doing that, but it wasn't needed

Only if you do a clean install if you do a repair or upgrade from within xp then I believe your grub
is safe.

---

