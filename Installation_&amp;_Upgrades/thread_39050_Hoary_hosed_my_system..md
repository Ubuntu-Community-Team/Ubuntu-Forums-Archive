---
title: "Hoary hosed my system."
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by Bleach on 2005-06-03
I thought it would be a good idea to install Ubuntu on my system after trialing it in vmware for a few months....

Boy was I wrong.

Simple install, except after the first boot (after it installs grub) it now displays

"error loading operating system"

Tried installing 3 times, also tried a fixmbr with my windows boot disk to recover my bootloader so I can load windows.  Of course that doesn't work.

Simple setup really, windows on hda and installing Ubuntu onto hdb.  Installed grub to the master boot record, not to any particular drive (it picked up my windows XP install)


Both harddrives are set to LBA as per some other suggestions for this problem from a few months ago. 

Im not exactly a newb, only have installed 5+ different distro's into a dual boot (including gentoo) environment.  Yet Ubuntu is the only one to have a problem?
Any ideas? 

Ive booted into it with both my Knoppix and Ubuntu Live CD and looked at the grub boot menu etc, nothing odd there.

 I though Ubuntu was supposed to be desktop "ready"

---

### Post by mingus on 2005-06-03
ouch, been there . . . have you tried the following:

I've got to run just now and will be back with a longer reply later, for now try:

>fixboot

This marks C as the active "system" partition, required by Windows to boot.

also, you aren't by chance using a drive overlay, are you?  If you are, re-writing the MBR will wipe it out and break the handoff from BIOS to ntldr - not a problem for Linux, though, so Linux can boot but Window's can't.

More later.

---

### Post by Bleach on 2005-06-03
No luck with anything.


Tried re-installing windows on hda and Ubuntu on hdb,

Put grub on hdb, but sure enough it writes the wrong values.

My menu.lst says Ubuntu is booting from hd(0,0) which would be my Windows install.

Funny that ubuntu boots from there fine, windows doesn't work though if i use any combinations (it should be at 0,0 considering its on hda and ubuntu should be 1,0)

---

### Post by mingus on 2005-06-03
After you reinstalled Windows - but before you reinstalled Ubuntu - were you able to boot Windows?

Please post back a copy of your menu.lst

---

