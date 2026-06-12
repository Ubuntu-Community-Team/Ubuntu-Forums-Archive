---
title: "Help with the partitions from hard disk"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by gurrunaki on 2012-05-20
Hi all, I try install ubuntu 12.04 in my laptop Toshiba Portege Z830 and I try make a dual boot with the win 7 64 that come with it. I use unetbooting for try the distro and when I decided install it is coming my problem with the partition, they show many of them and I want use 25 GB for ubuntu 12.04, I'm a bit loss, can I have some help? I attach a image from the step where I got stuck.

Thanks in advance

---

### Post by jadtech on 2012-05-20
ok so you have win7 install . Have you already booted windows done a defrag and ran check disk and after that it is best to shrink  the window volume from windows its self I know your plan say 25gb that is ok how ever 35gb to 60gb would be Ideal this in thinking ahead would give you space if you like ubuntu better then window to grow longer term .. 

once you have  got the defrag and check disk complete ready to shrink disk go to control panel type in partition the link to  where  you can shrink the partition will popup if you right click on the windows partition when you are there on the menu you will see the shrink volume option 

the nuimber you type in are in MB so for 25gb you would type in 25000 this will unallocate 25 gb when that is done just exist and you are ready again to boot ubuntu disk or usb again .. 

once you get back in to install you will see the area you set free on the drive for ubuntu to install..

you need at least 2 logical partition 1  for swap should be at least 2gb  the rest for / (root)

---

### Post by gurrunaki on 2012-05-20
Thanks a lot for your fast answer, I will try what you said, first I will try understand everything cos I'm not so good with all of this and I will let you know.

Thanks!!!

---

### Post by darkod on 2012-05-20
You have 4 primary partitions on the disk. You can't create more partitions.

To install, you would have to do two things:
1. Delete at least one partition (you must NOT delete sda1, the win7 boot files are there). That would allow you creating logical partitions for ubuntu.
2. Make sufficient unallocated space (not belonging to any partition) for ubuntu, depending how much space you want to use for it.

To make the space, you can delete sda3, depending what you have there. That will create some unallocated space. You will also need to shrink sda2 using windows Disk Management. Because sda2 and sda3 are next to each other, the created unallocated space will be one single space as you need it. When shrinking sda2 be careful to shrink it from the end where sda3 was so that the unallocated space stays in one.

After that you can install into that space.

---

