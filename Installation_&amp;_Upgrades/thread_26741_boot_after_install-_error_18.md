---
title: "boot after install- error 18"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by foilking on 2005-04-13
after i install ubuntu, the computer starts to load GRUB stage1.5, says GRUB loading, please wait, then error 18 and stops dead. i've reinstalled once and putting the cd in but it doesn't work. please help a noob to ubuntu.

---

### Post by Dr Gonzo on 2005-04-13
Please include the full output.  What did it say, exactly?  Also, did anything strange happen when the installer went through the grub install process?  What kind of filesystem did you install?  Did you use all the defaults?  Do you have an IDE, or SATA, or SCSI drive?

---

### Post by foilking on 2005-04-13
All it does at the beginning is say the specs, "GRUB Loading stage1.5." , " GRUB loading, please wait... Error18" and stops there. I am using the default settings when installing Ubuntu and it is an IDE drive.

---

### Post by Dr Gonzo on 2005-04-13
[quote="The GRUB Docs"]Errors reported by the Stage 2 (the "real" boot loader code)
18 : Selected cylinder exceeds maximum supported by BIOS
This error is returned when a read is attempted at a linear block
address beyond the end of the BIOS translated area. This generally
happens if your disk is larger than the BIOS can handle (512MB for
(E)IDE disks on older machines or larger than 8GB in general).[/quote]Are you running a newer hard drive on an older motherboard?  If so, you might try installing LILO instead.  There should be an option to do this from the installer.

Or, set up your system so that /boot exists on the first HD partition.

---

### Post by kmi on 2005-04-18
I have got the same issue... But my Hoary isn't a fresh install : i've ran it today in the morning like every day since setup... But now i've got Dr Gonzo's "GRUB Loading stage1.5." , " GRUB loading, please wait... Error18".

I've got an old TOSHIBA Satellite Pro 4290 (with an old drive...) which loves Ubuntu Hoary and faces its first real trouble in their honeymoon... :| 

I'm just beginning to look at solutions - as a noob - with a swapped Warty Warthog drive...

---

### Post by Vargyl on 2005-04-28
[QUOTE=foilking]after i install ubuntu, the computer starts to load GRUB stage1.5, says GRUB loading, please wait, then error 18 and stops dead. i've reinstalled once and putting the cd in but it doesn't work. please help a noob to ubuntu.[/QUOTE]

I had the same problem. Error 18 and After GRUB . The solution is in the bios. Put the hard disk detection on auto and not on user. It did the trick for me.

---

