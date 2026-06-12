---
title: "Need Guru help have tried everything to get 8.10 intrepid ubuntu sound to work"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Espryon on 2008-10-19
najix@Najix-Desktop-Project-Nemesis:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
najix@Najix-Desktop-Project-Nemesis:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Giga-byte Technology Device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fa104000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00007000-00008fff
	Memory behind bridge: fa000000-fa0fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at a800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ac00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fa105000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at c400 [size=16]
	I/O ports at c800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: medium devsel, IRQ 5
	Memory at fa106000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d000 [size=8]
	I/O ports at d400 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at e000 [size=16]
	I/O ports at e400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
	Subsystem: Giga-byte Technology Device 3448
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 6000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fa000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 7000 [size=8]
	I/O ports at 7400 [size=4]
	I/O ports at 7800 [size=8]
	I/O ports at 7c00 [size=4]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: ata_generic, pata_jmicron, pata_acpi

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at f9000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 9000 [size=256]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

najix@Najix-Desktop-Project-Nemesis:~$ 
__________________________________________________________________________

I Have tried everything on the forums but my sound still does not work , can someone offer some advice plz plz. I also have no pulse audio manager on my computer thats also weird.It worked when i first installed from my live disk the 8.9 intrepid, now it doesnt. Also the blacklist mod for the pulse audio is in the blacklist file too it makes no sense. 

:-({|=

Also the only thing that does work is the boot up sound and the desktop rdy sound i think thats only flash tho.

---

### Post by Bucky Ball on 2008-10-19
Have you tried putting a '#' before PulseAudio in the /modprobe.d/blacklist file to prevent it being blacklisted?

---

### Post by Espryon on 2008-10-19
> **Bucky Ball said:**
> Have you tried putting a '#' before PulseAudio in the /modprobe.d/blacklist file to prevent it being blacklisted?

no would that  work? hold on a sec ill try it

---

### Post by Espryon on 2008-10-19
heres the blacklist

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

---

### Post by Espryon on 2008-10-19
where should i put that btw? by pulse audio i ment the snd-pcsp because before i made this reinstall pulse audio was on it and i read a bug fix that had that listed to be blacklisted but it alrdy was and it was distinguished to be a pulseaudio file that caused audio problems

---

### Post by Bucky Ball on 2008-10-19
Looking at this page:

[https://bugs.launchpad.net/ubuntu/+bug/178504](https://bugs.launchpad.net/ubuntu/+bug/178504)

... and this search:

[https://bugs.launchpad.net/ubuntu/+bug/178504](https://bugs.launchpad.net/ubuntu/+bug/178504)

... seems your not the only one having problems with this card in Hardy. :(

If you have a speaker icon, double click it and check out there is nothing muted in there. Also check File->Change device and make sure your:
[B]
Intel Corporation 82801H (ICH8 Family) HD Audio Controller[/B]

is selected, or something like that and under Edit->Preferences, all the appropriate boxes are ticked.

---

### Post by Espryon on 2008-10-19
ive never really had audio problems tho till 8.10 its weird would you suggest pulling out an audio card and installing it ?? i have a couple in the other room

---

### Post by Bucky Ball on 2008-10-19
I suggest having a dig through some of the launchpad pages like the one in my last post and scrolling toward the bottom to see if anyone discovered a work-around or fix. And yea, it does seem to be only in the newer versions. :)

You could certainly try another card in there if you feel like it after that to see if the card is the culprit or it really is a software issue.

---

### Post by Espryon on 2008-10-19
> **Bucky Ball said:**
> I suggest having a dig through some of the launchpad pages like the one in my last post and scrolling toward the bottom to see if anyone discovered a work-around or fix. And yea, it does seem to be only in the newer versions. :)

You could certainly try another card in there if you feel like it after that to see if the card is the culprit or it really is a software issue.

im guessing a software problem because this is the first time ive had a problem with it in ubuntu everything else with ubuntu asfar as everything till now had worked extraordinaryly with no problems at all

---

### Post by Bucky Ball on 2008-10-19
Thinking a bit more about it I tend to agree. Reckon it is with Hardy and 8.10 for that card by the looks. There could be a work-around if you dig enough. On the other hand,  I am no expert and we could be overlooking something simple. :)

Are you dual booting with another OS and if so, does the sound work fine there? Anything you remember doing, updates or the like, that coincided with sound breaking?

---

### Post by Bucky Ball on 2008-10-19
Hey, I just came across this by complete accident. Might be of help:

[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)

---

### Post by Espryon on 2008-10-19
> **Bucky Ball said:**
> Thinking a bit more about it I tend to agree. Reckon it is with Hardy and 8.10 for that card by the looks. There could be a work-around if you dig enough. On the other hand,  I am no expert and we could be overlooking something simple. :)

Are you dual booting with another OS and if so, does the sound work fine there? Anything you remember doing, updates or the like, that coincided with sound breaking?

nope not dual booting just ubuntu

---

### Post by Espryon on 2008-10-19
heres a screnny 

[IMG]http://i295.photobucket.com/albums/mm124/Sevaix/something2.png[/IMG]

---

### Post by Bucky Ball on 2008-10-19
Check my last post .

---

### Post by Espryon on 2008-10-19
> **Bucky Ball said:**
> Check that my last post .

k

---

### Post by Espryon on 2008-10-19
should i do everything on that page?

also should i install the pulse audio manager stuff its not even installed btw which is kinda weird

---

### Post by Espryon on 2008-10-19
another screnny 




[IMG]http://i295.photobucket.com/albums/mm124/Sevaix/Screenshot.png[/IMG]

---

### Post by Bucky Ball on 2008-10-19
> **Espryon said:**
> should i do everything on that page?

also should i install the pulse audio manager stuff its not even installed btw which is kinda weird

? Odd, if that is what you were using before. Open a terminal and paste:
[B]
sudo apt-get install pulseaudio[/B]

and that should do it. Just before you do that, could you try:

**locate pulseaudio**

... to see if it is there already?

---

### Post by Espryon on 2008-10-19
> **Bucky Ball said:**
> ? Odd, if that is what you were using before. Open a terminal and paste:
[B]
sudo apt-get install pulseaudio[/B]

and that should do it. Just before you do that, could you try:

**locate pulseaudio**

... to see if it is there already?

LOL look at this

najix@Najix-Desktop-Project-Nemesis:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
najix@Najix-Desktop-Project-Nemesis:~$

---

### Post by directcharitycontribution on 2008-10-19
> **Espryon said:**
> najix@Najix-Desktop-Project-Nemesis:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
najix@Najix-Desktop-Project-Nemesis:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
	Subsystem: Giga-byte Technology Device 5000
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: intel-agp

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: f4000000-f7ffffff
	Prefetchable memory behind bridge: 00000000e0000000-00000000efffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at a000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at a400 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at fa104000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00004000-00004fff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00007000-00008fff
	Memory behind bridge: fa000000-fa0fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: f8000000-f9ffffff
	Prefetchable memory behind bridge: 0000000080000000-00000000800fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at a800 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at ac00 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Giga-byte Technology Device 5004
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at b000 [size=32]
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20)
	Subsystem: Giga-byte Technology Device 5006
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at fa105000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	I/O behind bridge: 00005000-00005fff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at b400 [size=8]
	I/O ports at b800 [size=4]
	I/O ports at bc00 [size=8]
	I/O ports at c000 [size=4]
	I/O ports at c400 [size=16]
	I/O ports at c800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
	Subsystem: Giga-byte Technology Device 5001
	Flags: medium devsel, IRQ 5
	Memory at fa106000 (32-bit, non-prefetchable) [size=256]
	I/O ports at 0500 [size=32]
	Kernel modules: i2c-i801

00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b002
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at d000 [size=8]
	I/O ports at d400 [size=4]
	I/O ports at d800 [size=8]
	I/O ports at dc00 [size=4]
	I/O ports at e000 [size=16]
	I/O ports at e400 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix
	Kernel modules: ata_generic, ata_piix, pata_acpi

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GTS (rev a1)
	Subsystem: Giga-byte Technology Device 3448
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	Memory at f4000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 6000 [size=128]
	[virtual] Expansion ROM at f7000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: nvidia
	Kernel modules: nvidia, nvidiafb

03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fa000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: ahci
	Kernel modules: ahci

03:00.1 IDE interface: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 85 [Master SecO PriO])
	Subsystem: Giga-byte Technology Device b000
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 7000 [size=8]
	I/O ports at 7400 [size=4]
	I/O ports at 7800 [size=8]
	I/O ports at 7c00 [size=4]
	I/O ports at 8000 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_jmicron
	Kernel modules: ata_generic, pata_jmicron, pata_acpi

04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
	Subsystem: Giga-byte Technology Device e000
	Flags: bus master, fast devsel, latency 0, IRQ 2299
	Memory at f9000000 (64-bit, non-prefetchable) [size=16K]
	I/O ports at 9000 [size=256]
	[virtual] Expansion ROM at 80000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: sky2
	Kernel modules: sky2

najix@Najix-Desktop-Project-Nemesis:~$ 
__________________________________________________________________________

I Have tried everything on the forums but my sound still does not work , can someone offer some advice plz plz. I also have no pulse audio manager on my computer thats also weird.It worked when i first installed from my live disk the 8.9 intrepid, now it doesnt. Also the blacklist mod for the pulse audio is in the blacklist file too it makes no sense. 

:-({|=

Also the only thing that does work is the boot up sound and the desktop rdy sound i think thats only flash tho.

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by Espryon on 2008-10-19
heres another paste

najix@Najix-Desktop-Project-Nemesis:~$ locate pulseaudio
/etc/default/pulseaudio
/etc/init.d/pulseaudio
/etc/rc1.d/K15pulseaudio
/etc/rc2.d/S25pulseaudio
/etc/rc3.d/S25pulseaudio
/etc/rc4.d/S25pulseaudio
/etc/rc5.d/S25pulseaudio
/etc/xdg/autostart/pulseaudio-module-xsmp.desktop
/usr/bin/pulseaudio
/usr/lib/pulseaudio
/usr/lib/pulseaudio/pulse
/usr/lib/pulseaudio/pulse/gconf-helper
/usr/share/doc/gstreamer0.10-pulseaudio
/usr/share/doc/pulseaudio
/usr/share/doc/pulseaudio-esound-compat
/usr/share/doc/pulseaudio-module-gconf
/usr/share/doc/pulseaudio-module-hal
/usr/share/doc/pulseaudio-module-x11
/usr/share/doc/pulseaudio-utils
/usr/share/doc/gstreamer0.10-pulseaudio/AUTHORS
/usr/share/doc/gstreamer0.10-pulseaudio/NEWS.gz
/usr/share/doc/gstreamer0.10-pulseaudio/README.Debian
/usr/share/doc/gstreamer0.10-pulseaudio/README.gz
/usr/share/doc/gstreamer0.10-pulseaudio/changelog.Debian.gz
/usr/share/doc/gstreamer0.10-pulseaudio/copyright
/usr/share/doc/pulseaudio/README
/usr/share/doc/pulseaudio/README.Debian
/usr/share/doc/pulseaudio/changelog.Debian.gz
/usr/share/doc/pulseaudio/copyright
/usr/share/doc/pulseaudio-esound-compat/README
/usr/share/doc/pulseaudio-esound-compat/changelog.Debian.gz
/usr/share/doc/pulseaudio-esound-compat/copyright
/usr/share/doc/pulseaudio-module-gconf/README
/usr/share/doc/pulseaudio-module-gconf/changelog.Debian.gz
/usr/share/doc/pulseaudio-module-gconf/copyright
/usr/share/doc/pulseaudio-module-hal/README
/usr/share/doc/pulseaudio-module-hal/changelog.Debian.gz
/usr/share/doc/pulseaudio-module-hal/copyright
/usr/share/doc/pulseaudio-module-x11/README
/usr/share/doc/pulseaudio-module-x11/changelog.Debian.gz
/usr/share/doc/pulseaudio-module-x11/copyright
/usr/share/doc/pulseaudio-utils/README
/usr/share/doc/pulseaudio-utils/changelog.Debian.gz
/usr/share/doc/pulseaudio-utils/copyright
/usr/share/lintian/overrides/pulseaudio
/usr/share/lintian/overrides/pulseaudio-esound-compat
/usr/share/lintian/overrides/pulseaudio-module-hal
/usr/share/lintian/overrides/pulseaudio-module-x11
/usr/share/lintian/overrides/pulseaudio-utils
/usr/share/man/man1/pulseaudio.1.gz
/var/lib/dpkg/info/gstreamer0.10-pulseaudio.list
/var/lib/dpkg/info/gstreamer0.10-pulseaudio.md5sums
/var/lib/dpkg/info/pulseaudio-esound-compat.list
/var/lib/dpkg/info/pulseaudio-esound-compat.md5sums
/var/lib/dpkg/info/pulseaudio-module-gconf.list
/var/lib/dpkg/info/pulseaudio-module-gconf.md5sums
/var/lib/dpkg/info/pulseaudio-module-hal.list
/var/lib/dpkg/info/pulseaudio-module-hal.md5sums
/var/lib/dpkg/info/pulseaudio-module-x11.conffiles
/var/lib/dpkg/info/pulseaudio-module-x11.list
/var/lib/dpkg/info/pulseaudio-module-x11.md5sums
/var/lib/dpkg/info/pulseaudio-utils.list
/var/lib/dpkg/info/pulseaudio-utils.md5sums
/var/lib/dpkg/info/pulseaudio.conffiles
/var/lib/dpkg/info/pulseaudio.list
/var/lib/dpkg/info/pulseaudio.md5sums
/var/lib/dpkg/info/pulseaudio.postinst
/var/lib/dpkg/info/pulseaudio.postrm
/var/lib/dpkg/info/pulseaudio.prerm

---

### Post by Espryon on 2008-10-19
> **directcharitycontribution said:**
> [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

i tryed the [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965) fixes gonna restart and see if this worked

---

### Post by Bucky Ball on 2008-10-19
> **Espryon said:**
> 
najix@Najix-Desktop-Project-Nemesis:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
najix@Najix-Desktop-Project-Nemesis:~$

I kinda half expected that. Hmm. Maybe the link in the previous post could give you some joy.

---

### Post by Espryon on 2008-10-19
i think intel should be banned from making soundcards

---

### Post by Espryon on 2008-10-19
Thanks for the help guys im going to wait till the fix on the 30th till then im going back to hardy then direct upgrading when the final release comes out. I love intrepid and i have until 8.10 when my sound bugged out with hope it will be fixed and good luck to the programmers and developers i have always loved ubuntu (:

---

