---
title: "Install GRUB2 on hard drive"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by Diablomonkey on 2013-04-06
Hello Forums,

Background:

I  a few months ago I found a Dell Latitude D420 in a box of office things  on the street. It was accompanied by its (19.5V 4.62A) [UNGROUNDED?!]  power adapter and a docking station.

I'm most familiar with Ubuntu so for convenience/functionality sake  I'm going to have Ubuntu 12.04 installed. I intend this laptop to be  available to my family for browsing and playback of music from Pandora  (via Pithos) and over our home network. In an attempt to extend the  battery life of the laptop I hope to keep puppy (undecided version) on  either an SD card (4 GB) or micro SD card (16 GB)(in adapter) inside the  laptop's card reader. I would like to install GRUB2 to the first  partition of the HDD (This is what I need help with!). Then an Extended  partition to hold Linux SWAP partition (will puppy try to use this?),  and partition for Ubuntu (leaving some extra unalocated space). Then a  partition for Storage, and one for Backups.
  
(Please help me out if this doesn't make sense in  anyway. I want Grub2 on its own mostly to keep it safe  and independent of Ubuntu. I want Puppy on the SD/MicroSD so that after  picking Puppy at boot the laptop wont need to access the HDD unless  accessing the Storage or Backup partitions. I'm hoping that accessing  the RAM requires less power than accessing the HDD, This is mostly a  guess so if anyone wants to poke a whole in that theory or recommend an  even more power efficient OS please do)
  
How I proceeded:

Once  home, after checking for moister, I plugged it in for a few minutes and  then turned it on, Went into the BIOS (version AO3) and looked  around...
  
Processor Type...Intel core duo
Video Controller...Intel 945GSM Graphics
RAM...................1536 MB (Installed)
HDD....................80 GB
 Modem...............Conexant HDA D110 MDC
Wi-Fi..................Intel Wireless
Cellular...............None
Bluetooth............None
Battery...............6 Cell (Healthy)
  
Can BOOT from:
HDD
CD/DVD
USB (I'm familiar with these 3)
Diskette Drive (floppy?)
Onboard NIC
 Cardbus NIC
D/Dock PCI slot NIC (I'm NOT familiar with these 3)

Power it on (booting from HDD) I'm presented with XP pro preparing me a new user.
 
XP was useful for updating the BOIS to version AO6 (X3 faster than AO3!)

BOOT off Ubuntu 12.04 x86 live CD.
Checked  (most) hardware to ensure compatibility with Ubuntu. (I can't remember  If i used a badblocks command or the GUI way to check HDD health, but I  don't believe the HDD is failing in any way)
  
Everything worked so the laptop earned its keep, and  a bath. (screen looked sneezed on, company stickers and scotch tape on  the shell, keyboard was pretty clean, but some wires below it weren't in  place creating uneven keys, no obvious spills or broken parts though!)
  
Launched Gparted, erased everything.

...I'm  unsure if this is relevant because I don't think I broke anything, but I  read this forums Code of Conduct before writing this so I'm being  trying to be clear and take responsibility for my actions. I tried to  setup the laptop as described above armed with my knowledge, a few how  to's, some live cd's and flash memory. Unfortunately I couldn't get  GRUB2 Installed on Sda1, so I decided it would be good to start over  with some help...
  
Launched Gparted, erased everything.
Reboot.
Launched Gparted, format as described above.
Opened a Terminal and executed:
```
sudo fdisk -l
```
 The terminal returned:
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2e97


   Device Boot      Start         End      Blocks   Id  System
 /dev/sda1   *        2048     1026047      512000   83  Linux
/dev/sda2         1026048    42958847    20966400   83  Linux
/dev/sda3        42958848   103872511    30456832    5  Extended
 /dev/sda4       103872512   156301487    26214488   83  Linux
/dev/sda5        42960896    51357695     4198400   82  Linux swap / Solaris
/dev/sda6        51359744    72407039    10523648   83  Linux
 

Disk /dev/mmcblk0: 15.9 GB, 15931539456 bytes
255 heads, 63 sectors/track, 1936 cylinders, total 31116288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006b7b1


        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1   *        2048    31115263    15556608   83  Linux
 

Disk /dev/sdb: 64 MB, 64225280 bytes
198 heads, 62 sectors/track, 10 cylinders, total 125440 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00090ede


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      124927       61440    b  W95 FAT32
 

Disk /dev/sdc: 16.0 GB, [16013852672]("tel:16013852672") bytes
64 heads, 32 sectors/track, 15272 cylinders, total 31277056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c9ef6


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32    31277055    15638512    c  W95 FAT32 (LBA)
```
 
This is my 1st post so I hope I didn't step on any toes, this forum has been massively helpful over the years. 

Thanks for your time!

---

### Post by ahallubuntu on 2013-04-06
~

---

### Post by darkod on 2013-04-06
+1. You definitely some bootloader on the MBR of the hdd since that is where the boot process starts. I suggest you install grub2 from ubuntu on the MBR and that should be able to boot any other OS you add on top of ubuntu. Simple, easy, and working solution.

---

### Post by Diablomonkey on 2013-04-07
Thank you both for your responses.

Both ahallubuntu and darkmod's response made me realize I need to know more about that booting process.
I thought that the MBR was in the first partition of the hard drive.
You can forget about windows, its been erased and is unwanted.
I'm only trying to dual boot Ubuntu and Puppy.
Does Ubuntu handle both adding and removing kernel versions? Does it have trouble doing this if something else installed GRUB2 or if its installed somewhere else?
It isn't Ubuntu I was worried about prtecting GRUB2 from. I was worried if something happened to Ubuntu would my GRUB2 still work.

If I let Ubuntu install GRUB2 in /dev/sda where on it does the GRUB2 keep its data?

I hear what your saying about not being able to boot off sd card in every case.
I agree with you the laptop can't find the sd card from the BIOS. I was hoping to have the BIOS boot off the hard drive, then have GRUB2 setup to boot off of either HDD or SD card.
Puppy on the hard drive is unapealing, sense the only reason I'm considering using Puppy is because I think it might draw less power from the battery accessing only the RAM after boot.

Thanks for the tid-bit about the powercords, I was aware they are out there but I thought it was based on the age of the hardware not its requirements. Is it safe to charge on ungrounded outlets?

---

### Post by fantab on 2013-04-07
If you are worried about losing Battery Power then you must actually consider [Lubuntu]("http://lubuntu.net/").

Simple solution: Remove all other external storage devices except the one you are installing from and REINSTALL UBUNTU. By default Grub will be installed on the HDD (/dev/sda), to be absolutely sure choose "SOMETHING ELSE" option when managing your Disks during installation. Make sure GRUB is being installed on /dev/sda only. Grub will store its files on the partition you have installed ubuntu on. 

There seems something amiss with your *fdisk -l *output. If  /dev/sda3 is an Extended Partition than the following Logical Partition  will be numbered as /dev/sda5 and not /dev/sda4. (I myself need to  confirm this, however).

---

### Post by darkod on 2013-04-07
> **fantab said:**
> 
There seems something amiss with your *fdisk -l *output. If  /dev/sda3 is an Extended Partition than the following Logical Partition  will be numbered as /dev/sda5 and not /dev/sda4. (I myself need to  confirm this, however).

It seems to look fine. sda4 is after sda3 which the start/end values of the sectors clearly show. sda5 and sda6 are of course inside sda3.

Since logical partition always have a 5+ number, if you have another primary after the extended the fdisk printout might look strange on first glance, since it lists them in ascending order, not how they are physically on the disk. But one look at the the start/end can show you what is where.

---

### Post by fantab on 2013-04-07
I had a re-look at start/end, and that explains. Thanks darkod. 

I keep my primary partitions first then I have Extended and as 4th partition.

---

### Post by oldfred on 2013-04-07
I also think you are over thinking things. In the old days with grub legacy many of us that multi-booted used a separate grub partition. But that required manual maintenance and/or each installs's grub installed to that partition's boot sector (PBR). But grub2 does not like to be installed to a PBR. 

The MBR is just the first sector of a hard drive that the BIOS automatically jumps to, to continue booting. First partition then used to start at sector 63 to leave room for grub legacy's stage1 or grub2's core.img, but now new drives all start at sector 2048 for compatibility with new 4K and SSD drives.

One of the real advantages of grub2 is its os-prober. It will update grub menu with all other installs on system and update when ever a kernel is changed (few cases manual effort still required). If you have a grub partition you have to do all that manually although that can be simplified in many cases. But you do not have os-prober in a grub only partition as it is part of the Ubuntu install not just a grub install.

I do install grub only to all my flash drives except the one with a full install. But that is primarily so I can boot ISOs directly with grub2's loopmount. And I have to totally manually maintain grub.cfg.

And I have my main install's grub2 boot loader in the MBR of my boot drive and let it automatically update. But I have to do some manual editing as I have several experimental installs and grub menu gets too large.

---

### Post by Diablomonkey on 2013-04-08
Hey Fantab,

Thanks for the Lubuntu suggestion, I was planning to insatll MATE as the GUI for Ubuntu, but now I think I'll give LXDE a whirl.

---

### Post by Diablomonkey on 2013-04-08
Thanks oldfred,

That gave me something to try next.
Loopmounting is new to me, so I'll need to do some reading.

I know that when I boot off of Puppy precise 5.5 live CD, by default it trys to find puppy .sfs files on the computer and if it does its loads it. (the CD can fin the .sfs files on my sd card)

So your post made me wonder if I could get grub to load an iso file from the HDD?

---

### Post by Diablomonkey on 2013-04-08
Thanks everyone!

Sense you all responed unanimously I let GRUB2 do what it will and intalled it to sda.

Will still be trying to get GRUB2 to load Puppy from SD card, so advice on that is still welcome, but this thread is solved.

---

### Post by oldfred on 2013-04-08
Ubuntu desktops installers will loopmount directly from any device with grub installed. Older Puppy did not as it had to have kernel extracted to boot. Have not tried with new versions.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

