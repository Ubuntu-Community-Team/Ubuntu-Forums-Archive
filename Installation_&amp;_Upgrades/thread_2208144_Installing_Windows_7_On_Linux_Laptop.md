---
title: "Installing Windows 7 On Linux Laptop"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by torstol818 on 2014-02-26
I am trying to install Windows 7 Professional on my laptop that currently just runs Ubuntu 13.10. Originally this laptop came with Windows 8, but I wiped the drive and install Ubuntu 13.04.

Currently I am using WinRAR to open up an .iso file of Windows that I got from dreamspark.org.

I can get to the point where I open up the setup.exe and it says "install windws 7.." but when I do this I get an error stated below this line.

"Windows Setup cannot find a location to store the temporary installation files. To install Windows, make sure that a partition of your boot disk has at least 829 megabytes of free space. "     error code: 0x80070490

I have already used Gparted to make a 60gb ntfs partition for Windows 7, and I also have roughly 465gb of unallocated space on my drive for windows to work with later.

What should be my next step to installing Windows 7?

I am also more than happy to post any screen shots I can take during this process if needed.

---

### Post by monkeybrain20122 on 2014-02-26
Install it in virtualbox.

---

### Post by torstol818 on 2014-02-26
Ill give virtualbox a whirl then. Wine already can run all the software well though.

---

### Post by monkeybrain20122 on 2014-02-26
Oh if wine runs it good enough I would use wine instead of vbox. It takes much less overhead.

---

### Post by torstol818 on 2014-02-26
Ill give virtualbox a whirl then. Wine already can run all the software well though.

---

### Post by torstol818 on 2014-02-26
The problem is that the setup.exe is not seeing the giant heap of space I have for it to install Windows 7.

---

### Post by mastablasta on 2014-02-27
it often wants the space in beginning of the hard disk.

---

### Post by torstol818 on 2014-03-01
Still not working sadly.

---

### Post by oldfred on 2014-03-01
Is drive still gpt from Windows 8?. Windows only installs to gpt partitioned drives with UEFI. And the Windows DVD only installs in BIOS mode. You can copy Windows DVD to flash drive and make a few updates and then it will install in UEFI boot mode.
Ubuntu will boot from gpt partitioned drives with either UEFI or BIOS.

Post this:
sudo parted -l

Windows also has to have a primary NTFS partition with the boot flag if in MBR(msdos) partitioning or space for that. If you have used all 4 primary partitions then Windows would not install.

---

