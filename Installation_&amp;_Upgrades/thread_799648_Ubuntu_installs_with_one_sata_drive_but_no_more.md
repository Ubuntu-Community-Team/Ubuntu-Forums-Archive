---
title: "Ubuntu installs with one sata drive but no more"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by Whaines on 2008-05-19
I am able to install ubuntu with no problems onto a single sata drive in a separate partition from the windows install but if there is more than one drive in the computer it will not load up the live cd or allow to install.  

It also will not boot up if I connect the other SATA drives after the install but runs fine if the drive is by itself.  Trying to boot with multiple dives attached goes to the Ubuntu loading screen with the progress bar forever bouncing back and forth with no hard drive activity. 

I believe it is getting hung up on grub, but I cannot be sure.  

What do I need to do to allow the other SATA drives connect?  All of them work fine in Windows.

Thanks, let me know if you need more information.

-Whaines

(Please don't make me go back to Windows!)

---

### Post by cdtech on 2008-05-19
Sounds like a conflict with the drive numbering scheme. I would boot into Ubuntu and edit the menu.lst to just include the Ubuntu disk then install the drives, boot and find out from Ubuntu the drives installed then edit the menu.lst to include these.

Just a thought.......

---

### Post by Whaines on 2008-05-19
I don't see anything in the menu.lst about hardware.  The only disks that has an operating system is the Ubuntu/Windows disk.  The others are just storage.  I'm new to linux so I could just be missing something obvious.

---

