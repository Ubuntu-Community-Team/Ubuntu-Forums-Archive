---
title: "Undetected SCSI hard drive installation"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by darklyndsea on 2007-11-16
I'm attempting to install Ubuntu 7.10 on a computer with a SCSI hard drive which is currently not detected.  What do I have to do to get it recognized and working?

---

### Post by Pumalite on 2007-11-16
Did you format the drive?

---

### Post by darklyndsea on 2007-11-16
I haven't, as I don't know how to format undetected drives, but it's possible that it has been formatted recently.

---

### Post by Pumalite on 2007-11-16
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it and see if it detects your hard drive.
If not, check BIOS to see that is well configured and recognized.

---

### Post by darklyndsea on 2007-11-16
I tried Gparted several times; however, it always got to the same point and then the screen went blank and stayed blank, so I was unable to tell if it detected the hard drive.

I went into BIOS after that and found that the SCSI options were disabled, so I enabled them and then the hard drive was detected by BIOS at least.  Unfortunately, when I try to install Ubuntu again, it finishes loading and does the same screen blank thing it does with Gparted (previously, the live CD had worked).

---

### Post by Pumalite on 2007-11-16
Now that BIOS detected it correctly, you have to boot from Gparted Live CD and format it (I suggest you format ext3). Then install Ubuntu>Guided>Use Entire Disk

---

### Post by darklyndsea on 2007-11-20
Strangely, Gparted reaches a section that looks like a prompt of some sort (red and grey writing, if that helps; it disappears too quickly for me to read anything) and then everything disappears off of the screen and never reappears.  So using Gparted doesn't work, and Ubuntu does the same thing now.

---

### Post by Pumalite on 2007-11-20
Maybe your SCSI drive is not compatible with the rest of your hardware.

---

