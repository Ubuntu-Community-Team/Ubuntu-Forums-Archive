---
title: "Win7 Dual Boot error: SATA link down?"
date: 2011-12-26
forum: Installation &amp; Upgrades
---

### Post by jrh382 on 2011-12-26
Hey all!

This is my inaugural forum post, so if I'm covering previously-established ground, I'm sorry in advance. Anyway, I recently got a System76 laptop for Christmas with the intention of installing Windows 7 ultimate and dual-booting it with Ubuntu 11.10. Win7 install went smoothly (though, as expected, it wiped Ubuntu off the drive) but I'm having some trouble getting Ubuntu to reinstall from the live CD I made.
Basically, when I open the Boot Options menu at startup and select the option to boot from the DVD drive, I get to a purple splash menu (no Ubuntu title) and then to a console view that terminates in the error: 

ata4: sata link down

(this isn't verbatim: there was a LOT of text and there's no way I could memorize it.)
Any ideas as to what I should do? I've followed the instructions on the community documentation to the letter as much as possible, and when I first fired up the laptop, Ubuntu 11.10 was running fine. Only other thing I've changed was updating the drivers so that Win7 would be able to run games (and install some Windows-side software, of course.) Sorry again--I realize this is probably a serious rookie question, but any help would be appreciated!

-J

---

### Post by fantab on 2011-12-27
Did your laptop come with pre-installed ubuntu?
Does it use BIOS?

There a few things you could look for:

[LIST=1]
[*]Download and make a [GPARTED LIVECD]("http://gparted.sourceforge.net/livecd.php"). And check the partition Table of your HDD. You will check to see if your Partiton Table is GPT or DOS or anything else. If its not DOS then I suggest you change it to DOS to keep things simple with respect to dual boot. (You may have to delete all the partitions on your HDD to create a new partition table).
[*]Make sure the CD you created with Ubuntu.**iso** is not corrupt; Check its integrity. If you are not sure then download it again using torrent if possible and burn it to the CD/DVD at the SLOWEST POSSIBLE SPEED. This according to me, is the more likely cause of the trouble you are having.
[/LIST]
To help you better post a Screen-Shot of your partitions.

---

### Post by jrh382 on 2011-12-27
> **fantab said:**
> 
To help you better post a Screen-Shot of your partitions.

Do I need to create a partition before running the CD? I was under the impression that I could create one using the installer.

---

### Post by fantab on 2011-12-27
> **jrh382 said:**
> Do I need to create a partition before running the CD? I was under the impression that I could create one using the installer.

NO, you don't need partitions on HDD to run both Gparted LiveCD or Ubuntu LiveCD.
Yes you can create partitions using installer but since you are having trouble with your installer you can use Gparted Live. Also Gparted Live is a good tool to have to manage your HDD as it works independent of an OS and without mounting any partition it is relatively safer.

You can post a screen-shot from WINDOWS...

---

### Post by jrh382 on 2012-01-11
Sorry it's been so long since I've updated on this.

I think performing a slow burn of the disc got rid of the SATA link down error--the new error I'm getting, though, is as follows:

(long string of numbers and letters)
[194] terminated by signal 9 (Killed)

Couldn't find anything else on the forums about this--should I start a new thread? Any suggestions?

---

### Post by Mark Phelps on 2012-01-11
Couple of suggestions ...

First thing to do is to use Win7 Disk Management utility to shrink the Win7 OS partition to leave room for the Linux partitions.  Don't use the Ubuntu installer with the slider to do this.  Win7 is finicky about its filesystem and doesn't do well when changed by an "outside" tool. Can sometimes result in filesystem corruption, rendering Win7 unbootable.

Second thing is to download and install the FREE version of Macrium Reflect in Win7, back up the install to an external drive, and use the option to create a Linux Boot CD.  This way, you have the ability to restore Win7 in a few minutes -- which you might need if anything goes wrong during the dual boot setup.

Then, (presuming your laptop can boot from USB), I would go to PendriveLinux.com, download their Universal USB Installer app, and use it to create an Ubuntu USB Installation stick.  That will work much faster than messing around with optical disks.

---

### Post by jrh382 on 2012-01-12
Right, Mark, that helped a lot--I think I'm closing in on this--but what's the correct format for an Ubuntu disk partition? 

-J

---

### Post by jrh382 on 2012-01-12
Nevermind, got that sussed--now, when booting from the USB, I get to the options screen (load from Live USB, Install to Hard Drive, etc) but both the Hard Drive and Live USB options lead to a fast code scroll that gets to another one of the "signal 9 (Killed)" errors above, followed by this repeated several times:

[sdb] No Caching mode page present

I am officially waaaaay far down the rabbit hole. Thoughts, guys?

-J

---

