---
title: "[SOLVED] Dual Booting"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by Ravensix on 2008-01-14
I have installed Unbuntu onto a ext. harddrive with windows vista on the main hardrive on my laptop.  The problem i am having is that when my computer boots up i have to leave the ext. hard drive attached to the computer when i want to boot into windows.  I dont want to have the ext drive attached all the time.  Can anyone help?

---

### Post by overdrank on 2008-01-14
> **Ravensix said:**
> I have installed Unbuntu onto a ext. harddrive with windows vista on the main hardrive on my laptop.  The problem i am having is that when my computer boots up i have to leave the ext. hard drive attached to the computer when i want to boot into windows.  I dont want to have the ext drive attached all the time.  Can anyone help?

Hi and welcome, it sounds like the grub is install on the external drive so you might need to reinstall grub to the internal hard drive. Maybe this link will help
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by logos34 on 2008-01-14
Install Grub to the mbr of the external drive using the[ live cd]("http://ubuntuforums.org/showthread.php?t=224351").

Then restore your Vista bootloader from the repair environment on the Vista install dvd.  If you don't have the dvd, get this:
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Ravensix on 2008-01-15
Thanks for the help.  All is working great.

---

