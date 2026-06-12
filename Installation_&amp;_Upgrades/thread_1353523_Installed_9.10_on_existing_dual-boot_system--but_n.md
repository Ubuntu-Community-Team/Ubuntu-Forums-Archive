---
title: "Installed 9.10 on existing dual-boot system--but no Ubuntu GRUB menu"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by wilberfan on 2009-12-12
I have a box with two hard drives.  The 2nd drive (hdb) has Windows 7 and Debian Sid (Sidux) installed on it.  When I boot the machine, the sidux grub menu let's me boot into Sidux (default) or Windows 7.

I just installed Ubuntu 9.10 on the first drive (hda) and when it reboots after the install, the Sidux grub menu is the one that opens.  (It, of course, has no option to boot into Ubuntu.)

I let the Ubuntu installer overwrite the MBR--but it doesn't seem to have done that successfully.

My goal is to have the Ubuntu GRUB menu with the three OS's listed on it to choose from.

---

### Post by presence1960 on 2009-12-12
without seeing your setup or boot process- try switching the hard disk boot order in BIOS. If that doesn't work then...

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by wilberfan on 2009-12-13
> **presence1960 said:**
>  try switching the hard disk boot order in BIOS. 

BRILLIANT, sir!!  :D

I had forgotten that was even an option...  That did the trick!  :guitar:

---

### Post by presence1960 on 2009-12-13
> **wilberfan said:**
> BRILLIANT, sir!!  :D

I had forgotten that was even an option...  That did the trick!  :guitar:

Glad you got it working.

---

