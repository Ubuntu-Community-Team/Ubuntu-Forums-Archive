---
title: "GRUB menu missing Windows entry"
date: 2024-04-10
forum: Installation &amp; Upgrades
---

### Post by AndrewMcNZ on 2024-04-10
Hi All

After replacing one of the disks on my Ubuntu and Windows dual-boot system, I made several mistakes that made the Grub menu stop working. :( After using [FONT=Courier New]boot-repair[/FONT] from an Ubuntu LiveCD, I now have a system with a working Grub menu that lets me boot into Ubuntu. This is good! :P However, the Windows entry is missing from the Grub menu. Is anyone able to advise me or point me to information on what I should do to recover the Windows entry on my dual-boot system?
I have uploaded a boot-repair report: [https://paste.ubuntu.com/p/d9DRn94P4x/](https://paste.ubuntu.com/p/d9DRn94P4x/)

Thanks
Andrew Mc

---

### Post by tea for one on 2024-04-11
The Windows boot files are missing from the Efi System partition /dev/sda2.
Line 118  - Windows Boot Manager entry.
Line 114 - Secure boot is enabled 

Can you boot Windows using the dedicated key to reach the PC boot menu (i.e. not grub)?

If so, then close Windows without hibernation
Open your UEFI setttings
Disable secure boot
Boot into Ubuntu
Open a terminal and enter:-
```
sudo update-grub
```
Did grub find Windows?

---

### Post by AndrewMcNZ on 2024-04-11
Unfortunately, I am now unable to boot to Windows when I use the boot selector in the BIOS setup. :-( I could do this previously, only a couple of days ago, so perhaps my recent use of boot-repair has stopped the Window boot from working.

---

### Post by oldfred on 2024-04-11
Boot-Repair will not modify default Windows boot entries.
It seems something happened to your Windows install & you need Windows repairs.
Use your Windows repair/recovery flash drive to repair Windows.

---

### Post by AndrewMcNZ on 2024-04-12
I have success! :P
I followed your instructions and used a Windows Recovery flash drive to recover the Windows boot.
I found the instructions at [https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records/](https://www.digitalcitizen.life/command-prompt-fix-issues-your-boot-records/) and [https://unix.stackexchange.com/questions/510013/cant-boot-to-windows-after-installing-ubuntu-in-uefi](https://unix.stackexchange.com/questions/510013/cant-boot-to-windows-after-installing-ubuntu-in-uefi) to be helpful for this.

I then booted Ubuntu by using the BIOS boot selector and used the command:
```
sudo update-grub
```
Grub found the Windows install and added it to the Grub menu.

I then used the BIOS settings to ensure that the ubuntu partition was the first in the boot sequence (instead of the Windows one), and now my system starts the Grub menu from which I can boot either Ubuntu or Windows. :cool:

Thank you so much for the help.\\:D/

---

