---
title: "Can i run 2 linux distros and a windows?"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by bbno3 on 2012-04-24
Can i run ubuntu 11.10, Backtrack 5 and WIndows 7 as a multi boot from my computer? so backtrack will appear on the grub boot menu??

---

### Post by ph4nt0m117 on 2012-04-24
Multiboot.  There should be an option during install.

It will list windows, BT, and w/e else you wanted.

---

### Post by RichardCain on 2012-04-24
Yes.
I'm not familiar with Backtrack, but in installing Ubuntu, the Grub setup should automatically detect other Linux installations and create Grub entries for them.

Just make sure to back everything up first!!  :)

---

### Post by mastablasta on 2012-04-25
Backtrack is Ubuntu based (basically ubuntu with hacking tools). not sure why would you need to have 2 Ubuntus... just add the programmes from backtrack to your current install.
 
but yes, you can multiboot like that.

---

### Post by Buddhika Udaya Sri on 2012-04-25
yes, you can multi boot,but why are you installing two Ubuntu versions . If you want more OS just try windows,   Ubuntu, Fedora etc. I didn't use Backtrack . but I think you can use same swap ares for both these destros. :p

---

### Post by robgraves on 2012-04-25
This is easy to do, just need to do the partitioning, however, backtrack shows up in GRUB as ubuntu, so it might get a little confusing.

---

### Post by km3952 on 2012-04-25
> **mastablasta said:**
> Backtrack is Ubuntu based (basically ubuntu with hacking tools). not sure why would you need to have 2 Ubuntus... just add the programmes from backtrack to your current install.
 
but yes, you can multiboot like that.

I thought backtrack was based on slackware; however, as has been said, it's just down to partitioning.

You only have 4 primary partitions to play with, but 1 of them can be made into an extended partition, which can then be sub divided multiple times.

I'm not familiar with multi booting with Win7, but others have done it. (I've done it with Win XP).

I believe your Win7 install will be using 3 of the 4 partitions so all of your Linux will need to go into the extended partition.

(More info should be available via the internet.)

---

### Post by Dngrsone on 2012-04-25
I am currently running Win 7, Ubuntu 10.04, and Ubuntu 12.04beta2 triple boot; so yes it can be done.

There's also your reason why someone might want to have two 'buntus-- one working and the other for testing/trying out.

My Windows install does own two of the partitions; a third is my swap, and the two Linux distros are in logical partitions on the fourth.

---

