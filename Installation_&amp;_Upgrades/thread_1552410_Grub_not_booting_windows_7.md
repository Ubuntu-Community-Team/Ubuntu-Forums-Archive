---
title: "Grub not booting windows 7"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Alexander Tang on 2010-08-13
Hi I have just installed Ubuntu alongside windows 7 on the same partition the other day and for some reason I cannot seem to start up windows 7 from the grub boot list.

I have tried to fix this by using the Windows 7 repair option on the installation disk and ran bootrec.exe/FixMbr and FixBoot but it still does not boot.

The installation disk recognizes that I have a windows installation on the HD and it appears on the boot list for Grub but whenever I try to start windows 7 it just simply reverts back to grub boot list... Anyone can help? Thanks...

---

### Post by MAFoElffen on 2010-08-13
So when you pick the Win7 item, what does it do? 

...As I remember there's also a "fix" were there is a backup instance of the winodws sector that you can copy over... I did it from within Ubuntu.  That's what I had to do about 2 month's ago... The Winodws Rescue didn't work for me and I had to go a step further.  I'll have to look back where I found that.  

Will get back with that...

---

### Post by MAFoElffen on 2010-08-13
Here it is:  [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector) It has all the instructions and how to install tesdisk to do the repair from Ubuntu.

Not sure about how "testdisk" is going to work with Ubuntu in the same partition, as all my installs are in separate partitions.  But "testdisk" will copy over the backup boot sector. The details on the testdisk package is here: [http://packages.ubuntu.com/dapper/testdisk](http://packages.ubuntu.com/dapper/testdisk)

I thank "[COLOR=SeaGreen]oldfred[/COLOR]" for referring this to me.  It worked for me - when all that I tried before didn't. Hope it works for you.

---

