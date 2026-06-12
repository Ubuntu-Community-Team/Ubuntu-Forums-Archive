---
title: "Chainloading GRUB2"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by IAmNotAUser on 2010-05-30
Hey there,

I'm back in the installation boards again, looking for some help with GRUB2 and chainloading.

Basically, I wish to have a dual boot of two *buntu-based distros on my netbook. I wish to be greeted to a GRUB2 screen that allows me to select "Distro 1" or "Distro 2". I'll then have each option take me to another GRUB2 screen where only the local OS options are available (various previous kernels, memtest, etc).

I've done some research into this, and have played, and gotten into some problems, with GRUB and GRUB2 before so I have a working understanding of what it is doing.

Basically, what I think I'm going to do is install both distros with a bootloader on their partition during the installer and then also make a separate partition in /mnt/GRUB and at the end of the second installation and do a grub-install as per here: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition") to /mnt/GRUB, and /dev/sda.

Then I'll create my own custom grub.cfg file for the opening GRUB2 screen, and then boot into each of the distros and turn off the OS prober inside them and update-grub on each.

Is this the right way to do things, and if not, what should I do different? This is a live machine so I'd like to be able to sit down in one evening and get it done and hopefully not have to leave it for a few days, so I figured I'd come get some advice first. :) Also, how do I tell my custom grub.cfg that I'll be chainloading into another GRUB, or will this happen automatically? Or will I need to create an entry like in this post? [http://ubuntuforums.org/showpost.php?p=8492118&postcount=4](http://ubuntuforums.org/showpost.php?p=8492118&postcount=4)

Thanks for your help.

---

### Post by darkod on 2010-05-30
Is there a specific reason you want the first Grub2 to jump to a second Grub2?

The first Grub2 located on your MBR can directly boot any linux (not just ubuntu) distro you will have on your computer, you know that right? Why the delay and complication of second grub2?

---

### Post by IAmNotAUser on 2010-05-30
Firstly, I wish to edit the names of the distros in that first GRUB. And I don't want to have to manually do it every time that a kernel update comes out, that is more hassle than I'm willing to put in when I have other things to do with my time.

Having that first GRUB means that I can have my custom names, and the second GRUB2 can continue to be updated whenever a new kernel comes out. Also, I dislike how quickly the single GRUB2 screen fills up and becomes cluttered. Having to go down 4-5 different distro1 kernels just to get to distro2 is annoying. If that could be moved to second in the list, again without having to do it manually to point it at the correct image every update, that might be ok, but I cannot find a way to do that.

---

### Post by darkod on 2010-05-30
The menu can be slimmed down, but it all depends what you want to "sacrifice".

1. The memtest is hardly needed, you won't run it on every boot. I have thrown it out myself.

2. You can disable the recovery mode entries too, but if you ever need to boot in recovery mode?

3. You can deinstall older kernels. It is best to keep at least one older kernel in case the most recent starts giving you headaches, but you can remove all but the latest if you wish.

So, if you are prepared to do all three things, you will literary end up with:

Distro 1
Distro 2

Then on every kernel update, you remove the older one, and again you have only one for each distro.

Ps. The text that ubuntu writes by default for the entry name can also be played with, if you want to go that far too.

---

### Post by recluce on 2010-05-30
Sounds to me as if your live would be easier if you used GRUB1 on the dedicated partition. GRUB1's menu.lst is easy to edit - and we know that GRUB1 is good about chainloading GRUB2. 

Instructions can be found on Herman's Legacy GRUB page.

---

### Post by confused57 on 2010-05-30
I've always preferred chainloading other OSes with legacy-grub in Ubuntu; however, I've been unable to chainload 10.04 grub2 when installed on an extended logical partition.  Now I prefer to use grub2 installed to the mbr to boot other OSes, I've found grub2 excellent at automatically detecting & adding entries to boot the other OSes.

---

### Post by oldfred on 2010-05-31
+1 for confused57 comments.

Darko & I have had this discussion before and I liked using old grub to chainload. I still have that working for some of my old installs but I rarely use them anymore.

Grub2 does not like to be in partitions. It talks about blocklists, but I guess it means it hard codes a location of the grub file and if anything moves the file then the partition boot will break. So they consider it less reliable.

Other ways to customize:
Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)
OR Partial Custom:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php?p=8082954&postcount=1](http://ubuntuforums.org/showpost.php?p=8082954&postcount=1)
In /etc/default/grub I added this:
GRUB_DISABLE_OS_PROBER=true

If you put your menu entry in /etc/grub.d/40_custom it will not be over written and will be at the end of your menu. Or you can copy it to 09_custom and make it executable and it will be at the top of your menu.

---

### Post by Keith Myers on 2010-05-31
> **confused57 said:**
> I've always preferred chainloading other OSes with legacy-grub in Ubuntu; however, I've been unable to chainload 10.04 grub2 when installed on an extended logical partition. Now I prefer to use grub2 installed to the mbr to boot other OSes, I've found grub2 excellent at automatically detecting & adding entries to boot the other OSes.

Excuse me for highjacking your thread but I am interested in your knowledge of how you got Grub2 to recognize other OSes.  I can't get Grub2 to see my eComStation installation on another hard drive that I spend most of my time in.  The results of the boot.info script were placed in my  help request in the Absolute Beginners forum but I have not received any direct response to my request.  It says at the beginning that no bootloader is on /dev/sba.  At the bottom it says "Unknown bootloader" on /dev/sdb1.  That is  where I boot my eComStation OS.  I would like to get this into Grub2 but have been completely unsuccessful.  You can see the thread titled "Help with Grub2" over in the Absolute Beginners forum.  Do you have any knowledge on how to get Grub2 to see my other OS?

Cheers,  Keith

---

### Post by IAmNotAUser on 2010-06-01
I am now chainloading Grub2->Grub2 for my 10.04 distro and Grub2->Grub for the 8.10 partition and it's all working grand. 

Just run the ubiquity program and install the bootloader to the local / partition in the advanced section of each install, and then in the 2nd livecd install, also follow Herman's guide to install Grub2 to the partition you wish to have as your dedicated Grub2 install, and set the MBR to /dev/sda.

Recluce, I find manually editing grub.cfg just as easy as menu.lst ;) and in a dedicated Grub2 install on a seperate partition, chainloading more Grubs you can edit it fine without having to every worry that it's going to get overwritten.

---

