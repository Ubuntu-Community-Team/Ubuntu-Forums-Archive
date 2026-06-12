---
title: "Install with no bootable drive but HD"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by DrSteve on 2006-11-13
Hello all.  Have done ubuntu and xubuntu installs on a half-dozen machines, also using SuSE 10, so not totally unfamiliar with linux but have made it pretty easy on myself so far.

I am looking to install ubuntu or xubuntu on a Toshiba Portege 7200CTe I've demoted to experimental use after it stopped booting "that other OS" last week.  This machine has no docking station, no internal CD-ROM, and does not boot from USB-connected drives.  The hard drive is currently sitting in a 2.5" enclosure, so I can convert it to a linux filesystem and put files on it over USB from one of my other linux machines.

I'm assuming there's something I can do to set up the filesystem and put an ubuntu installer on the HD via USB connection, then put it back in the laptop and boot it.  Does anyone have any detailed steps for this?

---

### Post by lha on 2006-11-13
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")
It's not a detailed how-to, but it might give you some ideas to work with.

---

### Post by DrSteve on 2006-11-13
I had seen this but my problem is the drive no longer boots the OS that's on it, namely XP.  Not sure why.  Maybe I should address this first; was just planning on reformatting it rather than booting XP to install Linux.

---

### Post by emdeem on 2006-11-13
You can do a PXE boot install.

---

### Post by notebook_ftw on 2006-11-13
I'm also wondering how to do this.  My problem is that I tried upgrading to Edgy from Dapper from the built-in upgrader, but things went terribly ary and my distribution is screwed up.  The CD-ROM on the old Dell Latitude C640 no longer works, nor does it support boot from a flash drive.  And unlike the OP I do not have it hooked up to a 2.5" USB enclosure.  It's an old IDE (I think) notebook hard drive, and my new notebook has an SATA hard drive, so I can't plug it into that.  So, I have a problem. 

All this being said, I would prefer not to have to reformat the machine.  I still have some info on the hard drive that I hadn't backed up.  Not to mention I don't want to lose all the little apps I'd installed.  I've tried several things to fix it including ```
sudo apt-get -f install
```, and that fixed a bunch of broken packages, except now hula-modweb is still not responding.  I tried ```
sudo apt-get dist-upgrade
``` to upgrade everything, and it got to like 90% and then had an error.  I tried booting into an old kernel and then doing ```
sudo apt-get -f install
``` to fix 6.06 but still nothing.  Now, when I boot into anything except a recovery mode, the screen fills with an error about something called /dev/null.  I'm really confused here.  X is of course screwed up, and ```
sudo dpkg-reconfigure xserver-xorg
``` did nothing.  Please help.

---

### Post by notebook_ftw on 2006-11-15
Bump... anyone?

---

### Post by lha on 2006-11-15
> **DrSteve said:**
> I had seen this but my problem is the drive no longer boots the OS that's on it, namely XP.  Not sure why.  Maybe I should address this first; was just planning on reformatting it rather than booting XP to install Linux.

You can install grub on that drive with a working computer and then grub to boot the net-installer.

---

