---
title: "How to Install Ubuntu From USB Pen Drive ?"
date: 2008-08-02
forum: Installation &amp; Upgrades
---

### Post by chinnaraaju on 2008-08-02
hi,

is it possible to install ubuntu 8.0.4 from USB Pendrive. ?
if so, what should be the boot options in BIOS settings...? 
do we need to have any additional files in pendrive other than .ISO file.. ?

Regards,
Chinna.

---

### Post by Tux Aubrey on 2008-08-02
There a a few tricks to this but there are several different methods.  The one I have used most is [THIS ONE]("http://ubuntuforums.org/showthread.php?t=740924").

RE bios settings - you just need to have usb above HDD in the boot order.  Each machine is subtly different - on some (mainly older machines) it isn't possible at all.  Some new ones have a separate "F" key that allows you to turn on a once-only USB boot.

---

### Post by nnamdi on 2008-08-02
hello i think your flash has to be bootable and also you have to make sure you did not copy the files like data files
it is suppose to be copied like an iso file into the flash ok

---

### Post by chinnaraaju on 2008-08-02
Hi All,
i have tried all the boot options listed below.
USB HDD
USB FDD
ZIP :\
USB RMD HDD
USB RMD FDD..

but my USB drive is not detected at all...
what could be the problem..
how to make it detected to boot from it ?

Cheers,
Chinna.

---

### Post by kpkeerthi on 2008-08-02
Does your BIOS support booting from USB? Check your system manual.

If it does, check [this]("https://help.ubuntu.com/community/Installation/FromUSBStick") out to boot Ubuntu off your USB stick.

---

