---
title: "Interrupted upgrade from 8.10 to 9.04 beta"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by areatha on 2009-04-02
Hello,

The powersupply of my computer broke down while I was upgrading from Ubuntu 8.10 to 9.04 beta. The archives reads that I am using Jaunty while updating, but something has gone wrong because I am unable to update or upgrade my system either through terminal or Synaptic.

I get the following error when trying to update/upgrade:
"dpkg: critical error, aborting:
files list file for package 'libpurple0' is missing final newline
E: Subprocess /usr/bin/dpkg returned an error code (2)" 

How can I fix this - and is it possible to fix without a complete re-install?

Thanks, areatha

---

### Post by Therion on 2009-04-02
Frankly, if it were me, I'd do a fresh install.

But... I also know most people, for whatever reason, would rather chop off a major limb than do a twenty-minute clean install.

So, if you want to try and salvage things, fire up a Terminal:```
sudo apt-get -f install
```
Then this:```
sudo dpkg --configure -a
```

Then try upgrading again.

---

### Post by areatha on 2009-04-02
I've tried both "install" and "dpkg configure" before. Get the same result this time around: An error-message on three packages: linux-image-generic, pidgin-data and libpurple0.

Another act of Murphy, I guess.... 

But thanks!

---

### Post by upchucky on 2009-04-02
it is possible to still back up any files you want to save then do a clean install, power supply fails are one of the worst things to happen to a drive during a write.

see knoppix or ubuntu live cd to save files to a usb, cd, dvd, stack of floppies, or network drive.

then re-install a fresh clean error free ubuntu, and restore your saved files.

---

