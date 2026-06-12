---
title: "GRUB2 Drive Translations - K16.04.2 LTS"
date: 2017-02-12
forum: Installation &amp; Upgrades
---

### Post by shadragon on 2017-02-12
I have four HD's in my machine, split with multiple partitions: 

sda1
sda2
sda5
sdb1
sdb2
sdb3
sdc1
sdc2
sdc3
sdd1
sdd2

sdaX are my Linux partitions and sddX is my Windows install. 

Grub2 uses the drive naming format "set root=(hd0,1)"

So do these two drive naming systems correspond directly? That is, in the following way:
[COLOR=#333333]
[/COLOR]sda1 = hd0,1
sda2 = hd0,2
sda5 = hd0,5
sdb1 = hd1,1
sdb2 = hd1,2
sdb3 = hd1,3
sdc1 = hd2,1
sdc2 = hd2,2
sdc3 = hd2,3
sdd1 = hd3,1
sdd2 = hd3,2


Or can the drive in the first list be in another order from the second? I can get all sorts of info on my drives with **fdisk -l** and **lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL**, but they all use the first drive naming convention where GRUB2 uses its own hdx,y format.  

I want to understand this before I start making script changes to the GRUB2 scripts. 

Thanks.

---

### Post by oldfred on 2017-02-12
No.
Possible most of the time.

BIOS/grub see drives in port order.
Ubuntu assigns devices in order mounted.

I have found with my BIOS system I originally had skipped a port. My sda never changed. But my flash drive as sdf on reboot would be in the second slot and becomd sdb and every drive changed up a letter.
I did something similar (slow learner) with new UEFI system. I put sda in SATA0, DVD in SATA1 & sdb in SATA2. But in trying to use grub to see sdb drive it was hd2 as it used hd1 for DVD.

So always put drives in SATA port order and then it should be consistent. But if scripting better to use drive or UUID.

disks by name & hardware path, sdc is a flash drive with a full install, so on USB port not SATA.
```
fred@Asusz97:~$ sudo lshw -C Disk -short 
[sudo] password for fred: 
H/W path               Device      Class          Description
=============================================================
/0/100/14/1/9/0.0.0    /dev/sdc    disk           30GB SCSI Disk
/0/1/0.0.0             /dev/sda    disk           128GB Samsung SSD 840
/0/2/0.0.0             /dev/sdb    disk           1TB WDC WD10EZEX-00B
/0/3/0.0.0             /dev/cdrom  disk           CD/DVDW SH-S183L



```

---

### Post by shadragon on 2017-02-12
Thank you for the concise and complete reply. Makes perfect sense. 

Cheers.

---

### Post by shadragon on 2017-03-04
OK, I got a chance to sit down this weekend and do further research. What seemed simple, turns out to be much more complex than I thought.  

Down below is the output for my PC with various terminal commands. I have Win 7 on sdd and Linux on sda. I can boot and run both OS from the BIOS screen. update-grub does not auto-detect my OCZ RevoDrive so I need to edit Grub2 manually to use sdd1 as my Win 7 boot disk.

oldfred suggests mapping the drive by UUID except all I can find is a PARTUUID. How do I translate this to a GRUB 2 script?

I also tried BURG bootloader, but in the Grub Customizer GUI, the windows partitions are not even listed.  


H/W path            Device      Class       Description
=======================================================
/0/100/b/0/0.0.0    /dev/sdd    disk        120GB OCZ-REVODRIVE3
/0/100/b/0/0.1.0    /dev/sde    disk        120GB OCZ-REVODRIVE3
/0/1/0.0.0          /dev/sda    disk        2TB ST2000DM001-1ER1
/0/2/0.0.0          /dev/cdrom  disk        iHAS124   D
/0/3/0.0.0          /dev/sr1    disk        iHAS124   D
/0/5/0.0.0          /dev/sdb    disk        3TB ST3000DM001-1CH1
/0/6/0.0.0          /dev/sdc    disk        3TB ST3000DM008-2DM1




Disk /dev/sdd: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xde7101af

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sdd1  *      2048    915704    913657 446.1M  7 HPFS/NTFS/exFAT
/dev/sdd2       915712 468879359 467963648 223.1G  7 HPFS/NTFS/exFAT




sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found linux image: /boot/vmlinuz-4.4.0-62-generic
Found initrd image: /boot/initrd.img-4.4.0-62-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Failed to probe /dev/sdb1 for filesystem type
Failed to probe /dev/sdc1 for filesystem type


sudo blkid /dev/sdd1
/dev/sdd1: PARTUUID="de7101af-01"

---

### Post by oldfred on 2017-03-04
I do not know OCZ-REVODRIVE3, but some old posts show issues.

See post on not bootable, but other model's drivers may work?
[http://askubuntu.com/questions/372906/installing-linux-on-ocz-revodrive3-x2](http://askubuntu.com/questions/372906/installing-linux-on-ocz-revodrive3-x2)
Says they are FakeRAID.
[http://www.average.org/ssdroot/how-to-boot-linux-from-revodrive.txt](http://www.average.org/ssdroot/how-to-boot-linux-from-revodrive.txt)

       [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
dmraid was replaced by mdadm for handling FakeRAID in Ubuntu 14.04.
15.04 or later now uses mdadm to support intel fakeraids 
User who installed fakeRAID
How to install Ubuntu 14.04 in software fakeraid RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

### Post by shadragon on 2017-03-07
Thanks oldfred. Those articles assume you want to install Ubuntu on a RevoDrive. To be clear, I do not want to boot Linux or Grub from the RevoDrive. That has my Windows 7 on it and works fine as my (current) primary drive. 

What I'm working towards is setting my Linux HD as the primary with GRUB2 active on that drive so I can choose Win7 or Kubuntu. The only missing piece of info I need is how to map the PARTUUID in the GRUB2 scripts - OR - map the drive in a hd(x,y) format based on the boot order.  

With that, I should be good to go.

---

### Post by oldfred on 2017-03-07
I do not know RAID, but then you you need to add the RAID drivers in Ubuntu to see them?
And grub has several RAID related .mod files (insmod to add them like other drivers) that you may need one or the other for when booting.

---

