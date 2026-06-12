---
title: "blank screen after loading the live cd ver 10.04"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by customan on 2010-09-05
ive downloaded the Ubuntu CD from the official website and burned it twice, once one a dvd and the other on a normal 700MB CD-RW.
in both, the screen went blank after the loading part before the main menu (installation, try it blah blah..)
what should i do?
btw i use a windows XP and here is my hardware details...
----------------------
sapphire hd 5770 1gb,
 4 gb of ram, 
Intel Core i5- P55 , 3.5 ghz, 
i think that its enough for the minimum of the ubuntu isnt it?

---

### Post by dino99 on 2010-09-05
there you will find a little help about how to install ubuntu:
[http://ubuntuforums.org/showpost.php...4&postcount=14](http://ubuntuforums.org/showpost.php...4&postcount=14)

instead of burning cd/dvd, better to use usb stick IMO

---

### Post by customan on 2010-09-05
the link is broken and leads me to the main forum ):P

---

### Post by gibbogle on 2010-09-05
[QUOTE=customan;9808361]ive downloaded the Ubuntu CD from the official website and burned it twice, once one a dvd and the other on a normal 700MB CD-RW.
in both, the screen went blank after the loading part before the main menu (installation, try it blah blah..)
what should i do?

Many people are having similar problems.  The first thing to do is to check that the iso you downloaded is complete and uncorrupted, since this is often not the case.  Best to do the md5sum check.

Look here:
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by GenBattle on 2010-09-05
This is a very common problem, usually due to the default graphics drivers Ubuntu selects on boot.

Follow the instructions here:
[http://ubuntuforums.org/showpost.php?p=9766336&postcount=8](http://ubuntuforums.org/showpost.php?p=9766336&postcount=8)

That should allow you to at least boot off the live CD. If you're booting off a USB disk you can edit the syslinux.cfg to change the boot options. I found once i got through the install (as painful as it was), Ubuntu worked (more or less) fine.

---

