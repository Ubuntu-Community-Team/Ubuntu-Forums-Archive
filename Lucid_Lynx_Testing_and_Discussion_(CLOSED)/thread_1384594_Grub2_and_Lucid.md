---
title: "Grub2 and Lucid"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by dsmithnc on 2010-01-18
So, I installed lucid on an external drive connected to my laptop via the esata port.

The one thing I forgot about Ubuntu installs is there isn't a choice of where the grub loader should go.  As a result the loader is on my HDD and in order to start just the laptop install of Karmic, I have to have the esata drive plugged in.  Not the end of the world, but it is a pain.

I have read some of the documentation for Grub2 but being relatively new to the linux world, I don't understand much of what I read.  There must be a way to set the grub2 loader so there is a different one for each drive?

I had a distro of Mandriva on the external drive recently.  That distro gave the user an option of which drive to put the loader.


Thanks for looking,

Dick

---

### Post by philinux on 2010-01-18
> **dsmithnc said:**
> So, I installed lucid on an external drive connected to my laptop via the esata port.

The one thing I forgot about Ubuntu installs is there isn't a choice of where the grub loader should go.  As a result the loader is on my HDD and in order to start just the laptop install of Karmic, I have to have the esata drive plugged in.  Not the end of the world, but it is a pain.

I have read some of the documentation for Grub2 but being relatively new to the linux world, I don't understand much of what I read.  There must be a way to set the grub2 loader so there is a different one for each drive?

I had a distro of Mandriva on the external drive recently.  That distro gave the user an option of which drive to put the loader.

Thanks for looking,
Dick
Last stage of install there is an advanced button. This allows you to select where to put grub.

---

### Post by dsmithnc on 2010-01-18
> **philinux said:**
> Last stage of install there is an advanced button. This allows you to select where to put grub.

Well, guess I'll need to pay more attention!  Thanks for alerting me to that.

I wonder if I reinstall Lucid, paying attention to the "advanced" button, will that straighten out the boot issue?

Dick

---

### Post by cecilpierce on 2010-01-18
I think you can install grub on the other drive with out reinstalling. I have two drives and grub on both just in case I mess one up I can get back in and TRY to fix it. In a terminal window :
"sudo grub-install /dev/sda" for first drive or "sdb" for second drive is what I use. Good luck.

---

### Post by dsmithnc on 2010-01-18
> **cecilpierce said:**
> I think you can install grub on the other drive with out reinstalling. I have two drives and grub on both just in case I mess one up I can get back in and TRY to fix it. In a terminal window :
"sudo grub-install /dev/sda" for first drive or "sdb" for second drive is what I use. Good luck.

Thanks. I'll give that a try.

---

