---
title: "Triple boot on a 320 gb internal drive"
date: 2011-07-31
forum: Installation &amp; Upgrades
---

### Post by cybertronix on 2011-07-31
Hi all, I would like to triple boot vista, opensuse and ubuntu.

I need to set aside 165 gb for Vista (which has been backed up to an external drive).  

Would like to make a fresh install of Ububtu and Opensuse with Ubunto being the main OS.  I figured 100 GB for Ubuntu and 55 GB for Opensuse would probably be fine (the remainder I need to set aside for Vista).

Ive popped in the Ubuntu DVD and am about to install it but am stuck on the  "allocate drive space" part.  I do not understand how to partition the hd and what to set each partition to in the "Use as" and  "Mount Point"

Any suggestions? 

Many thanks

---

### Post by oldfred on 2011-07-31
I do not know opensuse. But I would install Ubuntu last as that installs grub2's boot loader automatically to the MBR of your sda drive.

If opensuse is using grub legacy, I would install it's bootloader to the same partition as opensuse. Some other distributions require a separate /boot.

You cannot share /home and since you also have windows I would create another partition for NTFS shared data. All your system can then read/write into that shared partition. I do not suggest read/write into other install's system partition as that can lead to issues.

If you are writing most data into a shared partition you do not need a large system partition. You also should be able to share swap unless you really want to hibernate which with multiple installs is probably not a good idea anyway.

Yoiu can do 25 to 50GB for both Ubuntu & Opensuse with all the other space as the NTFS shared. Your Vista install may not have to be as large if you are putting most data into the shared also.

I have my Firefox & Thunderbird profiles & all photos in my Shared NTFS so I can use the same data in XP and several Ubuntu installs.

---

### Post by gordintoronto on 2011-07-31
Did you shrink the Vista partition to 165 GB, using Windows?

---

### Post by oldfred on 2011-07-31
I prefer to partition in advance & just format & choose which partition is / (root) and which is swap. 

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

