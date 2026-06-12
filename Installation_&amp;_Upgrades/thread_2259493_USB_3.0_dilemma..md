---
title: "USB 3.0 dilemma."
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by micheldurand on 2015-01-04
I installed Ubuntu 12.10 64-bit on an external SDD drive alongside Windows 7 32-bit
which runs on the main hard drive. It runs well.
My dilemma is that I also boot from the same SDD drive which normally runs on a 
USB 3.0 connection.
Unfortunalely my USB 3.0 connection (sofware activated) does not become active before 
GRUB and I have to plug into a USB 2.0 to boot successfully.
I lose all the USB 3.0 speed advantages not only to boot but to run Ubuntu itself..
It is an old machine and I do not have the original Windows 7 disk to reinstall
everything, is there a way out?
Thanks

---

### Post by ubfan1 on 2015-01-04
You could install grub on the HD to boot Windows and Ubuntu, or install grub to a USB2 to run the Ubuntu root on the USB3.  Did you check for BIOS options on the USB3?  Be aware not many (if any) USB3 enclosures with SSD allow the trim function, so expect performance to degrade if trim cannot be run (try it manually and see if you get complaints about ...not supported).

---

### Post by sudodus on 2015-01-05
> **micheldurand said:**
> I installed Ubuntu 12.10 64-bit ...
Thanks

Did you really install Ubuntu version **12.10 **? Or is it a typing error? You can check with

```
lsb_release -a
```

That version has passed end of life and will receive no more updates, not even security updates. Please install a current release instead, I suggest version **14.04.1 LTS** where Lubuntu and Xubuntu are supported until April 2017. Standard Ubuntu and Kubuntu are supported until April 2019.

See this link [Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.]("http://ubuntuforums.org/showthread.php?t=2229730")

---

### Post by plucky on 2015-01-05
> I suggest version 14.04.1 LTS which is supported until April 2017.


That should be April 2019.

---

### Post by sudodus on 2015-01-05
Yes, for Ubuntu, but there is a **lubuntu** tag in the header of the thread, and Lubuntu 14.04.1 expires in 2017. So I did not want to promise too much. 

Anyway, thanks for making it clear :-)

---

### Post by micheldurand on 2015-01-05
Yes it is 14.10 Codename: utopic. I wanted to use a 64-bit release. Thanks, I will consider 14.04, I thought I was getting the latest release.

---

### Post by micheldurand on 2015-01-05
Sorry, that was a typo on my part, it is Ubuntu.

---

### Post by micheldurand on 2015-01-05
Thanks, USB 3.0 was not part of the original machine, I had to install a PCi card with driver which probably explains why it doesn't start in time. But the USB 2.0 do.

---

### Post by sudodus on 2015-01-05
> **micheldurand said:**
> Sorry, that was a typo on my part, it is Ubuntu.

I edited the tag to Ubuntu

---

### Post by sudodus on 2015-01-05
> **micheldurand said:**
> Yes it is 14.10 Codename: utopic. I wanted to use a 64-bit release. Thanks, I will consider 14.04, I thought I was getting the latest release.

Then we are talking about modern and supported versions :-)

I recommend the long time support version, now 14.04 LTS (or the older 12.04 LTS), except in cases of brand new hardware, where you need the very latest release to get drivers, that work with it.

> **micheldurand said:**
> Thanks, USB 3.0 was not part of the original machine, I had to install a PCi card with driver which probably explains why it doesn't start in time. But the USB 2.0 do.

My experience is that retrofits like your PCI card or extension hubs work well for USB3 when you use it for storage, but it is hard to boot that way. So I'm afraid it might be hard to make it work.

Maybe some work-around, as suggested in post #2 by *ubfan* will work for you. Booting from another drive and chainloading into the USB 3 drive or simply pointing to the kernel files in grub.cfg.

---

### Post by micheldurand on 2015-01-05
Hopefully the 3.0 will be active when Grub is on the screen. Do you think something ( from another message) as simple as booting from usb(3.0 connected to 2.0) - type on root terminal # grub-setup /dev/sda ( or a USB 2.0 stick), and reboot without the usb (3.0 connected to 2.0) or ( a USB 2.0 stick) might work. Any danger to that?
Thanks for your input.

---

### Post by ubfan1 on 2015-01-05
I'm not sure I followed that, but if I understood, you are thinking of installing grub onto the Windows hard disk.  The danger in your case of not having an Ubuntu on the hard disk is where you have the GRUB files -- If you leave them on a USB device, your machine will not boot without the USB device. The GRUB files cannot be on an NTFS filesystem (the normal Windows C:), but Windows machines frequently have some small partitions with FAT filesystems which can contain a "boot" directory for the grub installation.  You could try to put GRUB onto a USB2 stick, to boot the USB3 SSD without touching the internal hard disk.

---

