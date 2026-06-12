---
title: "stupid mistake, need help"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by alpha_nova on 2008-06-23
Ok, so I decided to uninstall ubuntu but instead of doing it the right way I did something stupid and used the Windows Vista Disk manager to delete the ubuntu and grub partition and merged it with my vista one. Now whenever I start up my computer, grub tries to load and then gives me ERROR 17 and stops there. I'd rather not reinstall Vista, so if there's an easier way of fixing this problem, PLEASE HELP.

Thanks

---

### Post by Partyboi2 on 2008-06-24
Try fixing the master boot record 
1.    Put the Windows Vista installation disc in the disc drive, and then start the computer.
2.    Press a key when you are prompted.
3.    Select a language, a time, a currency, a keyboard or an input method, and then click Next.
4.    Click Repair your computer.
5.    Click the operating system that you want to repair, and then click Next.
6.    In the System Recovery Options dialog box, click Command Prompt.
7.    Type Bootrec.exe /FixMbr, and then press ENTER.

---

