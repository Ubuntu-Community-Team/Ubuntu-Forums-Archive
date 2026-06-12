---
title: "Move from Red Hat to Ubantu"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by gregj5916 on 2007-09-20
I have a system with Red Hat installed.  I want to switch to Ubantu.  I changed the BIOS to boot from the CD first and expected that I could boot from the CD and overwrite the Red Hat instal.  Instead, Red Hat booted.

How can I get the system to overwrite the Red Hat install and load Ubantu?

Thank you.

---

### Post by kellemes on 2007-09-20
Booting the Ubuntu LiveCD does not overwrite anything.. that's the great thing about it.. Only installing overwrites obviously.
In BIOS you need to set the diskdrive to be first in line of the bootorder.

---

### Post by Herman on 2007-09-20
If your LiveCD won't boot and you're sure you have the BIOS set to boot a LiveCD then there might be something wrong with the CD or something wrong with the CD/DVD drive.
The simplest ways to test which those two things is your problem are to try to boot a different LiveCD and see if that works and/or try the same CD in a different computer.
Regards, Herman  :)

---

### Post by gregj5916 on 2007-09-20
Changing boot order to floppy then CD has no impact.

The CD does work on other computers.  I realize that it doesnt overwrite on its own but you get the option to install when it runs.

Any other ideas?

---

### Post by Xoanan on 2007-09-20
Just curious;  I had a similar issue with mine and I took me awhile to find out how to boot it from CD;  One thing I did try was to test the CD through Red Hat.  

Try to see if you can access all the files on the CD from Red Hat.  This will tell you if the CD is functional.

---

### Post by gregj5916 on 2007-09-20
I am sure the CD is functional.

---

### Post by Herman on 2007-09-20
Can you boot a different LiveCD in that CD/DVD drive then?

Maybe your CD/DVD drive is okay for music or data CDs, but might have trouble with LiveCDs or installing software. Maybe you just need to clean your optical drive lens.

---

