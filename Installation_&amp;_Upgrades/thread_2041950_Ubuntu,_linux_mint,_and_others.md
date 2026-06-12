---
title: "Ubuntu, linux mint, and others"
date: 2012-08-13
forum: Installation &amp; Upgrades
---

### Post by blackmail on 2012-08-13
I have a question regarding the installation of Ubuntu 12.04, alongside Linux Mint, if i install Ubuntu first and then Linux Mint and give both of them the same partition as home directory, then one will mess up the settings on the other distro, this is true for backgrounds, themes and so on...

How coul i stop this, should i install then without a home directory and specify the partition in the fstab file so that it gets run while booting up one distro or another? is there no viable, more state of the art workaround?

---

### Post by cottfcfan on 2012-08-14
I had this problem, so my workaround was to have one large partition with all my personal data on eg. documents, downloads, music, videos etc.
Then just use a small partition 15-20 gigs for each system I install.
They then all have their own home partiton, & configs. but can all be linked to the same data partition.

---

### Post by hawkmage on 2012-08-14
The issue is that many of the personal settings for the desktop are saved in files in the users home directory.  By using the same home directory across distros you will not be able to avoid this unless someone who is more familiar with the configuration of the desktop is able to tell us how to change this default location for the desktop config.

---

### Post by efflandt on 2012-08-15
I installed both Ubuntu and Lubuntu 64-bit 12.04 on an SD card for a tablet PC using a common /home partition and they both work fine.  They use different desktops, although, they both use lightdm. I set and formatted /home partition while installing Lubuntu, and set (but did not format) that partition as /home when installing Ubuntu. 

If you are installing new systems, just backup anything you want to save, install them and thoroughly test them them both with a common /home.  While not an issue for me, it might be more of an issue if the distros are related to different Ubuntu versions (Mint uses a different numbering system than corresponding Ubuntu version).

One issue I had was that I first installed Lubuntu, and while installing Ubuntu and figuring out where to put its grub so they would not conflict, it would not let me put it on sdb3 for some reason.  So Ubuntu has no grub and if I get kernel updates, I just need to run **sudo update-grub** from Lubuntu.

That is strange because on my desktop I had no trouble putting grub on 12.04's own partition (sda4), although, it actually boots from 11.10's grub on sdb.  But in a pinch I could boot sda with Windows mbr to Win7, or to anything if I mark sda4 containing grub as boot.

---

### Post by Bucky Ball on 2012-08-15
In the manual partitioning section, use the existing /home, but DON'T format it. That will create a new user inside /home for the new install, leaving the user directory from any other install untouched and intact, settings and all. ;)

I had three installs with users in the /home partition. I could access directories in any other user booted into any install. Now I leave the /home directory in /, delete everything in it (except Desktop!), and fill it with symlinks created using the existing directories in the /home partition from my original 10.10 user which I was using for ages. It has all the files in there. I'll get round to changing the name of the 10.10 user directory and changing the symlinks when I want to kill that 10.10 partition. 

Hope that helps.

---

### Post by CaptainMark on 2012-08-15
This should work fine if you are using the same software version for all of your programs, the problem might arise if (for example) you use version 18 of chromium on one setup and version 20 on the other, once you've used version 20 and then go back to use version 18 you may get an error saying your configuration files were created using a newer version of chromium. Just an example it may or may not happen with literally any program. If you make sure they are always the same then youll have no troubles.

If your only thinking about your personal data files then you should create one install as normal with a / and a /home partition if you wish and for the second install just use a / partition and use symlinks for each of the visible folders within your home folder to connect to the first installs /home partition, seen as most people only have 5-10 of these it shouldnt be a major hardship

---

### Post by ads52 on 2012-08-15
Depending on your actual computer needs you might want to look at virtualisation, in particular my old friend VirtualBox. This ends the need for complex partitioning at the expense perhaps of the easy sharing you are after.

---

### Post by wildmanne39 on 2012-08-16
*Thread moved to **Installation & Upgrades**.*

---

### Post by blackmail on 2012-08-22
Here are some answers:
@cottfcfan: I have been playing with the same thought and will try it out :P

@hawkmage: this would be the manly way of doing things :D

@efflandt: regarding the grup issue, the thing is that when you have had the problem you said you wanted to put grub on sdb3 meaning second HDD 3rd partition, if i know well one limitation is that grub, and bootloaders in general need to be on the first HDD, and for best results on a primary partition. I am reading up on FreeBSD and they have a very good manual. I am currently at the partitioning chapter and it is talking something like what i said above regarding bootloaders but this ptoblem has been addressed with an interesting solution, if you would like more info just let me know.

@Bucky Ball: thanks Mr. nice forum staff guy :) the symlink thing is a very good idea i will try it. thanks again! why did i not think of this... :|

@CaptainMark: i might just try the symlink thing

@ads52: actually i am thinking of this, but i am doing the installs to test the appropriate distro for my laptop, just to see how it behaves. and i cannot benefit from that in VBox, but i have VBox on for BSD and Arch Linux

@Wild Man: thanks for moving the thread in the appropriate section! ;)

---

### Post by blackmail on 2012-08-22
...so then symlinks it is! in case something goes wrong i will just come back crying in a few days :lolflag:

---

### Post by Bucky Ball on 2012-08-22
> **blackmail said:**
> ...so then symlinks it is! in case something goes wrong i will just come back crying in a few days :lolflag:
It's a deal! Let us know how it goes or if you need help with it. Try one as an experiment and once you know what you're doing the rest of the process is pretty quick and easy. Good luck. ;)

---

