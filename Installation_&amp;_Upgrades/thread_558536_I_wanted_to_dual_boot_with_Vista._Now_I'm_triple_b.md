---
title: "I wanted to dual boot with Vista. Now I'm triple booting with it"
date: 2007-09-24
forum: Installation &amp; Upgrades
---

### Post by pandamonium54 on 2007-09-24
My laptop came with Vista preloaded. The 80GB drive was partitioned with 8GB hidden restore, 35GB C, 35GB D.

I knew I wanted to dual boot, so after reading a few guides, I used windows disk management to shrink my C drive by a little bit and manipulated it so that I had the "D" drive at the end of the physical disk.

I had: 8GB restore, 30GB C, 10GB unallocated, 30GB D.

Then I put the Ubuntu live CD in and installed. I screwed some things up while I was trying to get my wireless working, and I wanted to start all over. I booted into windows and was about to delete the Ubuntu partitions when I realized that I was using Ubuntu's bootloader. I figured if I reinstalled Ubuntu, it would be smart enough to install over itself. I was wrong. I let the installation do the guided partition.

Now I have: 8GB restore, 30GB C, 9.5GB ubuntu1, .5GB swap1, 13.7GB D, 12.4GB ubuntu 2, .6GB swap2

My bootloader now reads: 
Ubuntu
Ubuntu safe
XP/etc
Vista
Ubuntu
Ubuntu safe

My second attempt at configuring my wireless was successful. But now I've got two copies of Ubuntu taking up precious hard drive space. I've written down the commands I need to type in order to get my wireless working, so if I have to do another installation of Ubuntu, I'm okay with that.

What I want to do is have my bootloader read something like:
Ubuntu
Ubuntu safe
Xp/etc
Vista

And my partitions go something like: 8GB restore, 30GB vista, 9.5/.5GB Ubuntu, 30GB D
(My ultimate plan is to triple boot with OSx86, and after I get my hands on a Vista DVD, I'm going to dump the restore partition and do a clean install of everything.)

What's the best way to do this?

---

### Post by jnorthr on 2007-09-24
The ubuntu version of fdisk (not the windows version) has a delete partition feature where you could loose the last two partitions, but i dunno how you would add the spare disk space to the end of the last 'real' partition. run fdisk as root from a terminal otherwise you can try what i've done this morning: burn a new live CD of gparted andthen try to boot from that. [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

BTW: you [COLOR="Red"]DO[/COLOR] have backups of everything don't you ?

---

### Post by pandamonium54 on 2007-09-24
It's not a matter of removing the partitions. I have two Ubuntu installations that are almost identical. I can nuke the partitions just fine using the Vista disk management console, but I want the bootloader to also be aware of what I remove.

If I could go back to the Vista bootloader (pre-ubuntu), I could just delete all the ubuntu partitions and resize my drives so that Ubuntu is sandwiched between C:\ and D:\, and everything would be good.

I have restore DVDs, but this is a new computer, so I don't exactly have much in the way of important data. The restore DVDs also don't mess with my partition tables- all they do is copy data to C:\.

---

