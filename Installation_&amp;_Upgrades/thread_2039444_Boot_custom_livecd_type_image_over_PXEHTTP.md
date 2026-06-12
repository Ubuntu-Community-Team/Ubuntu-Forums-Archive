---
title: "Boot custom livecd type image over PXE/HTTP?"
date: 2012-08-08
forum: Installation &amp; Upgrades
---

### Post by bohiti on 2012-08-08
I've in the past configured a custom Ubuntu live CD to be used as a type of web-surfing kiosk on several PC's here at work.  It has been difficult keeping it under the 700mb or so on CD.

On this latest refresh, I don't want to bother keeping it that small, and I'd rather not go to DVD's.  I've got a PXE server in my environment (TFTPD32 on Windows), and think I'd optimally like to use that to network boot the kiosk PC's.  Optimally, HTTP would be used to download the bulk of the image, as TFTP is slow and we don't have an NFS server.  Obviously, this will boot "toram", and nothing needs to persist between reboots.

Is this possible?  I've Google'd for at least an hour without any definite leads.  A tripping point is that most of the PXE information refers to *installing *Ubuntu from PXE, not booting a type of live installation.  I guess my two questions would be: 
[LIST=1]
[*]How should I prepare my custom image?  Relinux?
[*]How do I configure the tftp boot to hand off to HTTP?
[/LIST]

Thanks for any guidance.

---

### Post by bohiti on 2012-08-09
Bump?

---

