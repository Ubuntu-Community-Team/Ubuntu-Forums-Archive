---
title: "Side-by-side installation of Lucid/Win 7 only boots into Windows"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Theophylact on 2010-05-05
Okay, here's the background. I had a working side-by-side installation of Win 7 Release Candidate and Jaunty (9.04), both 64-bit. When the official version of Win 7 came out, I installed that, leaving the Linux partition untouched but not editing Grub so it could be used; I figured I'd wait until 10.04 LTS was available.

Last night I installed Lucid into the existing Linux partition. The installation appeared to go correctly, and it imported settings from the old 9.04 system, but on rebooting I get no Grub menu; I just go directly into Win 7.

What should I do now?

System: Athlon 64 X2 7750 Kuma, Gigabyte GA-MA78GM-MS2H, 4 GB GSkill DDR2 1066, Western Digital 1TB Caviar Green WD10EARS, Windows 7 Professional, Ubuntu Linux 10.04

---

### Post by Theophylact on 2010-05-05
Oh, by the way: during the installation, I got the same message others have gotten, "No Operating Systems Found". But in fact, the correct *partitions* were found, and I installed 10.04 in what was clearly the Linux partition. This is probably a bug in the installation procedure, but it's a scary message to see.

---

### Post by lechien73 on 2010-05-05
If you boot from a LiveCD can you see your Linux partition? If so, it would be good if you could boot in from a LiveCD, download [boot info script]("http://bootinfoscript.sourceforge.net/") and post the output here.

If it appears that Grub needs reinstalling, then following the instructions in step 13 of [this post]("http://ubuntuforums.org/showthread.php?t=1195275") might help.

---

### Post by Theophylact on 2010-05-05
It's almost *certainly* a Grub2 problem. I had [similar issues]("http://http://ubuntuforums.org/showthread.php?t=1389505") doing a clean installation of 32-bit 9.10 on a laptop's brand-new 160 GB hard drive.

I don't think beta software should be used in final distros.

---

### Post by hvralpha on 2010-05-05
It is a reported bug. 10.04 does not read the WIN7 MBR correctly and will wipe the win7 MBR.

There is nothing you can do to fix this if you have only one hard disk. If you have 2 disks  ( Not partitions on the same disk), install 10.04 on the second disk and also install grub there. Point the bios to boot from the second disk.
Make sure the WIN& mbr is fixed with the WIN7 Disk before you install 10.04.

You can download suprgrub2 and see what you have.

---

### Post by Theophylact on 2010-05-05
Wewll, it *didn't* wipe the Win7 MBR, because Win7 is all I get.

---

### Post by wilee-nilee on 2010-05-05
> **lechien73 said:**
> If you boot from a LiveCD can you see your Linux partition? If so, it would be good if you could boot in from a LiveCD, download [boot info script]("http://bootinfoscript.sourceforge.net/") and post the output here.

If it appears that Grub needs reinstalling, then following the instructions in step 13 of [this post]("http://ubuntuforums.org/showthread.php?t=1195275") might help.

**This what you should do post the script**. I am running W7 with Lucid same HD no problems. Lets get it fixed then we can complain about the problems with grub which I have never ever had.

---

### Post by recluce on 2010-05-05
> **hvralpha said:**
> It is a reported bug. 10.04 does not read the WIN7 MBR correctly and will wipe the win7 MBR.



I am not sure what you are trying to tell us. Any installation of Lilo / GRUB / GRUB2 will need to OVERWRITE the Windows IPL in the MBR, otherwise it could not operate.

If it would wipe (as in overwrite with null characters) the MBR, nothing at all would boot.

---

### Post by wilee-nilee on 2010-05-05
> **hvralpha said:**
> It is a reported bug. 10.04 does not read the WIN7 MBR correctly and will wipe the win7 MBR.

There is nothing you can do to fix this if you have only one hard disk. If you have 2 disks  ( Not partitions on the same disk), install 10.04 on the second disk and also install grub there. Point the bios to boot from the second disk.
Make sure the WIN& mbr is fixed with the WIN7 Disk before you install 10.04.

You can download suprgrub2 and see what you have.

If your going to claim a bug give a link or this is FUD, besides terrible advice.

---

### Post by recluce on 2010-05-05
In order to keep multi-boot frustration to a minimum, especially when updating/reinstalling Linux installations frequently, I suggest the following:

1.) Make a small partition (100 MB is plenty) with reiserFS or EXT3. If  possible, a primary one (you can have no more than four primary partitions on one hard drive). 

2.) Install GRUB 1 ("Legacy GRUB") from a Jaunty Live CD to this partition. (If you use an older source than Jaunty, you will not have EXT4 support). Have GRUB install the MBR of your drive with this partition set as the GRUB root. You will need your usual GRUB files here (stage1, stage1_5, stage2, menu.lst etc)

3.) Edit the menu.lst file to CHAINLOAD into all Operating Systems that you have, including the Linux ones.

4.) Configure the bootloaders of your individual Linux installations to install themselves into the respective root partitions of their installations ONLY (no setup of MBR). This will cause the apropriate PBR (partition boot record) to be written that is required for chainloading.

Advantages:

1.) The chainload process will activate whatever bootloader is preferred by the respective Linux distro and avoid compatibility issues. So you can have GRUB2 for Lucid, GRUB1 with UUID for Jaunty, Grub 1 without UUID for Debian Stable, Lilo or whatever else.

2.) You will not need to manually maintain grub.cfg or menu.lst or equivalents, since each installation will only look at its own kernel list and does not need to care about the other installations.

3.) You can wipe any or even all of your Linux installations without loosing the ability to boot one of the other operating systems

4.) No need to edit the menu.lst of the GRUB partition, except for readability (lets say you replace Gentoo on sda7 with Sabayon, you would probably want to edit the title entry for sda7 to reflect that)

Disadvantage:

Two stage boot process, could take a few seconds longer. (You could boot your main Linux system directly from the dedicated GRUB partition, but than you would have to edit menu.lst for each kernel update).

Instructions here:

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)


Caveats:

If you insert the GRUB partition before any existing Windows OS partition, you need to edit boot.ini (Windows XP, Windows 2000) or use BCDEdit (Vista, Windows 7) to change the partition numbering for the windows boot manager. 

Use a Jaunty live CD to install the GRUB1 files, even if you are running Jaunty - if you updated from an earlier version of Ubuntu to Jaunty, you will still be running the older versions GRUB, as it will not have been replaced during a distro upgrade to Jaunty.

---

### Post by wilee-nilee on 2010-05-05
This situation needs to have the bootscript to solve lets get the OP to do this.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Giving advice without it is a assumption based approach= not good.
Your description may work but it is haphazard.
This is not a personal attack it is how things are done on the forum most of the time.

---

### Post by kansasnoob on 2010-05-05
> **wilee-nilee said:**
> This situation needs to have the bootscript to solve lets get the OP to do this.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Giving advice without it is a assumption based approach= not good.
Your description may work but it is haphazard.
This is not a personal attack it is how things are done on the forum most of the time.

+1! Or I guess we're up to 4! Without the results of the Boot Info script we're working in the dark!

We must see the results of the Boot Info Script to know where to begin.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by wilee-nilee on 2010-05-05
> **kansasnoob said:**
> +1! Or I guess we're up to 4! Without the results of the Boot Info script we're working in the dark!

We must see the results of the Boot Info Script to know where to begin.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Hey your one of the fix my computer chosen ones like several others we all know who you are, in a good way. ;)

---

### Post by recluce on 2010-05-05
> **wilee-nilee said:**
> This situation needs to have the bootscript to solve lets get the OP to do this.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Giving advice without it is a assumption based approach= not good.
Your description may work but it is haphazard.
This is not a personal attack it is how things are done on the forum most of the time.

The dedicated GRUB1 (or GRUB2) partition is a "silver bullet" for most multi-boot problems.

Haphazard? I don't think so, I specifically linked to the complete instructions on how to do this and just posted the most important steps, problems, advantages and disadvantages. Do you truely find it an advantage to copy and paste a couple of 100kB of text - instead of linking to them?

I believe that most users here are adults capable of making their own decisisions - and that is why I headlined my post with "CONSIDER...."

BTW: bootscript output would be interesting, even though it cannot answer all questions!

---

### Post by ResidentBio on 2010-05-05
I had the same problem. What i did is boot from different harddrive and voala! the grub lauched. I assume my old grub was found by the installation, and it decided to use the old location.

For the record, i have 3 HDs and i don't remember where i had installed previous ubuntus. So i just picked a partition where old linux was, still it seems i was booting from other drive, God know how.

---

### Post by Theophylact on 2010-05-05
> **kansasnoob said:**
> +1! Or I guess we're up to 4! Without the results of the Boot Info script we're working in the dark!

We must see the results of the Boot Info Script to know where to begin.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)Gonna try to fetch it with Lucid Live, but most likely I won't have the time until tomorrow evening. I have guests tonight.

---

