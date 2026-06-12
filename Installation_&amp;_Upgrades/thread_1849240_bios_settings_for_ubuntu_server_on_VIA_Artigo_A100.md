---
title: "bios settings for ubuntu server on VIA Artigo A1000"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by thinking on 2011-09-24
hi

since i had a bit of trouble with usb drive detection and installing 11.04
ill post here my bios settings during setup:

how i created the usb drive:
using my 11.04 desktop i used an 8GB with default "startup disk creator" and a 32bit ubuntu server 11.04 iso image
so this step is pretty default, no changes on the usb drive have been made

installation on via artigo a1000:
plug in the usb drive and enter the bios during startup.
the settings i changed are
```

Advanced Bios ->
       First Boot Device ->
               USB-CDROM
               LS120
               Hard Disk
Advanced Bios ->
       Boot Priority -> 
              1. Bootable Add-in Cards //<< this was on priority 2 before
              2. CHO-M OCZ ONYX //<< that's the final installation hard drive i use
Integrated Peripherals ->
       USB Settings ->
              Mass Storage Settings ->
                     Flash Drive: HDD-Mode

```
note:
at this point booting from usb drive succeeded, which didn't before
but after the successfull installation and unplugging the usb drive the hard disk didn't boot
im not sure what i changed here, but it was only in the above settings
i think it was advanced bios -> boot priority -> // switching back the OCZ ONYX to priority 1.
and setting the boot order to first device -> Hard Disk


cheers

---

