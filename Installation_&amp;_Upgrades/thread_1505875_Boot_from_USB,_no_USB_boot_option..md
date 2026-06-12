---
title: "Boot from USB, no USB boot option."
date: 2010-06-09
forum: Installation &amp; Upgrades
---

### Post by syonastarlight on 2010-06-09
I was wondering if anyone can help me in restoring on old laptop to working order.  This laptop is an old early 2000's Sony Viao, which I found in the trash.  Still powers on, and can boot the latest Ubuntu LiveCD.  The issue is that it did not have a harddrive in it, and I really do not want to shell out money for a drive for a laptop this old, but would still like to bring it back into service as a thin client or general purpose web/email terminal.  The BIOS does NOT have a USB boot option, and every tutorial I have seen requires that in order to boot Ubuntu from a USB stick (which is what I do have).  What I am wondering is, is there any way to just keep the LiveCD in the drive, and use that to boot the kernel, etc, and then have it look for the rest of the filesystem on the USB stick?

---

### Post by C.S.Cameron on 2010-06-09
[http://www.pendrivelinux.com/category/usb-boot-cds/](http://www.pendrivelinux.com/category/usb-boot-cds/)

Shows how to make a bootable Cd for booting bootable USB drives on computers that don't boot to USB but will boot CDs.

---

### Post by efflandt on 2010-06-09
Web search "boot from usb without bios support" (or without bios option).  You can boot from floppy or CD that supports USB (likely quicker than booting entire live Ubuntu CD).

---

### Post by wilee-nilee on 2010-06-09
This is what you need.
[Plop](http://www.plop.at/en/bootmanager.html)

---

### Post by at0msk on 2010-06-09
> **wilee-nilee said:**
> This is what you need.
[Plop]("http://www.plop.at/en/bootmanager.html")
 
 
Is it possible to set up a flash drive in such a way that it tricks the pc into thinking that it (the flash drive) is a CD in the CDROM drive?

---

### Post by wilee-nilee on 2010-06-09
> **at0msk said:**
> Is it possible to set up a flash drive in such a way that it tricks the pc into thinking that it (the flash drive) is a CD in the CDROM drive?

As I said in response to your thread on this I don't really know. Today I'm studying for a final tomorrow. I also don't need this function so for now it isn't of interest to me. I would like to help but I just have more important matters to attend to. I am not sure even If I spent time on it that I could figure it out either.

What I will share though is that I loaded Ubuntu into a thumb with one of the boot loaders, I used the plop disc to boot it and when I tried to install I couldn't trick or get the computer to recognize the thumb as the install media. So I put the identical ISO burned to a cd in the cd reader and it still would not install. I think it can probably be done but it will involve some sort of script. I can't write code so I am out of luck there.

I would look on the web using the key words that are your goal and you might find some help. Maybe somebody on the forum will come forward with some sort of answer as well.

---

### Post by C.S.Cameron on 2010-06-09
An alternate to a boot CD is to put a persistence partition, (casper-rw), on the thumb drive and select persistence when booting the CD.
It is much faster to run off USB than a CD though

---

