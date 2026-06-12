---
title: "unable to boot from USB drive"
date: 2018-03-10
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2018-03-10
In my Toshiba Satellite M 645 S 3070,
I went to BIOS, and changed boot order to usb drive,
hit  F10, save change and exit,
Windows 10 opens up.

plan to make dual boot.

---

### Post by oldfred on 2018-03-11
Is this a newer UEFI system?
Many have a UEFI setting to allow USB boot or full USB functions as allowing USB boot is not Secure.
Or may be easier to turn off UEFI Secure boot.

From link below in my signature.
**Summary UEFI install instructions:**
Back up Windows, your data, and make a Windows repair/recovery flash drive.
Download and create Ubuntu 64 bit  installer, flash drive or DVD.
Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often  better but not required to turn off Secure boot (may be called "other"  vs. "Windows"), some may need CSM mode on (Dell), but still select UEFI
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu. links to screen shots below
    If nVidia or AMD video may need nomodeset boot parameter. Some brands also may need other boot parameters.
Create backup procedure for your Ubuntu data and configuration files.
If Issue with install, more info needed, or terms not understood, see info & links below:

---

### Post by Matrix01 on 2018-03-11
Lubunutu live always ran from this laptop when this one had Windows 7.
This one now has Windows10 that was upgraded from 7.



> **oldfred said:**
> Is this a newer UEFI system?
Many have a UEFI setting to allow USB boot or full USB functions as allowing USB boot is not Secure.
Or may be easier to turn off UEFI Secure boot.

From link below in my signature.
**Summary UEFI install instructions:**
Back up Windows, your data, and make a Windows repair/recovery flash drive.
Download and create Ubuntu 64 bit  installer, flash drive or DVD.
Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkdsk.
Turn off Windows fast startup in Windows.
In UEFI turn off fast boot (different than fast start up) and often  better but not required to turn off Secure boot (may be called "other"  vs. "Windows"), some may need CSM mode on (Dell), but still select UEFI
Some UEFI may need you to turn on or allow USB/DVD boot, especially if Secure boot is on.
Boot Ubuntu installing in UEFI live mode, and verify your system works ok.
Install Ubuntu. links to screen shots below
    If nVidia or AMD video may need nomodeset boot parameter. Some brands also may need other boot parameters.
Create backup procedure for your Ubuntu data and configuration files.
If Issue with install, more info needed, or terms not understood, see info & links below:

---

### Post by oldfred on 2018-03-11
If upgraded from Windows 7, it probably is a BIOS/Legacy install. 
But hardware could still be UEFI, if within last 5 years.

Even if not UEFI, you need to have Windows 10 fast start up off.
And may need BIOS settings on USB boot.

Note that Windows 10 updates turn fast start up back on.
And will not include the Linux logical partitions in re-writing of partition table. 
Best to back up partition table and save to another device and have good backups of everything.

Does f12 show boot devices?
And only bootable flash drive will be shown, so make sure flash drive is correctly configured.

---

