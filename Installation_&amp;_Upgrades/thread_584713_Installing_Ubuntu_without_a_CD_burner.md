---
title: "Installing Ubuntu without a CD burner"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Tken on 2007-10-21
It has been unbelievably frustrating trying to find information on doing this.  I don't want to wait for an install CD to be shipped to me (if I'm going to be waiting on shipping, I might as well just buy a CD burner and wait on that :)).  

The only thing I have tried thus far is Unetbootin.  I don't know why, but for some reason it didn't install 90% of what I needed - I had to manually install X, gnome, etc.  Since I'm entirely new to linux, this caused way too many issues (couldn't get most of the programs I wanted working).  So unless someone knows an exact fix to this very problem, Unetbootin is out of the question.

Everything else is fair game.  I do have a USB drive, but it's 512MB, so not big enough for the whole Ubuntu install, but it could be used for any other methods, if there are such methods.  I'd be fine with either 7.04 or 7.10, by the way.  I do have a perfectly functional DVD drive if there's any way to get a bootable CD without a CD burner (Daemon tools maybe?).

So, does anyone know of any actual, *working* methods of installing Ubuntu without a CD burner?  Any help is *greatly* appreciated!

P.S. If anyone knows if Ubuntu is ever sold in stores, I'd be happy to buy a copy locally.

Edit/P.P.S.: Dunno if any of this will be relevant, but some system specs just in case:
320GB hard drive, split into two partitions, one running XP Home, the other running a very corrupt install of 7.04 (via Unetbootin).  I plan to reformat the 7.04 partition in order to reinstall it.
AMD X2 3600+
ATI X1900GT
2GB DDR2 800MHz
Random integrated network card that appears to be recognized just fine by GRUB and the Ubuntu installer.
Just ask if any other info is needed.  :)

---

### Post by Dr. Nick on 2007-10-21
for starters try this

[http://ubuntuforums.org/showthread.php?t=316093](http://ubuntuforums.org/showthread.php?t=316093)

---

### Post by pieisgood4589 on 2007-10-21
OK, the EASIEST way to dual boot Windows XP and Ubuntu Linux, go with [http://wubi-installer.org/](http://wubi-installer.org/) it installs Ubuntu on your PC with a simple (large) download, and then you can choose to boot into Ubuntu or Windows XP. There is also a way to make the Ubuntu a stand-alone system with Wubi, but it requires some searching in the forums. If you ever want to remove Wubi, just uninstall it in the Windows uninstaller! Good luck! :KS

---

### Post by Tken on 2007-10-21
> **pieisgood4589 said:**
> OK, the EASIEST way to dual boot Windows XP and Ubuntu Linux, go with [http://wubi-installer.org/](http://wubi-installer.org/) it installs Ubuntu on your PC with a simple (large) download, and then you can choose to boot into Ubuntu or Windows XP. There is also a way to make the Ubuntu a stand-alone system with Wubi, but it requires some searching in the forums. If you ever want to remove Wubi, just uninstall it in the Windows uninstaller! Good luck! :KS

I had heard of Wubi, but I can't seem to figure out how to make it work with my situation - that is, how do I get Wubi to recognize that I already have 40 gigs partitioned and set aside for it?  All it sees is C:, where my XP is installed, and I assume it wants to chop up that, make a new partition, and install Ubuntu to there.

And if Wubi can't select the right partition, what program should I use to consolidate my current setup of 3 partitions (one for XP plus one for the corrupt 7.04, plus one for linux swap, right?) into one big partition (like before I tried installing Ubuntu), so that Wubi can then chop that up?

Again, thanks for the help.  :)

---

### Post by pieisgood4589 on 2007-10-21
You should manually edit the partition tables. If you don't know how to, PM me.

---

