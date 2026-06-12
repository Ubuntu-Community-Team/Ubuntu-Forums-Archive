---
title: "Palimpsest and Brasero"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by keithpeter on 2009-08-11
Hello All

A fresh install of Karmic Alpha 3 on my Asus Pundit AH2 (Athlon Dual Core 4600, 2.4GHz, GeForce 6150 graphics, Samsung SP2504C 250Mb SATA hard drive), updated today, appears to work fine except for a couple of issues...

1. The Palimpsest disc utility pops up after booting into the desktop to tell me that the hard drive is failing.:eek:. Well, it isn't according to the Samsung HD utility that I downloaded and ran (2 hours to test the 250Mb drive, no errors, no issues, no bad sectors). In the palimpsest window, the 'self test' shows 'passed' in the assessment field, but the 'disk has bad sectors' warning persists.

2. Brasero won't see the CD driver, Gnome Baker did when I installed it, and burns ISOs fine.

Karmic is the only OS on the drive, and I just accepted all the defaults when installing, so ext4 file system, swap and / partitions and so on.

Any ideas or is it bug report time?

---

### Post by nhasian on 2009-08-11
the Brasero bug has already been fixed upstream.  should be fixed when it is updated in the repository.  might take a few days.

---

### Post by autocrosser on 2009-08-12
Take a look at the several Gnome-disk-utility & my-disk-is-failing threads.....You might run a testing utility like gsmartcontrol to verify that your disk IS really having a problem..if things look of--then report a bug & be sure to post it if you do.....

---

### Post by keithpeter on 2009-08-12
> **autocrosser said:**
> Take a look at the several Gnome-disk-utility & my-disk-is-failing threads.....You might run a testing utility like gsmartcontrol to verify that your disk IS really having a problem..if things look of--then report a bug & be sure to post it if you do.....

Aha, Palimpsest = Gnome-disk-utility, which explains why my search revealed no previous issues. Perhaps we need just the *one* name for these programs?:P

I've checked the hard drive using the bootable Samsung utility (Hutil210.iso) and it revealed no issues, so I assume the Gnome-disk-utility / Palimpsest is mis-interpreting the SMART data from the disc. I shall check for bugs already filed now.

Good to hear the Brasero bug is known. Thanks both.

---

