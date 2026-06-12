---
title: "installing ubuntu using usb external cdrom"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by voltage on 2007-01-26
hi,

 currently i were installing ubuntu to the new server which is without floppy drive and cd rom.
 but .. what we have is one usb external floppy and one usb external cdrom. 

 so do some body can tell me how to install the ubuntu using those device that i have at above ??

Thanks and good day.
rg,
frank ong
26-jan-2007

---

### Post by K.Mandla on 2007-01-26
Hi Frank. Can your computer boot from a USB drive? Check the BIOS and see if it is an option.

What kind of computer is it? Can you tell us the model number?

---

### Post by voltage on 2007-01-26
> **K.Mandla said:**
> Hi Frank. Can your computer boot from a USB drive? Check the BIOS and see if it is an option.

What kind of computer is it? Can you tell us the model number?

Our Server is Sun Fire x2100, But I can simply boot from USB Externel Floppy Drive using MS  Windows 98 Boot Disk.

So.. my I know do Ubuntu Installation CD have any special feature to create Ubuntu Boot Disk using Windows XP?

---

### Post by K.Mandla on 2007-01-26
Have you tried working with SmartBootManager?

[https://help.ubuntu.com/community/SmartBootManagerHowto](https://help.ubuntu.com/community/SmartBootManagerHowto)

That works for me on older machines that don't have a BIOS option to boot from CD; it might also work for USB boots, although I'm not sure.

If you can get the ISO  on to the machine, there is a supposed way to boot and install Ubuntu from an ISO. Look [here]("http://www.ubuntuforums.org/showthread.php?t=316093"). I've never done it, although I want to try.

Additionally, if you have a Windows setup on the machine already, [this]("http://instlux.sourceforge.net/") is supposed to work like an installer package and put Linux (of any flavor, not just Ubuntu) on the machine. Again, I've not used that, but I want to try it sometime.

---

