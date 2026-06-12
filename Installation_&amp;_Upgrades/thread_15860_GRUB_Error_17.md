---
title: "GRUB Error 17"
date: 2005-02-17
forum: Installation &amp; Upgrades
---

### Post by kwanbis on 2005-02-17
Ok, i deleted the Ubuntu partition, and now when i try to boot, GRUB says Error 17 ... and i'm trying to boot into my 2000 partition ... any idea?

---

### Post by kwanbis on 2005-02-17
ok, from [http://www.desktop-linux.net/grub.htm](http://www.desktop-linux.net/grub.htm)

Removing Grub From The MBR:

DOS and Windows 9x/ME

Create a rescue disk under DOS or Windows 9x/ME, use it to boot the machine, start fdisk with:  fdisk /mbr

Windows XP

Boot from the Windows XP CD, press the key R in the setup in order to start the restoration console. Select your Windows XP installation from the list, and enter the administrator password. Enter the command fixmbr at the input prompt and confirm the next question with Y. Finally, use exit to restore the computer.

Windows 2000

Boot from the Windows 2000 CD, press the key R in the setup and the key "C" in the next menu in order to start the restoration console. Select your Windows 2000 installation from the list and enter the administrator password. Enter the command fixmbr at the input prompt and confirm the next question with Y. Finally, use exit to restart the computer.

---

### Post by wallijonn on 2005-02-18
kwanbis,

I do not think that W2KP has a fixmbr command. Or does it?

On my system I had to copy NTDETECT.COM & ntldr to C:\ to get it to boot.

---

