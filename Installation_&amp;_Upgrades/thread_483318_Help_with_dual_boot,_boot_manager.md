---
title: "Help with dual boot, boot manager"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by cytg on 2007-06-24
problary trivial however a search doesnt quite clear it up for me, and i have an idea of what to do .. i just dont wanna mess up my windows install. Just yet anyway ;)

sda is 300G data storage ntfs
sdb got XP on 74G raptor
sdc 500G disk bought for linux, got a default ubuntu install right now 7.04

So after the installation, i get the regular bootmenu, a couple of windows install on sdb and no option to boot ubuntu
The HP machine doesnt allow me to change boot drives, only option is to boot C: (or cdrom or eth etc.), so i cant accees my new install this way.
I figure i gotta lilo or grub the boot partition and edit this to boot both ubuntu and xp .. but not quite sure how to go about it ... if i do it wrong, ill have no access at all.
And if im reading this correctly (off gparted) my boot partition is really on sda wich then allows me to boot sdb wich has the XP?

So what do i do to not f... it up ? ;)

---

### Post by fumduck on 2007-06-24
I think basically  what you have to do is this...
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

try this guide it might help also..

[http://apcmag.com/dualboot]("http://apcmag.com/dualboot")

---

### Post by madzieph on 2007-06-25
Check out my experience with dual-boot [here]("http://ubuntuforums.org/showthread.php?t=482051").

---

