---
title: "Reinstalling XP"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by nikolatran on 2007-10-23
Hey y'all

      I'm new to Ubuntu, and I have to say that I really like it. However, I need to switch back to XP to use photoshop and other things. I will probably attempt to use a dual OS when I get the chance to mess around with it. Anyways, so I've encountered a problem while trying to reboot XP (SP2). i try tried to reninstall using a cd, and it brings me to this screen where it asks me if i want to install windows XP or repair XP (after scaning my computer for a bunch of stuff). After I click that install, it says that "set up did not find any hard disk drives installed in your computer. Make sure any hard disk drives are powered on and properly connected to you computer. etc. 

I'm using a laptop btw. Compaq presario, celeron. I don't know if that helps. Anyways, I have no idea how to use Linux and I probably didn't know what I was getting myself into. I'll try again when I'm not bombarded with midterms. Anyways, any help would be appreciated. Thanks!

---

### Post by nikolatran on 2007-10-23
bump. anybody? :(

---

### Post by BoardDWorld on 2007-10-23
Hello,

You most likely used tour entire harddrive when you installed Ubuntu. When you boot from your CD into the XP install setup you need to delete the EX3 and SWAP partitions created by Ubuntu. XP can't be installed onto these. Once deleted create a new NTFS partition.


P.S. Photoshop CS2 is one of the easiest windows programs to get running on Linux and performs very well:

[http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps](http://luiscosio.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps)

---

### Post by fain on 2007-10-23
try "the gimp" for a photo shop alternative. 
as for the hard drive problem. 
windows setup should see your hard drive no matter whats on it. thats a tough one. might try repartitioning and formatting your hard drive to ntfs. windows cant read the ext3 but should see the hardware and want to format it. 

you could also dual boot by making two partitions and installing windows first then Ubuntu second
once you get windows to see your drive of course.

---

### Post by nikolatran on 2007-10-23
thanks a lot Fain and Boarddworld..I am reinstalling ubuntu and I've deleted the harddrives ext3 and that other one. When i make a new partition, there's an option for use as: I'm assuming that this is where NTSF should be located.. anyways, the options are ext3, ext2, reiserfs, jfs, xfs, fat16, fat32, swap, efi and don_use

which one should I use?

and thanks for the photoshop ideas, I'm def. planning on trying that as soon as I have some time to mess around with ubuntu

---

### Post by lgcabarcas on 2007-10-23
you should use NTFS  as it's the windows native filesystem

---

### Post by fain on 2007-10-23
wait you are putting Ubuntu back on there? 
make the Ubuntu partition ext3 and the windoze partition ntfs.

---

