---
title: "Installing Windows XP on Mandriva/Ubuntu"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by benniebrown07 on 2008-01-28
How do i install windows xp on a hard drive that has mandriva or ubuntu (I have one of each) on it?
 I've installed both linux versions my self, but windows always came installed. How do i set linux to boot from cdrom so i can install xp. If thats not how I do it then please tell me how. Thanks

---

### Post by logos34 on 2008-01-28
Go into the Bios at startup and set it to boot from cdrom drive.

XP will overwrite the grub bootloader on the MBR, so you'll have to restore grub (either [Ubuntu's]("http://ubuntuforums.org/showthread.php?t=224351") oir Mandriva's) from the live cd.

Then add XP to menu.lst

---

### Post by benniebrown07 on 2008-01-28
>>Go into the Bios at startup and set it to boot from cdrom drive.<<

how do i get to the bios

---

### Post by logos34 on 2008-01-28
try F2, F10, Esc, Del

[http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html](http://www.brunolinux.com/01-First_Things_To_Know/Change_BIOS_Settings.html)

---

