---
title: "Cannot boot from USB on Intel NUC"
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by stevermann on 2020-05-29
Intel NUC model NUC8BEB

I tried to install the Gnome Desktop on my NUC running Ubuntu Server using tasksel. When I reboot, everything goes to heck.

The error message is:
CIFS VFS: CIFS mount error: iocharset utf8 not found

I can log in on my admin account, but nothing will run.

I am assuming that fixing this will require reinstalling Ubuntu. But I have tried for hours to get the NUC to boot from the thumbdrive. Nothing works.

I downloaded the latest Ubuntu iso image ([https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)) and used Rufus to make a bootable drive. (Twice).
I hit F10 during the NUC boot and selected the USB drive.
But the NUC still boots from the M2 drive.

Help, please.

---

### Post by ubfan1 on 2020-05-29
Seems like there are a few problems here.  First, did you hashcheck the downloaded ISO and run a media check on the USB if offered?  A bad download or USB might explain not being able to boot from the USB.  Next, Ubuntu Server needs a lot of support for the Gnome Desktop, like X for instance.  might as well start with the desktop, which does all that.  Then delete pakcages you don't need or want.

---

### Post by oldfred on 2020-05-29
I do not know NUC models, but there seem to be some issues with them.

[https://askubuntu.com/questions/1208978/intel-corporation-device-80860d4f-is-not-supported-on-ubuntu-18-04-3](https://askubuntu.com/questions/1208978/intel-corporation-device-80860d4f-is-not-supported-on-ubuntu-18-04-3)
NUC10i7FNH
this Network adapter Intel Corporation Device [8086:0d4f] is new and supported by mainline Linux kernel since the 5.5 Linux kernel.

How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support  - using ppa
[https://ubuntuforums.org/showthread.php?t=2400400](https://ubuntuforums.org/showthread.php?t=2400400)
Updated drivers for Hades Canyon
[https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay](https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay)
Intel NUC
[https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified](https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified)
Certified ISO & Instructions
[https://www.ubuntu.com/download/iot/intel-nuc-desktop](https://www.ubuntu.com/download/iot/intel-nuc-desktop)
intel nuc - nuc5i5MYHE w/M.2 SSD 
[https://ubuntuforums.org/showthread.php?t=2376245](https://ubuntuforums.org/showthread.php?t=2376245)
boot into the EFI shell and manually point startup.nsh to the grubx64.cfg and run it
Running The Intel NUC6i7KYK On Linux With Skylake Iris Pro Graphics 16.10
[http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1)

---

### Post by stevermann on 2020-05-29
Thanks ubfan1.  I did not hashcheck the download- it's never been a problem, but I will try anything.

I am able to log in as admin, and I was able to copy my home, etc, lib, usr and var folders to a mounted SSD.

My intent is to simply reinstall Ubuntu and spend tomorrow to reconfigure everything.  But, if I can't get the NUC to boot from the USB, what can I do?

I got a bit further with a new USB drive.
It looked like it was going to boot and install from the thumb drive, but I am now getting:
"ubuntu 18.04 started wait until snapd is fully seeded"

All I can see from Google is that this was fixed in 18.04.4

---

