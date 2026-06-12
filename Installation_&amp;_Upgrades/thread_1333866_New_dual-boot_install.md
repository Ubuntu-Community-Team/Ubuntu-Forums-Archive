---
title: "New dual-boot install"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by Nistenf on 2009-11-21
I've got a new HDD (1 TB, SATA) so I'm going to reinstall everything. My other two drives:
80 GB IDE (Primary master), here I will install Ubuntu.
320 GB SATA, here I will install Windows XP.
The new one will be used for storage.

So first I will install Windows on the 320 SATA disk. Then Ubuntu on the 80 IDE. The question is, as the 80gb disk is the "first drive" (it's the C drive in my current installation of Windows), will the Windows installer write something to it? If it does the Ubuntu installer will erase it, but it won't be needed because of GRUB?

---

### Post by presence1960 on 2009-11-21
> **Nistenf said:**
> I've got a new HDD (1 TB, SATA) so I'm going to reinstall everything. My other two drives:
80 GB IDE (Primary master), here I will install Ubuntu.
320 GB SATA, here I will install Windows XP.
The new one will be used for storage.

So first I will install Windows on the 320 SATA disk. Then Ubuntu on the 80 IDE. **The question is, as the 80gb disk is the "first drive" (it's the C drive in my current installation of Windows), will the Windows installer write something to it? **If it does the Ubuntu installer will erase it, but it won't be needed because of GRUB?
Windows will write it's bootloader to MBR of whichever is the first hard disk to boot. I would prefer to keep windows bootloader on it's own disk when Windows & Linux are installed to separate disks. What you want to do is when installing Windows set the 320 GB SATA as first in BIOS in the hard disk boot order. After windows is installed make sure it boots properly and then switch the 80 GB IDE back to first hard disk to boot in BIOS. Install Ubuntu onto the 80 GB disk. When you boot GRUB will take over since GRUB will be on MBR of the first disk to boot (80 GB IDE)

---

### Post by Nistenf on 2009-11-21
Nice, thank you very much, I'll start installing as soon as I finish transfering files to my new drive.

---

### Post by Nistenf on 2009-11-22
I have a problem. I am trying to install Windows, but when I tell the installer to install in the 320 drive, it asks for a "Windows compatible partition" in my 80 drive, the one I will install Ubuntu to. Is there anything I can do to make Windows install completely on the 320 drive? Or should I just let it install the bootloader in the 80 drive?

---

### Post by lindsay7 on 2009-11-22
I think I would disconnect the other two drives and install windows where you want it.  After the install connect the other two drives and let windows find them.  Then install Ubuntu where you want it and let Ubuntu install the grub file where it wants to.

---

### Post by presence1960 on 2009-11-22
> **lindsay7 said:**
> I think I would disconnect the other two drives and install windows where you want it.  After the install connect the other two drives and let windows find them.  Then install Ubuntu where you want it and let Ubuntu install the grub file where it wants to.

you can do as lindsay suggests or your BIOS should have a setting to set the order of hard disk booting. Set the disk you want to install windows onto as first in the order of hard disk booting.

---

