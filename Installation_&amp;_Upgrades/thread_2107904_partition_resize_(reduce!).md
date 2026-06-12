---
title: "partition resize (reduce!)"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by desmane on 2013-01-23
Hi people, 

I need some advice before I start the following procedure, I hope someone is willing to think this through with me! 

The Problem: My Swap-Partition is a bit to small, if I have lots of memory in RAM and my System hibernates, sometimes I get a "not enough swap". Bad for battery and unsaved data! 

I have a 80GB Hard Drive, which is fully encrypted. I've got three partitions, root, home and swap in luks lvm. Swap needs to become bigger (2gb), home needs to reduce size in favour of swap! 

This is my stable system / production machine! The System is well configured and everything is awesome, so reinstalling and restoring is not an option for me. I have backups (rsync) of my root and home partition. Additionaly I am going to create an dd image of the drive, in case something goes wrong. 80GB is not that much! 

So, how does this work? I read guides on how to do this, but I am confused because I dont want to resize any volume group or something. 

Help is very much appreciated!! 

Any output will be provided as you whish!

thanks!

---

### Post by dino99 on 2013-01-23
what hibernate needs ? :

- at least 2 * installed ram
- at least 4 Gio

meaning : you need the highest value of the above minima for /swap

---

### Post by desmane on 2013-01-23
yes, thank you! So how do I proceed?

---

### Post by Cavsfan on 2013-01-23
I have 4GB memory and a 1GB swap file and the swap is never used. 
It suspends (sleeps)  fine.

---

### Post by dino99 on 2013-01-23
> **Cavsfan said:**
> I have 4GB memory and a 1GB swap file and the swap is never used. 
It suspends (sleeps)  fine.

the question is about "hibernate" which is way different of "suspend"; so no needs for confusion here.

---

### Post by dino99 on 2013-01-23
> **desmane said:**
> yes, thank you! So how do I proceed?

you need to resize the /swap partition:

- boot on a livecd/usb to be able to resize the partition(s), as they need to be unmounted
- use gparted to resize the partition(s)

as the partition(s) is/are modified, they get new uuids, so grub need to be aware:

sudo update-grub

---

### Post by Cavsfan on 2013-01-23
> **dino99 said:**
> the question is about "hibernate" which is way different of "suspend"; so no needs for confusion here.

My bad. Guess I misunderstood. I agree very different.

---

### Post by desmane on 2013-01-23
> **Cavsfan said:**
> My bad. Guess I misunderstood. I agree very different.

Nevertheless, thanks for trying to help though! 

I do suspend 99% of all times, swap is almost wasted space but hibernating still happens from time to time!

---

### Post by desmane on 2013-01-23
> **dino99 said:**
> you need to resize the /swap partition:

- boot on a livecd/usb to be able to resize the partition(s), as they need to be unmounted
- use gparted to resize the partition(s)

as the partition(s) is/are modified, they get new uuids, so grub need to be aware:

sudo update-grub

dino99, thank you for your reply. I've done that like 1000 times, in this case I have to deal with lvm and encrypted containers. So I am afraid I can't use gparted...

---

### Post by oldfred on 2013-01-23
I have never used LVM. But have a couple of links.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
lvm info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

    
       Resizing your encrypted file system can not be done directly as of yet with Gparted as Gparted sees the encrypted partitions as unformatted space.
How to: Resize an Encrypted Partition (LUKS)
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)

---

### Post by desmane on 2013-01-29
thank you!

---

