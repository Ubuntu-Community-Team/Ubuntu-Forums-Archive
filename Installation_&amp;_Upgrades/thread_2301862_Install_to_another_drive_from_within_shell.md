---
title: "Install to another drive from within shell"
date: 2015-11-05
forum: Installation &amp; Upgrades
---

### Post by faroutliving on 2015-11-05
This seems like it should be possible, but I don't know how :-)

I have two remote servers about 2000 miles away, and yesterday while updating one to 15.10 something went south. Someone stopped by the facility, but they know far less than I do. Average user might even be an over statement :-(

The system fails to boot, and the photo of the screen shows the system reports missing /sbin/init. The file appears to be truly missing. Since both machines where 99.999% the same before this failed update, I would like to either:

1) Stick the bad drive in the good machine and clone to the bad drive. How to get around cloning a live system?

2) Run a basic 15.10 installer on the good machine and install to the bad drive without screwing the good drive.

Are either of these possible? I could certainly send them a new HD to install, or a bootable USB, but I'd like to get the machine backup before this weekend.

Thanks for any clues!

Deron

---

### Post by TheFu on 2015-11-05
Use servers with DRAC, RIBLO, IPMI capabilities and do the install yourself.  A local person would only need to insert the install media.  Be certain these remote capabilities are not directly accessible over the internet. The  built-in security for these basically  ... er   ....   suck.

Lots of options here about cloning disks. Cannot safely clone a running system without non-trivial setup **before** the system was built. The safest way to  clone a disk is by using a live-boot linux and using **ddrescue** from source to target. Check the forums.

You can probably build the system disk locally then ship just the disk to the remote location if it isn't too complex. Linux installs are only loosely tied to the actual hardware.  Just fix the udev/rules for the network adapters - that should be enough for a  simple install.

Complex installations may not be this easy.  IPMI easily pays for itself after 1 use, even if it  just saves an hour drive.

---

