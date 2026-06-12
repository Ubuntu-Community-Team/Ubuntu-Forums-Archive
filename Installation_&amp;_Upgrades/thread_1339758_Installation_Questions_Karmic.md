---
title: "Installation Questions Karmic"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by apollo26 on 2009-11-27
Hey all, I had Wubi installed on my Dell Inspiron 6400 for the past couple weeks, and would like to do a full install onto an external hard drive I just bought tonight.  I searched through the forums and google, and I am slightly confused.  Just to clarify, I can install Ubuntu directly to the external hard drive and boot from there without any special tweaks (my BIOS can boot from USB)?  Also, do I really need to unplug my internal HD with XP installed on it?  I don't know how to do that stuff and I don't like the idea of fiddling with my computer's insides.  Also, its a 320gb external hard drive (the portable USB kind), and I plan on using Ubuntu more.  However, I'd like to keep a fairly large amount of space on the external that's useable by Windows for media and schoolwork, will this be accomplished if I make a partition NTFS?  Also, I have 2gb of RAM, so does that mean I should make it 2 gb of SWAP?  Basically, what would be a good way to set up my partitions? 100gb-ubuntu 2gb-SWAP the rest NTFS?  I really can't lose my Windows stuff because of school and my wireless is still a little quirky (Broadcom WLAN 1390).

Thanks all

---

### Post by presence1960 on 2009-11-28
> **apollo26 said:**
> Hey all, I had Wubi installed on my Dell Inspiron 6400 for the past couple weeks, and would like to do a full install onto an external hard drive I just bought tonight.  I searched through the forums and google, and I am slightly confused.  Just to clarify, I can install Ubuntu directly to the external hard drive and boot from there without any special tweaks (my BIOS can boot from USB)?  Also, do I really need to unplug my internal HD with XP installed on it?  I don't know how to do that stuff and I don't like the idea of fiddling with my computer's insides.  Also, its a 320gb external hard drive (the portable USB kind), and I plan on using Ubuntu more.  However, I'd like to keep a fairly large amount of space on the external that's useable by Windows for media and schoolwork, will this be accomplished if I make a partition NTFS?  Also, I have 2gb of RAM, so does that mean I should make it 2 gb of SWAP?  Basically, what would be a good way to set up my partitions? 100gb-ubuntu 2gb-SWAP the rest NTFS?  I really can't lose my Windows stuff because of school and my wireless is still a little quirky (Broadcom WLAN 1390).


Thanks all
That partition scheme for the external HD is good, but you may want to consider a separate data partition or separate /home partition for your files. Not necessary though.

No you do not need to unplug your internal disk to install Ubuntu to the external HD.

First setup your partitions on the external disk. Then when you install Ubuntu and get to the partitioner window (see attached pic) choose manual install. Be sure to choose the partition meant for Ubuntu and click change. Select use as (Filesystem-ext3 or ext4), tick the format box, and select mount point using drop doen menu as /. If you made a partition to use as a separate /home partition highlight that also & click change, select use as (Filesystem- ext3 or ext4). If your ubuntu partition is ext3 do not make /home ext4 as you won't be able to mount it (access it). But ext4 can mount ext3 partitions! Select mount point from drop down menu as /home. Finally highlight the swap partition & click change and select use as- linux-swap. 

Proceed with the install. When you get to the Ready To Install window (see second attached pic) click Advanced tab and choose /dev/sdx to install GRUB to. You want to put GRUB on your external disk which if you only have one internal hard disk will be /dev/sdb. Continue with install. Putting GRUB on MBR of the external HD will allow you to boot into windows without the external plugged in, if the external is plugged in at boot you will get GRUB to boot into Ubuntu- provided you set USB disk as first in the BIOS boot order after installing Ubuntu. Any more questions post back.

---

### Post by apollo26 on 2009-11-28
Thanks for the reply! How big should I make the "/" partition, is like 20gb good or too big/small?  The "/home" partition would be the one with all my configuration/personal files in it correct?  That could be like 80 I suppose (there's little chance I'd even use 80gb in total to be honest).  Do I have to partition my drive in Windows? I was under the impression I could use the install cd to partition the drives.  If so, can you point me to any good partition managers for XP? Thanks a ton really, I have the install CD burned I'm just about ready to make the plunge.

---

### Post by presence1960 on 2009-11-28
> **apollo26 said:**
> Thanks for the reply! How big should I make the "/" partition, is like 20gb good or too big/small?  The "/home" partition would be the one with all my configuration/personal files in it correct?  That could be like 80 I suppose (there's little chance I'd even use 80gb in total to be honest).  Do I have to partition my drive in Windows? I was under the impression I could use the install cd to partition the drives.  If so, can you point me to any good partition managers for XP? Thanks a ton really, I have the install CD burned I'm just about ready to make the plunge.

You have the space why not give it 15 GB for /? Even 20 GB will be fine. Your /home you can judge how much you think you will need. Remember Ubuntu can mount NTFS partitions & read/write to them also.

Home directory does contain config files.

You can partition from the Live Cd or you can download gparted Live and burn the iso to a CD and boot from that. A lot of us use gparted live. Get it [here]("http://gparted.sourceforge.net/livecd.php").

Once you get your partitions set up just be careful to choose the correct disk & partitions to install onto.

**_P.S. Be sure to click the Advanced tab on the Ready To Install window and select the external disk to install GRUB2 onto. If you mistakenly put it on your internal you will have to have the external plugged in when you boot or you will get a GRUB error._**

---

### Post by apollo26 on 2009-11-28
Hey, so I got everything installed it went quite smoothly, thanks for all your help.  No ethernet cable at home so I have to wait a couple days to set everything up in ubuntu.  Thanks very much

---

### Post by presence1960 on 2009-11-28
> **apollo26 said:**
> Hey, so I got everything installed it went quite smoothly, thanks for all your help.  No ethernet cable at home so I have to wait a couple days to set everything up in ubuntu.  Thanks very much

Great! Enjoy Ubuntu. It rocks.

---

