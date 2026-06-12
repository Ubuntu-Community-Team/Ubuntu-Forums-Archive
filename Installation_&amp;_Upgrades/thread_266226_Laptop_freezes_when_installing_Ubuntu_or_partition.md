---
title: "Laptop freezes when installing Ubuntu or partitioning"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by gspy on 2006-09-27
Hi,

I recently bought a SONY VAIO VGN-S660, and I have big problems installing Ubuntu 6.06. (I also tried SUSE 10.1, with no luck).

My problem is that when I load the live dvd and try to partition the disk, the computer freezes. The same happens if I try to install it to my hard disk. I've noticed that if I do an installation in text mode, then everything goes well, until I have to reboot the system without the dvd. Then it freezes again.

So the obvious problem is with the hard disk, but I don't know how to solve it! 

My specs are 

Intel Pentium M Processor (Centrino) 1.8GHz
NVIDIA GeForce Go 6400
Serial ATA Hard Drive 100gb

Thanks

---

### Post by cotcot on 2006-09-27
Can you be a bit more precise with "the computer freezes".
Do you see anything on the screen ? It could be that it freezes at the moment it starts X because of graphics card compatibilty for instance or that it freezes because the BIOS is not asked to check the HD for boot. 
Is the hd partition active (run "sudo fdisk -l" from the liveCD and see if you have a "*" before /dev/hda?

---

### Post by gspy on 2006-09-27
> **cotcot said:**
> Can you be a bit more precise with "the computer freezes".
Do you see anything on the screen ? It could be that it freezes at the moment it starts X because of graphics card compatibilty for instance or that it freezes because the BIOS is not asked to check the HD for boot. 
Is the hd partition active (run "sudo fdisk -l" from the liveCD and see if you have a "*" before /dev/hda?


When I do the partition or the installation, the image freezes after a while. So I cannot move the cursor and the progress bar is also frozen.

When I do the installation in text mode and I restart, the first time it takes some time to mount the root file system, then it manages to go until the login password, and then the image and cursor freezes again. If I switch off and restart, then the screen only gives some diagnostics and freezes again.

The last phrase is Uncompressing Linux... Ok, booting the kernel.

I did fdisk and there is a star is /dev/sda.

Thanks!

---

### Post by cotcot on 2006-09-27
I does not look as an X problem. 
/dev/sda is possible (you probably have a SATA hd in your laptop).
There are more issues like this with the Dapper CD. Try the Alternate install CD if you can get one. (it is on the same download page as the CD you have). Do a checksum and use it in text mode.

---

### Post by gspy on 2006-09-27
I tried the alternate installation CD, but the result is almost the same. This time the  screen froze right after the login.

---

