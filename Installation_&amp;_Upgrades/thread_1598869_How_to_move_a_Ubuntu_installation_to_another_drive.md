---
title: "How to move a Ubuntu installation to another drive?"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by dtwai on 2010-10-17
Hi Guys,
I'm having 3 harddisk and I'm going to move my Ubuntu 10.04 from one partition to another because I would like to have Windows on my computer for emergency purposes. Also the 12GB Ubuntu partition is going to be full.

Now I have the following config:
80GB HDD
[74GB ext4][Swap]

250GB HDD
[100GB NTFS][Free Space which Windows will install][20GB Backup]

500GB HDD 
[3 NTFS partitions][Extended partition[12GB Ubuntu][Swap][300+GB NTFS]]
(Can't think of a better way to describe it)

Can I put Ubuntu to the 80GB drive without reinstalling?
Also, I don't put the 250GB one in the system when I am using Ubuntu, so it can have its own NT bootloader.

Thanks :)

---

### Post by krishnandu.sarkar on 2010-10-17
I didn't understand your query. Do you already have Ubuntu on 80GB HDD..??
In that case just install Windows and follow [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) to restore Ubuntu.

---

### Post by dtwai on 2010-10-17
I only have Ubuntu on the 500GB HDD, and grub2 installed on the 80GB one.
Also, I just want to move my installation from the 12GB partition to the whole 80GB HDD.

BTW, GParted seems not working on my 500GB HDD. It keeps saying I have exceeded the disk at the partition, and I see negative bytes on the Disk Utility.

---

### Post by krishnandu.sarkar on 2010-10-17
Well..I think you can clone the existing system with clonezilla and put it in 80GB HDD. But I'm not sure whether you can extend the parition from 12GB to 74GB after that.

You may use GParted after that to extend it, but I'm not sure whether GParted can handle that.

---

### Post by dtwai on 2010-10-19
> **krishnandu.sarkar said:**
> Well..I think you can clone the existing system with clonezilla and put it in 80GB HDD. But I'm not sure whether you can extend the parition from 12GB to 74GB after that.

You may use GParted after that to extend it, but I'm not sure whether GParted can handle that.

Thanks. It worked.
Just reinstall Grub2 after moving the partition in a Live CD or USB, and I can boot to both Windows and Ubuntu.

---

### Post by krishnandu.sarkar on 2010-10-22
I'm glad that it worked. Enjoy :)

---

