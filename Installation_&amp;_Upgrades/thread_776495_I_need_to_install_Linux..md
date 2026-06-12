---
title: "I need to install Linux."
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by jesusfreak107 on 2008-04-30
I have a 700MHz Toshiba Satellite, w/10GB HDD, and 192MB RAM, with a working Floppy drive, and a dead CD drive. I cannot boot off of any external device via the BIOS.  I have Windows 98 SE on it.  I need Ubuntu/Xubuntu.  I have tried a heck of a lot of stuff to try to get it working.  I am trying wubi, but it needs 256MB RAM.  I am currently trying the alternate Xubuntu 7.04 iso, with Wubi 7.04, but the file is taking a few hours to download.  Any ideas?  I have a 2GB SD Card with a 760MB FAT32 partition, a 256MB EXT3 swap partition, and a 900-ish MB EXT3 partition, that I can use, if possible.  it is plugged in via USB adapter.

Any help?

---

### Post by Dylnuge on 2008-04-30
Wubi sounds to me like your only option, since Ubuntu doesn't offer floppy installs.

If you are somewhat skilled with CLI, you may want to try Pocket Linux ([http://www.pocket-linux.org/](http://www.pocket-linux.org/)) or the Gentoo minimal install ([http://www.gentoo.org/](http://www.gentoo.org/)). These are not easy distros, especially not Gentoo, but they fit on a floppy. Both boot into a CLI, with Gentoo requiring a very complex install (you learn a ton during it though). Pocket Linux is easy if you know your way around a Linux Terminal ([http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/) is the best for learning). And you do need a network connection. Gentoo is NOT a small distro, Minimal will take several days (it installs from the internet).

On the other hand, Damn Small Linux ([http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)) should be an easier install, and it has a GUI, but I haven't used it, so I am probably not the best one to give testamonials on it.

Your only other option is to upgrade your PC, unfortunatly. I know that it seems like a hard one, especially since Linux will work on older PCs, but unfortunatly, without a way to install it from a CD, and with only 10 GB of space, you are pretty limited in your options. The SD Card might work, but I wouldn't have any idea on how to strap an iso to one unless it was U3.

Hope that helps,
Dylan

---

### Post by jesusfreak107 on 2008-04-30
I cannot upgrade it.  it is a laptop that I found in the garage, that cannot take anymore hardware.  Thanks for the suggestions, although I am very set on installing Ubuntu/Xubuntu.  I do not want to start using another OS right now, unless it is puppy linux, which I have also used before.

---

### Post by RATM_Owns on 2008-04-30
If you have a big USB drive:
[http://ubuntuforums.org/showthread.php?t=575406](http://ubuntuforums.org/showthread.php?t=575406)

Or there is Wubi.
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by punkybouy on 2008-04-30
Remove the hard drive and mount it in a desktop via a laptop hard drive to desk top hard drive adapter you can buy for about $8.  Install Linux using the CDROM on the desktop. When done take the laptop hard drive out of the desktop and put it back in the laptop and it should boot, most likely to a prompt where you can run the command to reconfigure the X server.
This all assumes that both laptop and desktop are running the same types of CPUs.

---

### Post by jesusfreak107 on 2008-04-30
> **punkybouy said:**
> Remove the hard drive and mount it in a desktop via a laptop hard drive to desk top hard drive adapter you can buy for about $8.  Install Linux using the CDROM on the desktop. When done take the laptop hard drive out of the desktop and put it back in the laptop and it should boot, most likely to a prompt where you can run the command to reconfigure the X server.
This all assumes that both laptop and desktop are running the same types of CPUs.
I know that will work, but I am a teenager without a job, and I already spent $30 on this lappy to buy a power cord, and I am not willing to spend any more.  Thanks for the suggesstion, though.

---

### Post by jesusfreak107 on 2008-04-30
> **RATM_Owns said:**
> If you have a big USB drive:
[http://ubuntuforums.org/showthread.php?t=575406](http://ubuntuforums.org/showthread.php?t=575406)

Or there is Wubi.
[http://wubi-installer.org/](http://wubi-installer.org/)
> First you will need a computer that is already running Ubuntu or some other Linux distro.
I do not have Linux installed on the lappy, I have Windows 98SE. Also, my computer cannot boot off of the USB ports, I would need extra software to do that.  
Thanks anyway, though.

---

### Post by jesusfreak107 on 2008-04-30
Oh, crap!  It did not have 192MB RAM, it had 64!!!  NOW it has 192, I stuck another chip in there.  THAT would be part of my problem.  However, I STILL don't have a CD drive or USB support, so suggestions still welcome.

---

### Post by jesusfreak107 on 2008-04-30
Okay, I'd tried using GRUB to boot off of an iso file earlier, but it complained about the file not being "contiguous" and I did not know what that implied, so I asked Dad about it, and I am defragmenting the HDD right now ("You last defragmented this drive 930 day(s) ago").  He seems to think that will work, I'll let you know how that turns out.

In the meantime, feel free to continue to offer suggestions, there is no guarantee this will work.

---

### Post by punkybouy on 2008-05-07
Well I remember about 10 years ago creating a Free BSD boot diskette which allowed me to boot from the floppy and go out on the internet and fdisk and format and load Free BSD on a desktop (CDROMS were expensive then)and its hard drive was probably not even a GB.
Do you have a broadband connection?

---

### Post by punkybouy on 2008-05-07
This will work, I think.

[http://www.linux.com/feature/124684](http://www.linux.com/feature/124684)

---

### Post by punkybouy on 2008-05-07
Try this.

[http://www.linux.com/feature/124684](http://www.linux.com/feature/124684)

---

### Post by jesusfreak107 on 2008-05-07
Thanks, I'd actually already tried unetbootin.  Anyways, I actually gave up, and just installed Puppy Linux via a wakepup2 floppy, and my USB drive.  Thanks for the input, though.  I forgot about this post, and forgot to close it off.  Screenshots are below, you can also read about it on my blog, which is in my signature.

---

### Post by lamalex on 2008-05-07
Maybe you should stop being lazy and get a job? Then you could put a working CD drive in it. Also check if your town has any computer recycling centers, you can get really cheap parts there.

---

### Post by jesusfreak107 on 2008-05-07
ok, 1: I am 15, and cannot drive, and therefore cannot get a job (also encumbered with various physical problems preventing me from mowing, which I have done in the past).  and, 2:  calling someone lazy in public is being directly rude, and violates the Ubuntu Forums Code Of Conduct.  I suggest you delete your post, before an admin catches you.  

(also, all further attemts at communication will be ignored.)

---

