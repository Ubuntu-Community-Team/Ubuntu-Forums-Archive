---
title: "Can't get a clean install"
date: 2014-11-27
forum: Installation &amp; Upgrades
---

### Post by linpet on 2014-11-27
Ubuntu 14 proved too much for my old Satelite laptop so I created a Lubuntu Live CD and tried to 'downgrade'. it did not go smoothly. I was looking for a simple light OS on a non partitioned machine for a sole user. I got:
Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0005f74f


```
Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 143730685 143728638 68.5G 83 Linux
/dev/sda2       143730686 156301311  12570626    6G  5 Extended
/dev/sda5       154208256 156301311   2093056 1022M 82 Linux swap / Solaris
/dev/sda6       148969472 152113151   3143680  1.5G 83 Linux
/dev/sda7       152115200 154208255   2093056 1022M 82 Linux swap / Solaris
/dev/sda8       143730688 148967423   5236736  2.5G 83 Linux
```


Partition table entries are not in disk order.

Don't even know where /sda3 & 4 got to.
Is there any way to clean this or can some one point me to the proper 'fresh start' tutorial?
Thanks for any assistance you can render, Linpet

---

### Post by Rex Bouwense on 2014-11-27
Did you get a good download of Lubuntu 14.04?  In other words when you checked the MD5Sum were they the same? 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
If they are the same, then you can burn the ISO to your CD or Flash Drive (at the slowest speed possible to increase the possibility of a good burn)
Pop the bootable device into your machine and boot.  Enter BIOS and check to see if your CD or USB Flash drive is ahead of your hard drive in the booting order.  Sometimes a flash drive is seen as another hard drive so check if it is ahead of your machine's hard drive.  Save and exit to continue booting.
First choose try Lubuntu before you install.  This will enable you to take it for a test drive before installation.  It will also enable you to see if all is working.  After you are satisfied double click on the install icon that is on your desk top.  Choose use the entire drive which I think is the first choice.  This will erase everything that is on your computer so if you have any data or files that you want to save you better back them before you install to a CD or flash drive or a cloud or another hard drive.  You will be asked a few questions and the installation will proceed.  It will take between 20 to 30 minutes.
Enjoy.
By the way sda3 and sda 4 were never created.  There can be four primary partitions (1 through 4).  However there can be a greater number of partitions if an extended partition is created.  It appears that sda 2 is your extended partition and it contains sda5 through sda8.  All of that will be over-written when you install as I have already said.

---

### Post by mörgæs on 2014-11-27
> **Rex Bouwense said:**
> Choose **use the entire drive** which I think is the first choice.  This will erase everything that is on your computer so if you have any data or files that you want to save you better back them before you install to a CD or flash drive or a cloud or another hard drive.

Yes, you have probably installed the new system together with the old one in a dual boot. If you want a single system the quote above is all you need.

---

### Post by linpet on 2014-11-27
The boot disc (Lubuntu 14.10 i386) was burned slowly and the hash check was successful. The DVD is in the drive and is set to boot first. I get a black screen with blue shadowed, white lettering showing the Lubuntu logo. My options are: Install Lubuntu; Check disc for defects; Test memory; boot from first hard disc; and Rescue a broken system. At the bottom is the 'F' menu, F1 Help, etc.
I may have the wrong iso...

---

### Post by Rex Bouwense on 2014-11-27
Do you have anything on the hard drive that you want? ** If you do back it up before you proceed**.  It appears that you already have an installation on your hard drive.  You can boot to it or just install Lubuntu 14.04 over what is on your hard disk (only you know what that is).  If you want to install choose install Lubuntu.  Answer the questions and sit back and let the installer do its work.

---

### Post by linpet on 2014-11-27
I did that the first time and got the dual mess with no space on '/'
I will try again.
I think I found the question I incorrectly chose during the first attempt that created too many partitions and no space where it was needed. We'll see if this works better. Thanks for the patience and the responses so far!
Success!!! up and running. Thanks to those who generously took the time to to help. read the partition selection info incorrectly on the first install. got it right eventually, Cheers, Linpet

---

### Post by Rex Bouwense on 2014-11-28
Excellent.  Enjoy Lubuntu.  It is a very good Operating System.

---

