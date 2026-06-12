---
title: "Backup entire Ubuntu installation"
date: 2010-04-18
forum: Installation &amp; Upgrades
---

### Post by migrator90 on 2010-04-18
I start using Ubuntu, after successfully installed it without any problem.Then I downloaded latest updates, etc.
But,after installing a display driver, my computer freezes, refusing to go beyond the welcome screen. I tried several ways but could not solve the problem. So I decided to re-intall Ubuntu, download again the updates, again configure my settings, etc. 
Therefore, I'd like to know whether there is any application to backup or to create a full image of a hard disk so as to avoid the long hours of re-installation. Thanks for your help:confused:

---

### Post by quixote on 2010-04-19
Yes, something like that really ought to be part of the operating system!

For right now, the only thing I've found that works is [Clonezilla]("http://clonezilla.org/").  Download Clonezilla Live and burn a CD of it.  Find that spare USB hard drive you have lying around which is larger than the partition you want to back up.  Boot from the Clonezilla CD, fight your way through the rather obscure menu choices, attach the HD when it says, and it'll back up dozens of GB in less than half an hour.

It makes a complete duplicate, so if you want to restore the whole thing or just a file, it's simply a matter of copying it back over the original.

---

### Post by lisati on 2010-04-19
You might want to check out remastersys:
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[http://ubuntuforums.org/showthread.php?t=1455205](http://ubuntuforums.org/showthread.php?t=1455205)

---

### Post by migrator90 on 2010-04-21
I've tried the different options of this program, but none gives an exact copy of the system files, mainly the one in use. As a result, the restored copy is not identical to the original. Thanks anyway

---

### Post by quixote on 2010-04-22
Not sure if it was remastersys or clonezilla you tried, but you need to boot off a LiveCD or LiveUSB so that your system partition is *not* in use.  You're right that if you boot from it, you can never get a proper system backup.

About remastersys: I tried it for three different laptops I was setting up for people, and I couldn't get it to work on any of them.  :(  I got loads of good help on the remastersys and ubuntu forums, but finally had to give up.  Apparently, there are some setups it just doesn't work with.  So if you can't get it working, it may not be anything you're doing.

---

