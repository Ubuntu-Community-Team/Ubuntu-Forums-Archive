---
title: "No sound afteer upgrage to 8.10"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Zanian on 2008-10-31
Hey,
My sound was working fine until I upgraded today to 8.10.  I'm not really sure what the issue is.  I have made sure that the right sound card is set as default.  Sound isn't working for anything.

---

### Post by Zanian on 2008-10-31
bump

---

### Post by martrn on 2008-10-31
Upgrading to early hardy versions had this particular problem quiet a lot.  There was a lot more of it.

The official sound trouble shooting page is at :
[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

You need to open a shell and type :
lspci -v
aplay -l
This should give you a list of devices attached to your system, and then give you a list of hardware playback devices your system has recognised as sound hardware.

If you have got this far check using the terminal the alsamixer settings by typeing:
```
alsamixer
```

Whithout knowing the results of the above, not much more I could say.

I hope you get it working soon.

---

### Post by Dumdideldum on 2008-10-31
Try Start-> System -> Preferences -> Audio and select pulseaudio for playback - worked for me.

---

### Post by Zanian on 2008-10-31
Hey, thanks for replying.  I got as far as alsamixer and then, i get this when i enter it in the shell:
Card: PulseAudio                                                                                                                                          &#9474;
&#9474; Chip: PulseAudio                                                                                                                                          &#9474;
&#9474; View: [Playback] Capture  All                                                                                                                             &#9474;
&#9474; Item: Master

I don't know exactly what that means, but I think it's trying to use Pulseaudio, which is not what want?  I've done a whole bunch of the troubleshootings but nothing seemed to work for me so I came here.  Sorry I'm rather new to Ubuntu, thanks for your patience.

---

### Post by Lakelander on 2008-10-31
After killing Pulseaudio process and increasing speaker volume from Volume Control (upgrade process was set it to zero!?!) sounds work fine for me.

---

### Post by martrn on 2008-10-31
I don't know about pulse audio my sound card drivers use alsa (Advanced Linux Sound Architecture), kernel modules (drivers) and not pulse audio kernel modules (drivers) which are effectively alternatives to each other.  Look what is your sound card I still don't know ?

If you wish to know about ALSA kernel modules (drivers) You need to :
Select SystemSetting-->SoundSystem-->Hardware
and choose <Advanced Linux Sound Architecture>

then open a shell and type :
```
lspci -v
aplay -l
```
and post the contents of that here.  This should give you a list of devices attached to your system, and then give you a list of hardware playback devices your system has recognised as sound hardware.

See [https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") and start from ****Start here if you have no idea why sound is not playing**** and work through that.  Its kind of important to know your sound card (chipset) manufacturer (see above), before you know why sound can not work.

---

### Post by Zanian on 2008-10-31
Sorry, I thought that was just a preliminary test to running alsamixer, to see if Ubuntu was recognizing the hardware, I didn't realize you wanted me to post that.  I have two sound cards, I'm interested in using the Audigy2 soundcard.  Previously, in 8.04 I had a problem with my default not being set to the Audigy2.  This is not the same problem (I think).  Also, I have run through numerous troubleshootings, including the one you suggested. Hope this helps, thank for your patience. 

lspci -v:

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 8118
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: e4000000-e5ffffff
	Prefetchable memory behind bridge: c0000000-dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 1021
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at a000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
	Subsystem: Agere Systems Device 044c
	Flags: bus master, medium devsel, latency 32, IRQ 255
	Memory at e6000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at a400 [size=8]
	I/O ports at a800 [size=256]
	Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 808a
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at e6001000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ac00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at b000 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at c000 [size=16]
	I/O ports at c400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 17
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at c800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at cc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e6002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Flags: medium devsel, IRQ 21
	I/O ports at 1000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Flags: medium devsel, IRQ 21
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-via82xx-modem

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: ASUSTeK Computer Inc. Device 80ff
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at e000 [size=256]
	Memory at e6003000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
	Subsystem: ATI Technologies Inc Device 0002
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e4000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: radeonfb, fglrx

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
	Subsystem: ATI Technologies Inc Device 0003
	Flags: 66MHz, medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

aplay -l:

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
	Subsystem: ASUSTeK Computer Inc. Device 8118
	Flags: bus master, 66MHz, medium devsel, latency 8
	Memory at e0000000 (32-bit, prefetchable) [size=64M]
	Capabilities: <access denied>
	Kernel driver in use: agpgart-via
	Kernel modules: via-agp

00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: e4000000-e5ffffff
	Prefetchable memory behind bridge: c0000000-dfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:08.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 1021
	Flags: bus master, medium devsel, latency 32, IRQ 20
	I/O ports at a000 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: EMU10K1_Audigy
	Kernel modules: snd-emu10k1

00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
	Subsystem: Agere Systems Device 044c
	Flags: bus master, medium devsel, latency 32, IRQ 255
	Memory at e6000000 (32-bit, non-prefetchable) [size=256]
	I/O ports at a400 [size=8]
	I/O ports at a800 [size=256]
	Capabilities: <access denied>

00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80) (prog-if 10)
	Subsystem: ASUSTeK Computer Inc. Device 808a
	Flags: bus master, medium devsel, latency 32, IRQ 16
	Memory at e6001000 (32-bit, non-prefetchable) [size=2K]
	I/O ports at ac00 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 17
	I/O ports at b000 [size=8]
	I/O ports at b400 [size=4]
	I/O ports at b800 [size=8]
	I/O ports at bc00 [size=4]
	I/O ports at c000 [size=16]
	I/O ports at c400 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sata_via
	Kernel modules: sata_via

00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06) (prog-if 8a [Master SecP PriP])
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 17
	[virtual] Memory at 000001f0 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 000003f0 (type 3, non-prefetchable) [size=1]
	[virtual] Memory at 00000170 (32-bit, non-prefetchable) [size=8]
	[virtual] Memory at 00000370 (type 3, non-prefetchable) [size=1]
	I/O ports at c800 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_via
	Kernel modules: pata_via

00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at cc00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d400 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d800 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: uhci_hcd
	Kernel modules: uhci-hcd

00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86) (prog-if 20)
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at e6002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd
	Kernel modules: ehci-hcd

00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
	Subsystem: ASUSTeK Computer Inc. Device 80ed
	Flags: bus master, stepping, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: i2c-viapro

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
	Flags: medium devsel, IRQ 21
	I/O ports at 1000 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: VIA 82xx Audio
	Kernel modules: snd-via82xx

00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
	Flags: medium devsel, IRQ 21
	I/O ports at dc00 [size=256]
	Capabilities: <access denied>
	Kernel modules: snd-via82xx-modem

00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
	Subsystem: ASUSTeK Computer Inc. Device 80ff
	Flags: bus master, medium devsel, latency 32, IRQ 19
	I/O ports at e000 [size=256]
	Memory at e6003000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: via-rhine
	Kernel modules: via-rhine

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
	Subsystem: ATI Technologies Inc Device 0002
	Flags: bus master, 66MHz, medium devsel, latency 255, IRQ 20
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at e5000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at e4000000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: radeonfb, fglrx

01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)
	Subsystem: ATI Technologies Inc Device 0003
	Flags: 66MHz, medium devsel
	Memory at d0000000 (32-bit, prefetchable) [disabled] [size=256M]
	Memory at e5010000 (32-bit, non-prefetchable) [disabled] [size=64K]
	Capabilities: <access denied>

zander@zander-box:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy2 [Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy2 [Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy2 [Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by martrn on 2008-10-31
If you visit the matrix you will find the Creative Labs sound cards at [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") have the Sound Blaster Audigy4 Pro listed as having the chipsets listed as emu10k2 CA0151/P16V.

Now you can go back to the shell and type sudo modprobe snd-[NAME OF YOUR SOUNDCARD'S DRIVER]. For example, your driver might be emu10k2 so you could type, 
```
sudo modprobe snd-emu10k2 
```
or the other one
```
sudo modprobe snd-CA0151/P16V 
```
depending on the chipset.

That should load the driver for the current session.  To load the driver for all session open up (type this into the shell) /etc/modules
```
sudo nano /etc/modules
```
# Add only the name of the module to be loaded at the end of the file. In the case, of the via82xx module gave you sound add "emu10k2" to the end of the file.

Then run alsamixer. Type into the terminal :
```
sudo alsamixer
```
and un-mute all the sound channels and you should have sound.

---

### Post by Zanian on 2008-10-31
I tried that, seems I don't have the driver for it.  I looked around to see where I could get it but I'm lost.  I tabbed at sudo modprobe snd- and I got among many others:
snd-emu10k1        snd-emu10k1x       snd-emux-synth     
snd-emu10k1-synth  snd-emu8000-synth

but not emu10k2 or the CA0151/P16V.  I tried just entering them in copy/paste right from your reply but no dice.

Let me add, I tried emu101k as well, didn't work.

---

### Post by martrn on 2008-10-31
```
modprobe snd-via82xx
``` to get your via sound card to work.  
If I get this correct you have two sound cards. ???

a) VIA Technologies, Inc. AC97 Audio Controller
b.)Sound Blaster Audigy 2 or 4

Plus also some kind of sound operated win-modem.  (Don't think that will work.)

To recomile your kernel module (and get all the alsa drivers) visit [URL="https://help.ubuntu.com/community/SoundTroubleshooting"]
https://help.ubuntu.com/community/SoundTroubleshooting[/URL] and skip to the section where it says using alsa source.  

Then open up a shell and type :
```
sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source
sudo dpkg-reconfigure alsa-source
```

At this point you now have a big blue dialog box where you can step through compileing a kernel module for alsa source.  Its fairly easy to step through and has a help system.

After compileing kernel modules (drivers) wich should match what sound cards you have in your system, you should have sound.  From the previous webpage ignore the section that says, "If you did not choose module-assistant" and always use module-assistant as it does all of the work for you.

---

### Post by Zanian on 2008-11-01
I did what you said, emu10k2 did not appear as an option. so I did all, thinking I maybe should be using emu10k1.  I then compiled the kernel.  I also did the module assistant and it failed around 60%.

---

### Post by HessiaNerd on 2008-11-01
I am in the same position.  I am running an old Audigy 2 sound card as well as having on board sound.  I recently did a fresh install with 8.10 and nothing I do is getting sound up.

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

:(:confused:

---

### Post by Zanian on 2008-11-03
bump

---

### Post by CrazyMonkey77 on 2008-11-03
I also had a sound issue after installing 8.10 and tried most, if not all of this stuff.  

Finally, after installing the gui version of the alsa mixer (as it all looked ok in the cli one).  I found that although the master volume was on full, the main speaker was actually set to mute by default.  I almost feel a bit stupid admitting to this but it might help someone.. :)

---

### Post by Zanian on 2008-11-03
Okay, an update on the situation:
I have been having a bunch of different issues.  The first thing is, despite how hard I tried, there was an issue with the default sound card, which I eventually managed to set to Audigy2.  I also noticed that my driver for my sound card is in fact emu10k1.  So, I messed around a bit and still no sound.  The driver is running and the default card is Audigy2.
I've also made sure that all my channels are un-muted.

edit: Is it strange that when type alsamixer in to the shell the display says PulseAudio for card and chip?

---

### Post by Zanian on 2008-11-03
I have sound:
I have been reading around because I was really frustrated with alsamixer displaying chip and card as PulseAudio.  I looked around the forums and tried a suggestion of removing the pulseaudio package.  I then messed around with the levels in alsamixer (which now displays my actual sound card/chip) and voila, I have sound.

The only thing that still frustrates me is that I actually had to get rid of pulseaudio to get alsa to work properly.  I know a lot of people are having trouble with sound and Audigy cards in particular since the upgrade.  I am rather new to linux, and ubuntu, so perhaps I just don't know how to manipulate alsa and pulseaudio well enough.  Regardless, if someone knows what I was doing wrong please drop a line to help others and me prevent this in the future.

---

### Post by PaulHuffman on 2009-06-04
I have the same problem, I think.  After I upgraded to 9.04 I haven't heard a peep out of this Gateway E Series.  When I boot with a 8.04 CD the speakers come roaring back to life.  Under 9.04, lshw shows a SB Audigy using emu10k1 as a driver. Emu10k2 seems like a better match for this card but, I can't find it. PulseAudio Volume Control shows a bar moving  to the music when I put in a audio CD, but muting and unmuting things in Gnome ALSA Mixer hasn't helped.  How did you remove Pulse Audio? I didn't find it in the add-remove programs list.

---

