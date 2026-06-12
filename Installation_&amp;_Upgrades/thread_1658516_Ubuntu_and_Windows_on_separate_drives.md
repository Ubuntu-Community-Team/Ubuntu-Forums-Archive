---
title: "Ubuntu and Windows on separate drives"
date: 2011-01-02
forum: Installation &amp; Upgrades
---

### Post by bill_heckler on 2011-01-02
I installed Ubuntu 10.10 second with Windows 7 Home already on the machine.  Now Windows will boot fine if I point the BIOS to that drive, but when I point BIOS at the drive with Ubuntu on it, nothing.  I never get GRUb and I never get the option to boot into Ubuntu 10.10.

:confused:

---

### Post by MichaelGld on 2011-01-02
> **bill_heckler said:**
> I installed Ubuntu 10.10 second with Windows 7 Home already on the machine.  Now Windows will boot fine if I point the BIOS to that drive, but when I point BIOS at the drive with Ubuntu on it, nothing.  I never get GRUb and I never get the option to boot into Ubuntu 10.10.

:confused:

How are you telling the BIOS to boot to the Linux drive? Did you actually change the boot order?

---

### Post by bill_heckler on 2011-01-02
Yes, I manually redirect BIOS to a different drive.  That is the way I have installed every operating system I have ever installed.

:confused:

---

### Post by DasEi on 2011-01-02
You need a live cd then and repair the bootloader of the ubu-disk.
once it is running again, install and run os-prober to get the win7 partition
added to grub, too. You then choose from grubmenu,no more friggling around.
For additional guidance, call back here so we can meet on irc.

DasEi

---

### Post by wilee-nilee on 2011-01-02
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

If we use the script we wont be guessing.:)

---

