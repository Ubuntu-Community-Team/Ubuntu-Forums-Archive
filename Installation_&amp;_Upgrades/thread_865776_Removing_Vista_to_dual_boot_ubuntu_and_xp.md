---
title: "Removing Vista to dual boot ubuntu and xp"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by Aphawog on 2008-07-21
I recently bought a Toshiba Satellite A205-5855 and of course it came with Vista on it (which I hate).  So, my plan is to set it up as a dual boot system with Ubuntu and XP Pro.  I installed Ubuntu 7.10 as a quick way to reformat and rid the laptop as Vista, and am now having trouble trying to load XP Pro. My Questions are:

1)  Where can I find a simple guide to dual boot setup?  I have found guides that step you threw adding ubuntu to xp but not the other way around.  Also the Ubuntu 7.10 won't let me create a ntfs partition as was called for in those instructions.

2)  Should I try Ubuntu 7.10 or the newer version?

3)  What's the likelihood of this crazy plan working?

4)  Any help or future warning from people in this product range?

Thanks to everyone in advance that even bothers to read this post,

Alphawog

---

### Post by jimv on 2008-07-21
EASIEST way to do this:

Make partitions:

1 NTFS partition for Windows
1 Ext3 partition for Ubuntu
1 (about 2 gigs) SWAP partition for Ubuntu
(Optional) Make a FAT partition for storage.

Install XP, then install Ubuntu.  GRUB will automatically see the XP partition and add a entry to the boot menu for it.

---

### Post by xen-uno on 2008-07-21
1) ^^^

2) For me, 8.04 correctly saw the drive partitions where 7.10 didn't, which necessitated SuperGrub and a ton of searching for answers ... plus I was a total Linux noob.

3) Odds are in your favor

Once you get a bit of understanding on the dual boot process and Grub's menu.lst, it's not hard to grasp.

[http://ohioloco.ubuntuforums.org/showthread.php?t=865445](http://ohioloco.ubuntuforums.org/showthread.php?t=865445)

---

### Post by Aphawog on 2008-07-21
Here's what I've figured out so far.

XP Pro is giving me the stop error on the install b/c the BIOS are not compatible for XP only for Vista.  So I need to swap them for XP friendly BIOS (Which of course will not work with Vista).  So I'll be giving that a go today and will keep people updated.  So here's a new question for now, what's the chance and time range of someone getting Warhammer Age of Reckoning running on linux when it comes out, as it's really the only reason I'm bothering with windows at all.

-Alphawog

---

### Post by bigken on 2008-07-21
i dont were you get the idea that your bios is for vista thats rubbish

the bios has nothing to do with the OS

---

### Post by bigken on 2008-07-21
this is how I would do it fromat the hdd (NTFS)

in the xp install create a partiton install xp
then with the remaining portion of the hdd install ubuntu

---

### Post by aqk on 2008-07-21
First of all, why do you hate Vista?
I have a dual boot Vista / Ubuntu 8.04  and both systems work great (so far)

The Ubuntu installed in a breeze on the Vista system-
which BTW is a Toshiba laptop, and I guarantee, slower than yours! :lolflag:

 The trick with Vista is to get rid of all that squishy-blue menu crap, and make Vista look as closely as possible like Win2K. You'll find it runs much faster then.

Alas, Ubuntu cannot seem to work in dual-screen mode, (except as cloning) whereas Vista has no problems at all creating a two-screen desktop for my laptop. I have yet 
to test the Atheros wifi in Ubuntu, but works fine in Vista.

Just because everyone screams Vista is "crap", don't jump on the bandwagon. I remember they all said XP was lousy also. And now? :lolflag:

I run all three- W2K, XP and Vista (on processors of increasing power obviously) and really cannot see much diff in them, except that W2K now has limited support.

---

### Post by Aphawog on 2008-07-22
First the idea of the BIOS affecting the XP install comes from the stop error flag that comes up when I try to install XP and from the Toshiba site which has XP only and Vista only BIOS for the model.  I'm not saying I'm right for sure, just that some signs are pointing that way and it wouldn't be the first OS/BIOS conflict I've heard of.


As far as the hatred of Vista.  I had a relatively bad confliction problem with a work related program that had me making up a weeks worth of work due to corrupted data.  Normally I wouldn't have been surprised other than it was a Vista platform program.

At first I liked Vista but after a while I was begging for xp (about 50% is the forementioned incident).

In the long run I'll give it a try again when SP2 comes as most Windows aren't all that stable until the second big fix anyway.  But by then we'll have the next version of windows prolly.

-alphawog

---

### Post by bigken on 2008-07-22
if you want to create a partition in ubuntu using gparted then you need unused/partition free space if you have formatted partitions you need to unmount them 1st to reformat you could use something like vmware or virtualbox to install xp inside ubuntu another way to create partitions is to use the gparted live cd if you do a search in the forums you will answers to all your questions

---

### Post by jimv on 2008-07-23
> **aqk said:**
> First of all, why do you hate Vista?
I have a dual boot Vista / Ubuntu 8.04  and both systems work great (so far)


[http://jimvernon.com/archives/68](http://jimvernon.com/archives/68)

Vista is a piece of trash.  Ubuntu accomplishes the same functionality as Vista with 1/2 - 1/3 of the RAM usage.  I used Vista for a year and a half, and finally got fed up with the slowness, random program crashes, and file corruption and went back to XP.  So much faster.

---

