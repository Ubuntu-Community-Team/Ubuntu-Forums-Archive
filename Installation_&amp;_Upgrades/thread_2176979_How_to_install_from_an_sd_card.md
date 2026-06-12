---
title: "How to install from an sd card?"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by tahdas on 2013-09-26
I want to install ubuntu to an sd card, so i can live boot it on my new laptop. how would i got about doing this?

Ive only ever installed linux from a dvd drive so im kinda  noob at usb and sd stuff.

Thanks,
thadas

---

### Post by C.S.Cameron on 2013-09-26
Install to a SD card just like to a flash drive, use Startup Disk creator from the Live CD or UNetbootin.
(Older computer BIOS may not boot SD).

---

### Post by tahdas on 2013-09-26
yeah i tried the thing that ubuntu recomends on their site. And then when i tried to liveboot it, it didnt show up. BTW the laptop im trying this on is this: [http://www.amazon.com/gp/product/B00BC7DRXC/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00BC7DRXC/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1)

As i said im new to booting from a usb drive,.

---

### Post by Mark Phelps on 2013-09-27
> I want to install ubuntu to an sd card, so i can live boot it on my new laptop. 

Do you know for certain that your laptop CAN boot from an SD card? Just because you have an SD card slot, doesn't mean you can boot from it.

---

### Post by tahdas on 2013-09-27
Know i don't know that i can boot from a sd card, how do i check?

CC from somewhere else: [http://www.amazon.com/gp/product/B00BC7DRXC/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B00BC7DRXC/ref=oh_details_o00_s00_i00?ie=UTF8&psc=1)

I was trying to boot 13.04 off an sd card. 

Mine has windows 7 not 8, and i didn't see my model listed in your link. It turns my iso file are corupt-maybe because i download them in chrome-so im trying to re-download them in firefox.  It also might be an issue with my sd card so im going to buy a usb thumb drive today or tomorrow. 

Do i still need to download the bios even if im in windows 7?

Im not used to using usb/sd card, does anyone have any pointers? Whats usb burner should i use?

Thanks,
tahdas

---

### Post by sudodus on 2013-09-27
Maybe you will find some useful information at this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Many (but not all) computers treat an SD card in the same way as a USB pendrive (like any mass storage device).

---

### Post by tahdas on 2013-09-27
Im trying to burn it onto the sd card and it keeps saying files are broken, why is this, and to i fix them?

---

### Post by sudodus on 2013-09-27
- What flavour of 13.04 are you trying to install? 32-bit or 64-bit? Standard Ubuntu or Kubuntu, Lubuntu or Xubuntu? Did you check with md5sum, that the download was successful?

- What tool (or method) are you using to flash the iso file to the SD card? Several tools and methods are described in the link in post #6.

- Is there a way to put the SD card at the top of the boot order menu (in the BIOS menu system)?

- Have you checked if your computer is running in UEFI or old standard BIOS (alias CSM) mode?

---

### Post by tahdas on 2013-09-27
64 bit ubuntu 13.04. No i didn't, can you link me to where i can download that?

This [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

I dont think so.

No, how do i?

Thanks,
tahdas

---

### Post by sudodus on 2013-09-28
I try to make clear the connection between (q)uestion and (a)nswer:

> **sudodus said:**
> - q1: What flavour of 13.04 are you trying to install? 32-bit or 64-bit? Standard Ubuntu or Kubuntu, Lubuntu or Xubuntu?

- q2: Did you check with md5sum, that the download was successful?

- q3: What tool (or method) are you using to flash the iso file to the SD card? Several tools and methods are described in the link in post #6.

- q4: Is there a way to put the SD card at the top of the boot order menu (in the BIOS menu system)?

- q5: Have you checked if your computer is running in UEFI or old standard BIOS (alias CSM) mode?

> **tahdas said:**
> a1: 64 bit ubuntu 13.04.

a2:No i didn't, can you link me to where i can download that?

a3:This [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

a4: I dont think so.

a5: No, how do i?

Thanks,
tahdas

Tell me if I misunderstood :-)

-o-

And here are my (c)omments:

c1: 64 bit ubuntu 13.04 should be OK for that computer

c2: You find checksums at [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) and check the output of the terminal window command ```
md5sum ubuntu-13.04-desktop-amd64.iso 
``` (use the appropriate file name and the corresponding md5sum from UbuntuHashes).

c3: I'm not sure, but Pendrivelinux used to create boot disks with msdos partition tables and grub2. If you have UEFI, it will not work. Try Unetbootin, Startup Disk Creator or cloning with dd according to
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

c4: This link (paragraph) is probably relevant also for SD cards.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

c5: Start by reading about UEFI, [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Mark Phelps on 2013-09-28
> Do i still need to download the bios even if im in windows 7?

I thought you were asking about installing Ubuntu to an SD card -- so you can later, boot from it.

You should NOT be messing around with any BIOS update.  That is unlikely to do anything for the SD card -- unless the BIOS update notes specifically say so.  And, if anything goes wrong during the BIOS update (which can happen), you will end up with an electric brick.

You should NEVER do a BIOS update unless BOTH of the following are true:
1) You have a way of saving the current, working, BIOS to a media that can be read even if the OS can not start
2) You have a way of restoring that saved BIOS -- in the event that the BIOS update fails.

---

