---
title: "Trouble booting with SATA drive connected"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by darrentrials on 2007-05-15
After making the switch from Windows to ubuntu last night, and it going a bit rough, i have managed to get 3 of my 4 hard drives working. But I can not get my 4th drive to connect and the machine to boot with it connected.

You will have to be gentle as this is my first install of Linux. 

When you try and boot with the Sata(160GB Seagate) It displays the following message.

Starting Grub Stage1.5
Grub

Unplug the drive and will boot fine.  Any advice? or more information needed?

Thanks in advance, Darren.

---

### Post by markoloka on 2007-05-15
Do you have something like jmicron connector?

---

### Post by darrentrials on 2007-05-15
No i dont have a jmicron connector.

If it helps i have a Gigabyte GA-7VT600 1394 Mainboard

---

### Post by bulldog on 2007-05-15
Can you tell a bit more about your hdd configuration,things like how many IDE and Sata or only Sata,do you have native Sata on the MB or do you use a PCI card and so on.

Further could it be interesting to know what's on the Sata hdd,is it a data hdd or did you install any OS on it.

---

### Post by darrentrials on 2007-05-15
The hard drive is just a data drive, SATA is built onto the mobo. I also have 2 USB drives(working but read only as NTFS) and my install drive is IDE.

I originally had the SATA as my windows install, but formatted that and tried to put ubuntu on it. This wouldnt boot at all and after a little test found it worked from an old IDE drive. Reloaded windws on my spare old IDE drive and then formatted the SATA drive in NTFS(windows is gay). copied all the information between drives and now stuck here with 160gig of stuff i cant see. Other then that ubuntu is just what i want!

---

### Post by Crazy_Monkey on 2007-05-15
Does the controller happen to be a Sil 3114 or something like that?

I've found that I have to disable that controller or Grub won't even work.

I **REALLY** wish Grub would enter the modern world and not be such a PITA to configure!!

---

### Post by bulldog on 2007-05-15
> **darrentrials said:**
> The hard drive is just a data drive, SATA is built onto the mobo. I also have 2 USB drives(working but read only as NTFS) and my install drive is IDE.

I originally had the SATA as my windows install, but formatted that and tried to put ubuntu on it. This wouldnt boot at all and after a little test found it worked from an old IDE drive. Reloaded windws on my spare old IDE drive and then formatted the SATA drive in NTFS(windows is gay). copied all the information between drives and now stuck here with 160gig of stuff i cant see. Other then that ubuntu is just what i want!

You have to understand Sata is the same for GRUB as the USB devices.
If you put another hdd to your motherboard,your menu.lst isn't correct anymore.

Example:
IDE = hd0
USB =hd1
USB =hd2

Now you put another Sata to the motherboard,
IDE = hd0
Sata=hd1
USB =hd2
USB =hd3

You can perfectly install Ubuntu on the Sata disk or the IDE disk,it's all a matter of configuration.
GRUB will be installed on hd0 by default which is in most cases the IDE hdd.
You can change this manually when grub is installed,or change it later if this benefits you.

---

