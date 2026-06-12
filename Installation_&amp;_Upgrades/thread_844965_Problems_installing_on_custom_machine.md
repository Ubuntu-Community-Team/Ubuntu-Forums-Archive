---
title: "Problems installing on custom machine"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by johniv on 2008-06-30
Hey everyone! I would really like to use ubuntu but i've run into some problems.

When I try to boot Ubuntu the screen goes straight to the loaderbar screen, it never finishes and error messages show up.


My system is:
OS: Vista
CPU: intel Q6600
MB: ABIT IP 35 PRO
GFX: GeoForce  8800 GTS 512
CD: SATA
HD: SATA (primary) IDE (secondary)

INSTALL: ubuntu-8.04-desktop-i386

picture:
[[IMG]http://img413.imageshack.us/img413/3703/img0240oo3.th.jpg[/IMG]](http://img413.imageshack.us/my.php?image=img0240oo3.jpg)

please help,
John

---

### Post by starcannon on 2008-06-30
fd0 would be the first floppy disk drive, perhaps for the time being disable your floppy drive in the bios, and give it another go?

Oh do so even if you don't have a floppy installed, if the controllers on, it could be the issue.

---

### Post by johniv on 2008-06-30
Thank you very much! I should point out that ubuntu works fine for me within virtualbox...
and in virtual box access to the floppy is denied. So, I'll look into that!

will report back,
john

---

### Post by johniv on 2008-06-30
Floppy Access was already denied in BIOS.

I've got more of the error, this one repeats alot

ata4.00: Exception emask 0x0 SAct 0x0 SErr 0x0 action frozen
(line with numbers)
Status: { DRDY }

Does that help?
Thank you

picture (update):
[[IMG]http://img413.imageshack.us/img413/3703/img0240oo3.th.jpg[/IMG]](http://img413.imageshack.us/my.php?image=img0240oo3.jpg)

(update2): It's probably really important to mention i have a primary SATA drive and a secondary IDE drive.

---

### Post by starcannon on 2008-06-30
I'm lost, Perhaps ask or have thread moved to Absolute Begginers? 

Sorry, I gave my best :( just wasn't there this time. Please if you solve this let us know. I'm puzzled, your hardware list looks like it should go fine.

---

### Post by johniv on 2008-06-30
Aha! No It's fine. My computer seems to like to be difficult

---

