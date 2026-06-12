---
title: "Windows 10 wont boot after installing 14.04.3 LTS"
date: 2015-11-12
forum: Installation &amp; Upgrades
---

### Post by lewis-kimber7 on 2015-11-12
Instillation seemed to be going fine. Installed from USB flash drive. When I turn on my computer, a large purple box appears for a split second  after my BIOS screen (I assume this to be GRUB) however the system instantly proceeds to ubuntu, without showing me the GRUB menu.

I hit f12 while on the BIOS screen to try and change which boot I load. I have 3 options however they all seem to be for booting ubuntu, when previously the same boot options would load windows.

I assume the problem to be in my BIOS settings, and I think (and hope) that my hard drive still has windows on it, only the BIOS is ignoring it.

All I have is a 120GB SSD, and allocated 20GB free space in windows for me to install ubuntu. Interestingly, when I try to view my SSD in "Home - Devices - 98 GB Volume", I get the error message:

Unable to access "98 GB Volume"
Error mounting /dev/sda2 at /media/lewis/AAA24DDBA24DAC9F: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/lewis/AAA24DDBA24DAC9F"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

My motherbored is a Gigabyte G1 Sniper M5
I followed this tutorial to install ubuntu [https://www.youtube.com/watch?v=mOtMOws7GJg](https://www.youtube.com/watch?v=mOtMOws7GJg)

Thanks in advance.
I tried this before and the exact same occurred, if no fix I'll reinstall windows 10 with my CD and reinstall my software. All documents are on my HDD which is temporarily disconnected.
:)

---

### Post by oldfred on 2015-11-12
Are your installs UEFI or BIOS?
Post this:
sudo parted -l

Also in Windows you must turn off fast startup or its always on hibernation.
If BIOS you may be able to temporarily restore a Windows boot loader and boot into Windows to turn fast start up off. If UEFI you can directly boot Windows from UEFI boot menu.

 Fast Startup off/hibernation - Windows 8 or 10 UEFI or BIOS boot.
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by yancek on 2015-11-12
The error message tells you the problem, hibernation.  The drive/partition was not fully shutdown and needs to be before you can access it from Ubuntu.  You need to disable Fast Start or Fast Boot options in the BIOS.  You might take a look at the official Ubuntu documentation on dual booting using UEFI at the link below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

To check whether your windows install is still there, boot Ubuntu and open a terminal and enter this command and post the output here:

```
sudo parted -l
``` Lower Case Letter L in the command.

---

### Post by lewis-kimber7 on 2015-11-12
Thanks for replying both.
I went in to BIOS to check settings again, and after save and quit the GRUB menu appeared for the first time with windows there. Loading windows and everything is still there.
Once windows loaded I disabled fast startup, restarted my PC and I can use both OSs again.

Thanks alot for helping me on the issue and understand what was happening. Did windows go out of hibernating by itself after a certain time period?

---

