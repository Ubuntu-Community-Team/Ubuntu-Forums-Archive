---
title: "no boot into Ubuntu after installiing on second HD"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by lisa374 on 2010-09-08
Sorry for the really noob question.
I have Win XP on sdc. Boots fine:)
Installed 10.04 on a new sdb.
System still boots into XP without showing a menu. There is no grub loader and I couldn't find a place in the .iso install where the grub could be change from sdb to sdc. "Change location" only allowed sdb.
So what did I do incorrectly and how do I fix it.
Needless to say I've read many posts about multiboot, but this old brain can't determine what I did incorrectly:(

---

### Post by 0N3 on 2010-09-08
Have you 2 or 1 Hard Disks? Im kinda lost by what you mean

---

### Post by lisa374 on 2010-09-08
I have three HD's. But only two of them a mentioned. One has Win XP system, one has all of Ubuntu and one has data et. al.

---

### Post by 0N3 on 2010-09-08
have you selected the Hard Drive with Ubuntu on it as your first boot priority in your bios? if u dont know how when u boot your pc tap the del button to get into your bios change your first boot priority to the Hard drive with ubuntu on it or for a laptop its usually F2 and change your boot priortiy to the Hard drive with Ubuntu on it getting into the bios may vary on your machine if i can be of anymore help please let me know best of luck

---

### Post by wilee-nilee on 2010-09-08
I am assuming you are correct with sdb=Ubuntu sdc=XP you just have to install grub to the mbr=sdc and here is a link.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

It may be that as the post above suggests grub may pickup XP with a sudo update-grub, or at least boot from sdb.

---

### Post by lisa374 on 2010-09-08
Thanks for all the help. After three tries I found an "Advanced" menu just before the final install menu which allowed me to set the boot to sdb as I needed. That menu was between the partitioning selection and the final install button so I missed it the first two times. I thought I had finished with all the hard drive selection/partitioning part of installation and lo and behold there comes another "advanced" selection.

---

### Post by wilee-nilee on 2010-09-08
> **lisa374 said:**
> Thanks for all the help. After three tries I found an "Advanced" menu just before the final install menu which allowed me to set the boot to sdb as I needed. That menu was between the partitioning selection and the final install button so I missed it the first two times. I thought I had finished with all the hard drive selection/partitioning part of installation and lo and behold there comes another "advanced" selection.

Just a heads up for you if you try Maverick at some point you can set grub but it is in the partitioning part of the install rather then at the end with the advanced button.

---

### Post by 0N3 on 2010-09-08
Long live ubuntu so happy you got it wohoooo Meerkat is the s**t :P
happy ubuntuing :)  Love this place!!!!!!!!!!!!!

---

