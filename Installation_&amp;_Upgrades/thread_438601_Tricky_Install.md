---
title: "Tricky Install"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by SwarfEye on 2007-05-09
Ok,

I am a Mac/BSD/Unix guy.  I have this cool old Toshiba 3490CT PC laptop, and I want to install ubuntu on it.

Here's the rub.

The laptop suffered some sort of network failure in windows.  I am working with the assupmtion that this is a software problem as the windows that is currently installed on there is behaving terribly, but the hardware all seems to check out.

I do not have a boot able CD rom drive for this thing... in fact, I don't have a CD drive at all for it.

I've got a usb floppy drive that the machine will boot off of, and I've got various usb hard drives and macintoshs.

I am hoping that I could somehow write the ubuntu disk image to a usb hard drive and then boot the old laptop off of that... but it seems virtually impossible to get an iso file to write out to a hard drive?

Is there anyway that I could write a PC bootable image to a usb harddrive from a mac?

Any suggestions for how I can get an ubuntu install on there?

B

---

### Post by tgm4883 on 2007-05-09
Its possible, i have done it a long time ago.

Search the forums for usb persistant or something to that nature

---

### Post by Craigus on 2007-05-11
Do you have the port replicator with the ethernet port? If so, you can do a PXE boot / install:

[http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows]("http://hugi.to/blog/archive/2006/12/23/ubuntu-pxe-install-via-windows")


This is how I did it with mine.

---

