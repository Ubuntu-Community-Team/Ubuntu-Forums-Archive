---
title: "installing Marvel 8053 Gigabit LAN driver having problem"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by leonyeo on 2007-01-22
Trying to install ubuntu, but after installation was not able to connect up to internet. Using Gigabyte Mother board GA-965G-DS3. It has a integrated Marvel 8053 Gigabit LAN Controller.

The Hardware listing

00:00.0 Host bridge: Intel Corporation Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation SATA Controller 1 IDE (rev 02)
00:1f.3 SMBus: Intel Corporation SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation SATA Controller 2 IDE (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0392 (rev a1)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Unknown device 4364 (rev 12)
05:00.0 Communication controller: Rockwell International HSF 56k Data/Fax/Voice Modem (rev 01)

I have also gone to the marvell site to download a driver

install-8_4.1.tar.bz2

after unzip it and try to install it gave me an error

stating there is some error so was not able to complete the installation process.

/install.sh: 71: Syntax error: "(" unexpected

Any idea on that. Any idea what i need to change or other driver i could used.

---

### Post by Skrying on 2007-01-22
I'm sharing the same issue as you are. Exact same. I've tried tons of the driver releases from the one included with my motherboard disk, to ones online, etc. All run into the exact same issue. I've followed steps listed in others places and still no luck.

BTW: Using the same exact motherboard.

---

### Post by bingoUV on 2007-01-27
Can you post this install.sh file here? Which shell are you using? Post the output of the following command :
echo $SHELL

thanks
Bingo

---

### Post by seravitae on 2007-01-27
there is another thread discussing issues with marvell gigabit ethernet and the same motherboard, as i have it too. you should read the thread on this same page that i just posted on. there are packages there you might want to try out.

---

### Post by SuperMau on 2007-01-29
In Edgy, you want to try this command instead\\:D/  : 

$sudo bash ./install.sh

Download Driver: Download (using another OS) the sk98lin source from [syskonnect]("http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=10013&term=typ.treiber+bs.Linux+produkt.SK-9E21D&produkt=produkt.SK-9E21D&typ=typ.treiber&system=bs.Linux") website

Greetings
SuperMau

---

### Post by Hordro on 2007-03-17
> **SuperMau said:**
> In Edgy, you want to try this command instead\\:D/  : 

$sudo bash ./install.sh

Download Driver: Download (using another OS) the sk98lin source from [syskonnect]("http://www.skd.de/e_en/support/driver_searchresults.html?navanchor=10013&term=typ.treiber+bs.Linux+produkt.SK-9E21D&produkt=produkt.SK-9E21D&typ=typ.treiber&system=bs.Linux") website

Greetings
SuperMau

Great!! this worked for me in Edgy  \\:D/ , thanks!!!!

PD: Gigabyte 965P DS4 (rev. 3.3)

---

### Post by LowRadio on 2007-04-06
The sk98lin drivers seem to work fine (as did upgrading the kernel to 2.6.19+) but I seem to have another problem witch I believe is hardware related.

For some reason when I first enable the onboard marvell 8053  I get great speeds but within moments the transfer rates start to drop to a crawl even at 1000mbit, when connected at 100mb it does take longer to slow down but does eventually crash to a halt under heavy use, then takes the rest of my system down with it.

I've tried different cables, routers, switches, kernel versions, drivers  same results, only thing I can think of is either its a driver issue which I don't think it is since no one else seems to have the same problem or its a hardware defect, overheating and whatnot...

Anyway without going into too much detail, has anyone else experienced these same issues with your setup?

---

