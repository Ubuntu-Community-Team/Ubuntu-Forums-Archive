---
title: "where is grub installed?"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by xsxcn on 2010-07-16
[SIZE=4]I have one physical drive installed with windows xp. Now, I get another hard drive and I'm going to install ubuntu on it. I want to know where will be grub installed? my windows xp drive or the new drive?[/SIZE]

---

### Post by TechBeastie on 2010-07-16
That depends entirely on how you configure grub during the installation process.  By default, assuming that the 1st physical drive (the one with XP on it) is defined as the primary drive in the BIOS, GRUB will probably overwrite the bootcode in the MBR (very front) of the primary hard drive, and then install the 2nd stage of the bootloader in either your main linux partition or another partition of your choosing (if you decide to set up a dedicated /boot).  On the other hand, if you make the new hard drive your primary drive, GRUB will *probably* leave your old hard drive's MBR intact, and write new bootcode into the MBR of the new drive instead.  

The latter approach has the advantage of allowing your old hard drive to remain independently usable.  That is, should you ever need/want to boot from that old drive directly (without the help of grub), you should still be able to.

EDIT:
In case I haven't made it clear above (and I'm afraid I haven't), bootloaders operate in multiple stages.  The initial stage - the first code that the CPU pulls from any disk - is installed at the very front of the drive, in a region called the Master Boot Record (MBR).  That code in turn tells the CPU what partition to query for the next instructions it will need to boot the system (as well as how to read the filesystem on that partition) - which, in your case, is the location where most of the GRUB files are actually stored.

---

### Post by wilee-nilee on 2010-07-16
With the advanced button in the last window of the install, put grub in the mbr of the drive you install to, not a partition. If it's a internal HD make sure it shows up in the bios before installing anything

---

### Post by xsxcn on 2010-07-16
> **wilee-nilee said:**
> With the advanced button in the last window of the install, put grub in the mbr of the drive you install to, not a partition. If it's a internal HD make sure it shows up in the bios before installing anything

So there is an option for me to choose where to put grub, right?

---

### Post by confused57 on 2010-07-16
Here is an excellent guide by on forum member Herman's website for setting up a dual boot on 2 hard drives:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
He has illustrations showing the "Advanced" button & selecting where to install grub.  For example, if you're installing Ubuntu on /dev/sdb, then you'd select "/dev/sdb" to install grub.  Make sure NOT to select a partition, as in /dev/sdb1...this is important to remember.

---

### Post by wilee-nilee on 2010-07-16
> **xsxcn said:**
> So there is an option for me to choose where to put grub, right?

The grub bootloader yes, the other appropriate grub related files are in the OS like any operating system.

---

### Post by xsxcn on 2010-07-17
> **wilee-nilee said:**
> The grub bootloader yes, the other appropriate grub related files are in the OS like any operating system.

Thank you, I've done it!

---

