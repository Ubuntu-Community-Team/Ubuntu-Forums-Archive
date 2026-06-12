---
title: "[SOLVED] Partion &amp;quot;Locked&amp;quot; Drive?"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Rwild on 2008-01-14
OK.  Everything is in prime order on the Live Disk.  Now I am looking to install.  Thing is, the drive I am looking to make a new partition on has a symbol of a pad lock on it.  So, it it saying I can not play with the partitions on this drive.  

In a bind here because the drive I am looking to use has Vista on it.  But, I think I downloaded some questionable software and I can not do ANYTHING in the system once it starts.  

So, is there any way I can unlock this drive via the live disk?

---

### Post by logos34 on 2008-01-15
The lock symbol means it's mounted.  

Places>Computer>right-click on partition>unmount

Same thing if you are looking at it in gparted:  right click>unmount

But if you also need to shrink it down to make room for ubuntu, you should instead use Vista's own disk management tool.  Then boot the ubuntu live cd again and install in the freed space.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by JR Tyner on 2008-01-15
As for Visa, if you are only seeing your background when you load, Windows is not running Windows Explorer which is what handles all your folders and icons. A version of Windows that has trouble running Windows Explorer? Windows 3.0 had no problem with it. How stupid is Vista?

Try this. After Windows loads your desktop background, if it loads nothing else then hit Ctrl-Alt-Del and click on Start Task Manager when the blue screen comes up. Click on File in the upper left corner, then New Task (Run...) from the drop down menu, and type explorer into the field and hit ok.

---

### Post by Rwild on 2008-01-15
That's the thing... I can't do anything on Vista.  Everything I do bring's up a time out error... Even Crtl+Alt+Del.  So if I play with the partitions in Ubuntu, my Vists will be virtually unuseable... ever?

---

### Post by Partyboi2 on 2008-01-15
You could try one of these
[http://gparted-forum.surf4.info/viewtopic.php?pid=4450](http://gparted-forum.surf4.info/viewtopic.php?pid=4450)
[http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/](http://www.howtogeek.com/howto/windows-vista/using-gparted-to-resize-your-windows-vista-partition/)

---

### Post by Rwild on 2008-01-15
Thanks folks...  Everything worked out just fine using GParted. ;)

---

