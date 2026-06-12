---
title: "BOOTING FRM external hdd !! screenshot included!!"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by hydroparasite on 2008-03-07
**hello**

I am urgent need of help !! i have read hundres of post relateed to this and i finally decided to include the screenshot of my hdd so that i can get some help !! my linux us installed on the external hdd and i wantto boot from it !! don wanna write MBR as it will screw my ibm recovery at boot ( i ll not b able to access it ) .my bios is enabled to boot frm usb hdd and upon detection i get the options and boot doesnt occur ..

attached is the screenshot i obtained by booting into the live cd ! pls help ...........


thanks is advance :confused:

---

### Post by logos34 on 2008-03-07
> **hydroparasite said:**
> [B] don wanna write MBR as it will screw my ibm recovery at boot ( i ll not b able to access it ) .my bios is enabled to boot frm usb hdd and upon detection i get the options and boot doesnt occur ..

During install did you explicitly tell it NOT to install Grub?  Because you do need it, only not on the mbr of the internal disk.  If you told it not to install grub, it might be easiest to reinstall, but this time at the 'Ready to install' screen press 'Advanced' button lower left and replace '(hd0)' with **/dev/sdb**.  That will write grub to the mbr of the external usb drive.  Then finish install but continue using the live cd.  Edit menu.lst before you reboot:

(in a terminal):

**gksudo gedit /boot/grub/menu.lst**

change the **groot** line (near top) and **root** lines to (hd**0**,6)

(hd0,6 = sdb7 root)

---

