---
title: "Ubuntu 7.04 &amp; 7.10 64 bit on Lenovo Thinkpad r61"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by multiverse on 2007-08-29
Hi,

I'm trying to install Ubuntu onto my new R61, and the installation itself went well.  When I reboot for the first time, I get the grub screen, grub disappears and the screen goes black.  What should I do to proceed?  Here are the stats:

Ubuntu 7.04 & 7.10 64 bit on Lenovo Thinkpad r61

Intel Core 2 Duo T7300 (2.0GHz 800MHz 4MBL2)
Genuine Windows Vista Home Basic
15.4" WXGA
nVIDIA Quadro NVS 140M, PC Card/ PCIe
4 GB PC2-5300 DDR2 SDRAM 667MHz SODIMM Memory (2 DIMM)
100GB Hard Disk Drive, 7200rpm
CD-RW/DVD-ROM Combo 24x/24x/24x/8x Max. Ultrabay Enhanced
ThinkPad 11a/b/g Wi-Fi wireless LAN Mini-PCIe US/EMEA/LA/ANZ

---

### Post by multiverse on 2007-08-29
Here are the last messages that I see on my system before the LCD goes off:

1)

GRUB Loading stage1.5

GRUB loading, please wait
Press 'ESC' to enter the menu... <countdown>

2)

Kernel alive
Kernel direct mapping tables up to 140000000 @ 8000-e00

3)

[ 11.332898] PCI: Failed to allocate mem resource #6:20000@f0000000 for 0000:0
1:00.0

Then the LCD goes off.

---

### Post by multiverse on 2007-08-30
The issue is that the these distros don't have the required packages available at install time.  The work around is to add **[COLOR="Blue"]vga=792[/COLOR]** to the kernel line at the GRUB boot screen.  To access the screen you hit ESC when you see the GRUB loading message, and use the GRUB commands to edit that line and boot into VGA 800x1024 mode.

Check here for details on how to deal with the R61 now that you can see your console:  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_on_a_ThinkPad_R61](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_%28Gutsy_Gibbon%29_Tribe_on_a_ThinkPad_R61)

---

