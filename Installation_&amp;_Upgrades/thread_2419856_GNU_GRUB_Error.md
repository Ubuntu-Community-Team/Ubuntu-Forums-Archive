---
title: "GNU GRUB Error"
date: 2019-05-26
forum: Installation &amp; Upgrades
---

### Post by chillygal on 2019-05-26
Hi, 
I have a Windows laptop but installed Ubuntu OS on it so i was using Windows and Ubuntu both. I tried deleting Partition as i wanted to remove ubuntu just wanted to keep this laptop for windows only. I am keep getting this error

GNU GRUB version 2.02~beta2-36ubuntu3.14
Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.
grub>

---

### Post by chillygal on 2019-05-26
How can i attach images here plz?

---

### Post by yancek on 2019-05-26
You neglected to include vital information, which windows?  Also, when you had Ubuntu, were you seeing the Ubuntu Grub boot menu and booting both Ubuntu and windows from it?  If that's the case, most of the Grub bootloader files needed to boot are on the Ubuntu partition, the one you deleted.  If your system is UEFI, you should be able to go into the BIOS firmware on  boot and select the windows option. If you do not use UEFI, you will likely need a windows install disk or some repair software to repair the bootloader.  If you are not familiar with the above terms and still have your Ubuntu install media, go to the site at the link below and download and run boot repair according to the instructions.  Using the 2nd option described on that page to download it and when you run it, select the option to Create BootInfo Summary.  That will give you a link when it finishes which you should post here.  It will provide information on your system which should enable someone to make suggestions too repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

> How can i attach images here plz?

When you are posting a reply, there are a number of icons on the top left.  You need the one with the paper clip icon.

---

### Post by Rubi1200 on 2019-05-26
Just to add to what yancek said, do not attempt to repair the Windows bootloader using Boot-Repair because it will not work and may cause even more damage. Windows bootloader needs to be fixed using Windows tools not Linux tools.

[https://prnt.sc/ntgvcm](https://prnt.sc/ntgvcm)

Post the summary here and we can try and help further.

---

