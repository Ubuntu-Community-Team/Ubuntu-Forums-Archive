---
title: "how to revert boot to earlier kernel version?"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by thalo on 2009-12-14
[FONT=Arial Narrow]i have 9.10 installed on an acer aspire 3002LCi.  everything has been working well, i had earlier issues with the wireless modem but that is all fixed now.  recently, including today, i have tried to use a usb mouse (tried wireless and wired) and they didnt work.  i ran [/FONT]lsusb [FONT=Book Antiqua]and it showed both wired and wireless usb conncetions, but they still wouldnt work.  in addition[/FONT] when i would boot up the computer, i would show the ubuntu logo and then go black just before the login screen.  things are happening, the desktop sound bit happens, so i know that the login is working.

after dealing with this a couple times, i decided to hit the esc button at prompt during boot.  this showed me the different kernel versions, from 2.6.28-16 to 2.6.31-16.  so far i have booted in 2.6.28-16 and .31-14 and everything has worked well, including the mice.

is there anyway to set the boot to an earlier kernel version so i dont have to manually?  something is wrong with 2.6.31-16 (havent tested 31-15 yet).  i am going to boot an earlier version and then update to .31-16 to see if it is just a bad update or if it is bad all together.
cheers

---

### Post by thalo on 2009-12-14
well, i reinstalled the 31-16 update and things seem to be okay now.  maybe it was a bad update earlier.

---

### Post by drs305 on 2009-12-14
> **thalo said:**
> is there anyway to set the boot to an earlier kernel version so i dont have to manually? 

For future reference, you can change the default selection of GRUB 2 by editing /etc/default/grub. Here is a link on how to make some of the basic changes to the Grub menu. See #2:
[http://ubuntuforums.org/showthread.php?t=1302743]("http://ubuntuforums.org/showthread.php?t=1302743")

---

### Post by thalo on 2009-12-15
thanks for the reference

---

