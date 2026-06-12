---
title: "Scanning a drive for bad sectors"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by miltownkid on 2005-05-07
I bought a second hand computer I could use to play with Linux and ran into a problem.  It would freeze a lot.  Eventually I figured it out as being some bad sectors.  Being an old school Windowz/DOS user I think to myself "No problem, I'll just run a scandisk".

Well, it was a problem.  I did try to search the wiki here and stuff, but I didn't find anything.  Well, google lead me to this solution.

[http://yhslug.tux.org/docs/hdtest.htm](http://yhslug.tux.org/docs/hdtest.htm) (for information on how to do it)

and here [http://www.toms.net/rb/](http://www.toms.net/rb/) for a boot disk you can use it from.

(I ended up using this [http://ubcd.sourceforge.net/](http://ubcd.sourceforge.net/) it has the toms disk on the CD).

Anyhoo, I'm sure many of you know about this little solution so I guess I'm suggesting that a way to test a drive before doing the install would be nice.

If there already is a way (to test a drive from the installation CD) I wasn't aware of I'd like to know it.

thanks

---

### Post by tonym on 2005-05-08
Either from the install CD or a Live CD partition the disk and then run mke2fs -cc /dev/xxx

The  -cc carries out a read/write test.  If you had only one c it would do a read only test.

After that do the install but tell the installer not to reformat the partition.

---

### Post by Gandalf on 2005-05-08
[QUOTE=tonym]Either from the install CD or a Live CD partition the disk and then run mke2fs -cc /dev/xxx

The  -cc carries out a read/write test.  If you had only one c it would do a read only test.

After that do the install but tell the installer not to reformat the partition.[/QUOTE]
 or just badblocks /dev/hdX no???
(where hdX is the device (normally it's hda1) type fdisk -l /dev/hd* to see alla available devices)

---

