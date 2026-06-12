---
title: "Booting won't recognize XP"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by PoisonedV on 2008-02-14
I installed Ubuntu Gutsy Gibbon, alongside windows XP. Afterwords I went into the OS choice menu and looked at the choices, but XP was not on there. The partition is still there, however. How can I get the BIOS to recognize Windows as an operating system?

---

### Post by Pumalite on 2008-02-14
Do you see the Grub menu?

---

### Post by oilchangeguy on 2008-02-14
> **PoisonedV said:**
> I installed Ubuntu Gutsy Gibbon, alongside windows XP. Afterwords I went into the OS choice menu and looked at the choices, but XP was not on there. The partition is still there, however. How can I get the BIOS to recognize Windows as an operating system?

uh, the bios has nothig to do with this. you'll probably need to edit your grub menu, to include windows.

---

### Post by PoisonedV on 2008-02-15
I added Windows XP to the boot menu and it gets to the XP loading screen but restarts. I don't think there is any way to fix it, oh well. I have to find some way to backup my files, though

---

### Post by Pumalite on 2008-02-15
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

