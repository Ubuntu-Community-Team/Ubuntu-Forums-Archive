---
title: "How to burn a Windows 7 .iso from Ubuntu?"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by tekron on 2009-11-30
Hi. I need to use the "Startup repair" recovery tool that is on the Windows 7 "disc." I have a copy of it in iso forum sitting on my ubuntu desktop so what I need to do is format my 8 GB SD card with the proper boot files and then burn it with a program. None of the programs that came with Karmic seem to be working for me so I was wondering if someone could point me in the right direction. Would unetbootin work for me if I pointed it to my ISO or would the boot files it puts on the card not be correct?

---

### Post by phillw on 2009-11-30
Hi,

Popping an iso onto a pendrive is here --> [http://www.pendrivelinux.com/boot-iso-from-usb-flash-drive/](http://www.pendrivelinux.com/boot-iso-from-usb-flash-drive/)

They also cover things like dual booting and multi-booting os's from pendrives - they should apply to your sd card, PROVIDED you bios can boot off sd card.

Alternative, is just make a boot cd from your iso file.

The easiest way I have found is from within ubuntu.  Right click on the iso image and select "Write to disk".

Regards,

Phill

---

### Post by tekron on 2009-11-30
I formatted the usb to FAT and gave it a filesystem, copied the windows 7.iso contents to the usb and it doesn't boot which leads me to believe it needs some type of bootloader... am I missing something? 

I am using an MSI Wind, NO cd rom.. supports booting from USB. I've done this many times before, just never tried putting a WINDOWS installation onto a usb with no cd-room present from inside of UBUNTU

---

### Post by darkod on 2009-11-30
Yes, you are missing bootloader but I don't know how to do it in ubuntu. Otherwise the win7 dvd inside the boot folder has a program bootsect.exe which is writing boot information to usb stick. And then you only copy all files.

Unetbootin might be one of the options, as you said yourself. It's working in ubuntu too, so give it a try. Specify the ISO in unetbootin and your usb stick as destination. Have the stick formatted as FAT32 or even NTFS. Not FAT16.

---

### Post by tekron on 2009-11-30
Unetbootin extracted the iso successfully but seemed to freeze @ 0% when it came time for the bootloader option. I will try again, though..

---

### Post by jrrader on 2009-11-30
system > administration > usb startup disk creator

---

### Post by darkod on 2009-11-30
Strange, unetbootin is adding it's own boot (grub) and connects (chainloads) to the windows one, or at least I thought so. I have only used it for ubuntu images so it might work different if you supply it with windows image.

---

### Post by tekron on 2009-11-30
> **jrrader said:**
> system > administration > usb startup disk creator

Only seems to work if you're using an ubuntu image. When I point to the iso it goes back to the gui and there is nothing in the input box.

---

### Post by Megafag on 2009-11-30
> **tekron said:**
> Only seems to work if you're using an ubuntu image. When I point to the iso it goes back to the gui and there is nothing in the input box.

I am fairly sure you cant do it in ubuntu. there is an easy way to do it using a windows installation here:

[http://dotnetwizard.net/vista-stuff/tips-how-to-bootinstall-windows-7vista-from-usb-flashhard-drive/](http://dotnetwizard.net/vista-stuff/tips-how-to-bootinstall-windows-7vista-from-usb-flashhard-drive/)

---

