---
title: "Cant boot ubuntu 13.10 after instaling it"
date: 2014-01-24
forum: Installation &amp; Upgrades
---

### Post by leonardo7 on 2014-01-24
So, i've always been a Windows user, but yesterday i downloaded 64 bits Ubuntu 13.10 and created a bootable usb to install from it.

I choose the option to install it alongside with Windows, it partitioned my hd, installed sucessfully but after the message I restarted it it automatically entered windwows (same hd)...

I tried using boot repair while on "try" experecience, but it didnt work.

Reinstalled it twice after but no sucess but it didnt work either, one of them i made 4 partitions.. (/boot, / , /home, swap), choose it to boot from /boot partition..
 
It doesnt even shows up grub for me to choose which OS i want to boot.

Am I doing something wrong?? Shoud i try installing it from DVD?

---

### Post by oldfred on 2014-01-24
If older Windows did you specify to install grub to MBR of drive sda or sdb etc and set BIOS to boot that drive, not a partition like sda5?
Or if new UEFI type system have you gone into UEFI or one time boot key and booted ubuntu entry?

Best to see details.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by leonardo7 on 2014-01-24
no uefi.... choose to install grub same hd windows boot's..

i saved this link home, gonna post it later..

---

### Post by leonardo7 on 2014-01-24
Turns out my booting hd was slave at bios, I switched the cables with my other HD, then it started booting ubuntu... xD

---

