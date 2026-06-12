---
title: "Hardy Live CD - denied permission to all disks"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by jonboy99 on 2008-04-27
Aaargh, this is driving me nuts.  I'm testing out the feasibility of upgrading to HArdy using the live cd on my mothers computer (currently running dapper).  
The wireless card requires ndiswrapper - shouldn't be  a problem.  The issue is that the liveCD is saying I don't have permissions to read any hard disks (apart from the root file system) so I can't get the wireless card drivers into the system.
It's saying I don't have permissions to read any fat32 drives, the ext3 partitions from the dapper install or indeed any usb sticks!  
I can browse the directories but when I try and copy any files onto the liveCD desktop, I get permission denied.  Using nautilus as su (ie sudo nautilus) doesn't change this at all!

I'm wondering if i've downloaded a dodgy livecd becasue I have to manually edit sources.list to accesss the universe main repos, but does anyone have a fix for the permissions issue?

Thanks
Jon

---

### Post by jonboy99 on 2008-04-27
ok, rebooted now and all working perfectly.  Sigh.

---

