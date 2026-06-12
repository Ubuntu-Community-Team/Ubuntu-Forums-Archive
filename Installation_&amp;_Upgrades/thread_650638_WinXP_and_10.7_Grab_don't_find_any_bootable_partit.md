---
title: "WinXP and 10.7: Grab don't find any bootable partitions"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by dhl on 2007-12-26
I am trying to install the 10.7 ubuntu on a computer, running WinXP. The hard disc was formated under win into 4 partitions: 
NTFS (WinXP)
Fat32 (for file sharing between the OSs)
Unallocated (swap)
Unallocated (for system)

The disc partitioned from the LiveCD in manual mode shows the layout like this:
dev/sda
  sda5 - an other hard drive
dev/sdb
  sdb1 - NTFS and Win on it
  sdb5 - Fat32
  sdb6 - unallocated
  sdb7 - unallocated
dev/sdg - an other, external USB hard drive  

Installed giving sdb6 to / and sdb7 to swap - successful install (on default  grab was set to (hd0)). But after reboot there is no grub and win is booting. Tried so several times, but with the same result. 

Then tried to change the drive in grab's settings to sdb, in response to the above mentioned table. Install successful, and grab actualy appeared after reboot, showing standard choice (7.10, 7.10 under root, etc., WinXp blah blah blah). On everywhere I get Error 22 (No such partition). 

Tried to install ubuntu and thus grab with hd0, as was on default, grab loaded, the same error with ubuntu (no partition) and starting win returns "no NTLDR", which is quite logical...

Under LiveCD session, ubuntu "sees" and mounts on desktop only the external hard drive.

What are the suggestions? 
Overwrite grab with NTLDR from win's boot floppy/fdisk/mbr? As I understand, now there are grab's on both sda and sdb? So should I overwrite the boot loader on both disks?

---

### Post by Pumalite on 2007-12-26
Use Gparted live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it. Resize XP partition. For the new partition this is a good scheme:
10 GB for '/'
1 GB for /swap
The rest for /home.
Install going Manual and use the already made partitions.

---

### Post by TrapMakeR on 2007-12-26
dhl,

Could you please post your grub commands?

---

### Post by dhl on 2007-12-26
TrapMakeR, sorry, what do you mean under grub commands? I haven't installed it manually, it was installed with Ubuntu LiveCD during installation....

Pumalite,
Can't boot from this disk... Boot from cd/dvd starts but nothing happens, it just stays so, and cdrom stops also after a few seconds... 

P.S. I have changed the drives in their sockets so that the system disk is the first, sda, and installed ubuntu+grub with grub on hd0. Now I get simply Error 22 without grub loading.

---

### Post by Pumalite on 2007-12-26
[http://users.bigpond.net.au/hermanzone/p15.htm#22](http://users.bigpond.net.au/hermanzone/p15.htm#22)
Check your menu.lst and make the changes necessary in 'root'
If you are able to boot a Live CD, post:
sudo fdisk -lu

---

### Post by dhl on 2007-12-27
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 80.0 GB, 80026361856 bytes  *My system drive
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0ce50ce4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   122672339    61336138+   7  HPFS/NTFS
/dev/sda2       122672340   156296384    16812022+   f  W95 Ext'd (LBA)
/dev/sda5       122672403   126961694     2144646    b  W95 FAT32
/dev/sda6       126961758   154882664    13960453+  83  Linux
/dev/sda7       154882728   156296384      706828+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes *Data drive (valuable data!)
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8abd22a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16065   488392064   244188000    5  Extended
/dev/sdb5           16128   488392064   244187968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes *Data drive (valuable data!)
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

Was unable to access 'boot' on sda6 under LiveCD, but got there under knoppix live session. Here is my menu.lst: [http://files.andreykulpin.com/temp/menu.lst.txt](http://files.andreykulpin.com/temp/menu.lst.txt)

---

### Post by Pumalite on 2007-12-27
What's the state of affairs today? When you power up the computer, what do you see?(your menu.lst seems OK.)
Did you partition with Gparted? Do you have more than 4 primary partitions per disk?)

---

### Post by lswest on 2007-12-27
umm a problem may be that you have too many primary partitions on one hard drive, would work better if you made the linux chunk into an extended partition and put those 3 partition within the extended partition, because if there are too many primary partitions usually gparted won't partition it.

---

### Post by dhl on 2007-12-27
It was partitioned under win, using acronis. Then partitioner from livecd formated two partitions to swap and ext3.
Whan I power up, the grub starts and whan I select ubuntu - I receive error 22 and No such partition, when Win - NTLDR not found.
There were 4 partitions: NTFS, Fat32 (should stay empty), ext3 and swap...

---

### Post by Pumalite on 2007-12-27
Boot from Gparted Live CD and post a screenshot.

---

### Post by dhl on 2007-12-27
Can't boot from Gparted Live CD at all...
Will now try to overwrite Grub with NTLDR from WinMe boot floppy's fdisk and try partitioning the disk one more time...

---

### Post by dhl on 2007-12-27
Ok, the problem is solved. Run fdisk/mdr, after reboot changed the 1st boot device to hdd (have this function in my MB, no need do change it in BIOS), then was asked to select the hdd to boot from, and grub started fine. Both WinXP and Ubuntu are working fine now.

---

