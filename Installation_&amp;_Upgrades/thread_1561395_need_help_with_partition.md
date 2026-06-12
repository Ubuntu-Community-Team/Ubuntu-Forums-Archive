---
title: "need help with partition"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2010-08-26
Hello  
 my windows crashed so i switched to linux completely.
 I used ubuntu 10.04 cd to boot my system.
 At the point of partition selection i selected erase and use disk completely. I thought that it'll erase only one drive and will use it. But instead it erase all my drives and installed there. Now the problem is all is have is just one drive and linux installed in it. I want to create some partitions for my movies and other types of files.
 Can anyone please tell me how to do it. Reformatting and installing the linux again is not possible for me as i updated and installed many softwares in it.
 Please reply
 thank you

---

### Post by plucky on 2010-08-26
> **c2tarun said:**
> Hello  
 my windows crashed so i switched to linux completely.
 I used ubuntu 10.04 cd to boot my system.
 At the point of partition selection i selected erase and use disk completely. I thought that it'll erase only one drive and will use it. But instead it erase all my drives and installed there. Now the problem is all is have is just one drive and linux installed in it. I want to create some partitions for my movies and other types of files.
 Can anyone please tell me how to do it. Reformatting and installing the linux again is not possible for me as i updated and installed many softwares in it.
 Please reply
 thank you


Welcome to the forum

Open a terminal (**Applications > Accessories > Terminal**) and post the output of ```
sudo fdisk -l
``` It will ask you to input your password,but will not echo it.

To resize your / partition,it is best to use the Live CD and run the partition program (Gparted) from **System > Administration > Gparted**

---

### Post by viralmeme on 2010-08-26
> **c2tarun said:**
> I want to create some partitions for my movies and other types of files

Post the output of [Qparted]("http://gparted.sourceforge.net/screenshots.php")

---

### Post by c2tarun on 2010-08-26
> **plucky said:**
> Welcome to the forum

Open a terminal (**Applications > Accessories > Terminal**) and post the output of ```
sudo fdisk -l
``` It will ask you to input your password,but will not echo it.

To resize your / partition,it is best to use the Live CD and run the partition program (Gparted) from **System > Administration > Gparted**


reply of sudo fdisk -l


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e8409

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37814   303735808   83  Linux
/dev/sda2           37814       38914     8833025    5  Extended
/dev/sda5           37814       38914     8833024   82  Linux swap / Solaris

---

### Post by c2tarun on 2010-08-26
> **viralmeme said:**
> Post the output of [Qparted]("http://gparted.sourceforge.net/screenshots.php")


Qparted is not working my friend

---

### Post by c2tarun on 2010-08-26
come on.... :(
please help me!!!!

---

### Post by plucky on 2010-08-26
You have to boot the Live Cd and run Gparted from there (**System > Administration > Gparted**) as it will  not allow you to resize or move a mounted partition.

It is not that difficult, give it a try.

---

### Post by c2tarun on 2010-08-31
view this page for complete step by step procedure.


[http://tricksfind.blogspot.com/2010/08/how-to-create-partitions-after.html](http://tricksfind.blogspot.com/2010/08/how-to-create-partitions-after.html)

---

