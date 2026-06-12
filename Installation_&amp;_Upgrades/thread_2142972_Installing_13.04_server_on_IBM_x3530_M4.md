---
title: "Installing 13.04 server on IBM x3530 M4"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by cod3Monkey on 2013-05-07
Hi,

I tried for most of the day installing Ubuntu server on this hardware (x3530 M4 [COLOR=#000000][FONT=arial]7160-E2G[/FONT][/COLOR]), but without success :(
My problem is that once everything is installed Linux will not boot.

I tried all kind of bios/EFI settings but non of them seem to work.
So installing and booting in legacy mode won't work, or installing and booting EFI mode.

The drive is never detect on boot, I can see in legacy mode the MBR gets used and in EFI a special partition is created...

Any idea? The hardware has a C105 controller, and a 500G SATA drive. For HW details see here; [http://www.redbooks.ibm.com/abstracts/tips0888.html](http://www.redbooks.ibm.com/abstracts/tips0888.html)

//E

---

### Post by dominictorreto87 on 2013-05-07
upgrade your UEFI BIOS for first [http://www-947.ibm.com/support/entry/portal/docdisplay?lndocid=migr-5092199](http://www-947.ibm.com/support/entry/portal/docdisplay?lndocid=migr-5092199), during install use non uefi boot from CD/DVD/Blueray is your Server Motherboard using RAID option always if not just turn it off in BIOS and just install ubuntu hope it helps

---

### Post by dennis20pl on 2013-08-23
Hi,

I have the same problem, have you got solutions for that?

I have firmware 1.41

---

