---
title: "New system Core 2 Quad, Intel P35, 8800GT"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by stchman on 2008-03-12
Hello all, I am planning on building a new rig with the following hardware:

- GIGABYTE GA-P35-DS3L LGA 775 Intel P35 ATX All Solid Capacitor Intel
- MSI NX8800GT 512M OC GeForce 8800GT 512MB 256-bit GDDR3 PCI Express 2.0
- Intel Core 2 Quad Q6600 Kentsfield 2.4GHz LGA 775 Quad-Core Processor
- mushkin 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) with EPP
- Seagate Barracuda 7200.10 ST3320620AS (Perpendicular Recording Technology) 320GB 7200 RPM SATA 3.0Gb/s Hard Drive - OEM

It looks as though Envy will install the drivers for the 8800GT card.

The Core 2 Quad should work just fine.

How about the P35 chipset motherboard?  Does Feisty or Gutsy support the chipset out of the box?  The mobo has the follwong specs:

1. Northbridge: Intel® P35 Express Chipset
2. Southbridge: Intel® ICH9
3. Gigabit Lan Controller
4. 8 Channels ALC888 Audio controller

I don't really care about the soundcard as I have an Audigy2 I plan to put in.  I really need everything else to work (i.e. NIC, chipset, SATA, etc).

Let me know your thoughts.

Thanks.

---

### Post by stchman on 2008-03-12
No one has any input?

---

### Post by Nighthawk71 on 2008-03-13
I plan to build a similar system.  

Here are the specs of the new box:
GIGABYTE GA-P35-DS3L LGA 775 Intel P35 chipset
Intel Core 2 Quad Q6600 Kentsfield 2.4GHz LGA 775 Quad-Core Processor
Crucial 4gb(4x1gb) DDR2 667 MHz memory
2 Western Digital 250gb 2500AAKS Hard Drives
Optiarc SATA DVD Burner
EVGA GeForce 7300 GT / 256MB GDDR2 / SLI Ready / PCI Express / DVI / VGA / TV Out / Video Card

I use vmware player to run sessions of Windows XP and Windows 2000 on this box so the 4gb ram becomes very useful.

My old box has been running very well for about a year without problems.  Its specs are:
Gigabyte GA-945P-S3 LGA 775 Intel 945P chipset
Intel Core 2 Duo E4400 2.0 GHz LGA 775 Dual Core Processor
Crucial 4gb(4x1gb) DDR2 667 MHz memory
2 Western Digital 160gb 1600AAKS Hard Drives
Optiarc SATA DVD Burner
MSI GeForce 7300 GS Video Card.

---

### Post by stchman on 2008-03-13
I changed the mobo to an Asus P5K as the Marvell gigabit NIC is more Linux friendly than the Realtek 8111B on the Gigabyte mobo.  The Asus mobo also has Firewire and another PCI-E x-16 slot.  It is about $35 more.

---

### Post by PmDematagoda on 2008-03-13
You would mostly have to wary of the 8800GT as I do not think you can get the VGA card to work simply using Envy and may have to resort to manual methods of installing the driver.

---

### Post by stchman on 2008-03-13
> **PmDematagoda said:**
> You would mostly have to wary of the 8800GT as I do not think you can get the VGA card to work simply using Envy and may have to resort to manual methods of installing the driver.

I have been reading about that.  Can I do this?

Nvidia has a Linux driver (169.12) on their website and these drivers support the 8800GT.  Can I use Envy to install the 169.12 driver manually?  If no, what is the procedure to install drivers for the 8800GT in Fesity or Gutsy.  There has to be an approved method.

Thanks.

---

### Post by Pumalite on 2008-03-13
I can tell you how to install a driver manually, but I'm stll not sure it'll work with 8800 card.
Do it from a Virtual Terminal:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linuxxxxxxxxx.run
Accept License
Let the driver compile the modules into your kernel
Let the driver reconfigure your xorg.conf file
Then:
sudo /etc/init.d/gdm start

---

### Post by stchman on 2008-03-13
> **Pumalite said:**
> I can tell you how to install a driver manually, but I'm stll not sure it'll work with 8800 card.
Do it from a Virtual Terminal:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linuxxxxxxxxx.run
Accept License
Let the driver compile the modules into your kernel
Let the driver reconfigure your xorg.conf file
Then:
sudo /etc/init.d/gdm start

According to Nvidia's site the 8800GT drivers for Linux are the 169.12.

I was reading Alberto Milone's site and he sayd you can do the manual installation and point to the proprietary driver you downloaded.

---

### Post by Pumalite on 2008-03-13
Good luck.

---

