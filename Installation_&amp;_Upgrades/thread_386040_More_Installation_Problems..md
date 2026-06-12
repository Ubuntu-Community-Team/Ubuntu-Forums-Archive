---
title: "More Installation Problems."
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by Kaphix on 2007-03-16
When I try to install it gives this error:

No root file system is defined.
Please correct this from the partitioning menu.

These are my partitions:

/dev/sda2 ext3 30 gigs
/dev/sda1 ntfs 30 gigs boot
/dev/sda3 extended 10 gigs
     >/dev/sda5 linux-swap 10 gigs

---

### Post by dannyboy79 on 2007-03-16
you need to define a partition as / (commonly referred to as root) also, you can't have your /boot partition be an ntfs formatted partition. also, linux can't even support more than 4gb for swap nor would it ever even use it. go with the same as the amount of physical ram you have or 1.5 times the amount (ie if I have 1 gb of ram, I would either go with 1 gb or swap or 1.5gb of swap)

here is what you should put when you're partitioning your system with gparted.

/boot only needs to be 50mb minimum I would say, others may say you don't need a /boot partition, others may say you want it to be a different size, it's all about preference. format it as ext3

/ is going to be your main hard drive, where basically everything is kept, system files, programs etc etc. make this at a min 10gb. format it as ext3

/swap I have already told you the suggested size.


make an extended partition, then make /home there. use remaining size

/home  this is where all your settings will go for all your programs, customization stuff. also, you can put your personal stuff here, so you'll want this to be large. use remaining size, format as ext3

if you have a ntfs partition already and you don't want to change or format it, than make sure that the check box for format is unchecked. this is done in the manual partioning sceme.

---

