---
title: "Ubuntu mini iso"
date: 2019-07-27
forum: Installation &amp; Upgrades
---

### Post by prabuhari on 2019-07-27
I installed Ubuntu 18.04 LTS mini iso on my sd card. It's working fine, when it's inserted in my system. Once removed sd card and re insert. System not detect sd card. It's telling no boot device found. Kindly help me to solve this issue

---

### Post by Bashing-om on 2019-07-27
prabuhari; Hello - Welcome to the forum.

Please describe the procedure you do: "Once removed sd card and re insert". I hate to assume but - cleanly UN-Mounting and safely ejecting ?

Else one can have a corrupted file system if not cleanly removed from the system.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by tea for one on 2019-07-27
> **prabuhari said:**
> I installed Ubuntu 18.04 LTS mini iso on my sd card. It's working fine, when it's inserted in my system. Once removed sd card and re insert. System not detect sd card. It's telling no boot device found. Kindly help me to solve this issue

I assume that the OS and grub is installed on the SD card.

Some desktop/laptops have a bios/uefi set up screen which is designed to help with booting external devices. The manufacturers control the appearance and facilities of these embedded systems.
Regrettably, no two are alike and it is a matter of careful trial and error with the settings. I do not suspect that your difficulty is an Ubuntu problem.

I have seen this lack of detection on various PCs and I have found that, if I leave the SD card or USB device in the port, and boot once or twice into the OS on the internal drive, the set up screen somehow detects the external device and then presents itself as a booting option.

This lack of boot consistency remains a mystery to me.

---

