---
title: "Ubuntu Dual Boot Loader won't boot Ubuntu!"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by Thlorian on 2008-10-29
I loaded Ubuntu (Latest version but I don't have the disk in front of me right now) to dual boot with WinXP.  When my system boots up, during start-up, both WINXP and UBUNTU options are shown but when I try to arrow down (or PAGE DOWN or simply GO DOWN!!!!!) it will not allow me to select UBUNTU.  Instead the Highlight just remains on WINXP and after the seconds tick down, WINXP loads up.  My keyboard functions/keys are working fine as the moment WINXP loads, I tested them out.  What happened?

I am a rookie so any easy step-by-step help would be greatly appreciated!

Thanks!

---

### Post by lemming465 on 2008-10-30
Do you by chance have a USB keyboard?  You may need to adjust BIOS options to let GRUB use it.

---

### Post by Thlorian on 2008-10-31
Yes I do have a usb keyboard.  How would I do this please?

Thanks

---

### Post by lemming465 on 2008-10-31
Unfortunately the details vary depending on the motherboard and exact BIOS version.  If you post the exact maker and model number, we might be able to find the manual on-line and spelunk in it together.  There should be a key to press to enter BIOS setup as the computer boots, perhaps F2 or F10 or something.  Once in the BIOS settings, you'll have to look around for stuff related to USB and keyboard.  If it offers you some kind of legacy emulation, try it.

---

### Post by Thlorian on 2008-11-04
Ok, so strangely after about a month of having Ubuntu on my system but never being able to access it through the bootloader program, yesterday I had to do a **_restart _**on my system (up to this point I have always simply shut down for the day/time and then powered on again the next day/time I needed to get back on).

After the restart began, I was able to toggle back and forth between selecting WinXP and Ubuntu during the bootloader time frame.  Now I know this sounds strange but I know for a fact that I was not able to access Ubuntu at all through the loader before this restart.  In any event, I thought I would post this here in case someone else has the same problem/issue.

Thank you

:guitar:

---

