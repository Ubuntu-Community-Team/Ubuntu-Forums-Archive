---
title: "'boot error' while installing ubuntu using usb pendrive"
date: 2011-12-18
forum: Installation &amp; Upgrades
---

### Post by wankhaderoshan on 2011-12-18
Hi Friends, I'm new to Linux. Currently using windows xp & would like to install ubuntu as many says that it's easy for begginers.
I have downloaded the **'ubuntu-11.10-desktop-i386.iso'**
then uses **'Universal-USB-Installer-1.8.7.4'** for my 4 gb pendrive and its giving success msg.
then i reboot the system (my board is intel D102GGC2 and supports usb booting option) 
and after pressing the F10, i have 2 boot options one is my hard disk and other for my pendrive. now the problem is when i boot through pendrive then it gives only 2 words error msg [B]'boot error'.
[/B]where am i wrong please help me out... :confused:

---

### Post by Mark Phelps on 2011-12-19
I went through the same steps with the recent 12.04 Alpha -- and it worked great.

I originally tried unetbootin (the recommended approach). My experience there matched yours with the other installer.

However, more folks seem to be successful using unetbootin.  Suggest you give that a try.

---

### Post by IPEX-731BA5DD06 on 2011-12-20
Look for the obvious problems;

1) have you enabled the usb boot option in you Bios, its not enough to have the option, it has to be enabled.
2) Have you set the 'pen drive' as your 1st boot option.
3) have you enabled the Pen drive as a boot option.

From the sounds of your problem, boot error, means its trying to boot with the 'pen drive', but its not enabled as an option in BIOS, or you've enabled the cd/dvd drives instead above that drive.

---

