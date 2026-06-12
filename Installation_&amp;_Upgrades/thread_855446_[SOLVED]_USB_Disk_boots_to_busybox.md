---
title: "[SOLVED] USB Disk boots to busybox"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by amlucent23 on 2008-07-10
I am trying to set up a 4gb USB Disk as a persistent Hardy usb installer for a coworker of mine.  I am following this guide [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/") and we have set this thing up exactly like the instructions stated no less than 8 times now and we always get the same result, it boots to the menu fine but when you choose persistent option it boots to a busybox terminal.  I have done everything from blowing away the partitions and recreating them to re downloading ubuntu and burning a new cd! Always the same result. :mad: 

I am starting to wonder if the last 2 files the guide has me download are set up correctly?

> # Type wget pendrivelinux.com/downloads/u8/syslinux.cfg
# Type cd casper
# Type rm initrd.gz
# Type wget pendrivelinux.com/downloads/u8/initrd.gz
 
Anyone have any ideas or advice? Thanks!

---

### Post by avtolle on 2008-07-10
The problem may not be related to the USB installation at all (or it might). I've seen many a thread about booting into Busy Box from the Live CD, for example. Does your coworker have a SATA drive? What graphics card does that computer have? These are but two of the things that seem to cause a boot into Busy Box.

---

### Post by avtolle on 2008-07-10
Take a look at [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for some boot options to try as well.

---

### Post by avtolle on 2008-07-10
Take a look at this, too: [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) especially about the problem with Hardy.

---

### Post by amlucent23 on 2008-07-10
> **avtolle said:**
> The problem may not be related to the USB installation at all (or it might). I've seen many a thread about booting into Busy Box from the Live CD, for example. Does your coworker have a SATA drive? What graphics card does that computer have? These are but two of the things that seem to cause a boot into Busy Box.

but the Live CD boots fine.. its a Dell Latitude D610, sata drives I think. Excellent compatibility with Ubuntu.

---

### Post by avtolle on 2008-07-10
There have been several threads about the Live CD working well, but upon installation ending up in Busy Box as well. The key may well be in the last link I posted earlier.

---

### Post by amlucent23 on 2008-07-10
We finally got it to work using these instructions [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/]("http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/").  It wasnt a problem with hardy or the machine, I think it was the altered files in the original instructions are not working for the current version of hardy.

---

### Post by avtolle on 2008-07-10
Glad to hear you got it working. Would you please mark the thread as solved, using the thread tools at the top? Thanks.

---

### Post by ctefer on 2010-02-05
Your USB stick must also be fat32 formatted

---

