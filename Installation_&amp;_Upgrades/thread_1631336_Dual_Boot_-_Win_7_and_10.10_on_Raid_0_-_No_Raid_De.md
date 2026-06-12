---
title: "Dual Boot - Win 7 and 10.10 on Raid 0 - No Raid Detect"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by STM127 on 2010-11-26
I have installed Ubuntu on my m1530 since 8.04 and currently dual boot Win7 and 10.10. I would like to dual boot on my PC, but I have run into a problem. I am not a pro at Ubuntu, but this problem I can not solve by reading forums like I have in the past.

I realize this is a common problem, but I have noticed people having success.

I have a M4A87TD EVO MB with two Seagate drives in Raid 0. (The raid controller is a SB850 on that MB) I use the raid utility to create the raid drive that Windows7x64 uses. I have 2 partitions and 1 unused space. Partition 1 is Windows, partition 2 is for media, and the remaining unused space is for Ubuntu.

I am running ubuntu-10.10-desktop-amd64 off a Cruzer 16GB flash drive that was installed via Universal-USB-Installer-1.8.1.4.

My problem like so many others is that when I load into Ubuntu, gparted detects two separate hard drives instead of the raid. I read that this is because kpartx is not installed on 10.10. I then went in LiveCD mode and downloaded kpartx from Synaptic Manager. Gparted still reported two drives. I opened terminal and run a few commands with kpartx. I received an error. (Forgive me I didn't write it down, but I believe it said something about a communication error. I will try again later and see.) 

Currently I am reflashing the Cruzer with a persistence of 4GB. I am not familiar with this process, but I understand that my LiveCD boot will save information I download to it. I decided to try this method because I was going to install kpartx and reboot to see if this made a difference.

I am looking for any suggestions on a different method or perhaps someone to tell me that the raid controller or some hardware isn't supported. I did install ubuntu-10.10-alternate-amd64 on my flash drive, but fail to get past detecting my CD-ROM drive since it's not plugged in. If this method is viable, I will plug it in. I also watched the youtube video were a guy creates Raid 0 with the alternated CD, but it wasn't a dual boot and didn't use a raid controller from a MB.

---

### Post by Greggi on 2010-11-26
If you have an external harddisk, backup your files, and install win7x64 first and then ubuntux64, both from livedisk. @my Notebook, the "Recover"-partition was also seen as a own harddisk, but it wasn't!
Normally Ubuntu have no problems with raid drivers, but in windows you have to load them before starting installing,after the language selection!

I don't know if this is what you want, and if it works, but good luck!

---

### Post by ronparent on 2010-11-27
Your problem is common right now with 'fakeraid' (MB raid that works fine with windows, and usually with Ubuntu 9.04 and later also). It is usually fixed with kpartx. A permanent fix has been made upstream but has not apparently made its way to the distributions. 

To install to a raid drive, I recommend installing kpartx to the live cd session before starting an install to that session. With kpartx gparted will see the raid partitions as it should. Then start the install while  still in the session and select the manual partitioning option when you get to that step.

To the best of my knowledge dmraid works with all raid types it supports. To verify that your chip set is supported type dmraid -l in a terminal for a list of supported types. Also use 'sudo dmraid -r', '-s' or '-ay' to verify that the raid partitions are being discovered.

I use various Ubuntu and Mint distro's installed to a raid 0 disk set with no problems. Although my Win7 is installed to a separate ssd I have no problems accessing my Win 7 created ntfs partitons also on the same raid. It is very likely that your raid chip set is supported for raid0.

I'm not completely following your plans, but, you should be able to do a straight forward install to a partition on your cruiser to test it with the raid. If dmraid is not installed automatically you should be able to install it booted to the cruiser. I also use a 16 Gb cruiser as a carry around system. Good luck and post if you have any problems.

---

### Post by STM127 on 2010-11-28
I installed kpartx and rebooted the LiveCD, and gparted still sees two independent drives with kpartx installed.

I opened terminal and ran the suggested commands.

dmraid -l 
asr     : Adaptec HostRAID ASR (0,1,10)
ddf1    : SNIA DDF1 (0,1,4,5,linear)
hpt37x  : Highpoint HPT37X (S,0,1,10,01)
hpt45x  : Highpoint HPT45X (S,0,1,10)
isw     : Intel Software RAID (0,1,5,01)
jmicron : JMicron ATARAID (S,0,1)
lsi     : LSI Logic MegaRAID (0,1,10)
nvidia  : NVidia RAID (S,0,1,10,5)
pdc     : Promise FastTrack (S,0,1,10)
sil     : Silicon Image(tm) Medley(tm) (0,1,10)
via     : VIA Software RAID (S,0,1,10)
dos     : DOS partitions on SW RAIDs

sudo dmraid -r
/dev/sdb: pdc, "pdc_bbifihidai", stripe, ok, 781249792 sectors, data@ 0
/dev/sda: pdc, "pdc_bbifihidai", stripe, ok, 781249792 sectors, data@ 0

That is the correct size of the raided drive. I see pdc which is shown as being supported.

sudo dmraid -s
ERROR: pdc: identifying /dev/sdb, magic_0: 0xe1e2e3e4/0x46af1124, magic_1: 0xd9dadbdc/0x0, total_disks: 0
ERROR: adding /dev/sdb to RAID set "pdc_bbifihidai"
ERROR: removing RAID set "pdc_bbifihidai"
ERROR: pdc: wrong # of devices in RAID set "pdc_bbifihidai" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "pdc_bbifihidai"
ERROR: no RAID set found
no raid sets

sudo dmraid -ay
ERROR: pdc: identifying /dev/sdb, magic_0: 0xe1e2e3e4/0x46af1124, magic_1: 0xd9dadbdc/0x0, total_disks: 0
ERROR: adding /dev/sdb to RAID set "pdc_bbifihidai"
ERROR: removing RAID set "pdc_bbifihidai"
ERROR: pdc: wrong # of devices in RAID set "pdc_bbifihidai" [1/2] on /dev/sda
ERROR: removing inconsistent RAID set "pdc_bbifihidai"
ERROR: no RAID set found
no raid sets

I did a quick search of the "ERROR: pdc: wrong # of devices in RAID set" but I didn't see any solutions for the error.

---

### Post by dino99 on 2010-11-28
why using raid0 (you cant boot with anyway), better to use LVM

[https://help.ubuntu.com/community/Installation/RAID1%2BLVM](https://help.ubuntu.com/community/Installation/RAID1%2BLVM)

[http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/](http://www.davelachapelle.ca/guides/ubuntu-lvm-guide/)

to remove raid: sudo dmraid -rE

---

### Post by ronparent on 2010-11-28
STM127 - kpartx will be installed to the live cd session only if you install it in and for that session. It is not persistent and disappears with a reboot. In the live cd session, simply install kpartx and when you start gparted all the raid partitions should be picked up. You should do this to verify that the raid partitions will be picked up prior to an install to a 'fakeraid'. 

Meanwhile ignore the raid errors. I don't know what is happening but it is a recent development. At this point it doesn't seem to interfere with installing to a raid0 or booting from it. You have a pdc raid chip set, incidently, which is what I am currently using.

Try again. Open the 10.10 live cd session and install kpartx. Then open gparted to view the raid partition. If you want to install to the raid I suggest using gparted to create at least an extentded partition to install to. You will have to use the manual partition option during the install to create your '/' (the installation target) and a swap. If you not familiar with partitioning during an install, Just be sure to select the unallocated space within the extended partition and 'change' to designate a file system and mount point (/) to install to (formating is optional on an emptey partition). dino99 is incorrect on this point, you will be able to boot to a fakeraid 0 if properly installed. 10.10 ususally will correctly install the boot loader to the raid as boot drive. But if you run into problems, post.

---

### Post by mikebailey on 2010-11-30
i think i may have found a solution to your "ERROR: pdc: wrong # of devices in RAID set" issue.

short story, if the only drive in your computer is the raid array, windows creates a 100 mb partiton for the boot files and MBR. like grub 1, the windows MBR will not function on a raid array, so it created the 100 MB partition on only one of the drives, so that 100 mb partition messes up the partition boundaries on one of the drives in the array so they don't match, causing the "ERROR: pdc: wrong # of devices in RAID set" issue.

long story, if you wish to read it.

i too was plagued by that issue. i decided to try and find out the problem to it. after many hours of backing up my windows 7 install on my raid array, i decided to take the plunge and start from scratch. 

i noticed in ubuntu 10.10 that i had installed to one of the ide drives on my computer, that when i looked at the 2 drives in the fakeraid raid 0 array on my computer (amd sb750 chip) as separate drives with "fdisk -l", one drive had an extra partition that the other did not. i looked at its size and noticed it was only about 100 MB in size.

when the only drive in your computer is the raid array drive, and you install windows 7 to the raid array with no other drives in the computer, windows creates that 100 mb partition to store the boot data on (i think thats what they put on it). when i created the raid array in the bios i then went in the windows install far enough to create the partitions, i have 2 other ide hard drive in my computer, a 200 GB and an 80 GB. when i created the partitions, it used my 200 GB ide drive to put the mbr and the other windows boot stuff on it, instead of creating the 100 mb partition on the raid array. linux now sees the raid array properly, and i am going to be putting ubuntu 10.10 on it later, using my 80 GB ide drive grub.

i hope this solves a few peoples issues with the "ERROR: pdc: wrong # of devices in RAID set"

---

