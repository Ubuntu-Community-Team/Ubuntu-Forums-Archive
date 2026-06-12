---
title: "Won't boot"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by Chondro_Biak on 2008-08-14
I have installed Ubuntu on a computer I have just built and the installation went very smooth... No hang ups... 

However when it was done installing it gets hung up on the boot. If I go into the Grub and go in through recovery mode it gets hung up... 
It gets hung up and says   ata2: DUMMY

From there it goes to the busy box terminal. If I type in mount from busy box it shows no hard drives are installed.

Also I went into my BIOS and noticed my hard drive is labaled as a slave. There are no jumpers in the hard drive, so it should be saying it's a primary... 

I have done checks on my disk and everything is good. I have tried installing 7.10 in standard as well as primary and get the same result and I of course tried 8.04 with both disks and got the same result.

I booted to Knoppix and the hard drive was clearly visable and so was the Ubuntu files.

My system is as follows:
GIGABYTE GA-EP45-DS4P LGA 775 Intel P45 ATX Intel Motherboard
XFX PVT96GYDDU GeForce 9600 GT 512MB 256-bit GDDR3 PCI Express 2.0 x16
SAMSUNG SH-S223F DVD Burner
Intel Core 2 Duo E8500 Wolfdale 3.16GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
Kingston HyperX 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 1066 KHX8500D2K2/2G


Any thoughts?

---

### Post by Pumalite on 2008-08-14
Drives:what kind? how are they connected?

---

### Post by Chondro_Biak on 2008-08-14
I am using a 500GB Wester digital Hard Drive connected through SATA... I have tried the HD in 4 different SATA ports on the board with no change... I have also tried disconnecting my DVD drive and booting with no change..

---

### Post by Pumalite on 2008-08-14
Did you try: all_generic_ide at the end of the boot line?

---

### Post by Chondro_Biak on 2008-08-14
I typed that in on the boot disk... F6 all_generic_ide then enter and loaded the OS... Is that what you mean?

I should also mention. I am unable to get to a normal terminal. Busy Box is all I have been able to get to. 

Any slick ideas on how to get to a terminal?

---

### Post by Pumalite on 2008-08-14
Here are other boot parameters you might want to try:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off
To get a CLI:
Ctrl+Alt+F1 (2, 3, 4, 5, 6)

---

### Post by Chondro_Biak on 2008-08-14
Is that typed in before installation? 

So I pop in the OS disk... move my arrows over Install Ubuntu, hit F6, type that in and hit enter to install under those parameters? 

So I am going to have: Whatever is says already +

--all_generic_ide noapic nolapic acpi=off irqpoll pci=noacpi pnpbios=off

And then of course reinstall... 

Right?

---

### Post by Chondro_Biak on 2008-08-14
Am I going to edit anything on the kernal line? or am I just going to add:
all_generic_ide noapic nolapic acpi=off irqpoll pci=noacpi pnpbios=off

Do I need to delete "quiet splash --."

---

### Post by Pumalite on 2008-08-14
Boot parameters are to be tried one by one or in different combinations.
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Chondro_Biak on 2008-08-14
Ohhhhh... my bad... 

I will give this a shot when I get home and let you know...

---

### Post by Chondro_Biak on 2008-08-15
That did not work... 

It was suggested to me that this may be happening because of the size of my hard drive. When I am installing this I am selecting "Use Entire Disk"... I was told that if I net up a 500MB partition as a boot and set up the rest of the HD as swap with the grub boot on it that it will work... 

Has anyone experienced this?

---

### Post by Pumalite on 2008-08-15
First of all; how many drives do you have? 2nd; Are you planning to install Ubuntu alone in the 500 GB?

---

### Post by Chondro_Biak on 2008-08-15
I have 1 500G drive. and yes I was planning to put Ubuntu on there alone. The connection is SATA.

Am I going to need to set up a partition to make this work?

---

### Post by Pumalite on 2008-08-15
Get Gparted Live CD to do the job:
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)
Burn the iso to disk and boot from it
First delete everything in your harad drive. In the unallocated space left, make 3 'New' partitions:
15 GB for '/'
The rest minus the amount of your RAM for /home
The amount of your RAM for /swap
Remove Gparted. Boot from your Ubuntu CD; install, go Manual and use the already prepared partitions. Good luck

---

### Post by Chondro_Biak on 2008-08-15
Setting up partitions from the Ubuntu install disk is pretty easy from the manual option. Why not set up the partitions that way? I don't mind doing it that way, just curious as to why you suggest this way... 

Have you heard of this issue before? Noting being able to boot because of the partition being too big?

---

### Post by Pumalite on 2008-08-15
Gparted Live CD is a newer version, more flexible, more powerful, gives you more control. If you are going to be using Ubuntu or Linux in general; it's nice to have around, besides doing a superior work. Gparted is the best partitioner around. Period.

---

### Post by Chondro_Biak on 2008-08-15
Sweet... I will download it and give it a shot... 

I am still wondering if you have heard of this issue before...

---

### Post by Pumalite on 2008-08-15
You were partitioning your drive wrong. Follow my instructions.

---

### Post by Chondro_Biak on 2008-08-15
So are you saying you have to partition to get Ubuntu to work? 

I don't remember doing that before... Does the option "Use Entire Disk" no longer work?

---

### Post by Pumalite on 2008-08-15
It does. You can use it if you prefer it. Having a separate /home is nice in case of reinstall. You can keep your data and settings. In any case before you use 'Guided>Use Entire Disk'; use Gparted to delete everything in your hard drive and format it.

---

### Post by Chondro_Biak on 2008-08-15
The problem I am having is that I can install Ububtu using the entire disk. Then when it reboots the computer can't find the hard drive to mount it...

I was told that partitioning may fix this problem... I was curious if you had heard of that issue being caused by a big non partitioned HD?

---

### Post by Pumalite on 2008-08-15
I just used the entire disk on a 1000 GB drive. I partitioned first with Gparted Live CD just as I told you.

---

