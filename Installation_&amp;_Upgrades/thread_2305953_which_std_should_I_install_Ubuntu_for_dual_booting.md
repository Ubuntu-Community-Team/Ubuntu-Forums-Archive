---
title: "which std should I install Ubuntu for dual booting"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by springwater2015 on 2015-12-10
Hello,

I already have Windows 7 installed in my PC. My computer has two internal harddisks: one is master, the other is slaver. Windows 7 is installed in the master one. 

Now I want to install Ubuntu and want the PC to be dual-bootable. I see that Ubuntu names the master harddisk as stda and the slaver harddisk as stdb. Should I install Ubuntu on the master harddisk (i.e. stda which has already Windows 7) or to the slaver one (i.e. stdb).

What are the advanatages of the first choice (on stda) over the second choice (i.e. on stdb)?

Thanks,

---

### Post by oldfred on 2015-12-10
Is your IDE so old that only the master is bootable?
Newer IDE have cable select with 80 conductor cables & different jumpers on drive for cable select instead of master/slave.
And if system is that old Ubuntu will not run. Lubuntu would be a much better choice. But how much RAM and what video card/chip?

I prefer to keep one drive Windows and other Ubuntu, but many with laptops & one drive install both to the one drive. But not much of an advantage to have Ubuntu on sdb, unless you can directly boot sdb from BIOS.

Most newer systems are SATA, not IDE anymore.
 with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
[http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1](http://en.wikipedia.org/wiki/Parallel_ATA#IDE_and_ATA-1)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

   If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by grahammechanical on 2015-12-10
There is something else to keep in mind.

If the BIOS boot system is set to sda then if all you have on sda is Windows then you will not get an option to load Ubuntu as the Windows boot loader will not recognise Ubuntu. If you install Ubuntu on sda then the Ubuntu boot loader will overwrite the Windows boot loader but you will have options to load either Ubuntu or Windows.

If you install Ubuntu on sdb then disconnect sda for the period of the installation because the Ubuntu installer will default to installing its boot loader (Grub) into the MBR of sda. We can force the installer to install Grub into sdb but that is a more complicated install process. With only one hard disk present the installer will put Grub the only place it can.

After installation reconnect sda and set the BIOS to boot from sdb and it should load Ubuntu. Then when Ubuntu is laoded run this command

```
sudo update-grub
```

That should reconfigure the Ubuntu boot loader to detect Windows  and then by booting from sdb you will get a choice of booting either Ubuntu or Windows. If anything goes wrong with Ubuntu you can then always load Windows by changing the disk that the BIOS boots from.

Regards.

---

