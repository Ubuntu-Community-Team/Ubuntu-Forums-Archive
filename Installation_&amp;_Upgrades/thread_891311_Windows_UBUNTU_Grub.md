---
title: "Windows UBUNTU Grub"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by Aragon12345 on 2008-08-15
Hey guys.

I have decided to install Ubuntu onto one of my partitions but i still needed windows XP. 

When i formated one of my drives a month ago i knew i was going to get around to installing Ubuntu so i left a 25gig section partition to do this and installed windows in the other partition. 

I also have another hard drive with windows XP 64 bit installed on it. This copy shows up on grub but is not the copy which i use. Its an old copy from my old 64 bit computer. 

When i installed Ubuntu i needed to enable ACHI for the hardrives to be detected by Ubuntu. Then Ubuntu installed and crashed at about 94% installation. Then i tried again and it worked properly this time with full working Ubuntu.

Now the windows XP home edition does not show up on GRUB and when trying to add it to the grub startup menu an error just occurs and it dosn't even try booting windows. 

My guess is the boot section for windows is corrupt or something along those lines. Is there any way to fix the boot section or is this another problem?

---

### Post by meindian523 on 2008-08-15
What is the error shown?

---

### Post by Aragon12345 on 2008-08-16
The Error is : Error 12: invalid Device Detected.

GRUB didn't pick up the installation for Windows XP Home Edition. This is what i wanted picked up but it never did. So what i did was added it to the GRUB list and that is the error received!

---

### Post by Aragon12345 on 2008-08-16
To help with this i also got Gparted working to have a look at the partitions. 
This is the list: 

Sda1 Linux Swap Space.
Sda2 is extended down to:
Sda6 which is ext3. Mount point /
sda5 which is ntfs where the Windows Installation is. No mount point.

---

### Post by Aragon12345 on 2008-08-16
Ok i noticed a difference between the two different windows installs. The one i want to work dosn't have AUTOEXEC.bat, boot.ini, bootex.log, CONFIG.SYS, IO.SYS MSDOS.SYS, NTDECT.COM, ntlrd.

In the base directory where they should be. Does this mean this windows is corrupt or is there a way to fix this?

---

### Post by cariboo on 2008-08-16
It would help us help solve your problem if in a Applications-->Accessories-->Terminal you typed:

```
sudo fdisk -l
```

and pasted the output in your next post.

Jim

---

### Post by Aragon12345 on 2008-08-16
Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1df61df5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         317     2546271   82  Linux swap / Solaris
/dev/sda2             318       36480   290479297+   f  W95 Ext'd (LBA)
/dev/sda5            3188       36480   267425991    7  HPFS/NTFS
/dev/sda6             318        3187    23053212   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
102 heads, 51 sectors/track, 281651 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      281650   732571624+   7  HPFS/NTFS

---

### Post by Herman on 2008-08-16
> sda5 which is ntfs where the Windows Installation is. No mount point.     A partition number of 5 or greater always represents a logical partition.
Normally, Windows can only boot in a primary partition unless the boot loader files are installed in a primary partition which has the boot flag. 
Did you delete another Windows? That one probably was your 'boot partition'.
> Ok i noticed a difference between the two different windows installs. The one i want to work dosn't have AUTOEXEC.bat, boot.ini, bootex.log, CONFIG.SYS, IO.SYS MSDOS.SYS, NTDECT.COM, ntlrd.That could be because when you installed Windows XP it detected another Windows installation so it set up a 'Microsoft dual boot', without warning you. That means it copied out it's vital boot loader files into the other Windows system, which you have since deleted. [MultiBooting Principles]("http://www.goodells.net/multiboot/principles.htm").

All is not lost though. You can get another copy of boot.ini, NTdetect.com and ntldr from some other Windows XP and paste them into the Windows XP you want to boot. You can also get those files from the CD you can download from this site:  [How to fix: NTLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").

The next problem is that some computers, (mine at least), have BIOSes that require Windows to have the boot flag on the Windows partition to be booted. 
Boot loaders don't seem to be able to set a boot flag on a logical partition.
You can either copy and paste your entire operating system into a primary partition with a partition editor like GParted or Gnome Partition Editor, then GRUB can manage the boot flag. 
Or you can use a partition editor to set a boot flag on the partition as it is and just leave the boot flag there.

---

