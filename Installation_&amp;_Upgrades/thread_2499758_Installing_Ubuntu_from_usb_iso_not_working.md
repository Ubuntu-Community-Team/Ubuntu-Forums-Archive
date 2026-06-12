---
title: "Installing Ubuntu from usb iso not working"
date: 2024-08-09
forum: Installation &amp; Upgrades
---

### Post by ash1621 on 2024-08-09
When I select the boot option in the boot menu, nothing happens, and I am still presented with the boot menu.

I am trying to install from an ISO from a USB with NTFS file formatting. I understand FAT32 is the default, but ubuntu ISO's these days are too big to store on FAT32.

[IMG]https://cdn.discordapp.com/attachments/435148149263433751/1271501046119923833/image.png?ex=66b79120&is=66b63fa0&hm=9f261d802dca848b504b3e82a3ab266e5e67ff4da8975e191581330c840e4684&=[/IMG]



Here are the relevant options I could find on the BIOS setup. Secure boot looks disabled, but i can't find a legacy boot option anywhere which i've seen references to in other sources.

[IMG]https://cdn.discordapp.com/attachments/435148149263433751/1271506820287955005/security-boot.jpg?ex=66b79681&is=66b64501&hm=d5ff2d6bde9ccaaf5ce7bd194ede36aea5c326a26d90c3728ca25e3dc1ba3583&=[/IMG]
[IMG]https://cdn.discordapp.com/attachments/435148149263433751/1271506820573171783/boot.jpg?ex=66b79681&is=66b64501&hm=2fcd85a87b4f02e093cb87178f6409e8c2241b837a8f49ef46226a327f904aff&=[/IMG]



And here are my specs (from [https://www.pcspecialist.co.uk/):](https://www.pcspecialist.co.uk/):)
[CENTER][COLOR=#000000][FONT=&amp][RIGHT][FONT=Montserrat-Medium]Chassis & Display[/FONT][/RIGHT]
[LEFT]Gemini Series: Aluminium Chassis: 14.1" Full HD IPS LED (1920 x 1080)[/LEFT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][RIGHT][FONT=Montserrat-Medium]Processor (CPU)[/FONT][/RIGHT]
[LEFT]Intel® Celeron® Quad Core Processor N4120 (1.10GHz, 2.60GHz Turbo)[/LEFT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][RIGHT][FONT=Montserrat-Medium]Memory (RAM)[/FONT][/RIGHT]
[LEFT]4GB LPDDR4 2133MHz LOW PROFILE SOLDERED[/LEFT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][RIGHT][FONT=Montserrat-Medium]Graphics Card[/FONT][/RIGHT]
[LEFT]INTEL® HD GRAPHICS (CPU Dependant) - 1.7GB Max DDR4 Video RAM - DirectX® 12[/LEFT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][RIGHT][FONT=Montserrat-Medium]1[SUP]st[/SUP] M.2 SSD Drive[/FONT][/RIGHT]
[LEFT]1TB WD BLUE SA510 SATA SSD M.2 (560 MB/R, 520 MB/W)[/LEFT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp][RIGHT][FONT=Montserrat-Medium]Memory Card Reader[/FONT][/RIGHT]
[LEFT]Integrated Micro-SD Memory Card Reader

[/LEFT]
[/FONT][/COLOR][/CENTER]

Can anyone notice anything that may cause the booting issues?

Any suggestions highly appreciated. O:)

---

### Post by currentshaft on 2024-08-09
be

---

### Post by oldfred on 2024-08-09
UEFI only boots from ESP - efi system partition which must be FAT32.

[https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-ubuntu#1-overview) & 
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#1-overview) & 
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)

---

### Post by ash1621 on 2024-08-09
oh, so it's impossible to boot Ubuntu 24.04 from .iso now? Max file size FAT32 can take is 4GB, but latest Ubuntu LTS is 6GB.

---

### Post by ash1621 on 2024-08-09
Oops, it looks like I missed a step, thanks for spotting that, I will try it with balenaEtcher as suggested on ubuntu.com

---

### Post by tea for one on 2024-08-09
> **ash1621 said:**
> Any suggestions highly appreciated. O:)
Secure Boot Mode states Customized - Can you not disable it?
> Intel® Celeron® Quad Core Processor N4120
Xubuntu 24.04 would be more suitable for this processor

---

### Post by yancek on 2024-08-09
If you have a Linux OS installed using Grub2 it is simple to boot the Ubuntu (or other Linux) iso file.  It does not matter if the partition filesystem is a Linux fs or ntfs because you will be using iso9660 as the filesystem but you have not indicated what you are using to boot or how you put the iso on whatever partition you are using.

---

