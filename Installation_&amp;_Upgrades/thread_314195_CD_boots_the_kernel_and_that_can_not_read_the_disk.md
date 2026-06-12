---
title: "CD boots the kernel and that can not read the disk"
date: 2006-12-07
forum: Installation &amp; Upgrades
---

### Post by muxecoid on 2006-12-07
I just tried to install Ubuntu on friend's computer and failed. When it boots it shows the list of boot option, than it loads the kernel and stops accessing the CD and can not "see" it. I tried booting Knoppix - the same problem it just boots the kernel and than says, that it can not read the disk. I guess that it's due to improper "numbering" of disk somewhere cause it attempts to read first IDE master as hdd. I attempted to disable other driver via BIOS but it did not work.

Device configuration:
1*HD master at IDE0
2*DVD master and slave at IDE1
1*SATA HD shown in BIOS as master at IDE channel number four (it's SATA)

How can I boot from CD?

---

### Post by randiroo76073 on 2006-12-07
You will have to go into bios and change boot order to:
CD
IDE-1
IDE-2
SATA-1

Don't know what your bios says, but look for something that says "Boot order"  Once you do this it should boot from cd & allow install
HTH

---

### Post by muxecoid on 2006-12-07
BIOS has only 3 items in boot order the current config is

1. Floppy.
2. IDE1 - master DVD
3. IDE0 - master HD

---

### Post by randiroo76073 on 2006-12-07
Then change Floppy to CD or CDrom, depending on your BIOS, should either be up/down arrows or pgup/pgdown buttons on keyboard

Does this machine have only 1 IDE hard drive & 1 SATA hard drive, a floppy & cd/dvd drive?

---

### Post by muxecoid on 2006-12-07
> **randiroo76073 said:**
> Then change Floppy to CD or CDrom, depending on your BIOS, should either be up/down arrows or pgup/pgdown buttons on keyboard

Does this machine have only 1 IDE hard drive & 1 SATA hard drive, a floppy & cd/dvd drive?
Tried it. Did not work.


First knoppix kernel boots. Than it shows message that hda, hdc, hdd found and list type of each, hda is hard disk. Than it attempts to read CD filesystem from hda and, indeed, fails. Why does it stupidly try to read from hda?

I even added third CD device at hdb, it keeps trying to read from hda. Stupid linux. It sees that hda is Hard Disk and still attempts to read boot cd from there. :(:(:(

---

### Post by randiroo76073 on 2006-12-07
Without seeing bios screen I would say 2 possiblities, 1-something in bios is directing it to wrong place, 2- depending on age of cd/dvd drive it is not reading the disk properly.  You might try turning off "acpi".  Also you might have to open case & disconnect sata drive till after install. I'm fresh out of other ideas, sorry.

---

### Post by muxecoid on 2006-12-07
acpi=off - did not work.

I attempted to remove the hard disk on IDE0 master and put CD instead. This way Cd was on hda. Knoppix was "searching" for CD at hda AND DID NOT FIND IT. The same for Ubuntu.

WTF. Would linux someday have less installation problems, than Windows?

Ah, at last. I started again with fresh BIOS and it worked. Still do not know what was wrong with old BIOS conf.

---

