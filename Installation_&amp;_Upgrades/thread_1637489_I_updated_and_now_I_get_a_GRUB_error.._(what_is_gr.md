---
title: "I updated and now I get a GRUB error.. (what is grub?)"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by schwghrt on 2010-12-04
Had windows installed.  I installed Ubuntu using the windows installer.  Everything worked great for a while.  Today, ran the updater, and it asked which drive was the primary so it could install GRUB.  Now computer when reboots states.... No Such Device: XXXXXX
Grub Rescue>

Help! 

Thanks
Sam

---

### Post by karthick87 on 2010-12-04
Post the ouput of [COLOR=DarkOrange]**[Bootscript]("http://bootinfoscript.sourceforge.net/")**[/COLOR]

---

### Post by wilee-nilee on 2010-12-04
> **karthick87 said:**
> Post the ouput of [[COLOR=DarkOrange]Bootscript[/COLOR]]("http://bootinfoscript.sourceforge.net/")

+1 that will be the best thing here you it sounds like have a wubi install. Wubi=install from a live windows environment.

Download a Ubuntu cd burn it or load a thumb boot either and run the script and post it.

---

### Post by schwghrt on 2010-12-04
Definitely a noob.  Where do I get a thumb boot at? Tx

---

### Post by schwghrt on 2010-12-04
I followed the advice on this thread, and it worked... Thanks!!!

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by karthick87 on 2010-12-04
Download ubuntu from [http://www.ubuntu.com/](http://www.ubuntu.com/) and burn the iso image to your CD.Now boot your system with that cd,run the bootscript and post your results here.

---

### Post by karthick87 on 2010-12-04
If your problem is solved.Then mark this thread as[COLOR=Red] [SOLVED][/COLOR]

---

### Post by wilee-nilee on 2010-12-04
> **schwghrt said:**
> I followed the advice on this thread, and it worked... Thanks!!!

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Awesome;) so make sure in the future that you don't do any grub update/upgrades in the wubi. It puit Grub in the master boot record most likely when you want the MS bootloader in the MBR.

Also be sure to mention exactly what installations you have eg which windows, and which Ubuntu.

---

