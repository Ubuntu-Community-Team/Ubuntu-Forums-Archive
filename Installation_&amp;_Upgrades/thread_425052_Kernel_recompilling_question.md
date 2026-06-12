---
title: "Kernel recompilling question?"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by Ubimad on 2007-04-27
I have Toshiba A 100 Notebook Duo Core.
installed Feisty but the Canon scanner does not work. 
Backed a new 2.6.20 custom kernel fixing the scanner problem and the performance settings according to [this.]("http://ubuntuforums.org/showthread.php?t=56835")

Now my ATI X1400 card does not run in  3D and the wireless card not working anylonger, here I am stuck:

How I get the 3 d on the graphic card again and how to make the wireless card working again.
The performance has increased a lot with this kernel, would not like to miss it.


[COLOR="Red"]**lspci**[/COLOR]

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
[COLOR="Red"]01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400[/COLOR]
[COLOR="Red"]05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)[/COLOR]
07:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
07:06.3 Generic system peripheral [0805]: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)

---

### Post by NoUseForANick on 2007-04-27
Just a quick shot for your network:
I also installed a custom kernel today and had to symlink /lib/firmware/2.6.20-1-generic to 2.6.20-3-ubuntu1, so that the firmware files for my ipw2100 are found. Check the name of your symlink with `uname -r`. Good luck!

---

