---
title: "Kernel panic not syncing"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by hocico0777 on 2010-11-05
In my internal disk i had installed 10.04 and 10.10. 2 days ago after a restart my system did not boot and i got the message: kernel panic:not syncing VFS unable to mount root fs on unknown block(0,0).

For 2 days i tried to solve the problem without success and today i installed 10.04 in the entire internal disk but the problem(message above mentioned) remains.

the result of the sudo fdisk -l command is this 

>  ubuntu@ubuntu:~$     sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000c340

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482347008   83  Linux
/dev/sda2           60050       60802     6037505    5  Extended
/dev/sda5           60050       60802     6037504   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d96c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       29432   236407938+   7  HPFS/NTFS
/dev/sdb2           29432       29554      975872    b  W95 FAT32
/dev/sdb3   *       29554       30094     4339712   83  Linux
/dev/sdb4           30094       30402     2473984   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


sdb is my external hard drive in whick i also had 10.04 installed but never used it.

Iwould appreciate any help because my pc does not boot for 2 days now.

---

### Post by BlackCat13 on 2010-11-05
> **hocico0777 said:**
> In my internal disk i had installed 10.04 and 10.10. 2 days ago after a restart my system did not boot and i got the message: kernel panic:not syncing VFS unable to mount root fs on unknown block(0,0)

On Maverick I got this same message just now... the system has been working fine all day... I installed it last night... then on a reboot tonight got that message.

before the kernel panic output the system says

RAMDISK: gzip image found at block 0
usb 1-2: new high speed usb device using ehci_hcd and address 2
uncompression error
VFS: Cannot open root device "mapper/mylaptop-root" or unknown-block(0,0)
Please append a correct "root=" boot option; here are the available partitions
0b00      1048575 sr0 driver:sr

Then it gives the Kernel Panic

Kernel Panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
Pid: 1, comm: swapper not tainted 2.6.35-22-generic #35-Ubuntu

Then a call trace...

This is a brand new install of Maverick I copied my files onto a USB and did a fresh install on the whole drive using the alternate CD (the desktop and netbook editions both failed to read on my system)

was previously using Karmic with no issues.

I tried to e2fsck the dev/sda1 from the CD in "repair broken system" mode but the return was "clean" I read that as the file system being intact but this is an area that I have no real knowledge in.

---

### Post by dino99 on 2010-11-05
usually this happen with bad kernel compilation or this kernel has not been compiled with the driver(s) you need.

you might either download the kernel again and reinstall it or modprobe the missing driver(s)

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

---

### Post by hocico0777 on 2010-11-05
@dino99
you might either download the kernel again and reinstall it or modprobe  the missing driver(s)

i do not understand how to do that (the reinstall) or the other thing you suggest,could you be more specific?

ps i am writing through a live cd

---

### Post by BlackCat13 on 2010-11-05
@dino99

Hey thanks for the very quick reply... unfortunately I have no idea how to do that... I used a CD to install... and have never compiled from source... 

Do you mean to say that I can download one of the kernels and install it in the system somehow using the "repair a broken system" option on the Ubuntu install disk?

---

### Post by BlackCat13 on 2010-11-05
@hocico0007

I have also posted this on a couple other forums so if I get any help there I will transfer the answer here...

---

### Post by BlackCat13 on 2010-11-05
I reinstalled... is working now

---

### Post by hocico0777 on 2010-11-05
> **BlackCat13 said:**
> I reinstalled... is working now

&#933;ou reinstalled from the cd or just the kernel?

---

### Post by BlackCat13 on 2010-11-07
Hi Hocico

I had only done a fresh install so i reinstalled from CD... seemed quickest for me given the answers I was finding here...

Serafean on Linux Questions.org had a different way around it but I had already started the re-install... if u like visit the thread here

[http://www.linuxquestions.org/questions/ubuntu-63/kernel-panic-on-maverick-842569/](http://www.linuxquestions.org/questions/ubuntu-63/kernel-panic-on-maverick-842569/)

may find some assistance there...

---

### Post by hocico0777 on 2010-11-07
Today i disconnected the cables of the hard disk and reconnected them,i also changed the dimm slot of my ram (1 only) and i managed to make a new clean install (and very fast indeed).
I dont know how to explain this but it solved the problem.

---

### Post by drs305 on 2010-11-07
Just for future reference, the error message in the first post ( "kernel panic:not syncing VFS unable to mount root fs on unknown block(0,0)" ) could also be attributed to a boot hiccup by Grub. If Grub can't find some of the boot files because the 'root' designation is incorrect the same message can be generated.

We won't know what caused the problem in this case, but it's something to keep in mind should it happen again.

Glad you have your system back working.

---

### Post by dino99 on 2010-11-07
im glancing about this problem (got it always on first boot only) for a while (might be since we have dropped hal), hope this will be fixed soon

---

### Post by hocico0777 on 2010-11-09
Hi,new problems today,at some point this morning the windows of the various programs did not show the operational functions of the programs (i do not know how to describe it exactly they appeared as empty windows) so i decided to reboot,after the reboot it gave me  a black screen with initramfs prompt which i managed to surpass by giving some orders in the terminal and boot.

I begin to think that there is some hardware problem with my system and not with the software.
Which is the best way to test my hard disk through ubuntu (10.04)?

---

### Post by dino99 on 2010-11-09
dont post different problem into the same thread, create a new thread, its easier to follow and get answered.

try:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

metacity --replace

good luck :)

---

### Post by drs305 on 2010-11-09
> **hocico0777 said:**
> I begin to think that there is some hardware problem with my system and not with the software.
Which is the best way to test my hard disk through ubuntu (10.04)?

One method is to use the Disk Utility program (System, Administration, Disk Utility). You can run a test via the Smart Data" section from a normally running system or boot to the LiveCD and also run the "Check Filesystem".

---

