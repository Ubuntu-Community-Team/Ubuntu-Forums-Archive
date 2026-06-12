---
title: "Installing Ubuntu on a SD card"
date: 2018-09-20
forum: Installation &amp; Upgrades
---

### Post by titant3k on 2018-09-20
Hello there. I'm trying to install Ubuntu on my laptop, an HP Envy 13, which has a micro SD slot. I want to keep Windows 10 on the internal ssd and install Ubuntu on the SD, so when I need it I could boot from the SD.
This is the issue: I can't boot from the SD card, the BIOS doesn't read it. No problems instead with other USB devices, such as the USB drive with the Ubuntu live iso.

Any suggestions? I thought that maybe I could install what is necessary to boot on the internal SSD and leave the rest on the SD card.

---

### Post by cmcanulty on 2018-09-20
This could be worth a try. Put the SD card in a usb sd card reader. Install ubuntu to the usb card reader. You can get one for a few bucks on ebay. Then try it again by putting it in slot and telling grub to boot to it. Just an idea.

---

### Post by yancek on 2018-09-20
You indicate that you cannot boot from the SD card as your BIOS doesn't read it.  Nothing Ubuntu can do about that, your BIOS not recognizing the card.  Have you installed or tried to install Ubuntu on the card?  Are you just booting Ubuntu from the usb and haven't installed yet?  The Ubuntu documentation on dual booting with windows 10 is at the link below, reading that might help you understand.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by webmiester on 2018-09-20
> **titant3k said:**
> Hello there. I'm trying to install Ubuntu on my laptop, an HP Envy 13, which has a micro SD slot. I want to keep Windows 10 on the internal ssd and install Ubuntu on the SD, so when I need it I could boot from the SD.
This is the issue: I can't boot from the SD card, the BIOS doesn't read it. No problems instead with other USB devices, such as the USB drive with the Ubuntu live iso.

Any suggestions? I thought that maybe I could install what is necessary to boot on the internal SSD and leave the rest on the SD card.

The main problem here is that the card reader needs a driver which is loaded by the Operating system.  If you put the SD card in a card reader and put it in the USB slot, you still need the driver for the USB card reader too, which your BIOS doesn't have built in.  In this case, you might need to just boot from USB.

---

### Post by titant3k on 2018-09-20
I can install Ubuntu on the SD if I connect it through an USB hub (Type C), but I'm not able to boot it if I insert the card in the micro sd slot.

I got more informations:
- in Windows, the SD card reader uses an hardware named Alcorlink PCIE Card Reader
- from Ubuntu I can't read the SD through the internal reader.

---

### Post by webmiester on 2018-09-21
> **titant3k said:**
> I can install Ubuntu on the SD if I connect it through an USB hub (Type C), but I'm not able to boot it if I insert the card in the micro sd slot.

I got more informations:
- in Windows, the SD card reader uses an hardware named Alcorlink PCIE Card Reader
- from Ubuntu I can't read the SD through the internal reader.

Yes, exactly my point.  The SD Card reader needs a driver to function which isn't accessible by your BIOS.  Apparently, the BIOS has a built in driver for the USB port though.  Its not ubuntu that needs the driver to boot-up, its the BIOS.  Although you will need the driver on ubuntu to be able to access the sd card after bootup.

One possibility is to upgrade your BIOS, but this for me, sounds risky and not worth the effort.  I would suggest to just boot from a USB flashdisk whenever you need ubuntu.

---

