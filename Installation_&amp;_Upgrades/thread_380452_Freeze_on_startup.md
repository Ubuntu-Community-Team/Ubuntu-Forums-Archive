---
title: "Freeze on startup"
date: 2007-03-09
forum: Installation &amp; Upgrades
---

### Post by LJM on 2007-03-09
After about a month of a problem-free Ubuntu experience, I've started to experience the following problem on startup.

The machine will freeze at different stages and will only load Ubuntu after several trials. The first point at which it freezes is usually on prompting:

>Verifying DMI Pool Data...

If this hurdle is cleared successfully, it then tends to freeze on prompting:

>GRUB loading, please wait... 1 [second] 

or

>GRUB loading, please wait... 0 [second].

Alternatively, it has every now and then immediately displayed the error message:

>CMOS checksum error -- Defaults loaded
>Warning! CPU has been changed.
>Please Enter CPU Speed CMOS Setup and Remember to Save before Exit!

At times, though more rarely, all went well but GRUB loaded as a command screen, and I knew no better than to type "reboot" from there.

Does any of this make any sense? Any clues? Thanks in advance!

---

### Post by Vajra Vrtti on 2007-03-10
IMHO it seems to be a hardware problem.

---

### Post by Segura on 2007-03-10
If you've made any recent BIOS changes then change them back. But more likely it sounds like a definite motherboard/cpu issue. :( Try verifying power supply voltages to be certain but I think it's the mobo IMHO.

---

### Post by LJM on 2007-03-10
Here are more details on what seems to be wrong (see beginning of thread). I got the following message today:

>Activating swap...
>Checking root file system...
>fsck 1.39 (29-May-2006)
>/dev/hda1 has been mounted 30 times without being checked, check forced.
>checking /dev/hda1..................... etc.

Any ideas how to fix this problem?

---

