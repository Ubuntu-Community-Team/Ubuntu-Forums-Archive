---
title: "[SOLVED] How to multiboot; with 2 OS already multibooting"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by Lateforgym on 2008-08-30
I wasn't sure how to describe it well enough to get a good search, but I have a desktop with 2 HDDs, XP on each that uses the Boot.ini to multi boot. I now want to add Ubuntu. I know how to shrink a single HDD and install ubuntu, I'm not sure how its going to deal with XP already set up on the 2 HDDs. Some tutorials say to disconnect all HDDs except the one your installing Ubuntu on, but if I do that, then I'm thinking GRUB wont know that I have another OS on my other HDD and not set the GRUB up correctly. I have heard something about chainloading but I couldnt find a definition on what that means.

---

### Post by cdtech on 2008-08-30
**Update::.**
You don't need to remove your drives, Ubuntu will see the added partition. Just point the install to that partition. When it ask where to install the GRUB bootloader then use the MBR of your primary drive, it will see the additional OS.

---

### Post by Lateforgym on 2008-08-30
OK. Your answer was fairly clear but I want to make sure I understand. What you saying is, on my system which has 2 HDD's with XP on each and boot.ini already setup for dual boot:

Dont remove any HDDs
Just shrink SATA1(primary Drive)
Install in the free partition
GRUB will see 2 HDD ask ask Which one to load it on
Tell its SATA1(primary)

At this point GRUB will be able to see the XP OS on SATA1(primary) and SATA2(data)as well as Ubuntu. 

Will the multi boot I already setup in boot.ini mess up GRUB? or will GRUB know to just overwrite that?

Thanks

---

### Post by cdtech on 2008-08-30
GRUB will over write the MBR on the primary drive. If after the install it does not see the two OS's, you can add these within the "menu.lst" and be able to boot from the GRUB list. Your drives will be listed as "sda / sdb". Be sure to install to the correct partition and not the sda1 partition (XP).

---

### Post by Lateforgym on 2008-08-30
"Your drives will be listed as "sda / sdb". Be sure to install to the correct partition and not the sda1 partition (XP)."

I would just tell it to install to the Continuous partition right?

---

### Post by cdtech on 2008-08-30
Correct........

---

