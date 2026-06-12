---
title: "Editing GRUB Files"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by Kerry Lange on 2006-11-01
Frustrated newbie here.

I've been trying for a week to get Ubuntu working properly on my machine without success.  In dealing with an XP dual boot situation , a RAID, and the fact Grub always gets installed on the first hard drive (despite the fact it's part of a RAID and craps out my XP boot loader), I finally disconnected all my drives, except the one I wanted to use with Ubuntu.

Installation went fine and I booted from the hard drive while only the one drive was connected.  As soon as I connected the other three drives, Grub no longer knows where everything is and I'm left with a "busybox" shell prompt early on in the boot process.

So, I'm looking for advice on how to edit the Grub boot files to see if I can get it to point to the correct drives.  One person suggested editing the "menu.lst" file and another person suggested editing the "/boot/grub/device.map" file.

Do I need to edit one or both of these files?  Where do I find "menu.lst?"

BTW, I downloaded and tried "Super Grub Disk", which looks like a great tool, but I'm afraid I don't know enough that I can use it effectively.

---

### Post by davidsolar on 2006-11-01
I'm a new dude myself, but this is what I wrote to edit the file: 
First line for backup ofc =)

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
gksudo gedit /boot/grub/menu.lst
```

But dont know how to add the other disk and such. Mounting is still a blurry area for me =)

---

### Post by Kerry Lange on 2006-11-01
Thanks, that's helpful.  It would be great to know how to add the other devices as well; however, I'm more concerned about just getting it to boot right now.

---

### Post by randyh on 2006-11-01
This may help?
 [https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html](https://help.ubuntu.com/ubuntu/desktopguide/C/partitions-booting.html)

Randy

---

