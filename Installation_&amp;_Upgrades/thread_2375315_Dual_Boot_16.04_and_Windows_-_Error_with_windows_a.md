---
title: "Dual Boot 16.04 and Windows - Error with windows after updating"
date: 2017-10-23
forum: Installation &amp; Upgrades
---

### Post by hoactzin on 2017-10-23
Hey y'all, first post. Woo.

So about a week ago I managed to get my ubuntu / win10 dual boot working after a pretty fraught period with my Inspiron 15 laptop. It seemed to be working fine for a while until my computer updated windows for the first time since I got ubuntu. Now when I boot up my computer:

-It goes from the dell screen into GRUB, which is nice, and I can select windows 10, but.
-When I select windows 10 it either stays on ubuntu's blank purple startup screen or
-goes to black, and then goes back to GRUB without displaying an error message.

Also, whenever I try to run the recommended repair on boot-repair it hangs and freezes my computer while it's scanning my system. I originally installed boot-repair when windows 10 didn't show up in grub, and it did the same thing. After I restarted it then, however, windows 10 appeared on the menu and I figured that it was probably best not to mess with something that apparently worked now. 

If there's more information that I could/should provide, I'd be happy to give it. The boot-repair link is pasted below, but I want to check here before I do anything else that might mess up whatever's happening here.

[http://paste.ubuntu.com/25804739/](http://paste.ubuntu.com/25804739/)

Thanks, y'all!

---

### Post by yancek on 2017-10-23
You have two windows entries in the grub.cfg menu.  Do they both fail?  One points to the boot partition and the other to the system partition.

---

### Post by hoactzin on 2017-10-24
Uh, to be honest, I've only ever tried the first one. 

This morning my windows install reverted the updates and so now both are working again? I don't even know. 
Also this morning, I remembered that I have a 4-year-old asus laptop that I don't use anymore, so I might just install ubuntu over that and get rid of it on my current laptop. Seems like a good way of not having to worry about dual booting.

---

### Post by oldfred on 2017-10-24
Windows on updates usually turns fast start up back on. That must be off and is probably why you are getting this in Boot-Repair.
> The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /mnt/boot-sav/sda2

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

