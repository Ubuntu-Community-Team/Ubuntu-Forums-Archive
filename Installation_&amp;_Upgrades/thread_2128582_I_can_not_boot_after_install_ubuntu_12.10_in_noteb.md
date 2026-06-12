---
title: "I can not boot after install ubuntu 12.10 in notebook with windows 8"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by talpoflo2 on 2013-03-23
Hi everyone¡
Im sorry, but mi English is not good
I have an HP 2000 notebook with windows 8 preinstalled
I installed ubuntu 12.10 64-bit together windows
First  I traied to do it using wiki, but at restart I can not boot, then I  used a live usb, the install was successful, but I still can't boot. 
The ubuntu pastebin number is [http://paste.ubuntu.com/5640903/](http://paste.ubuntu.com/5640903/)

Thanks for all

---

### Post by oldfred on 2013-03-23
Not sure if this is only issue, but you can only have one efi partition per hard drive.

 /dev/sda2         821,248     1,353,727       532,480 EFI System partition
/dev/sda3       1,353,728     1,615,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,615,872   479,711,215   478,095,344 EFI System partition

Gparted used boot flag to define efi partition in gpt partitioned drives. It is not the same as a boot flag in MBR(msdos) partitioned drives. But all booting with UEFI is from efi partition. 

Use gparted and remove boot flag from sda4.

---

