---
title: "booting failure from USB stick"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by sam622 on 2020-05-30
on an old laptop I formated my hard drive with windows Vista installation disk (to eliminate it completely), then I tried to install Ubuntu 18.04 LTS with an iso on USB stick but it failed and I only have this message "BOOTMGR is missing" ? what's going wrong? any one has an idea?

---

### Post by oldfred on 2020-05-30
Bootmgr is the Windows boot loader.
It seems you did not install grub2's boot loader to MBR assuming Vista based system is BIOS/MBR.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sam622 on 2020-05-30
in fact, the problem was that usb port wasn't working properly. I changed to another port and I could install ubuntu, however wifi still not working like when I was in dual boot ubunt/windows, removing completely windows didn't solve my problem!

---

### Post by CelticWarrior on 2020-05-31
> **sam622 said:**
> (...) however wifi still not working like when I was in dual boot ubunt/windows, removing completely windows didn't solve my problem!

Why would removing Windows solve anything of that sort?

Please open a new thread for that specific problem at Networking & Wireless. Please provide the info as mentioned in the sticky thread: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

