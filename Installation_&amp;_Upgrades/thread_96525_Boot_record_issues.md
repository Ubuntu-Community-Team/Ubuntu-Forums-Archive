---
title: "Boot record issues"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by Daminator on 2005-11-29
Hello all

Over the past 3 days, I've formatted my drive and reinstalled XP and Ubuntu 3 or 4 times. A couple of times, this was through choice due wanting to set up partitions differently, and I couple of times I was scared by boot problems.

Once, I fixed the boot problems, by booting into recovery mode in XP and using FIXMBR. Then I just had to set up Ubuntu again. The last time, FIXMBR didn't work and I couldn't boot from the drive at all. I had to format everything and start again.

All seems fine now, but what if this happens again for some reason. It's very frustrating to have to format and start from scratch when you know that everything is still there on the drive just fine apart from something that's messed up with the boot section.

There must be a way to fix this if it happens! Any tips or sites to look at so that I'm better prepared for when I next don't see the friendly grub loader?

Damian

PS
I think I posted this in the wrong place previously. Sorry for re-post, but really wanting to be prepared for if/when this happens again as XP's 'FIXMBR' and 'FIXBOOT' didn't work for me at all.

---

### Post by Herman on 2005-11-29
Hello, Damian, If you want, you can use GAG bootloader instead, it is free and open source software and it's only a small download. Once you download the file for it you can copy it to a CD or to a floppy and use it from there, leaving your origninal MBR untouched. Later, you can install it to your MBR if you wish, but you don't have to.
The GAG CD will not be able to boot Ubuntu though, unless you install either GRUB or LILO to your Ubuntu partition or to a boot partition, (not your MBR) and you can do that during your next install. LILO is the easiest in my opinion. The Ubuntu installer gives you a chance to do that.
I haven't been successful in installing LILO to a Ubuntu partition after the install, I have tried and keep getting a message something about an 'unclean target', and it won't do it. It would be nice if I could, then it would help a lot of people with boot loader troubles. Unfortunately GAG is something you have to decide you want beforehand.
You will need a GAG CD ready during the install if you decide to try it sometime, to put in your CD drive when you remove the install CD and boot Ubuntu for the first time.
I tried GAG out for a while but I'm back to using GRUB now, I'm lucky, I 've never had any problems with GRUB. I think it's because I only have computers with one hard-disk each and just regular IDE, no SATA  drives.
GAG would be worth a try for those people or for people who like to multi-boot and also change operating systems a lot. GAG can be re-configured easily each time. I haven't tried it on a computer with more than one hard-disk, but I think it would be very good for that situation too.
More on GAG:            [http://www.users.bigpond.net.au/hermanzone/p6.htm](http://www.users.bigpond.net.au/hermanzone/p6.htm)

---

### Post by bwog on 2005-11-29
For windows you have fixmbr fixboot and rebuild boot.ini. However, check a windows tutorial so you know what you are doing. When you havent made big mistakes (like installing on the wrong partition) there is  no need to reinstall windows.

Before that you can try to restore grub with: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253)
To do this you have to know which partition you boot from, so
# grub-install /dev/hda can be # grub-install /dev/sda or even # grub-install /dev/fd0, depending on your setup. It is not risky to try the latter to my knowledge.

---

### Post by Herman on 2005-11-29
INSTALL LILO BOOT LOADER TO UBUNTU PARTITION
                               (so you can boot with GAG bootloader)

1. Boot the computer with the 'Breezy' install CD.
2. Complete the questions for the first stage of the installation as if you were installing, until '[!!] Partition Disks' is reached.
3. Select 'Manual Partitioning'.
4. Select your Ubuntu partition.
5. (a) change mount point from /media/hda4 (or whatever) to /.
     (b) change 'bootable' off to 'bootable' (a progress bar will display).
     (c) choose 'done setting up the partition'.
     (d) choose 'finish partitioning and write changes to disk. 
6. Sign says: 'If you continue, changes will be written to disk, etc,''Continue?'choose 'Yes'.
7. A red warning screen appears, saying 'Not installing to unclean target' choose 'continue'.
8. A second red warning screen says 'Install the base system failed' choose 'continue' again. (we don't care!).
9. This sees you back in the 'Ubuntu Installer Main Menu', and once there you can scroll down to 'Install Lilo boot loader to a hard disk'.
10. 'Install Lilo to target' '/dev/hda: new Ubuntu partition' (not your MBR if you are doing this for GAG). A progress bar should display as Lilo gets   installed.
11.A red warning screen appears, saying 'Not installing to unclean target' choose 'continue'.
12. A second red warning screen says 'Install the base system failed' choose 'continue' again.
13. Then you will be back in the 'Ubuntu Installer Main Menu' again, but be careful not to press 'enter' on anything you don't want,but scroll down immediatley to 'Abort   Installation'.
14.Exit the installer.
15.Remove the install CD from your CD drive quickly as soon as you can before it boots from it again!


These instructions are taken from vnbuddy2002's famous howto on restoring GRUB to MBR, and I have only modified them a little bit. (I hope vnbuddy2002 won't mind, without his howto to start with, I wouldn't have been able to do this).

I have tested this twice on a computer with Windows98SE and two installations of 'Breezy'. (Triple-boot). I already had GRUB working alright before doing this. The results were that my computer still boots all three operating systems as it did before using GRUB, plus I have configured a GAG floppy disk, and all three operating systems also boot from the GAG floppy disk, using Lilo for the two 'Breezy' installs I am runnning. So to make it plainer; installing Lilo to my Ubuntu partitions has not affected Grub, and using GAG from a floppy doesn't change the MBR either. (So this is a safe thing to do, and can be done anytime.):D 

I am sure there's an easier way to install Lilo using a quick command or two in 'terminal', and while I am aware of this easier and better way to do it, I have not tested that yet, even though I expect it will work and would be quicker and easier. 
(Give me some more time) (Herman):D

---

