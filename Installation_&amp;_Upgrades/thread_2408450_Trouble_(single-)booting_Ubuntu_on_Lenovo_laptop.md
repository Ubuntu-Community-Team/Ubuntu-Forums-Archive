---
title: "Trouble (single-)booting Ubuntu on Lenovo laptop"
date: 2018-12-18
forum: Installation &amp; Upgrades
---

### Post by lukerm on 2018-12-18
[FONT=Arial]Hi folks,[/FONT][FONT=Arial]
[/FONT]
[FONT=Arial]I first got into trouble when I tried to re-install Ubuntu 16.04 on my machine (Lenovo IdeaPad Z570). I was able to boot from USB, at which point I ran the fresh install, deleting my previous OS (also Ubuntu). When it finished and I rebooted, it would not get to GRUB. That's when my problems began.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]However, I was still able to boot from USB at that point. Naturally, I tried again and a few more times before realising this wasn't working.[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]I followed the advice on the page: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), in particular the section Install Ubuntu for Single Boot (Random Boot Mode). I went to the liveUSB boot, downloaded Boot Repair, ran it, and followed the commands there. It generated this code: W4WttC6NHd (pastebin).[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Unfortunately, that didn't work. In fact, it made the problem worse, as I now can't even boot from USB :( . When I try to do so, I get the error:[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]*Failed to open \EFI\BOOT\grubx64.efi - Not Found*[/FONT]
[FONT=Arial]*Failed to load image **\EFI\BOOT\grubx64.efi: Not Found*[/FONT]
[FONT=Arial]*start_image() returned Not Found*[/FONT]

[FONT=Arial]Do you have any advice on what to do next? Is this fixable?[/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]For your information, here's some info on BIOS:[/FONT]
[FONT=Arial]BIOS Version: 45CN36WW[/FONT]
[FONT=Arial]KBC Version: 45EC28WW[/FONT]
[FONT=Arial]Hard disk: WDC WD7500BPVT (750GB)
Pastebin code: W4WttC6NHd [/FONT]
[FONT=Arial]
[/FONT]
[FONT=Arial]Many thanks in advance for your help,
Luke[/FONT]

---

### Post by ubfan1 on 2018-12-18
The USB install media should have a /EFI/BOOT directory containing files BOOTx64.EFI and grubx64.efi.  If either is missing, the UEFI boot will fail -- but the legacy boot would not be affected.  Neverthless, it seems like your install media is not right.

---

### Post by lukerm on 2018-12-19
So it looks it's trying to boot in UEFI mode. Is there any easy way to make my laptop boot in legacy mode from the USB?

How can I get the /EFI/BOOT partition onto the USB if it won't boot?

---

### Post by ubfan1 on 2018-12-19
Booting mode of the USB is selected in the BIOS/UEFI Settings. Legacy before UEFI may be the Lenovo setting,  CSM or compatibility mode is the way other machines may enable legacy.
Rather than trying to fix the install media, I'd recreate it, using official ISOs.

---

