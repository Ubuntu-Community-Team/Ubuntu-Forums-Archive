---
title: "Invalid system disk on boot error"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by ftchere on 2010-06-17
Hi
 
I am a long time Windows user and attempting to install Ubuntu Netbook 10 on my Acer Aspire netbook.
 
I followed the steps:
 
1) Downloading the Ubuntu ISO to my netbook hard drive.
 
2) Installed Ubuntu from the netbook HD to USB using USB universal installer (also using the universal installer to format the USB)
 
3) Set bios to first read USB device
 
I receive the following message during the boot "Invalid system disk. Replace the disk, and then press any key.
 
I have retried this process several times.
 
Can anyone help?
 
Thanks in advance

---

### Post by libssd on 2010-06-17
> **ftchere said:**
> Hi
 
I am a long time Windows user and attempting to install Ubuntu Netbook 10 on my Acer Aspire netbook.
 
I followed the steps:
 
1) Downloading the Ubuntu ISO to my netbook hard drive.
 
2) Installed Ubuntu from the netbook HD to USB using USB universal installer (also using the universal installer to format the USB)
 
3) Set bios to first read USB device
 
I receive the following message during the boot "Invalid system disk. Replace the disk, and then press any key.
 
I have retried this process several times.
 
Can anyone help?
 
Thanks in advance
That error message  means the USB is not a bootable device. You could try using [Unetbootin]("http://unetbootin.sourceforge.net/") to install the ISO on the USB. Once you have Ubuntu successfully installed, "Startup Disk Creator" works very well for creating bootable Ubuntu installation USBs, but it's a chicken/egg situation if you can't do the initial installation. The nice thing about Unetbootin is that there are versions for both Linux and Windows.

---

### Post by leorolla on 2010-06-18
Try UnetBootIn

---

