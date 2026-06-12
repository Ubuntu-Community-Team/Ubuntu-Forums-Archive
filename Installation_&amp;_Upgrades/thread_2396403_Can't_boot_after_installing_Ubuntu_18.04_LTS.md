---
title: "Can't boot after installing Ubuntu 18.04 LTS"
date: 2018-07-15
forum: Installation &amp; Upgrades
---

### Post by jbond2000 on 2018-07-15
I recently decided to replace Windows 10 on my laptop (ASUS VivoBook E403SA-US21) with Ubuntu 18.04 LTS. This isn't my first time installing Ubuntu, so I thought it'd be a piece of cake.
I downloaded the Ubuntu 18.04 LTS amd64 image and created a bootable USB drive using Rufus and GPT partition scheme (UEFI, non-CSM). I disabled Fast Startup in Windows, as well as disabling Fast Boot and Secure Boot in the BIOS. However, when I tried to install, I got the following errors:[INDENT]
usb 2-1: device not accepting address 2, error -62
usb 2-1: device not accepting address 3, error -62
usb 2-1: device not accepting address 4, error -71
usb 2-1: device not accepting address 5, error -71

(initramfs)   Unable to find a medium containing a live file system[/INDENT]

I am unsure as to why this is happening. Considering that both Windows and the USB drive are using GPT, there is no obvious reason the drive shouldn't be working. I have tried multiple times to get the USB to work, but to no avail.

I am getting frustrated as I need this machine for work and was hoping it would be a quick install. Any help would be very much appreciated.

UPDATE: Tried switching to a USB 2.0 port, and got endless "device descriptor read/64, error -71" errors followed by "unable to enumerate USB device"

---

### Post by yancek on 2018-07-15
Did you do a n md5 or sha check on the downloaded iso to verify it?
Do you have another computer available on which you can test booting the usb to eliminate that as a problem?
Do you have multiple usb ports?  Have you tried them all?
Try shutting down the computer completely then unplugging it and waiting 5-10 minutes, plug it in an try again.

---

### Post by oldfred on 2018-07-15
Many UEFI also require you to turn on or allow USB boot or a full USB access type setting.
Often related to UEFI secure boot but separate USB setting as USB boot is not considered a Secure setting, so default is USB boot off.

---

