---
title: "Dual booting Vista &amp; Ubuntu w/ HW MIRRORING"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Stephen8454 on 2007-05-11
Ok, here are my spec's:

CPU: C2D E6320
Mobo: EVGA 680i SLI T1
RAM: 2 x 1GB OCZ DDR2 1066 SLI Certified
GPU: GeForce 7600GT CO
HDD's: 2 x 80GB HDD's in a RAID 1 Mirror

So, I have Vista Ultimate 64-bit installed on a 40GB partition

I want to dual boot Ubuntu 7.0.4 x64 on the remaining 40GB partition.

I got Vista installed and then installed Ubuntu on the remaining 40GB and auto partitioned w/ the ext3 partition and a swap partition.

Then I couldnt boot anything (error msg: "No Operating System Found") so I booted to Ubuntu Live CD and flagged the Vista partition as "boot" but it still wouldnt boot. So, I tried again and flagged the boot partition for Vista on both disks in the mirror set as "boot" and it worked...

So, I then tried the same exact thing only this time I enabled the ext3 partition w/ ubuntu on it as boot on both disks in the mirror and it didnt boot saying "no operating system found" or something like that...

I also tried using EasyBCD to add the linux OS into the Vista Bootloader and still had no affect...

I posted this message on anandtech forums and all the users have so far told me that Ubuntu does not like mirrored sets and that I have to find a way for Ubuntu to see the 2 disks as a mirror and not 2 seperate disks...

Any ideas?

---

### Post by Computer Guru on 2007-05-11
Get Vista booting.
Use a Live CD or Super Grub Disk to install GRUB to the bootsector of your Feisty partition.
Boot back into Vista. Delete old Linux entries in EasyBCD.
Add new Feisty partition in EasyBCD 1.6.

Details: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Stephen8454 on 2007-05-11
When I installed Ubuntu from the Live cd it asked what boot loader to install and I specified GRUB.

I added it w/ EasyBCD and it isnt working. Does the fact that my 2 HDD's are mirrored have anything to do w/ it because the guys on anandtech forum said it does?

---

### Post by Computer Guru on 2007-05-12
It depends.

If they're mirrored on the BIOS/Controller level such that no PC software actually sees 2 HDs and they only see one - then it shouldn't matter.

Otherwise.....

---

### Post by Stephen8454 on 2007-05-25
When I boot into Ubuntu it shows both drives... It doesnt see it as one volume. Some folks at anandtech said so far Fedora is the only one w/ the right driver 

honestly i dont care anymore...

---

