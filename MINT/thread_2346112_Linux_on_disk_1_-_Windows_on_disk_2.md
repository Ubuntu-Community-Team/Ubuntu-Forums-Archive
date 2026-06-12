---
title: "Linux on disk 1 - Windows on disk 2"
date: 2016-12-11
forum: MINT
---

### Post by wcdba132 on 2016-12-11
Totally separate installations.  Both, installed with single disk connected at install time.  They both boot on its own.

I want to use grub2 to dual boot.  I am not a novice but this grub2 area seems to be unclear to me for some reason.

What steps would I do to get dual boot setup (with grub2).  Please be specific as possible.

---

### Post by ajgreeny on 2016-12-11
BIOS or UEFI?

Exactly how you proceed will depend upon the answer to this.

---

### Post by wcdba132 on 2016-12-11
Linux Mint 17

---

### Post by coffeecat on 2016-12-11
> **wcdba132 said:**
> Linux Mint 17

*Thread moved to the **MINT** sub-forum.*

If that was meant to be an answer to ajgreeny's question, it isn't. You were being asked whether you have a legacy BIOS or UEFI system.

---

### Post by oldfred on 2016-12-11
Only if both installed in UEFI boot mode or both in BIOS boot mode.

sudo update-grub

---

### Post by wcdba132 on 2016-12-13
Bios

---

### Post by ajgreeny on 2016-12-14
I presume that grub is therefore on the disk where Ubuntu is installed and the Windows bootloader is on the disk with Windows on it; this is the ideal way in my opinion, when using a BIOS machine with two disks.

If I am correct, boot to Ubuntu and run the command **oldfred** showed ```
sudo update-grub
``` and it should add Windows to the grub menu.

If you now set the Ubuntu disk as first boot priority you should get the option to boot either OS from grub; if the Windows disk is first boot priority the computer should boot direct into Windows without seeing grub and with no option to boot Ubuntu.

---

