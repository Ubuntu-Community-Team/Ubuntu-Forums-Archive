---
title: "Asus motherboard bios error"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by jhoke on 2006-10-18
Hi,
I just bought a computer from Cool Tech PC, Inc in Vancouver, WA (endpcnoise.com). I ordered it without Windows installed since I plan to run Ubuntu on it. They did a 48 hour burn-in with Windows and then wiped the disk and declared the computer ready. When, when I try to run Ubuntu live/install 6.06.1 LTS the first error message I get is

   	"Detect drives done: not any drive found".

Then the "Start or Install Ubuntu" screen comes up and when I click this I get the following BIOS error message:
	
	MP-BIOS bug: 8254 timer not connected to IO_APIC
	Kernal Panic - not syncing: IO-APIC + timer doesn't work!
	Boot with apic=debug and send a report. Then try booting with the      "noapic" option.

I was able to format the drive using a GParted Live CD so it found the HD OK and the problem appears to be strictly in the bios setup for the motherboard.  Here is a summary of the system - motherboard et al:

	
Asus M2N-SLI Deluxe Motherboard
AMD Athlon 64 AM2 X2 Dual Core 3800 CPU
2GB ( two 1GB ) PC-5300 Kingston memory
56K V.92 PCI Hardware modem
Microsoft BLACK Keyboard/Mouse Combo
Samsung Quiet 160GB SATA2 HDD HD160JJ
No Operating System
Nexus 500W NX5000 Power Supply
MSI NX6200TC 256MB PCIE (Fanless)
Antec P180 BLACK Case
Plextor (Beige or Black) PX-760A DVDRW
Zalman CNPS9500AM2 CPU Cooler

Anyone have any experience with this motherboard?
Any help you can offer will be greatly appreciated.

Jack Hoke

---

### Post by encompass on 2006-10-18
did you "try booting with the 'noapci' option"
I double checked... this is how you do it...
when the countdown starts... youhave 3 seconds to press escap and see you boot options...
press escape then press e then down then e to edit the boot like... it is the longest one... it will take you to the end of that line... add the option...
noapci
at the end.
press enter then b to boot that line... did it get any further?

---

### Post by jhoke on 2006-10-19
I took the system back to the shop. They said the Live CD doesn't have the noapic option which is why I kept geting the 'Could not find kernal image: noapic' message whe I tried the noapic option. Turns out they install using the non-graphics iso. There may be more to it than that. Anyway the promised to get me going. Thanks for the help!

jhoke

---

### Post by boxarocks on 2006-11-09
I have the same motherbboard and a similar AMD64 dual core CPU. The current BIOS on the board was 307, the beta version is 601.

I found a link to the beta BIOS on the ASUS forums for the M2N-SLI Deluxe motherboard with the n570 chipset:

[http://vip.asus.com/forum/view.aspx?id=20061102231726172&board_id=1&model=M2N-SLI+Deluxe&page=1&SLanguage=en-us]("http://vip.asus.com/forum/view.aspx?id=20061102231726172&board_id=1&model=M2N-SLI+Deluxe&page=1&SLanguage=en-us")

Once I installed a floppy disk drive, I was able to update the BIOS from a floppy disk using EZ Flash 2. (I couldn't get EZ Flash 2 to recognize my USB flash drive, so I went the floppy route.)

Then it was on to installing Edgy! I'm still updating the machine, but this BIOS update did the trick for me.

---

### Post by encompass on 2006-11-23
A recent bios update fixed my system.  It would boot either.  But now it works great.  It had the seporate bridge from the main one and that was where the problem was.

---

