---
title: "Installing to a SD card"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by danbert on 2007-11-07
I want to try something new with my ubuntu installation on my laptop.  My hard drive is very slow, and I would like to move to a solid state solution.  However, I do like the storage space that the hard drive allows and I also have Windows installed on it.  I do however have an SD card slot built into my laptop.  However, I don't think my BIOS supports booting from USB disks.

Is there any way I can use a /boot on the hard disk to load grub and then use the SD card for the / directory?  This way, Ubuntu would be running from a flash drive, but I would be booting to the hard drive.

---

### Post by dabl on 2007-11-07
Here's how to do it on a USB thumb drive  -- I suppose the principle is the same for a SD card:

[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)

:)

---

### Post by logos34 on 2007-11-07
From what I read the above guide assumes your bios can boot usb in the first place.  

You can try this howto (not sure if it will work with SD card though):

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

(-->'Booting via grub' or 'Booting the kernel from an internal hard drive')

---

### Post by danbert on 2007-11-07
Thanks, that is exactly what I was looking for.  I'd let you know if it works, but Ubuntu's installer didn't detect the SD card.  I might have to try CF later.

---

