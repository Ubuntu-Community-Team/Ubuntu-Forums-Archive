---
title: "Error installing ubuntu on asus, ubuntu don't load"
date: 2016-01-15
forum: Installation &amp; Upgrades
---

### Post by kevin202 on 2016-01-15
Hello, i'm had some time in Ubuntu, beginning in Linux, in my PC it was installed perfect, but when i try install ubuntu un other computer(ASUS X453MA), i has too problems... i use LiLi, and i download Ubuntu 14.04.3, i change the BOOT:
USB MENU SECURITY: DISABLED;
CMS: ENABLED;
IXHC (or any simiar): DISABLED;
When i run the Ubuntu's installer, when i select LiveCD or Install beggins load, and you know, the beautiful balls with color, but in a moment it stop, and i should reboot the PC with the main button...
I was try 
IXHC (or any simiar): ENABLED,
desactivate with F6 icp(i unknow the correct names) AND
desactivate with F6 ALL;

I'M WAITING YOUR HELP PLEASE

*: sorry for my bad english

---

### Post by ubfan1 on 2016-01-15
This is a UEFI machine, so if you are trying to dual boot Win 8, turning on CMS is a bad idea.  Just to be sure, is your disk partitioned with gpt partitioning?  Are you trying to dual boot?  Did you read [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported) ?

---

### Post by SeijiSensei on 2016-01-15
I had problems with my ASUS machine and UEFI.  

I had to turn off some switches in the BIOS during installation and then switch them back: [http://www.eightforums.com/installation-setup/51645-uefi-settings-asus-z77-prior-clean-install.html](http://www.eightforums.com/installation-setup/51645-uefi-settings-asus-z77-prior-clean-install.html)

I created a UEFI USB image with rufus as described here: [http://www.techerina.com/2015/01/dual-booting-windows-8-and-ubuntu-uefi-using-rufus.html](http://www.techerina.com/2015/01/dual-booting-windows-8-and-ubuntu-uefi-using-rufus.html)

---

### Post by kevin202 on 2016-01-16
Ok, i'll see my disk partition and read, wait me, thks for your answer

---

### Post by kevin202 on 2016-01-16
thaks for your answer, i will read and try it.

---

### Post by kevin202 on 2016-01-20
[COLOR=#000000]i try:
USB MENU SECURITY: DISABLED;
[/COLOR]FAST BOOT: ENABLED;
[COLOR=#000000]CMS: DISABLED;[/COLOR]
[COLOR=#000000]IXHC (or any simiar): DISABLED;

i was do a usb with uefi and with gpt uefi, (yes, my disk is gpt) but the error continue.
i unknow what do

*: i dont know if i use dual boot, i think what yes.[/COLOR]

---

### Post by kevin202 on 2016-01-20
Ah, and i select [UEFI: DATA TRAVELER] in boot priority

---

### Post by kevin202 on 2016-01-20
I try with lubuntu and not function!

---

