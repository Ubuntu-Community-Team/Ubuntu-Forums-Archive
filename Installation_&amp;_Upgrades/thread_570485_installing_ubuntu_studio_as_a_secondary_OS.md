---
title: "installing ubuntu studio as a secondary OS"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by suya4ocha on 2007-10-08
I have Windows XP as primary OS and right now I want Ubuntu Studio on my notebook as secondary OS [ learning to use Linux ]
the condition of my notebook is:
1 HDD with 3 partition
C [ windows] = 35GB [ 7GB free ]
D [data] = 39GB [ 2GB Free ]
L  [was prepared for Ubuntu] = 2.9GB [ empty ]

I want to install the Ubuntu Studio at L
how should I install it? I did not understand with the partition section on installing process [ and so I exit the Ubuntu setup when I try it for the first time ]

Do I need more partition to be prepared?

---

### Post by por100pre1 on 2007-10-08
The easy way is to delete L partition with Gparted or other partitioning tool and select the Guided - use largest free space option to install. However, you must give some more space to Ubuntu Studio install.

---

### Post by dabl on 2007-10-08
> **suya4ocha said:**
> 

L  [was prepared for Ubuntu] = 2.9GB [ empty ]



I'm afraid you're 4 or 5GB short of enough space for Ubuntu.  The basic system will need around 4.0 - 4.5GB, and then you need to allow for some music files or whatever you want the Studio for.  So you probably need at least 8GB to do anything substantial with it.  :)

---

### Post by suya4ocha on 2007-10-10
> **por100pre1 said:**
> The easy way is to delete L partition with Gparted or other partitioning tool and select the Guided - use largest free space option to install. However, you must give some more space to Ubuntu Studio install.

It's work for the Installation, but **thank you for the big trouble**
after following your suggestion all my Partition was merged
and my windows XP installation is gone and worst, all my files that worth 5 years hunt are gone [ music, softwares, documents, videos, images, my design, my website, my games, and all my best configuration

now I can't do anything!
no documents, no tools, no music, no image and nothing

**To dabl**
The Ubuntu Studio that I installed yesterday [ and give a big damn trouble ] is only occupy not more than 2,5 GB plus 1,4 GB swap

---

### Post by suya4ocha on 2007-10-19
@all
I have solved my own problem and got dual boot [ Linux Ubuntu Studio and Windows XP ]
here is the "how to"

1. make two more partition on your PC [ assuming you're using windows xp and wants to get on Linux ]
2. the first partition most worth more than 4 GB and the second [swap]  is worth twice of your RAM [ if your RAM is 512 MB this partition should occupy at mn 1GB ]
3. boot the ubuntu studio installation and proceed till the partitioner comes
4. on the partitioner, make sure that your windows xp and your other partition [ excluding two new partition above ] are mounted as "/media/hdc/sda*/" and marked "K" [ K means the partition will be left as is ]
5. for the 4GB partition set it as ext2 file system, and the 1GB [ on 512 RAM ] as swap
finish

---

### Post by Fantomäs on 2007-10-21
Hi all,

Same here but my PC has a Q6600 and 2GB of RAM. Plus I have two HD, one 75GB raptor only for system and progs, and 500GB WD for data. I would like to install Ub Studio 7.10 64-bit, making 25GB space on the raptor mainly for music. 

I would like to know if Ub Studio is going to see the second HD and beign able to use the content such as .wav files I create in XP?  Plus, do I need a 4GB swap? I read somewhere that 2GB is the limit.


Thanx for helping

---

### Post by suya4ocha on 2007-10-21
> **Fantomäs said:**
> Hi all,

Same here but my PC has a Q6600 and 2GB of RAM. Plus I have two HD, one 75GB raptor only for system and progs, and 500GB WD for data. I would like to install Ub Studio 7.10 64-bit, making 25GB space on the raptor mainly for music. 

I would like to know if Ub Studio is going to see the second HD and beign able to use the content such as .wav files I create in XP?  Plus, do I need a 4GB swap? I read somewhere that 2GB is the limit.


Thanx for helping

well i read on a magazine that we should use 2 x RAM for swap
but if they say 2GB is the limit, then you should use 2 GB
I think swap works just the same as page file / virtual memory on windows

---

### Post by Fantomäs on 2007-10-21
but I 'm not sure about that, could someone confirm please?

---

