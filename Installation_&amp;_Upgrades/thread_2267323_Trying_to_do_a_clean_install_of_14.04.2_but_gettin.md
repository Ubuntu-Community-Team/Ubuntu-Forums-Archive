---
title: "Trying to do a clean install of 14.04.2 but getting stuck"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by marinecomm on 2015-02-28
I used to have 14.04.1 installed on part of my computer. I decided to upgrade and do a clean install of 14.04.2. When I first tried to do a clean install over the older Xubuntu, the installation kept getting stuck and the wifi would disconnect about every minute and reconnect. I've tried reformatting the partition, and installing without wireless. Right now it is stuck at 'Removing conflicting operating system files' I do keep getting a warning saying **WARNING: Source ID ##### was not found when attempting to remove it** and each time I get the warming it is a different number. I was running 14.04.1 64-bit dual-booted with Windows 7 HE. 3.2ghz processor, 10gb ram. I'm not sure what else to do.

---

### Post by tgalati4 on 2015-02-28
It's normally not a good idea to perform an installation with wireless.  Too much chance of interference and leaving your system in an undefined state.  Use a wire for connectivity.

You might have to wipe the drive completely--back up your data to another media, not just to another partition on the same drive.  Delete the partition and recreate it and format it.  Then start your installation with a known, working LiveUSB stick.  Run the "check disk integrity" on the USB stick to make sure you have a consistent file set to install from.

Each package that gets installed has a pre-installation script, an installation script, and a post-installation script--in that order.  The pre-installation script checks for the current version of a package, stops any affected services, then deletes the files (but not all the time) that are obsolete.  If this script fails, then you don't get to the next step of installing the package.  Troubleshooting the exact problem would take more time than performing a clean wipe and reinstalling.  With a wire.

Normally one would expect to perform a one-button-upgrade and have it work.  And that is fine.

Except when it isn't.

---

### Post by Bucky Ball on 2015-02-28
> **tgalati4 said:**
> It's normally not a good idea to perform an installation with wireless.  Too much chance of interference and leaving your system in an undefined state.  Use a wire for connectivity.



^^^
This. Use a wired connection for installs.

Just curious as to why you decided to do a clean install over a working system that would have been upgraded to 14.04.2 with normal updates. Most people are there now. :-k

From where you are now, I would plug a cable in and try a regular clean install.

---

