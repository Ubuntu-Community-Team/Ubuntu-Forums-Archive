---
title: "Windows 7 showing as windows 8 in grub"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by chromium1 on 2013-04-12
Hi, i just installed ubuntu alongside windows 7.
I created a 1gb swap, and a 100gb ext4 partition to install ubuntu to. My windows partition is 365gb.

Just before i installed ubuntu, i had deleted my previous install of windows 8 (which i was dualbooting with win7).
I removed the win8 entry from the msconfig of win7, and then deleted the partition win8 was on. 

Now when my pc turns on and goes into grub, it shows my win7 entry as win8. Any ideas why?
Not really too much of any issue, but any help would be great. Also is it possible/recommended to switch back to the win7 bootloader instead of grub?

Thanks.

---

### Post by Mark Phelps on 2013-04-12
Windows 8 uses a different boot loader from Windows 7, but like previous versions, when you install Win8 to a PC already containing Win7, it updates the boot loader for Win7.  So, even though you removed Win8, you still have the Win8 boot loader in place.

You could boot into Ubuntu and run "sudo update-grub" and see if it updates the Windows grub entry -- but I suspect it will still say Win8.

To replace the Win8 Boot Loader with Win7, use the Startup Repair option in Win7.  You may have to do that several times.  That will also remove GRUB from the MBR of your hard drive.

---

### Post by chromium1 on 2013-04-13
> **Mark Phelps said:**
> Windows 8 uses a different boot loader from Windows 7, but like previous versions, when you install Win8 to a PC already containing Win7, it updates the boot loader for Win7.  So, even though you removed Win8, you still have the Win8 boot loader in place.

You could boot into Ubuntu and run "sudo update-grub" and see if it updates the Windows grub entry -- but I suspect it will still say Win8.

To replace the Win8 Boot Loader with Win7, use the Startup Repair option in Win7.  You may have to do that several times.  That will also remove GRUB from the MBR of your hard drive.

Thanks.
What about using easybcd through windows to re write the mbr, then later adding an entry for ubuntu? Would that work?
Heres a tutorial i found:[http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/](http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/)

---

### Post by Mark Phelps on 2013-04-13
Don't know how EasyBCD works in that respect. I do know it has a feature to "rewrite" the MBR, but I don't know where that information comes from.

If Win7 is still working OK, you could use the Backup feature to create and burn a Win7 Repair CD, and run Startup Repair from that -- but that will overwrite the MBR in the process, and while that repairs Win7, you will then have to reinstall GRUB to the MBR.

---

