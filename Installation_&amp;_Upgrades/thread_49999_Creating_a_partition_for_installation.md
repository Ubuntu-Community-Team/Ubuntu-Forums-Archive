---
title: "Creating a partition for installation"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by lbut on 2005-07-18
I want to install Ubuntu on a hard disk where Windows XP is already installed, however I want to keep  both OSs, and activate dual booting. What exactly is a partition and how can I successfully install Ubuntu without messing up my Windows XP os? 

Thank-you very much for anyone who can help.

---

### Post by damonw5 on 2005-07-18
[QUOTE=lbut]I want to install Ubuntu on a hard disk where Windows XP is already installed, however I want to keep  both OSs, and activate dual booting. What exactly is a partition and how can I successfully install Ubuntu without messing up my Windows XP os? 

Thank-you very much for anyone who can help.[/QUOTE]
 Hi lbut and welcome to Ubuntu Forums!

A partition is like... Well, imagine your hard drive is a room. You can put up (moveable) walls that split it up into parts, almost like each part is its own "room" or "hard drive". Then you can have Windows in one "partition," linux in another, etc.

To install Ubuntu, you need to free up some space by resizing that Windows partition to a smaller size. I'd reduce it by at least 5gb, if not more. I believe the installer lets you resize the Windows partition.

Next, in this free space, you need to create two partitions for Ubuntu: a "swap" partition that's about twice the size of the amount of RAM you have, and one "main" partition, which will be type "ext3" that takes up the rest of the free space.

Then you can install Ubuntu on the "main" partition, (setting its "mount point" to "/"), telling it to use the swap partition as swap.

Notice that you DO NOTHING to the Windows XP partition except resize it. DO NOT install Linux on your XP partition, "format" the XP partition, or anything but resize it.

You can play around with the partitioning tool all you want without making changes as long as you don't commit to those changes. If you have any questions, please ask first! It's easy to do, but if you do it wrong you could lose data.

When the installer asks if you want to install "GRUB" to the "master boot record (MBR)", choose yes. This is a program that will let you choose between Linux and Windows as soon as you turn your computer on. It will automatically detect windows and add it to the list of options.

Damon

---

### Post by WildTangent on 2005-07-19
just to clarify, the install CD CANNOT resize partitions. first, you need to defragment your hard drive. right click your C: drive in My Computer and select properties, in this window, select the tools tab, and find the defragment button. this may take a long time depending on the size of your hard drive, how much data is on it, and the last time youve defragged it. next, you need to get a program for windows called Partition Magic. it should have instructions for resizing partitions. like the previous poster said, reduce it by 5GB or more (assuming you have enough free space to do so). then, put in the Ubuntu CD and reboot. when it asks you where you want to install it, there should be an option that says something like "largest contiguous free space" or something like that. from there, the default choices should be adequate. just make sure you DO NOT FORMAT A PARTITION CALLED **HDA1**!!!!!

-Wild

---

### Post by lbut on 2005-07-19
Yes, OK I understood, thanks a lot. But do I have to buy Partition Magic? Is there a free program to do a similar job? 

Thank-you  :smile:

---

### Post by mingus on 2005-07-19
Umm . . . the installation partition program **can** resize partitions, and will offer you the option of resizing XP's NTFS partition.

As indicated above, it is wise to prepare the XP partition ahead of time.  The disk should be defragmented (Start/Accessories/System Tools/Defragmenter).  However, before doing that you should run Chkdsk to fix any filesystem errors; as I recall you can find that in XP under MyComputer/Properties/Advanced.  Be sure to check all the options.  Chkdsk will run when you next reboot, and the process could take a while.  Then after defragmentation, backup up your data.

Having prepared the partition, it's likely that the Ubuntu installation partitioner will be able to resize it.  If the installer's safety checks prohibit it from doing so, you can cancel the installation and resize with another tool.  You can download a Knoppix or SimplyMEPIS live-CD and use the program QTParted for this.  Note that on rare occasion it is necessary to use PartitionMagic, which has more features than these other programs.

Finally, since you will be setting up a dual-boot machine, for maximum safety, consider doing one of the following:  (1) In the Ubuntu installer, when you get to the step to install the grub boot loader, it will see XP and ask you if you want to install grub to the Master Boot Record or a different device.  Select the MBR but *also* "go back" and repeat this step except this time install grub to a floppy disk.  Type "/dev/fd0" where it asks for a device.  This assumes your computer can boot from floppy.  Or, (2), makes sure you have either a W2K/XP install CD or a W98/ME bootable diskette.  In the event that there is a problem with the dual-boot later, having one of these floppies or CD's will allow you to boot and fix the problem.

These steps and precautions are recommended whenever partitions are being changed and another OS is being installed, regardless whether that OS be Linux or W$.

---

### Post by not_yet on 2005-07-19
the ubuntu installer can resize your windows NTFS partition as mingus has suggested

after  reading mingus's excellent instructions look here 

[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)

for a visual on how to set up your partition

cheers

---

### Post by lbut on 2005-07-19
Ok, I installed linux and windows is still ok, i activated dual booting, its great! I love linux! Anyway, now that everythings installed and working, and I gave linux a partition of 20 gb, how exactly do you set up internet access? I had tried using the live cd but without success... :neutral:   that was before I installed linux.

Thank-you to all the people who helped me install linux  :)  I would have never succeded...  :) 

Luke

---

### Post by mingus on 2005-07-19
[QUOTE=lbut]how exactly do you set up internet access?
Luke[/QUOTE]

That depends on what your network access is.  Dial-up, DSL, cable?  Thru a router on a LAN; wireless or wireline?  etc.

---

### Post by az on 2005-07-19
[QUOTE=lbut]Ok, I installed linux and windows is still ok, i activated dual booting, its great! I love linux! Anyway, now that everythings installed and working, and I gave linux a partition of 20 gb, how exactly do you set up internet access? 
Luke[/QUOTE]

Time to start a new thread about it:  That way, the solution can help others, too!

Link you new thread here so that everybody can follow from here, too...

Thanks!

---

### Post by lbut on 2005-07-19
Post continued here: 

[http://ubuntuforums.org/showthread.php?p=262416#post262416](http://ubuntuforums.org/showthread.php?p=262416#post262416)

 :)

---

