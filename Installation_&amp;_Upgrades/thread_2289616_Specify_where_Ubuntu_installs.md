---
title: "Specify where Ubuntu installs"
date: 2015-08-05
forum: Installation &amp; Upgrades
---

### Post by jgedri on 2015-08-05
Hi, I'm New. Could someone tell me how to specify which partition Ubuntu installs in?

---

### Post by deadflowr on 2015-08-05
Be default Ubuntu installs the main root partition in the first partition(usually /dev/sda1), then also creates an extended partition(usually marked as /dev/sda2) and adds a single logical partition for a swap partition.(usually marked as /dev/sda5).

If you want to install Ubuntu to a specific partition or with a specific partition scheme in mind, you would have to use the Installation option "Something Else".

I'm not sure if this helps, but I hope it does.

---

### Post by howefield on 2015-08-05
I like to partition the drive before install, then select "Something Else" at the partitioning screen during the install process and mount the relevant partitions then.

If you have a specific scenario in mind, do share.

---

### Post by jgedri on 2015-08-05
I don't know what I'm doing if I choose 'something else'. Ideally, I'd like to have a system with Ubuntu and Windows 7 coexisting peacefully. Also, I don't know if this is possible, but I want to try running Windows 10 from a flash drive in order to give it a whirl without actually changing my system.

---

### Post by buzzingrobot on 2015-08-05
> **jgedri said:**
> I don't know what I'm doing if I choose 'something else'. Ideally, I'd like to have a system with Ubuntu and Windows 7 coexisting peacefully. 


That's dual booting.  Plenty of threads and guidance here on this forum.  It's a perennial question.  

Start here for the ISO's and info on burning to DVD/USB: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop).

Here's a page in the wiki about dual booting: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot).  Read it thoroughly.

---

### Post by jgedri on 2015-08-05
I don't want to know about dual booting. I want to know *how to use the partition manager *when I choose 'something else'.

---

### Post by oldfred on 2015-08-05
Many Windows 7 systems have used all 4 primary partitions. 
How many partitions do you have?
Often you can backup one and delete the data to convert to an extended partition which then can have an unlimited number of partitions. 
From Live Install's teminal mode, copy & paste into terminal & copy & paste output back here:
sudo parted -l

Several similar posts on using Something Else.
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by Dennis N on 2015-08-05
> **jgedri said:**
> I don't want to know about dual booting. I want to know *how to use the partition manager *when I choose 'something else'.

On the next screen, "Installation Type" 
**+** will add a partiton if you have selected unallocated (free) space;
**-** will delete a selected partition; 
**change** will reuse a selected partition.

You have to then fill in the details for the chosen action (except delete) in the popup box.

---

### Post by jgedri on 2015-08-05
Details?

---

### Post by yancek on 2015-08-05
The link below is about as detailed as you will find.  Best to read it top to bottom, especially if this is all new to you.

 [http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

An extremely detailed tutorial on using GParted, the graphical partition manager which comes with Ubuntu is at the link below.


[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by jgedri on 2015-08-05
Sorry; I was referring to what Dennis said.

> You have to then fill in the details for the chosen action (except delete) in the popup box.

Good news: I have Ubuntu installed, safe and sound.

---

