---
title: "cant install ubuntu 12.4 :("
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by acepro71 on 2013-10-09
[COLOR=#282828][FONT=helvetica]ok i downloaded ubuntu-12.04.3-desktop-amd64[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]but i used to install it with wubi.exe[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]but this time it wont let me as i am running windows 8 it just gives an error [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]so i made an usb drive of ubuntu with Universal-USB-Installer-1.9.4.3[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]it runs and when i clicked on install ubuntu inside windows 8[/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]it restarted my system and booted back into windows 8 any help ?

than i burned the dvd and the same thing happened with dvd too 

my bios isn't uefi and they do not have secure boot too but still i am not able to install it [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] 
it runs fine if i click try ubuntu :* [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica] [/FONT][/COLOR]
[COLOR=#282828][FONT=helvetica]how can i install it ? 


my system ~ [CENTER][COLOR=#FF0000]CPU[/COLOR][COLOR=#A4A4A4]: Fx 8350 | [/COLOR][COLOR=#FF0000]CPU Cooler[/COLOR][COLOR=#A4A4A4]: Coolermaster Hyper 212 Evo | [/COLOR][COLOR=#FF0000]Motherboard[/COLOR][COLOR=#A4A4A4]: Gigabyte GA-970A-DS3 (rev 1.1) | [/COLOR][COLOR=#FF0000]Ram[/COLOR][COLOR=#A4A4A4]: Corsair Vengence 8GB DDR3 | [/COLOR][COLOR=#FF0000]Graphics Card[/COLOR][COLOR=#A4A4A4]: SAPPHIRE HD 7870 GHz Edition 2GB GDDR5 |  [/COLOR][COLOR=#FF0000]HDD[/COLOR][COLOR=#A4A4A4]: 1 TB samsung [/COLOR][/CENTER][/FONT][/COLOR]
[CENTER][COLOR=#A4A4A4][FONT=helvetica][COLOR=#FF0000]Case[/COLOR]: CM elite 310 | [COLOR=#FF0000]Monitor[/COLOR]: Aoc e2050S[/FONT][/COLOR][COLOR=#A4A4A4][FONT=helvetica][COLOR=#FF0000]OS[/COLOR]: Windows 8 Professional 64 Bit[/FONT][/COLOR][/CENTER]

---

### Post by grahammechanical on 2013-10-09
This is happening because the Windows installer (Wubi.exe) is incompatible with Windows 8

[http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows](http://www.ubuntu.com/download/desktop/install-ubuntu-with-windows)

Regards.

---

### Post by acepro71 on 2013-10-09
i know thats why i tryed using usb and also burned a dvd still it wont install ... it just restarts  system when i click install within windows 8

---

### Post by hakuna_matata on 2013-10-12
> **acepro71 said:**
> it just restarts  system when i click install within windows 8
If you can click on "install within windows 8" booting a Ubuntu-CD/DVD/USB, maybe there are 4 primary partitions. 4 is the maximum number of primary partitions with [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") partition table. You can change this with tools like [GParted ]("http://en.wikipedia.org/wiki/GParted"). Be careful, deleting a partition deletes your data on this partition, too. "install within windows 8" copies wubi.exe to windows autostart and then it reboots. But if your windows 8 uses MBR partition table and not [GPT]("http://en.wikipedia.org/wiki/Master_boot_record") and [UEFI]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface"), an installation with wubi is possible.

---

