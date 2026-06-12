---
title: "Problems installing OpenElec with Windows 7!"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by killernads on 2012-11-09
Hi Guys,

Have been stuck on trying to create a Dual Install of OpenElec+XBMCEden and Windows 7 for the past two days now! 
Im on the verge of giving up after so many unsuccessful attempts.  :(  

I have used a variety of different guides, and im just missing a point somewhere or maybe its just not possible?!

Ok, heres what I'm doing (all installs via Bootable USBs):

- I have one SSD 64GB hard drive.

Option 1:
- First i install the OpenElec from bootable USB. It shows that i only have one disk, i do the install successfully!
- Second, i boot into Ubuntu from USB, run the Gparted partition software and resize the STORAGE partition.
- I then make a Windows NTFS formatted partition with the unallocated space!
- I also now have a 4th partition which i have tried leaving formatted for DATA and also just leaving it unallocated.
- I then load the windows 7 installer from USB.
- I try to select the Windows Partition i created earlier from Gparted to install to.

Then the error comes:
Windows can not be installed on a GPT partitioned hard disk!

Why is this happening as ive followed the guides accurately?!?


Option 2:
- First i install the OpenElec from bootable USB. It shows that i only have one disk, i do the install successfully!
- I then load the windows 7 installer from USB.
- I create a new partition for windows 7 on the unallocated space.
- Install windows successfully.

Problem:
I can now never boot into my OpenElec partition, and it only ever recognises my windows install.


Option 3:
- Boot into Ubuntu
- Use Gparted to create 4 partitions (windows ntfs, ext4 partitions for openelec)
- Boot up OpenElec install.
- The install option only shows me one 64GB hard disk partition (dev/sda) to install to, and doesnt list out any of the seperate partitions?!
- Windows can install fine though.


Any help would be greatly appreciated!

Thanks.

---

### Post by grahammechanical on 2012-11-09
I cannot give you expert advice. I can only pass on the little bit I have learned from the advice that others have given to similar problems.

1) It is my understanding that Windows need to be installed first. It has to be in the first partitions of the hard disk.

2) You must use Windows utilities to de-fragment the Windows partitions and to shrink them or delete them to create space for Ubuntu partitions.

3) If Windows creates four primary partitions then you cannot install another OS unless you turn one of those partitions into an extended partition that can be used to create logical partitions into which Ubuntu can be installed.

4) Windows sometimes looks like it has created primary partitions when in fact it has created what Microsoft calls dynamic partitions. Ubunut cannot be installed into a dynamic partition. You have to do some kind of a conversion to get actual primary partitions.

5) That is all I can think of.

Regards.

---

### Post by killernads on 2012-11-09
Thanks for your help mate.

However, i have tried that way also. ie. installing windows first then trying to install openelec.

The problem is that when i try to install openelec the problem i get is that it doesn't recognise separate partitions, it only recognises the whole disk as one partition! So i cant install it to one partition!

---

