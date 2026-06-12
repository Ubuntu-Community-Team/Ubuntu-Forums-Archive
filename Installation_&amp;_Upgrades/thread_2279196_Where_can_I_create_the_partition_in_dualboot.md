---
title: "Where can I create the partition in dualboot"
date: 2015-05-21
forum: Installation &amp; Upgrades
---

### Post by UnknownAssassin on 2015-05-21
Hey,
I want to install Ubuntu, but want Windows also.
In the tutorial it says I have to create a new partition for it.
Does this partition need to be created, where windows is installed
(1. Im using UEFI 2. I have a SSD (Windows 8.1) and a HDD)

---

### Post by oldfred on 2015-05-21
Do you want Ubuntu on SSD? If so use Windows to shrink the NTFS partition and immediately reboot so it can repair itself to its new size with chkdsk.
Make backups and a Windows repair flash drive.
Do not make partitions for Ubuntu with Windows.
Make sure Windows fast startup is off. If UEFI has a fast boot make sure it is off. 
And while Ubuntu will boot with secure boot on, generally better to turn off secure boot.
Keep UEFI on, do not change to CSM/BIOS.
Be sure to boot flash drive Ubuntu installer in UEFI mode.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
More info on Windows:
[http://www.eightforums.com/](http://www.eightforums.com/)

More info in link in my signature.

---

### Post by UnknownAssassin on 2015-05-22
I want it on the HDD where Windows is NOT installed

EDIT: Question - How can I change what system I want to boot (when Ubuntu is installed)?

---

### Post by oldfred on 2015-05-22
If you have both systems installed in UEFI mode, and have Windows fast startup off, you can use grub menu to choose which system to boot. You have to set ubuntu entry in UEFI as first boot option. But some systems just boot Windows by default and we have to do work arounds for those systems.

But UEFI is also a boot manager or has a boot menu. You should have a one time boot key that will just show the boot options as the same as you see in UEFI boot tab. Key is often f10 or f12 but varies by vendor,, check manual.

Do you have partitions on your hard drive with data? If so you still should use Windows to shrink a NTFS partition and run chkdsk on it as d: or whatever partition/drive it is called in Windows. And with two drives be sure to only use the Something Else install option, not any auto options. And be sure to boot installer in UEFI mode if Windows is in UEFI mode, so Ubuntu installs in UEFI mode. How you boot install media is how it installs.

---

### Post by UnknownAssassin on 2015-05-23
So:
- FastBoot off
- 193 GB free (without partition) space on the HDD
- Ubuntu installed on USB Stick
- Secure Boot can't be changed( it's on: default)
Am I ready to install?

EDIT: chkdsk? Do I have to do that? Where are instructions?

---

### Post by yancek on 2015-05-23
An  explanation of running chkdsk from windows at the link below.  Make sure you have carefully reviewed the suggestions and links above by oldfred. 

[http://www.tomshardware.com/faq/id-2080276/run-chkdsk-windows.html](http://www.tomshardware.com/faq/id-2080276/run-chkdsk-windows.html)

---

### Post by UnknownAssassin on 2015-05-23
Thank you,
CHDSK says, no problems detectet
So I'm ready?

---

### Post by UnknownAssassin on 2015-05-23
I just need a yes or a no you have to do...

---

### Post by oldfred on 2015-05-23
If you do everything else in post #2 other than the first part on shrink of the install on SSD, you can just install.
Have you done good backups?
Do you know how to boot in UEFI mode?
Have you tested that live mode works well with your system, or do not just start with install.
And with two drives only use Something Else install option.
Have you followed at least one of the detailed links that show all the screens you see, so you know install process? ?Especially important with Something Else type installs.

---

### Post by UnknownAssassin on 2015-05-23
Live Mode?
Is that the thing, when you click Try at the installation screen?

USB FDD or
USB HDD
What do I have to boot?

---

### Post by UnknownAssassin on 2015-05-23
Didn't work. Can't I doubleklick the iso and install it this way?

---

### Post by oldfred on 2015-05-23
No, you have to create a bootable DVD or flash drive.
You can use any of the tools like unetbootin, rufus, pendrive etc.
Since you only want UEFI boot, you can just extract ISO with 7-zip to flash drive formatted as FAT32 and it will boot in UEFI only mode.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Please review links in post #2. If you skip steps, you will have issues.

---

