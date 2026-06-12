---
title: "Flash Drive Install Questions"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by mcmanigle on 2010-09-21
Hi all,

I've installed Ubuntu on my USB flash drive.  The goal is to have an always-available desktop for those times I encounter a computer that doesn't have what I need, and as a rescue tool.  I made a full installation to the flash drive (rather than a persistent ISO setup) because I want to be able to distupgrade, etc., without worrying about changing the ISO file and messing around too much with GRUB.  If you're curious, the key has three partitions (fat32 for general flash drive use, mounted at /usbkey, ext4 mounted at /, and swap).  I have Dropbox sync to /usbkey/Dropbox.  I also have a folder /usbkey/Dropbox/.encdocs that is the encrypted side of an encfs mapped to ~/Documents (with similar setups on my mac and other Ubuntu boxes) so that my documents are always available but not exposed on Dropbox.

With that lengthy introduction, I have three questions:
1. I would like to be able to use this USB key to install Ubuntu on a given computer as well.  It seems like it is impossible (or next to it) to convince GRUB to chainload an ISO file that is living on my ext4 partition within the usb key.  Given that, it would seem my only option is to create a dedicated installer partition or to manually install with debootstrap or similar.  If anyone knows how to get GRUB to boot from an iso on ext4, or how to run the Ubuntu installer from within a running Ubuntu system, please let me know.

2. Many computers these days rely on bluetooth keyboards and mice exclusively.  I haven't come across any way to handle these computers without bringing my own USB mouse along.  For instance, a program that will detect that no input devices are available and begin to automatically attempt to pair with available bluetooth input devices upon Gnome launch (obviously before login).

3. Are there any particular packages I should install to make as many hardware drivers as possible (particularly as regards network/wifi adapters) available?

I know this was a long and disjointed post; please forgive me, I'm happy for any general advice people care to provide about my setup as well.

John

---

### Post by C.S.Cameron on 2010-09-21
You should be able to get Grub to boot an iso file on the FAT32 partition.
I would think just add a menuentry with the full path to that iso.

---

### Post by mcmanigle on 2010-09-22
It looks like [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604) gives a very nice solution for making Grub boot from an ISO on the ext4 filesystem.  Just tested it and it works very nicely.

---

