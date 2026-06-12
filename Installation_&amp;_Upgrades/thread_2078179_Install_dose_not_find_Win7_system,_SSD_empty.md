---
title: "Install dose not find Win7 system, SSD empty?"
date: 2012-10-30
forum: Installation &amp; Upgrades
---

### Post by PendragonUK on 2012-10-30
I have been using Ubuntu for a number of years, installed on countless machines. I have become so used to the install being easy I had forgotten about things like this...

I want to install 12.04 LTE 64bit on my main gaming rig in preparation for the upcoming fun and games, valve and the like. 

I have Windows 7 installed on an SSD and a 1TB mechanical drive that I have made some space on for the Ubuntu install. I want to duel boot between the two OS's

Booting from a USB stick into the live desktop, click on install and it fails to see Windows 7 and reads my SSD to be empty. I can mount the volumes outside the installer and see the contents of the drives. However the installer can not see inside the SSD. 

As this is a test to see the gaming performance in Ubuntu I'm not willing too mess to much with my Windows 7 instillation right now. If things work out then yes I will wipe the system and configure it differently...

System Spec:
Intel i7 3930K @4.5GHz
Quad channel DDR3 2133MHz 16GB
MSI X79A-GD45
SSD 256GB (Windows 7 64bit)
1TB mechanical (800GB NTFS + 120GB empty for Ubuntu)
2X XFX R7970 Crossfire

---

### Post by darkod on 2012-10-30
If the ssd has been used in fakeraid before (maybe to test lightning fast sd raid speeds) it still has meta data remains. Windows ignores this, but ubuntu doesn't.

Since one ssd is clearly not running in raid now, try to remove any possible meta data from live mode with:
sudo dmraid -Er /dev/sda

If the ssd is /dev/sdb adjust the above command. If that asks you if you want to remove the meta data, it means it found it. Just confirm and you're good to go.

---

### Post by PendragonUK on 2012-10-30
Thanks for your suggestion but the drive has never been part of a RAID set up. I did try the command but it did not work saying something about no RAID detected...

There is something about this disk that stops it being discovered on install...

---

### Post by darkod on 2012-10-30
Hmm, in that case double check the cables, and also try it in another sata port. If it still doesn't get detected, there might be some problem with it.

---

### Post by PendragonUK on 2012-10-30
This may help :) GPD Grrrr I'm going to need some help here...

> ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd4a28c55

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   500115455   249954304    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065d12

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1689991167   844994560    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     7821311     3910640    b  W95 FAT32
ubuntu@ubuntu:~$ 


---

### Post by darkod on 2012-10-30
Yeah, you found it. :)
The disk had GPT table before but later it was converted to MSDOS with windows. However windows doesn't delete the backup gpt table and linux can see it, creating confusion whether the disk is msdos or gpt.

Use fixparts and it will safely delete the backup table without any data loss. Only open it with fixparts and it will offer to do it for you, something like:
sudo fixparts /dev/sda

You can get fixparts here, including for windows I think:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by PendragonUK on 2012-10-30
Woot!


[[IMG]http://img820.imageshack.us/img820/3212/screenshotfrom201210301.png[/IMG]]("http://imageshack.us/photo/my-images/820/screenshotfrom201210301.png/")

Fixparts did the trick...


Thank you :)

Just have to make sure Ubuntu installs in the empty space on sdb ;)

---

### Post by darkod on 2012-10-30
Ubuntu usually installs automatically into the biggest unallocated space.

But for best control, including a choice where to install the bootloader on a system with multiple disks, I always recommend the manual install (Something Else). It gives you total control what goes where.

---

### Post by PendragonUK on 2012-10-30
Me thinks the boot loader didn't go where it should LoL

[[IMG]http://img696.imageshack.us/img696/2579/damnhj.jpg[/IMG]](http://imageshack.us/photo/my-images/696/damnhj.jpg/)

Got to admit it was fast :) Also that's a lot of swap for a PC with 16GB of RAM...

---

### Post by darkod on 2012-10-30
I think in the latest versions they are trying to desing it so that the bootloader goes to the disk that is first in the boot order (windows does the same). It might be because many people with multiple disks installed ubuntu on their second or third disk, and got surprised when windows continued booting directly as if you have no ubuntu. Because the first disk is still with the windows bootloader and of course the user never changed the boot order in bios.

So, like it or not, from now on it seems the bootloader will go to the disk first in boot order regardless where ubuntu is installed.

That's why i mentioned the manual install, but too late. :)

PS. The swap is made to fit your RAM if there is enough unallocated space to use. This is so that you can hibernate if you want. Again, windows does the same, the page file is equal to RAM and the hibernation file too I think. Another good reason to use manual install, you control the partition sizes, not just the bootloader destination.

---

### Post by PendragonUK on 2012-10-30
That got it :) Again thanks for all of your help...

[[IMG]http://img593.imageshack.us/img593/3212/screenshotfrom201210301.png[/IMG]](http://imageshack.us/photo/my-images/593/screenshotfrom201210301.png/)

Damn look at all them cores! This is going to be mad!!! :guitar:

---

