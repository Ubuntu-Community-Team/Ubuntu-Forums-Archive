---
title: "desktop disposal"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by kcs636 on 2012-09-28
I am disposing of my Ubuntu older Natty system, and have performed a wipe.
When it boots I'm at the 
error: unknown filesystem.
grub rescue>

This doesn't feel like a system that is safe to donate....

Do I need to do more to finish off this system? 

thanks

---

### Post by sidzen on 2012-09-28
Suggest using [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/"), booting to it and, at the multi-colored prompt on the page asking the user to enter either "wizard" or "startx," type the dd command which will wipe the entire hard drive with zeros.  Either that or discover which partition still exists and wipe only it.

[PHP]dd if=/dev/zero of=/dev/sdaX bs=4096 conv=notrunc,sync[/PHP]

where the capital X is the partition number (leave it off to wipe entire hard drive)

---

### Post by kc1di on 2012-09-28
> **kcs636 said:**
> I am disposing of my Ubuntu older Natty system, and have performed a wipe.
When it boots I'm at the 
error: unknown filesystem.
grub rescue>

This doesn't feel like a system that is safe to donate....

Do I need to do more to finish off this system? 

thanks

by simply erasing he OS and formatting the drive you are not destroying the actual data.  formating only erases the location indicators on the H.D but all most all of the date survives.

If you want the disc to be completely clean down load and run boot and nuke.  here :[http://www.dban.org/]("http://www.dban.org/")

---

### Post by sidzen on 2012-09-28
@[kc1di]("http://ubuntuforums.org/member.php?u=1839") 
FYI dban is included in SysResCD

---

