---
title: "Help with grub configuration"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by spiderbaby on 2008-05-13
Hi,

I've got a newbie grub problem if anyone can help.

I'm running a dual boot system with Windows XP on a master IDE drive (installed on the primary partition) and Ubuntu on a SATA drive connected using a PCI SATA adapter. I set up grub to allow dual boot which works when both drives are connected but which fails when the SATA drive is disconnected. I do disconnect this drive periodically and am trying to get grub to work when the drive is missing.

I'd like to get grub to allow me to boot into the Windows drive regardless of whether the SATA drive is connected to the PC. I think this should be possible but I've no experience in configuring grub and would appreciate any help.

Thanks,

Spiderbaby

---

### Post by spiderbaby on 2008-05-13
Sorry, I forgot to add some more details.

The output of "fdisk -l" is:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       14593   117170077+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       13054   104856223+   7  HPFS/NTFS
/dev/sdb2           18057       60801   343349212+   f  W95 Ext'd (LBA)
/dev/sdb3   *       13055       18056    40178565   83  Linux
/dev/sdb5           18277       34072   126881338+   7  HPFS/NTFS
/dev/sdb6           34073       47126   104856223+   7  HPFS/NTFS
/dev/sdb7           47127       60180   104856223+   7  HPFS/NTFS
/dev/sdb8           60181       60801     4988151    7  HPFS/NTFS
/dev/sdb9           18057       18276     1767087   82  Linux swap / Solaris

Partition table entries are not in disk order
```

The Windows partition lives on /dev/sda2.

---

### Post by housam on 2008-05-13
Read this [[COLOR="Red"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=781957&highlight=usb+drive") , it has the solution to your problem.

---

### Post by logos34 on 2008-05-13
> **housam said:**
> Read this [[COLOR="Red"]_thread_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=781957&highlight=usb+drive") , it has the solution to your problem.

That thread is about Vista and EasyBCD.  The OP has XP.

spiderbaby,

The problem is grub overwrote the windows bootloader on the ide drive, but the menu.lst is on the sata (in /boot/grub).  When you remove the drive it can't find menu.lst. 

One solution is to restore windows bootloader to ide disk and grub to mbr of the sata, then select the boot drive in the Bios at startup. (in which case you'll have to edit 'root' lines in menu.lst).

I think the easiest solution in your case is to use XP to boot linux.  Try [WinGrub]("http://users.bigpond.net.au/hermanzone/p9.html").  It will edit boot.ini and everything for you. Restore windows bootloader with the XP install cd:

-boot into Recovery Console (->press 'R')
-at the prompt type **fixmbr**

Or use the **Super Grub Disk**

---

### Post by spiderbaby on 2008-05-13
Thanks for the quick replies. :)

I'll try using WinGrub (hopefully tonight) as logos34 suggested and let you know how it went.

---

### Post by spiderbaby on 2008-05-13
I ran fixmbr in the recovery console which reverted me back to a Windows boot but the bootup hung trying to load the agp440.sys service. However, I think this problem is fairly specific to my PC - my SATA PCI adapter works some of the time but it arbitrarily fails to pick up the SATA drive (at this stage, I think it's a conflict with an interrupt or between the motherboard BIOS - which is old - and the PCI adapter). In these particular boots, the SATA drive was not picked up; otherwise, I think the boot would have succeeded. This seems similar to Windows boot problems people have reported when USB keys are left plugged in during boots.

Anyway, I plugged out the SATA drive and my PC booted into Windows perfectly. This is all I want for now since I'll be upgrading soon. 

Thanks for the help - I can now at least boot into Windows regardless of whether the adapter acts up. I hadn't overwritten the MBR before since I was unsure whether I would be able to recover my Ubuntu installation but I'm sure your suggestion of using WinGrub will work. When I have some free time at the weekend, I'll mess with the SATA adapter until it gets picked up on boot and then try WinGrub. I'll post back on how that goes.

---

### Post by spiderbaby on 2008-05-20
I tried WinGrub like logos34 suggested and it worked like a charm! Thanks for the help.

---

