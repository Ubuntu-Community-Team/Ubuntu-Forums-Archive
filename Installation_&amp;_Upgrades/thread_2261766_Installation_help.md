---
title: "Installation help"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by Jeff_Kerner on 2015-01-20
Yes, I'm new to Ubuntu, and need help.  I'm trying to install onto a NEW SATA SSD drive (256GB Samsung 840 Pro), and it keeps aborting the installation.  I keep getting "X has at least 6.3GB available drive space".  The drive appears to be fully recognized in the BIOS (clearly says "Samsung 840 Pro" on the main BIOS page).

There doesn't seem to be an option to format the drive.  Would it help if I formatted the drive under Windows, or would that bung things up further?  I'm installing from the 14.04.1 Ubuntu iso, burned onto a disc from a Windows machine.  The installing drive is a USB dvd drive.  I am fresh out of ideas here...

Jeff

---

### Post by yancek on 2015-01-20
> X has at least 6.3GB available drive space

That message generally is information indicating that you must have at least that much space available on which to install Ubuntu.
Is this an empty drive?  You don't indicate any other operating system installed though you make a passing reference to windows.  Do you have windows on this computer?  Which version?  If you have windows, do you have any free/unallocated space on which to install?  You could use the Try Ubuntu option and boot to the Desktop, then open a terminal and enter this command and post the output:  sudo fdisk -l(Lower Case Letter L in the command)

> There doesn't seem to be an option to format the drive.  Would it help if I formatted the drive under Windows,  

Yes there is, at least if you select the "Something Else" option which is a manual install.  And you can't format from windows.  Windows can't even read a Linux filesystem and there is no way to format a Linux filesystem from windows.

Doesn't seem as though you have read the tutorial on how to install at the Ubuntu site.  You might try that or take a look at the more detailed tutorial at the link below so you know what to expect.  It explains using the "Something Else" option.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

