---
title: "boot loader question for new xubuntu installation"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by notgoingbackto_ms on 2013-12-06
Hello,
I just installed xubuntu in a separate partition on my c drive. Windows xp is in the first partition. Everything went successfull and I allowed the system to update its software. I rebooted the system, but GNU is all that the machine boots to, with no options to boot to xp or xubuntu. I did a FIXMBR to allow access back to XP. What would be the best method re-allow boot to xp or xubuntu?

---

### Post by oldfred on 2013-12-06
You only have one MBR, so you need to reinstall grub and update it to add the Windows entry. If XP now boots ok it should find XP and add it to your grub menu. Usually it finds Windows during install. If not you can run this after booting Ubuntu.

sudo update-grub

To reinstall grub to MBR, you need live installer. You can manually do it or use Boot-Repair.
       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by notgoingbackto_ms on 2013-12-06
Thanks. I used boot repair and everything is okay.

---

