---
title: "The Great Battle: Ubuntu vs. Parental Controls"
date: 2011-06-04
forum: Installation &amp; Upgrades
---

### Post by Phillip Lober on 2011-06-04
I am running a Windows 7 machine with parental controls on them. My parents are skeptical against me downloading things, and I don't blame them.
 
Anyway, here's the main point: The parental controls block the ability to run .exe files, and the Ubuntu boot up is on a file with a .exe extension, so is there an alternate route I can take to install Ubuntu in dual boot that doesn't involve a .exe file?

---

### Post by tgm4883 on 2011-06-04
> **Phillip Lober said:**
> I am running a Windows 7 machine with parental controls on them. My parents are skeptical against me downloading things, and I don't blame them.
 
Anyway, here's the main point: The parental controls block the ability to run .exe files, and the Ubuntu boot up is on a file with a .exe extension, so is there an alternate route I can take to install Ubuntu in dual boot that doesn't involve a .exe file?

That would be wubi. You could download the ISO, burn to CD (or USB key) and do a proper dual boot (resizing partitions, installing grub, etc)

---

### Post by IWantFroyo on 2011-06-04
You don't have to use wubi.exe
Just download the normal Ubuntu file, and burn it to a disk (you'll have to already have a disc burner on your system).
Reboot, and go into setup (BIOS) to switch the boot order with CD first, save, and exit. Boot into the disc, and select it to install alongside Windows.

EDIT: Make a repair disc and backup of your Windows. If my memory doesn't fail me, you should find these settings somewhere in the Windows Control Panel.

---

### Post by uRock on 2011-06-04
I would definitely recommend getting permission before partitioning the machine. You may want to talk them into letting you install VirtualBox, then install Ubuntu within the VM.

---

