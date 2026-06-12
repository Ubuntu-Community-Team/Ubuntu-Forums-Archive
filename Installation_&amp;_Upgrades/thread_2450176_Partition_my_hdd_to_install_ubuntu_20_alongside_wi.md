---
title: "Partition my hdd to install ubuntu 20 alongside with windows 10"
date: 2020-09-09
forum: Installation &amp; Upgrades
---

### Post by ahti-sc on 2020-09-09
I want to install ubuntu 20 without messing up windows 10.

Here is my current partitions: [https://ibb.co/JF3CWzX](https://ibb.co/JF3CWzX)

As you can see partition C is windows partition, E and D is filled with important data and there is just 60GB free available space although I can make more space available by moving data of partition D to E and delete D partition to make a total available space 310GB (250gb + 60gb). I would do it in order to run ubuntu as fast as possible. I will use ubuntu for programming, browsing, learning ubuntu e.t.c

My laptop specs:

Core i5 6th gen
8gb ddr4 ram 
1TB hdd

So which partitions I need to create and how much in my case for heavy use of ubuntu ?

---

### Post by Impavidus on 2020-09-09
If you wish, you can squeeze Ubuntu in 15GB. 30GB is comfortable for the OS. How much more you need depends on your file storage habits. Note that your D and E partitions can be used from both Windows and Ubuntu for simple data (not for your home directory or executables or anything else that cares about permissions).

To get more than 60GB for Ubuntu, first shrink one or more of the Windows partitions. If you shrink E, you have to move D, so that all unallocated space is one continuous block. Reboot Windows a few times to let it run its filesystem checks. The Ubuntu installer can use this block of unallocated space to make its partition.

BTW, you do have backups of your important data, right? Because hard drives fail, computers get stolen, people format the wrong partitions or delete the wrong files etc.

Added: Make sure about 10% of the space allocated to Ubuntu remains unused. This will prevent fragmentation and speed up access to the drive. On SSDs it allows wear levelling to do its job. Other than that, the size of the partition has no effect on how fast Ubuntu works. You don't need a lot of disk space for programming, browsing and learning Ubuntu. You may need it for video editing, a media server or virtual machines.

---

### Post by ahti-sc on 2020-09-09
So do I have to create just two partitions ? root and home ? I am planning to keep my root partition to 80GB so that I have more space to install applications and home partition to 120GB rest will be for windows.

---

### Post by ActionParsnip on 2020-09-09
You can have one partition for everything. a separate /home partition isn't mandatory

---

### Post by ahti-sc on 2020-09-09
But itsn't swap partition necessary to seep up programs if run out of ram ?

---

### Post by Impavidus on 2020-09-09
You don't have to create multiple partitions, but it's sometimes recommended. You can create a swap partition, but Ubuntu can use a swap file too. A swap file is the default nowadays, but it's your choice. You can create a /home partition, which makes it easier to reinstall your OS (or install a new release). If you allocate more than 50GB to Ubuntu, I'd make a separate /home partition. But you have to choose reasonable partition sizes, or one partition will get full with another mostly empty.

You have to install some very big applications to fill a root partition of more than 30GB. Linux tends to be more space-efficient than some other OSs.

---

