---
title: "Persistent partitions on USB?"
date: 2008-03-27
forum: Installation &amp; Upgrades
---

### Post by walkingbeard on 2008-03-27
Hi,

Questions for those in the know about installing on USB sticks:

What are these persistent partitions all about?  Why can't I just have a normal ext3 partition and a swap partition and be done with it?

What is Casper and how does it fit in?  I ask because it's used in the tutorial for 7.10 on pendrivelinux.

Thanks,

Beard

---

### Post by mrsteveman1 on 2008-03-27
Casper is the livecd system ubuntu uses. The reason you need a persistent partition with casper is that the main system image is a squashfs filesystem, which is compressed and read only. So there has to be a way to write changes to the disk.

However you don't have to do things this way if you have enough space on the stick, I've installed ubuntu to usb drives like normal hundreds of times. You don't want a swap partition on a usb stick though.

If the usb stick is big enough just run the real installer and install to the usb stick like normal with one big partition, it should install grub correctly and then you can boot from it.

---

### Post by walkingbeard on 2008-04-24
Thanks.

It's been a while, so maybe you won't ever read this, but thanks anyway.

---

### Post by mrsteveman1 on 2008-04-24
I see everything

/evil-laugh

actually i search by my user name for posts i've responded to so i can keep track of them and follow up :D

---

### Post by Confused_Phil on 2008-04-24
> **mrsteveman1 said:**
> If the usb stick is big enough just run the real installer and install to the usb stick like normal with one big partition, it should install grub correctly and then you can boot from it.

Hi mrsteveman,

I've got a 4GB usb stick, which I think should do the trick.  However, I've read that this reduces the life of the usb stick due the amount of read/writes that takes place on a full install.  Is this something to worry about - ie will it ruin my usb stick after 2 weeks or more like 2 years?

Thanks for any help.

Phil

---

### Post by mrsteveman1 on 2008-04-24
Up to a few weeks ago i ran a linux server from a 2gb USB stick, so that was a period of around a year.

Most of the files on a linux installation don't ever change though, so the stuff you would be updating and writing back to the stick all the time is a relatively small number of files.

I haven't seen any real problems though, the stick still works fine and doesn't have any bad blocks.

The numbers I've seen are that cheap flash chips can do around 10,000 write cycles per block, though they only guarantee the first block for some reason.

More expensive flash chips like the ones in the Iron Key can do 100,000 writes per block or more from what i remember.

In short, it isn't a real issue most of the time. If you write the same sector on a magnetic hard disk over and over they eventually fail too. Its worth noting that the EeePC and similar devices run full Linux installations from flash chips, though the original OS that comes with them only writes to a small percentage of the chip, because the rest of the chip is a read only partition.

---

