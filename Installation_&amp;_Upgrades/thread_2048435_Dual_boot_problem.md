---
title: "Dual boot problem"
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by tomaasj on 2012-08-26
Hallo anyone,

dualboot problem:

I used gparted to create partitions:

first partion 160 GB NTFS
2nd partion 300 GB Ext4
3rd partition 4 GB Linux-Swap

I first installed Vista on the NTFS partition.  Restarted the laptop and it works.

Continued with the install CD for Ubuntu 11.04.  Seemed to go fine.  No hickups.

Did not use the option to have Dual Boot process. Went on with the alternative advanced option.  I got to the point that I was able to choose the 2nd partition of 300 GB and assigned it boot (/) and continued to install Ubuntu 11.04.

After restart I did not get the possibility to choose between the operating systems, instead it simply started up Vista.

What did go wrong and what do I have to do to get the option to choose between the installed operating systems when the laptop starts up ?

If anyone has a suggestion, would be appreciated.

Thanks in advance,

---

### Post by Finnicella on 2012-08-26
It can be a grub problem.
Try to reinstall it in your HD.
This is the link:
[https://help.ubuntu.com/community/Grub2/Installing]("https://help.ubuntu.com/community/Grub2/Installing")

---

### Post by darkod on 2012-08-26
Also, any particular reason you decided to install 11.04? In October the support ends, it will be end of life. There will be no more updates issued for it.

I suggest 12.04 LTS since this is a new installation anyway.

When you were installing, in the partitioning step, where did you select to install the bootloader? On the MBR of the disk, which is like /dev/sda, /dev/sdb, etc?

Or on some partition like /dev/sda2? If it has a number then it's a partition and grub2 needs to be on the MBR not on a partition so that it can be booted.

---

### Post by tomski on 2012-08-26
sounds to me like you have installed grub on the wrong partition.
When you installed vista it inserted the M$ loader in the MBR which windows will see as the first few bits of the first drive (first partion 160 GB NTFS) & when you installed ubuntu & opted to install grub to / (root) you have installed it to the second partition but you need it inside the MBR.

use the above link given by Finnicella & install it to hd0,0 or /dev/sda & all should be well

---

### Post by darkod on 2012-08-26
> **tomski said:**
> 

use the above link given by Finnicella & install it to hd0,0 or /dev/sda & all should be well

(hd0,0) is not /dev/sda. In fact, with grub2 the second parameter can never be 0 since it starts counting from 1. Grub1 was counting partitions from 0.

With grub2, the MBR of /dev/sda would be only (hd0). But using /dev/sda is much easier and better.

---

### Post by tomski on 2012-08-26
> **darkod said:**
> (hd0,0) is not /dev/sda. In fact, with grub2 the second parameter can never be 0 since it starts counting from 1. Grub1 was counting partitions from 0.

With grub2, the MBR of /dev/sda would be only (hd0). But using /dev/sda is much easier and better.

opsie lol
noted!!!!

---

### Post by tomaasj on 2012-08-26
Thanks for the info.  I need to do some studying on it further.  When I faced the install options, I simply chose to install Ubuntu on the second partition.  It only went ahead when I designed it as /.  I do not recall for giving me the option to put the Grub in the MBR.
I am new to all this and will take the info from all of you and try to go ahead.

---

### Post by tomaasj on 2012-08-26
I do not recall having the option to install Grub2 anywhere.  I only could go ahead by designating the partition with the Ext4 filesystem as root.

I will look at it again.

---

### Post by darkod on 2012-08-27
> **tomaasj said:**
> I do not recall having the option to install Grub2 anywhere.  I only could go ahead by designating the partition with the Ext4 filesystem as root.

I will look at it again.

At the manual partitioning step, under the windows with the list of the partitions on the disk, there is the drop down box for selecting the bootloader destination.

You need to install it on the MBR of the disk, if you have only one hdd, that is /dev/sda. Without any number in it.

---

### Post by tomaasj on 2012-08-29
Because of all the helpful comments, I got my dualboot on the laptop up and running.

Thank you all for responding !

gr. Tomaasj

---

