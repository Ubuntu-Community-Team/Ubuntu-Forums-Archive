---
title: "Rather more of an uninstallation than installation"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Hickeydog on 2007-06-07
SOOOOOOOooo.   I decided to uninstall Ubuntu (not because it is a bad OS, just because everyone else in my family didn't like it).  So I googled it and found directions telling me to run some sort of "Recovery" option from my XP cd.  Well, that didn't work, so I found this utility that bassicaly loads that text-based recovery thingamajig.  I had read that you needed to reinstall the boot sector.  Anyways, I ran the "fixmbr" thingy and rebooted  and you guessed it.  I get the error "error loading OS".  So, being the idiot that I am, I try to reinstall XP w/o reformating the hhd.  THAT didn't work.  So I tryed the "fixboot" option.  still didn't work.  So, I tryed recovering XP.  still no luck.  I ithink that I have not damaged the main data sector, only the boot sector.  I was wondering if reinstalling Ubuntu (thus loading GRUB) might help solve the problem.  thanks.

---

### Post by hardyn on 2007-06-07
I woud say not.

for reference, your must use the recovery console, a command line from the windows disk then FIXMBR.
Unless anybody wants to correct me, im pretty sure your boot table is probably damaged.

what you may want to do is to boot the ubuntu disk, mount the windows partition back-up to a USB external or something, and re-install windows... yes, a bit brute force, but will get you off to the races.

cheers.

---

### Post by Hickeydog on 2007-06-07
I did that whole recovery console routine, but that's what (i think) damaged the boot sector.  I downloaded "WindowsXp-kb310094-sp2-pro-bootdisk-enu.exe" and wrote it to the 6 floppies.  I loaded it and ran "fixmbr".  I wonder if the fact that my computer is XP Media Center Edition has anything to do with it?  If I cant get it to boot, I'm just going to say "screw it" and install Windows 2000.  O yeah.  I just ran "fxmbr" again and "fixboot", but to no avail.  :(.  I do dislike windows, but the rest of my family does not like Ubuntu, sooo

---

### Post by zvacet on 2007-06-08
Download Gparted live CD.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

Delete all partitions with it and make them unallocated space.After that reinstall windows.

---

