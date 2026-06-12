---
title: "Grub error 18 after installing 7.10"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by brad1150 on 2008-03-11
After I installed ubuntu 7.10 and did the first restart I got error 18. I am using an old computer, i don't know how, or even if there is an upgrade, to update the bios on the mainboard. I don't know how to make or move partitions in grub, it will not boot a disc. I have my main partition and a swap on a 200gb hd. Bios shows 137gb when I look at the drives.

---

### Post by Pumalite on 2008-03-11
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
From Herman's site:

Making a separate /boot partition would probably still be the best answer even with a relatively modern computer if you think you might have the 137 GB hard drive limit.
In the following thread, Ioza had a system that wouldn't boot after and upgrade from Feisty to Gutsy. Here is the link, [http://ubuntuforums.org/showthread.php?t=582855](http://ubuntuforums.org/showthread.php?t=582855)
Apparently, an operating system that is partly inside the hard drive limit may boot for some time as long as the kernel happens to be located within the part of the disk that the BIOS can 'see'.
After an update, if a newer kernel  happens to be placed somewhere outside the limit, the operating system might suddenly become unable to boot (at least by the new kernel), and most users would find it difficult to understand the reason why not.
Here is a great explanation of how that might happen, also already linked to in the above link, [http://www.nabble.com/Grub-tf4291271.html#a12218543](http://www.nabble.com/Grub-tf4291271.html#a12218543)
That might also explain the real reason why resizing the Linux partition to a smaller size has helped some people cure GRUB error 18.  A separate /boot partition could have fixed that and allowed them to make better use of their hard disk.
Here's how to make a separate /boot partition: How to make a separate /boot partition.
Actually, as you will see, re-installing might be easier if it's a new install anyway.

How much memory do you have?

---

### Post by brad1150 on 2008-03-11
Well, I think it might actually be the bios not supporting anything over 200gb. My main desktop reports about 197gb, the computer I'm trying to use reports 137gb. I don't seem to have a working floppy drive, the light just stays on and the drive doesn't read floppies, so I can't do a bios update. GRUB won't let me boot from a disc.

---

### Post by Pumalite on 2008-03-12
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by brad1150 on 2008-03-13
I am a novice Linux user, can someone maybe help me through putting grub in a boot partition in the first 1024 secters of my hd?  Ihave 2 partitions, etc3 and swap, etc3 is at the beginning of my drive I think. I have several movies on it, and if I have to format, I would also like to know some way to back those up to my main windows computer.

---

### Post by Pumalite on 2008-03-13
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by logos34 on 2008-03-13
> **brad1150 said:**
>  I don't seem to have a working floppy drive, the light just stays on and the drive doesn't read floppies, so I can't do a bios update. 

You can do it from a cd:
[HOWTO: Flash BIOS, The Ubuntu Way]("http://ubuntuforums.org/showthread.php?t=318789")
(-->'**CD-Method**')

But as there is a slight risk to all Bios updates, you should probably try making a separate /boot instead. 

> I am a novice Linux user, can someone maybe help me through putting grub in a boot partition in the first 1024 secters of my hd? Ihave 2 partitions, etc3 and swap, etc3 is at the beginning of my drive I think.

Between the Grub page guide suggested above and [this howto]("http://tekguru.wordpress.com/2007/09/04/howto-moving-boot-to-its-own-partition/"), you should be able to figure it out.

Concerning backup, are you computers networked?

---

