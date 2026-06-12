---
title: "In a messy situation. Ubuntu upgrade."
date: 2010-11-10
forum: Installation &amp; Upgrades
---

### Post by vivek_12315 on 2010-11-10
Here is the condition of my laptop:

Initially it had:

ubuntu 2.18
Windows XP.

While upgrading on internet my ubuntu, laptop got shut down. Though kernel version was upgraded as shown in grub but things didnt work well and older version of ubuntu also got corrupted.

So, i installed WUBI from within windows...

Now when i power on, i get :

Grub 1 list

> goto Windows option
> windows loader shows windows , new ubuntu (by WUBI)
> select WUBI one

Grub 2 list: (which shows all the OSes on my laptop)

Now, is there a way by which I can totally remove my old ubuntu and use that space by the new ubuntu installation ? Will WUBI support extension in space ?

---

### Post by Bucky Ball on 2010-11-10
Ubuntu 2.18???? Are you talking about the Linux kernel version? What Ubuntu _*release*_ is it?

Your much better off just downloading the latest ISO and installing and doing manual partitioning, which means you just leave your windows install alone. Ubuntu will pick up its there and add it to the menu at boot. That easy. Wubi can be problematic.

This way you just install the new one where the old one is, go to Windows and uninstall Wubi.

---

### Post by vivek_12315 on 2010-11-10
> **Bucky Ball said:**
> Ubuntu 2.18???? Are you talking about the Linux kernel version? What Ubuntu _*release*_ is it?

Your much better off just downloading the latest ISO and installing and doing manual partitioning, which means you just leave your windows install alone. Ubuntu will pick up its there and add it to the menu at boot. That easy. Wubi can be problematic.

This way you just install the new one where the old one is, go to Windows and uninstall Wubi.

The primary reason i went for WUBI is becoz my cdrom is not working and by BIOS doesnt has option for boot from USB ...

WUBI is latest release.

Old ubuntu is 8.xx release.

---

### Post by sikander3786 on 2010-11-10
> BIOS doesnt has option for boot from USB ...

If you've got a working floppy drive, you can use plop to boot a USB drive.

[http://tipsfromgeek.com/2010/07/boot-from-usb-device-even-if-not-supported-by-the-bios.html](http://tipsfromgeek.com/2010/07/boot-from-usb-device-even-if-not-supported-by-the-bios.html)

[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

If you could somehow setup Ubuntu in a true dual boot to Windows, it would be far more stable and will perform lot better than Wubi.

---

### Post by Bucky Ball on 2010-11-10
> **sikander3786 said:**
> 

If you could somehow setup Ubuntu in a true dual boot to Windows, it would be far more stable and will perform lot better than Wubi.

+1. It will also pick up Windows and rewrite the bootloader and you're in business.

---

### Post by bcbc on 2010-11-10
> **vivek_12315 said:**
> 
Now, is there a way by which I can totally remove my old ubuntu and use that space by the new ubuntu installation ? Will WUBI support extension in space ?

Yes you can remove the old ubuntu. First reinstall the windows bootloader (on XP run fixmbr, on Vista/7 run 'bootrec.exe /fixmbr') or from ubuntu run:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
This will give warnings about booting linux that don't apply. You should also check that the boot flag is still set on your windows partition. This is important with a windows-style bootloader:
```
fdisk -l
``` (small L)

Then you are free to reuse that Ubuntu partition - you can format it ext2/3/4 and mount it from wubi - or format as ntfs and share it on wubi/windows.

OR,
you can actually migrate your wubi install to the old Ubuntu partition which is what I would do. So that will keep your current brand new ubuntu but in the traditional dual boot, removing the need for a virtual (wubi) disk. [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Bucky Ball on 2010-11-10
Why bother removing the old Ubuntu? Shove in a fresh install CD and install straight over it when you set up manual partitioning. 

Just don't touch the Windows partition; it will be marked as NTFS. DON'T TOUCH any of the NTFS partitions. 

As mentioned, the install will pick up the Windows 7 install and add it to your choices at boot. That easy.

---

