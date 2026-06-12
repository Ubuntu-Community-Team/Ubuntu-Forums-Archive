---
title: "Can't get Windows 8.1 to boot again (Ubuntu 14.04)"
date: 2014-09-23
forum: Installation &amp; Upgrades
---

### Post by marco63 on 2014-09-23
This is the second time I'm typing out my problem, as this forum erased it when I tried to preview my message.[I] As if using the Ubuntu operating system wasn't frustrating enough.

[/I]Anyway, I'm having a huge problem because I cannot boot Windows 8.1 from Grub no matter what I do. I've typed every single command line into terminal that I've seen, I've edited 40_custom (and yes I ran sudo update-grub), I ran boot-repair... 

Here is my pastebin: [http://paste2.org/553mWkjO](http://paste2.org/553mWkjO)

Everytime I try to click my Windows 8 option on grub, I get "[COLOR=#000000][FONT=verdana]error: file efi/microsoft/boot/bootmgfw.efi not found "

[/FONT][/COLOR]:mad:

---

### Post by ajgreeny on 2014-09-23
I am afraid that you have no Windows OS partitions on your computer; you seem to have wiped it when you installed Ubuntu, so I hope you have either the Win8 installation DVD, or that you made your own Win8 Restore DVDs when you first got the machine, as at the moment, it is all gone.

How did you do the installation of Ubuntu, as there are a number of errors showing in your boot-info-report.  Grub is shown in the MBR of sda which is not correct for an UEFI installation, so I suspect that you started wrongly by installing Ubuntu as if for a legacy BIOS system.  This may also explain why Windows has gone, though it is a long time since I had Windows to worry about so I'm not sure that is relevant.

The reason that your 40_custom file does not help is that there is no Windows to chainload to, so even though Windows appears in the grub menu from this 40_custom file you don't have any Windows bootloader files remaining.

---

