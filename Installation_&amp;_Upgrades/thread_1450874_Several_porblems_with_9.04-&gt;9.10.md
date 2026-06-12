---
title: "Several porblems with 9.04-&gt;9.10"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by shmeegull on 2010-04-09
Hey guys.  I've had several problems with Ubuntu ever since I upgraded to 9.10.  The first one was something about "filesystem could not be mounted."  I would boot up the computer and I would get that error message when I tried the latest kernel.  At the grub menu, I eventually found a kernel that would load, so I got into that.  However, everything was kinda hokey there, windows weren't loading properly, networking issues arose, etc.  I found several threads on here that offered help, so I tried them.  However, one of them just messed my system up even more.  It recommended editing my fstab file, so I did that.  I can find a link to the threads if necessary, but here's my current fstab:

> fstabn

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f2d530bd-7116-44bd-b36c-c4971e0dc023 /               ext3    errors=remount-ro,noatime,relatime,nodiratime 0       1
#defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=09e68f2d-b0ef-4429-b601-56bcc86256fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
/dev/sdb1    /media/tera   ext3    errors=remount-ro,noatime,relatime,nodiratime     0        2
#defaults,relatime     0        2
devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)Now, I think this is what it looked like before, but I'm not sure.  the "fstabn" looks suspicious to me, I can't remember whether it was there before or if I somehow managed to accidentally edit the file.

> 
fstabn

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f2d530bd-7116-44bd-b36c-c4971e0dc023 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda5
UUID=09e68f2d-b0ef-4429-b601-56bcc86256fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
/dev/sdb1    /media/tera   ext3    defaults,relatime     0        2
devpts /dev/pts devpts (rw,noexec,nosuid,gid=5,mode=620)So, after I made those edits and rebooted...nothing worked!  Which was kinda not my intention.  I'm not sure of the exact error it gave, but it failed after the grub menu.  I can recreate the error and post it here if someone would like me too.  Now, for reference, before I edited the fstab I also did a fsck and checked the UUIDs of all the drives.
I'm currently running off of a a liveCD, version 9.10.  Ideally, I would like it if I could somehow fix this and be running 9.10 like nothing happened.  However, if that is not possible I'd also be willing to do a fresh install of 9.10 and then migrate all of my data to it.  Now, this would mean that I would have to reconfigure all my settings, but as long as I can do this and keep all of my data intact, I'm okay with that, not pleased, but I would rather have a working OS than have to boot from a liveCD all the time.
So, my question is, how do I fix this (ya, I'm very specific, right?) and, barring that, can I do a fresh install of 9.10 while keeping all of my data?
Thanks for reading!

---

### Post by shmeegull on 2010-04-20
Hey guys, sorry for the double post, but since no one has responded, can I assume my system is now useless and I should just do a clean install?  If I had to do a clean install, is there any way to transfer my preferences and programs, this way I wouldn't have to reconfigure everything?

Thanks

---

