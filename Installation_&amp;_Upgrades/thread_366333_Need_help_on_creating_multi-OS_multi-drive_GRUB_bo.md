---
title: "Need help on creating multi-OS multi-drive GRUB boot floppy / CD"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by fable on 2007-02-20
I have three PC's with separate monitors and keyboards.  They are using up lots of space.  One has Ubuntu installed, one has Windows XP, and one has Windows 98.  The Ubuntu PC was installed with 6.06.  I have the Ubuntu machine for over one year using it frequently for web access, email and wordprocessing.  I still use Windows XP for financial applications and occassionally use Windows 98 for some old financial applications.  

I want to consolidate the 3 PC's into one machine. My plan is taking out the three IDE hard drives, put them into one P4 machines, and use multi-OS GRUB boot floppy or CD to select the boot drives.

I am not familiar with creating and customizing GRUB boot disk.  I did a search in this forum for "multi-OS GRUB" but did not find exactly what I need.

Can someone point my to the right direction or explain how I can create a multi-OS GRUB floppy or CD to access 3 separate drives with different OS's?

:)

---

### Post by dcstar on 2007-02-21
> **fable said:**
> I have three PC's with separate monitors and keyboards.  They are using up lots of space.  One has Ubuntu installed, one has Windows XP, and one has Windows 98.  The Ubuntu PC was installed with 6.06.  I have the Ubuntu machine for over one year using it frequently for web access, email and wordprocessing.  I still use Windows XP for financial applications and occassionally use Windows 98 for some old financial applications.  

I want to consolidate the 3 PC's into one machine. My plan is taking out the three IDE hard drives, put them into one P4 machines, and use multi-OS GRUB boot floppy or CD to select the boot drives.

I am not familiar with creating and customizing GRUB boot disk.  I did a search in this forum for "multi-OS GRUB" but did not find exactly what I need.

Can someone point my to the right direction or explain how I can create a multi-OS GRUB floppy or CD to access 3 separate drives with different OS's?

:)

You basically just need to use the Ubuntu drive as the boot device, and then manually add in some basic entries to boot the various Windows devices.

The actual designations will depend on how you set up your hardware, easiest thing would be to install all of the drives, boot Ubuntu and then use gparted to see the allocated drive (and partition) designations - then you will have some idea of what to put into Grub.

Just do a search for the numerous posts on booting Windows with Grub for detailed instructions on this sort of thing.

---

### Post by fable on 2007-05-07
After I manually tested the Grub commands for dual boot between Ubuntu and Win98, I created a menu.lst file with the manual commands I tested. I created a Grub floppy and copied the menu.lst file to this Grub boot floppy. Now every time I boot I can select the operating system using the Grub menu.  I also tried burning a floppy image into a CD and the boot CD works fine.

My simple menu.lst file contains the following commands:

```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/mapper/Ubuntu-root ro quiet splash
initrd		/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,0)
kernel		/vmlinuz-2.6.15-28-386 root=/dev/mapper/Ubuntu-root ro single
initrd		/initrd.img-2.6.15-28-386
boot

title		Windows 98
root		(hd1,0)
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
boot
```

---

