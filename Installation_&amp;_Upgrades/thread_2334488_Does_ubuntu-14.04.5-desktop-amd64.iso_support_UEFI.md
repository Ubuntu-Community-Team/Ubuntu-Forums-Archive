---
title: "Does ubuntu-14.04.5-desktop-amd64.iso support UEFI usb installtion?"
date: 2016-08-19
forum: Installation &amp; Upgrades
---

### Post by jimhce on 2016-08-19
Hi,

I thought ubuntu-14.04.5-desktop-amd64.iso can be used by usb UEFI installation, I copied the iso to a usb stick:


$ sudo dd if=/tmp/ubuntu-14.04.5-desktop-amd64.iso of=/dev/sdc bs=1M

Plugged it into a new Dell 11 3000 laptop, the bios boot option list pointed UEFI (the only option), but it could not detect the usb iso, it went to the Windows 10 straight away, what I could be missing here? The files copied to usb stick seems fine when I checked by mount:

/dev/sdc1 on /tmp/usb type iso9660 (rw)

$ ls usb

$ ls usb
autorun.inf  EFI	 pics		     ubuntu
boot	     install	 pool		     wubi.exe
casper	     isolinux	 preseed
dists	     md5sum.txt  README.diskdefines

Appreciate any clues.

Thank you.

Kind regards,

- j

---

### Post by sudodus on 2016-08-20
Yes, it works in UEFI mode as well as in BIOS mode after cloning like you describe (but I would use a tool to wrap security around dd and avoid overwriting the family pictures by mistake).

There could be a few different problems.

1. Your computer is not really trying to boot from the pendrive.

Several computers let you use the Escape key to get to a simple menu, where you can select boot drive in UEFI mode. Use an F (function key) in other computers, often F12, F10 or F9 key. Press that key during boot. In some computers you should tap it and in other computer you should press it continuously.

Browse the internet for documentation of your particular computer, how it is booted and about its UEFI/BIOS system.

Maybe it helps to turn off secure boot (in the UEFI menu) and fast boot (which is actually a kind of hibernation in Windows).

See the links about UEFI at the following page: [FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

2. The iso file might be bad, because of a failed download. Did you check with md5sum, that the downloaded iso file is good? See [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

3. The pendrive might be bad. Please try to use it to boot another computer.

---

### Post by jimhce on 2016-08-20
You right, tuning off secure boot and fast boot, enabled legacy boot which can install the Ubuntu, it automatically installed without asking the partition, after installation, it asked for reboot, I took off the usb stick, it restarted, then could not find boot loader, inserting the usb stick again, it can boot ..., how to fix it?

Thank you

---

### Post by sudodus on 2016-08-20
At the end of the installation, you should be asked if you want to reboot. Answer yes (reboot), and after a few seconds you should be asked to remove the install media and press the Enter key. (After that the computer should boot into the installed system).

Generally, Dell computers work well with linux. Depending on the graphics chip and wifi chip, your installed system might work well, or have some problems. Maybe you need to add some boot option and install some proprietary driver.

---

### Post by jimhce on 2016-08-20
The graphics works fine, but during the installation, it could not find hard disk, it can only find the 32 GB MMC/SD and installed the Ubuntu to the MMC/SD. That's why it could not find the boot table device. I have to insert the usb stick in reboot, then select "try the Ubuntu without installing", then it boot to Ubuntu desktop. The spec has following HD, how could not find HD?

SATA 6 Gbps
One 2.5-inch drive

---

### Post by yancek on 2016-08-20
A pre-installed windows 10 system is almost certainly using UEFI and if so, you would need to install Ubuntu UEFI.  See the Ubuntu documentation at the page below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If it installed to the 32GB drive rather than the main hard drive, is this the drive on which you have windows installed and if so, did you shrink the windows partition from it's Disk Management tool to create free space on which to install Ubuntu?

---

