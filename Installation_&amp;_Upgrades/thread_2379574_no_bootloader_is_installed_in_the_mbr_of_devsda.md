---
title: "no bootloader is installed in the mbr of /dev/sda"
date: 2017-12-07
forum: Installation &amp; Upgrades
---

### Post by chery1232 on 2017-12-07
[COLOR=#000000]Hey everyone. 
I have dual boot of Windows 10 and ubuntu 16.04.
I don't know why but I accidentatly deleted some partitions related to bootload and to linux.
Now While booting, I don't get the grub graaphical interface, I'm direct to grub command lign grub> ,
When trying "shift", I was able to access to windows, but with ubuntu I'm always redirected to grub prompt.
I have tried with boot repair, but nothing happened, and I get "[/COLOR]no bootloader is installed in the mbr of /dev/sda" in the boot info file,
I am confused, how can I resolve the problem without having to reinstall ubuntu again, 
thank you,

---

### Post by ajgreeny on 2017-12-07
See **Boot-Repair** in my signature below and follow the instructions there to run the **Boot-Info-Script** again showing us all the info.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system than you have told us so far. 

You say > I have tried with boot repair, but nothing happened, and I get "no bootloader is installed in the mbr of /dev/sda" in the boot info file, I am confused, how can I resolve the problem without having to reinstall ubuntu again, 
but we need more than that to assist, but it seems likely from that comment that there is a BIOS/UEFI problem which may be easy to solve once we know what's wrong.

---

