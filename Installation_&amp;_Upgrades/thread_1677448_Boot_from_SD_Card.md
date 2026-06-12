---
title: "Boot from SD Card"
date: 2011-01-28
forum: Installation &amp; Upgrades
---

### Post by I_Am_Einstein on 2011-01-28
Installed on SD using the USB installer

Installed Ubuntu Server 10.10 x64 on 8GB SD card in mmc reader
How do I boot into it.

I assume I need to edit Grub, since I don't know anything about editing BIOS settings to allow to boot from internal card reader

Currently I have Windows 7 Ultimate x64 and openSUSE 11.3 on a dual boot, and installed grub with openSUSE which overwrote the MBR, so I cannot edit boot menu from EasyBCD in Windows, have to edit grub from openSUSE

How do I do it

Thanks

NOTE: I know I can put in external card reader and boot into it. But I want to install from internal card reader, so I don't have this giant USB thing jutting out the side of my laptop.

---

### Post by rocthrttle on 2011-01-28
[http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)

try this boot cd and see if the card reader shows up. also with dell you can hit f12 and get a boot selection menu. maybe yours has a similar option. i wouldnt go messing with grub. its just going to get updated when 10.10 server enters the fray.

if that doesnt work, i have this opinion...dood you should be installing it to a partition. that way one time your going to "have this giant USB thing jutting out the side of my laptop." big deal. if it works it works....just be careful not to bump it until your done.

---

### Post by C.S.Cameron on 2011-01-28
In BIOS try setting the SD card as first hard drive.

You might also try pressing F2, F10, F12, Esc, etc when booting. some computers will give you a choice of what to boot.

---

### Post by I_Am_Einstein on 2011-01-30
> **rocthrttle said:**
> [http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)

try this boot cd and see if the card reader shows up. also with dell you can hit f12 and get a boot selection menu. maybe yours has a similar option. i wouldnt go messing with grub. its just going to get updated when 10.10 server enters the fray.

It is not an option in BIOS. I am looking for a hack.

> **rocthrttle said:**
> 
if that doesnt work, i have this opinion...dood you should be installing it to a partition. 


I do already have it installed to a partition... and also have it installed in VirtualBox as well. I want to have a portable version on my SD Card that I can keep in at all times and be unobtrusive to my daily work. I spend 12 to 16 hours a day online or on my computer. I am a professional web designer and developer.

> **rocthrttle said:**
> 
that way one time your going to "have this giant USB thing jutting out the side of my laptop." big deal. if it works it works....just be careful not to bump it until your done.

Honestly I was hoping if I came on this forum and put I_Am_Einstein, that people might give me better answers, knowing I am smart enough to figure out anything intuitive.

> **C.S.Cameron said:**
> In BIOS try setting the SD card as first hard drive.

You might also try pressing F2, F10, F12, Esc, etc when booting. some computers will give you a choice of what to boot.

It is not an option in BIOS. I am looking for a hack.

---

### Post by oldfred on 2011-01-30
I have not used plop but they say they were converting it to boot other devices:

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

If you do a grub partition it may let you boot the SD card. You might have to load a kernel first, but not sure.

Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_)

---

### Post by rocthrttle on 2011-01-30
> **I_Am_Einstein said:**
> 
Honestly I was hoping if I came on this forum and put I_Am_Einstein, that people might give me better answers, knowing I am smart enough to figure out anything intuitive.


sorry didnt notice the name. gratz on being a superuser. we dont get too many of them on here. let us know how you make out. i think PLOP is your best bet. most computers will boot to cd without any mod to the BIOS. all seem to have it as an option.

---

