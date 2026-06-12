---
title: "ntldr is missing"
date: 2005-02-23
forum: Installation &amp; Upgrades
---

### Post by movery on 2005-02-23
Please help!!!

Trying to get XP/Ubuntu dual boot up and running so did the following on my single 80GB drive:

 - wiped the drive completely
 - installed winxp from cd onto a 15GB partition at the start of the drive (everything works fine)
 - installed warty ubuntu from cd
 - created /boot (hda2), / (hda3), /home (hda4)
 - rebooted, got the grub menu, chose ubuntu and everything works fine
 - added the windows xp entry to menu.lst, rebooted and tried XP...got the message:

"ntldr is missing"

So far I have checked:

 - i have ntldr and ntdetect.com on the root of my c:
 - hda1 (xp) is the active partition
 - the grub entry is correct (i think):

title win xp
rootnoverify (hd0,0)
makeactive
chainloader +1
boot

I would boot from the xp cd and use the recovery console to fixmbr but cannot as when I try and boot from the CD it hangs if I have anything other than plain ntfs/fat partitions anywhere on my drive!!!

please please help.  this si getting very annoying!!  debian never did this to me... :(

Thanks,

---

### Post by wallijonn on 2005-02-23
[http://www.ubuntuforums.org/showthread.php?t=15934](http://www.ubuntuforums.org/showthread.php?t=15934) may help.

[http://www.ubuntuforums.org/showthread.php?p=73978#post73978](http://www.ubuntuforums.org/showthread.php?p=73978#post73978)

---

