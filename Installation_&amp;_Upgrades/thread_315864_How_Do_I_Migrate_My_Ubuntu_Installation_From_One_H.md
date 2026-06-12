---
title: "How Do I Migrate My Ubuntu Installation From One Hd To A New One? Plz Help!"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by amaurynieto on 2006-12-09
Hello Fellow Ubuntuers! 

I've had the priviledge of using Ubuntu for a little over a month now, and am ecstatic. I rarely use Windoze anymore, and since I'm no avid gamer, I've found the ubuntuforums to be my new obsession/hobby, to the point where it's my homepage.

However, I've run into a bit of a snag which I can't seem to get out of, and request your kind and expert assistance: 

I have two Hard Drives, one is a 40 gig which has Windoze XP,
and the second is a 10 gig empty one which I used to place Ubuntu in.

From the BIOS, GRUB 1.5 loads and gives me the option on what I can load. 

The problem is the 10 gig HD is starting to act up, has several bad clusters, and in general I believe to be somewhat damaged. I checked and everything is running fine so far, however, I want to migrate from the 10 gig to the 40 gig, and keep both OS's.

Please, be so kind as to instruct me on a how-to- since I am a new Ubuntu/GNU/Linux user and have little to no clue other than what I've managed to pick up over the weeks in this forum.

Thank you kindly, 
A desperate user
Amaury.

---

### Post by aysiu on 2006-12-09
**Make room**
Well, you'll have to make space on your 40 GB drive first. You can use GParted for that: ```
sudo aptitude update
sudo aptitude install gparted gksu ntfsprogs
gksudo gparted &
``` **Copy Ubuntu**
Once you do that, you can use *ddrescue* to copy over your 10 GB drive to your 40 GB drive. If you have a Knoppix CD, *ddrescue* should already be on it. If you have a Ubuntu Desktop CD, you can install it once you enable the Universe repositories (if you need help with that, let us know): ```
sudo aptitude update
sudo aptitude install ddrescue
``` Let's assume, for the sake of this example, that your new partition on the 40 GB drive is called /dev/hda2 and that your 10 GB drive is /dev/hdb1. The output of ```
sudo fdisk -l
``` will let you know, as will GParted. ```
sudo dd_rescue -v /dev/hdb1 /dev/hda2
``` Make sure both drives are unmounted before you run this command. Also, note that the package is called *ddrescue*, but the command to run it is *dd_rescue*. I don't know why there's that discrepancy between the two.

**Clean up**
Now, once you've copied over the drive, you might still have some problems. For example, I think Grub will be looking for the /boot/grub/menu.lst file on /dev/hdb1, and your Grub config (/boot/grub/menu.lst) and your /etc/fstab will both have that Ubuntu is on /dev/hdb1 even after it's been moved to /dev/hda2. So you will need to [restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113) and also edit those two files to reflect Ubuntu's new location.

Post back any questions you may have.

---

### Post by amaurynieto on 2006-12-09
Wow! That's a great tutorial Sir! precisely what I was looking for. Makes me very Ubuntified. I love that philosophy and how we users actually make it true. (admittedly at the learning stage for myself, but soon to cooperate with answers as well)

Couple thoughts:

GRUB, is that installed on my Ubuntu 10 gig drive? or on the 40 gig drive. I have the 40 gig as the Primary boot drive both through IRQ's and BIOS.

If installed on the 40 gig drive, how do I remove it?

and last but not least, How do I unmount the volumes?

Subsequently, if I unmount the Ubuntu volume, and i am IN ubuntu, won´t my system crash or be unresponsive?

APPRECIATE ALL THE HELP!!! :)

---

### Post by aysiu on 2006-12-09
As far as I know, Grub is installed to your Master Boot Record, but it's probably looking for the configuration file on your 10 GB drive.

That's why I thought you should reinstall Grub to the MBR so that it knows to look for the config file on the 40 GB.

I don't really know much else about Grub, to be honest.

---

