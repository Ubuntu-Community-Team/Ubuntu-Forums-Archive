---
title: "Dual boot upgrade question"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by staib on 2009-12-11
Hi all,

Ubuntu 9.10 and Vista (64-bit) are happily co-existing on my PC. I select the appropriate o/s from Grub and all is good. I use Vista for Flight Sims and video editing, and Ubuntu for everything else.

I have been gifted a Windows 7 ultimate 64-bit dvd and would like to upgrade Vista to Win 7 as it seems to be lighter and faster than Vista.

Has anyone seen any threads that explain how best to do this without inadvertently wiping the Ubuntu partition. I am expecting that W7 will also overwrite the Grub bootloader, so would love to know how to get that back if needed?

Cheers,

Nick

---

### Post by darkod on 2009-12-11
If you are doing a clean install of win7 over vista, you're selecting the destination partition yourself so just make sure you point the installer to the vista partition and your ubuntu is fine.
If using the upgrade function, it should install itself over vista and ubuntu should be fine too.
Yes, grub2 will be lost. Instructions to restore different bootloaders here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by staib on 2009-12-11
Thank you for the reassuring comments and that link to advice on restoring the bootloader. I will be attempting this over the weekend, so I will update here if all is successful :D
Your quick help is much appreciated Darko.
Cheers!

---

