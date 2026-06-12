---
title: "Using Hoary, how can I burn a bootable CD from a Breezy ISO"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by kurtkraut on 2005-10-16
I've just downloaded Breezy (ISO) and I'm using Hoary. How can I burn this ISO image in a bootable CD to instal Breezy ?

Thanks.

---

### Post by Redindian on 2005-10-16
Install gnome baker 0.4.2 and use burn CD image (ISO) option. Make sure you intalled 0.4.2, lower versions may not have CD ISO image burning capability.

---

### Post by az on 2005-10-16
If you right-click on the file, you get the option to burn the cd image.  You do not need anything other tha the default nautilus installations (which includes nautilus-cd-burner by default)

---

### Post by kurtkraut on 2005-10-16
[QUOTE=azz]If you right-click on the file, you get the option to burn the cd image.  You do not need anything other tha the default nautilus installations (which includes nautilus-cd-burner by default)[/QUOTE]


I've already did that but the CD is not bootable. The system does not recognizes it as bootable and I'm getting to Hoary insted of Breezy-CD.

I'm using a CDRW. Is this the reason of my problem ?

---

### Post by SickTwist on 2005-10-16
Few tips:

-Make sure that your computer's BIOS is configured to boot from the optical drive before the hard disk.

-run md5sum on the file you downloaded to make sure there were no errors while downloading. (open a terminal and run: md5sum /path/to/breezy.iso ) this will print a checksum that you can compare with the ones on Ubuntu's download page.

-Also, some older drives will not boot correctly from CD-RW. Try using a CD-R to see if that clears it up.

---

