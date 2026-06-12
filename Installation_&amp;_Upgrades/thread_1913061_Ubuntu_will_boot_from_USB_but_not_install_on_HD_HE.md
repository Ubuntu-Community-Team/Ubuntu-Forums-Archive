---
title: "Ubuntu will boot from USB but not install on HD HELP MEEE!!!"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by Matthew Sainsbury on 2012-01-21
Hello, I am new to Ubuntu and have decided to wipe my new laptop of all things Microsoft.

My fresh Ubuntu installs works up until the final point where it displays an error saying something like 'an error with disc D:\ cannot be found' but this was being installed from a USB drive.

Please help! I've been going round in circles for hours

---

### Post by C.S.Cameron on 2012-01-21
> **Matthew Sainsbury said:**
> Hello, I am new to Ubuntu and have decided to wipe my new laptop of all things Microsoft.

My fresh Ubuntu installs works up until the final point where it displays an error saying something like 'an error with disc D:\ cannot be found' but this was being installed from a USB drive.

Please help! I've been going round in circles for hours

Welcome to the forums.

I recall a problem like this requiring a check disk.

Have you tried formatting the hard drive using gparted? you can check the disk at the same time

---

### Post by darkod on 2012-01-22
Disc D: ? That is MS talk, linux never calls partitions C:, D: etc.

You are not installing wubi right?

How are you installing it, you booted with the prepared usb stick and select Erase and use whole disk option?

---

### Post by WasMeHere on 2012-01-22
Hi Matthew,

I think that you want to ***install Ubuntu as the only operating system*** on your computer. Then it should be easy, unless the hard disk drive is not recognized properly.

0. Do not install from Windows. Insert the CD or USB boot drive and reboot the computer! You may need to reset the boot order in the BIOS menus, in order to make the computer boot from your CD or USB drive instead of the internal hard disk drive.

1. Boot a live session from the CD or USB boot drive 'Test Ubuntu before installation'. Use that system (if it works) to look at the hard drive with the file browser (similar to Windows Explorer).

2. When you feel that Ubuntu works, click on the install button to start the installation script. This will prompt you with a few questions. When you come to the question about how to use the disk drive, choose 'Use the whole disk' (instead of side by side with Windows or manual method).

Have fun finding out :-)
Olle

---

