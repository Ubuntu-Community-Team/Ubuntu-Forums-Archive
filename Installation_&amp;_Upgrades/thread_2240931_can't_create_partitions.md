---
title: "can't create partitions"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by ali29 on 2014-08-23
I'm having a problem installing Ubuntu(14.04) and Elementary OS(luna). at both installations it gives me the same error, no partition tables shows, nor i can create one. here is an image from the installation of Luna :
 [IMG]http://i.imgur.com/oop1j22.jpg[/IMG]

---

### Post by grahammechanical on 2014-08-23
Do you have a hard disk in that machine? I ask because you give no information about your hardware. You do not tell us if you have another OS installed. If you can run a Ubuntu Live session, then run it and open Gparted and take a screen shot of what it shows of your hard disk. Also open the Disks utility and take a screen shot of what it shows about your hard disk. And post the screen shots here.

If you have another OS in that machine use a utility that shows the partitions on the hard dsik and take a screen shot of what it shows about that hard disk.

---

### Post by ali29 on 2014-08-23
thanks for the information supplied. So i run Windows 7 home premium (SP1), HP Envy 6 notebook, 6gb RAM 64bit operating system , HDD 500GB. [IMG]http://i.imgur.com/VPDuRXz.png[/IMG]
I think these arethe partitions. 
Thanks :)

---

### Post by Mark Phelps on 2014-08-23
You already have the limit of 4 partitions on the drive -- the installer won't let you create any more. If you force the creation of a fifth with Windows tools, it will automatically convert all your partitions into Dynamic Disks -- something you do NOT want.

Since you have an HP Tools partition, read through the material below ...

Preinstalled Win7 PCs typically come with a small boot partition, a large OS partition, a Recovery partition, and (in the case of HP) a Tools partition.  

If you have this last one, that's the logical one to remove. So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by ali29 on 2014-08-24
Thank you for your reply. I did everything you mentioned above. I runed the Elementary OS install and the same result was showing(like in the first image). Now i have 2 partitions(OS and SYSTEM). 

Thanks for your support :)

---

