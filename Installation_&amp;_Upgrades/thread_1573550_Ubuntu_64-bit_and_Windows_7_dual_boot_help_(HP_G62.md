---
title: "Ubuntu 64-bit and Windows 7 dual boot help (HP G62 notebook)"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by II Traveler II on 2010-09-12
Hey guys! I'm a bit of a Linux n00b :p, so I was hoping someone out there could help me. 

I'm trying to install a dual-boot setup with Ubuntu 64-bit and Windows 7. I've followed the steps until you get to step 4, and then my screen looks like this: [http://farm5.static.flickr.com/4084/4985150566_b898815996_b.jpg](http://farm5.static.flickr.com/4084/4985150566_b898815996_b.jpg) . 

I know that usually on this screen there is a simple slider, letting you choose how much Windows space and Ubuntu space you want. Since the partitions are set up strangely with the factory settings on the HP G62 notebook, Ubuntu seems to think that I have many operating systems on the laptop. When I choose "Specify partitions manually", this is the screen I see: [http://farm5.static.flickr.com/4128/4985150676_c0e3c19cdf_b.jpg](http://farm5.static.flickr.com/4128/4985150676_c0e3c19cdf_b.jpg) (NOTE: /dev/sdc and /dev/sdc1 is my flash drive, so that wouldn't be displayed when I actually install the OS).

Now I have tried creating an empty, unformated partition via G-parted, but Ubuntu says that the newly created partition is unusable. Speaking of G-parted, this is what is displayed when I run the program: [http://farm5.static.flickr.com/4148/4984548941_65ae74db62_b.jpg](http://farm5.static.flickr.com/4148/4984548941_65ae74db62_b.jpg) . I can't seem to do anything with that 5.18 MB: I can't merge it into another partition. Thus it just sits there all alone...

One forum I read suggested defragmenting the hard drive. I have done that, but the same thing still happens.

Last but not least, here are the specs on this laptop:
Pentium (R) Dual-Core CPU
3 GB of DDR2 RAM
Intel integrated video card (I'm not sure which model).

Thanks so much for your time :D!

---

### Post by presence1960 on 2010-09-12
You have 4 primary partitions. You need to back up data on one of them and delete that partition. You can then make an extended partition from that unallocated space. Inside that extended partition you may create as many logical partitions that you want. The only limit on that is how much space you allot for the extended partition. You can use gparted Live CD to do this. Then you can install ubuntu to the logical partition from the Ubuntu Live CD.

If this sounds confusing here is some reading to get you up to speed:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

You really need to understand this or you risk wiping all your data and OSs if you do not understand partitioning basics. If you can't grasp the concepts then it may be best to study further or ask someone who knows how to partition hard disks to do it for you and install ubuntu also.

---

### Post by II Traveler II on 2010-09-13
Thanks presence1960! I'll think about it and see if it's worth the slight risk. Sheesh, why can't PC manufacturers just leave stuff alone lol...

---

