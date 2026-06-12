---
title: "systemd-udev[344]: Error calling EVIOCSKEYCODE: Invalid argument errors"
date: 2016-01-21
forum: Installation &amp; Upgrades
---

### Post by shawn37 on 2016-01-21
Hello and good day. I'm having the subject error when booting into Kubuntu 14.04.3. Here's some background.

I bought an HP STREAM 13-c110nr laptop specifically to start learning Linux and eventually move over to Linux with my main laptop. Over the past week I've tried about a dozen different distros like Ubuntu, Kubuntu, OpenSUSE, Mint, Fedora, Red Hat. Each time I would use UNetbootin to put the iso on a usb stick and load the OS. The reason I had gone through so many is because I was trying to find one that worked with the wireless card. Unfortunately this laptop has the RealTek RTL8723BE card which is renowned for being CRAP in a Linux machine, so I bought a nano wifi dongle.

At any rate, things were going rather smooth until I loaded OpenSUSE, Red Hat, and Fedora. Fedora says to use their own usb writer or Rawrite32, rather than UNetbootin or any Universal USB writer. I downloaded both products and was able to create the usb boot disks without issue, but OS installation was full of problems. On reboots after installing the system would either hang or I would have no video. I noticed that this only happened on the Debian distros, so I went back to the Ubuntus. Now we get to the subject issues. 

I used UNetbootin to create a usb boot disk with Kubuntu 14.04.3. It installed fine but each time I reboot I get this [splash screen]("http://i.imgur.com/96pMF1K.jpg") followed by these [errors]("http://i.imgur.com/0vnkNoP.jpg") (pictures are worth a thousand words, right). After the boot completes everything seems to run ok. I've done some research and found [this thread]("http://ubuntuforums.org/showthread.php?t=2250210") and was able to determine that the errors correspond to line 344 in the udev log. Here is lines 343 - 347 of my udev log.

KERNEL[4.367486] add /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01$
ACTION=add
DEVPATH=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:01
SEQNUM=1402
SUBSYSTEM=acpi

Is anyone able to tell me what the problem is and how to fix it? In that thread I linked the person was able to tell that his issues were due to the keyboard, but he did go into detail about how he knew that. Please teach me to fish.

Thank you for your time.
Shawn

---

