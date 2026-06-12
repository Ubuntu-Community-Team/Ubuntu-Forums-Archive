---
title: "2nd try: Sound volume is 50% of what it is in windows."
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by paradigm2 on 2009-04-14
My sound at full volume is still half of what it was in windows.  It is very difficult to hear.  I have installed the alsa-mixer control and made sure all settings which are relevant are set to max.

What else can I try here to resolve this?

It isn't a critical problem, but a small annoyance...

---

### Post by nwadams on 2009-04-14
May I ask what kind of sound hardware do you have?

---

### Post by paradigm2 on 2009-04-14
> **nwadams said:**
> May I ask what kind of sound hardware do you have?

Here's what I get from 'lspci -v':

```

me@ubuntu-laptop:~/$ lspci -v 
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64
	Kernel modules: ati-agp

00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=64
	I/O behind bridge: 00009000-00009fff
	Memory behind bridge: c0100000-c01fffff
	Prefetchable memory behind bridge: 00000000c8000000-00000000cfffffff
	Capabilities: <access denied>
	Kernel modules: shpchp

00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0004000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0005000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at c0006000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: 66MHz, medium devsel
	I/O ports at 8400 [size=16]
	Memory at fed00000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 8410 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01)
	Flags: bus master, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=06, subordinate=08, sec-latency=64
	I/O behind bridge: 0000a000-0000afff
	Memory behind bridge: c0200000-c02fffff
	Prefetchable memory behind bridge: 50000000-53ffffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
	Flags: fast devsel
	Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
	Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
	Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	Flags: fast devsel
	Capabilities: <access denied>
	Kernel driver in use: k8temp
	Kernel modules: k8temp

01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
	Memory at c8000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 9000 [size=256]
	Memory at c0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c0120000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel modules: radeonfb

06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 21
	I/O ports at a000 [size=256]
	Memory at c0210000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device 0418
	Flags: bus master, medium devsel, latency 168, IRQ 22
	Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k_pci
	Kernel modules: ath_pci, ath5k

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, medium devsel, latency 168, IRQ 20
	Memory at c0211000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=06, secondary=07, subordinate=07, sec-latency=176
	Memory window 0: 50000000-53fff000 (prefetchable)
	Memory window 1: 54000000-57fff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0210400 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

06:04.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 23
	Memory at c0210800 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at c0210c00 (32-bit, non-prefetchable) [size=128]
	Capabilities: <access denied>

06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: medium devsel, IRQ 23
	Memory at c0210100 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci



```

This is on an Acer aspire 5100 series (exact model # unknown - the sticker is worn off and it says nowhere else :( ) laptop.  Stock sound card, all stock devices.

---

### Post by paradigm2 on 2009-04-14
More concise answer (my old ailing eyes missed it before) :

Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)

```

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 009f
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at c0000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel


```

---

### Post by nwadams on 2009-04-14
ok. Sorry, I cannot help you. I know a lot about how to make the intel work or the older realtek ac 97. But I know nothing about ATI. 

You could try adding 

```
options snd-hda-intel model=auto
```
to /etc/modprobe.d/alsa-base and rebooting. 

some ppl find adding model=3stack isntead of model=auto works for them.

---

### Post by dasme on 2009-04-14
> **paradigm2 said:**
> My sound at full volume is still half of what it was in windows.  It is very difficult to hear.  I have installed the alsa-mixer control and made sure all settings which are relevant are set to max.

What else can I try here to resolve this?

It isn't a critical problem, but a small annoyance...

Wow i have the same problem. My sound card is Realtek RTL268 any seggestion how to fix this problem?

---

### Post by nwadams on 2009-04-14
> **dasme said:**
> Wow i have the same problem. My sound card is Realtek RTL268 any seggestion how to fix this problem?

I recommend trying what I suggested in my previous post. If it doesn't help you can always revert it.

You could try adding

```
options snd-hda-intel model=auto
```

to /etc/modprobe.d/alsa-base and rebooting.

some ppl find adding model=3stack isntead of model=auto works for them.
nwadams is online now Report Post   	Edit/Delete Message

---

### Post by dasme on 2009-04-14
> **nwadams said:**
> I recommend trying what I suggested in my previous post. If it doesn't help you can always revert it.

You could try adding

```
options snd-hda-intel model=auto
```

to /etc/modprobe.d/alsa-base and rebooting.

some ppl find adding model=3stack isntead of model=auto works for them.
nwadams is online now Report Post   	Edit/Delete Message

Whr exactly should i add this command in the alsa base file.

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

```

---

### Post by nwadams on 2009-04-14
at the bottom, or anywhere you want. put it at the bottom and add a comment above it so you know what it is for future reference and to remove if neccessary

---

### Post by dasme on 2009-04-14
> **nwadams said:**
> at the bottom, or anywhere you want. put it at the bottom and add a comment above it so you know what it is for future reference and to remove if neccessary

Thx buddy for quick reply. I will report back after reboot. ;)

---

### Post by nwadams on 2009-04-14
thanks. To both of you guys. One of the fixes may fix the volume but may stop your headphone jack from working. So make sure you test your headphone jack. And if your headphone jack doesn't work try the other fix i talked about (model=3stack instead of model=auto)

---

### Post by paradigm2 on 2009-04-14
> **nwadams said:**
> ok. Sorry, I cannot help you. I know a lot about how to make the intel work or the older realtek ac 97. But I know nothing about ATI. 

You could try adding 

```
options snd-hda-intel model=auto
```
to /etc/modprobe.d/alsa-base and rebooting. 

some ppl find adding model=3stack isntead of model=auto works for them.

Thanks I will give it a shot.  I'm doing some work in Firefox right now but will add it tonight and reboot and see what happens.  The only thing I wonder about is that I use an ATI sound device though, not intel so would this still work?

---

### Post by nwadams on 2009-04-14
> **paradigm2 said:**
> Thanks I will give it a shot.  I'm doing some work in Firefox right now but will add it tonight and reboot and see what happens.  The only thing I wonder about is that I use an ATI sound device though, not intel so would this still work?

your lspci says that the driver being used is hda-intel which is just some generic name probably. I looked it up online and it worked for some people but for some the headphone jacks behaved oddly.

---

### Post by dasme on 2009-04-14
hi nwadams tried adding both of ur commands, but my card just muted itself and thr was no sound. So i reverted back to original.

Anyway thx for the suggestion :)

---

### Post by nwadams on 2009-04-14
Tough luck. Sorry that i could be of no help, I hope you find help from someone else.

---

### Post by cszikszoy on 2009-04-14
In a terminal:
```
$ alsamixer -D hw:0
```

Then make sure each mixer is set to 100%.

---

### Post by dasme on 2009-04-14
> **cszikszoy said:**
> In a terminal:
```
$ alsamixer -D hw:0
```

Then make sure each mixer is set to 100%.

What u suggested can also be done from kmix in kubuntu. Anyway thx.

If any1 knows a good tutorial how to upgrade alsa driver to .19 pls post the link.

Thx

---

### Post by paradigm2 on 2009-04-16
> **nwadams said:**
> ok. Sorry, I cannot help you. I know a lot about how to make the intel work or the older realtek ac 97. But I know nothing about ATI. 

You could try adding 

```
options snd-hda-intel model=auto
```
to /etc/modprobe.d/alsa-base and rebooting. 

some ppl find adding model=3stack isntead of model=auto works for them.

I tried it but it did not help, unfortunately.

I've also installed the new alsa and pulseaudio from a PPA.  I guess the next thing to try is the kernel upgrade.

In fact it seems to have actually hurt?  I removed the alsa-base file entirely and rebooted.  Shouldn't this restore it to how it was? 

CORRECTION:  My apologies, I see somewhere that the front speakers were somehow turned down and this made the difference.  Now with the new PA 9.0.15 and the new Alsa from the PPA, my audio is now at least usable, although still a little low in my opinion.

Comment on PulseAudio:  It's awesome.  Make sure to install 'pavucontrol' aka Pulse Audio Volume Control.  Using it I finally found how to get the benefits of PulseAudio.  I am able to set volume levels per application (i.e rhythmbox at 80%, sound from Firefox at 100%) and the applications can all play at once.  Pretty awesome.  I would say PulseAudio is definitely worth all the hassles.  Great job to the developers!

---

### Post by Taiebot65 on 2009-04-16
Have you checked the pcm volume ?  click on the volume applet and increase all the volume

---

### Post by paradigm2 on 2009-04-16
> **Taiebot65 said:**
> Have you checked the pcm volume ?  click on the volume applet and increase all the volume

Yes, thanks.  I just edited the last post a few minutes before you replied.  Somehow (it was checked before posting this topic but might have happened when upgrading PA or installing a different mixer.  I don't know) the front speakers got reset to like 50% volume.  I changed that and it is probably about 75% of what it was n windows (which is usable and better).

I actually installed the PulseAudio 0.9.0.15 update just released the other day from a special PPA though.  I'm considering updating kernels as well to get some intel HDA fixes.

---

### Post by Methuselah on 2009-04-16
I didn't get whether the pulse audio volume controls was installed.
I know that to get capture working I often have to unmute multiple volume controls.

---

### Post by paradigm2 on 2009-04-16
> **Methuselah said:**
> I didn't get whether the pulse audio volume controls was installed.
I know that to get capture working I often have to unmute multiple volume controls.

'pavucontrol' aka Pulse Audio Volume Control should show up in Applications -> Sound and Audio -> (Pulse Audio Volume Control)

While you have something playing it should show up and allow you to change the volume level per application/channel.  It looks like it remembers the setting as well for next time, storing it in ~/.pulse.  Its pretty cool.  It would be even better if I get the volume up another 25% or so, but hey at least it is functional now.

---

### Post by ubu-for on 2009-04-16
I haven't read the hole thread but maybe the following hint helps?

[http://ubuntuforums.org/showpost.php?p=6862535&postcount=5](http://ubuntuforums.org/showpost.php?p=6862535&postcount=5)
[http://ubuntuforums.org/showthread.php?t=1090643](http://ubuntuforums.org/showthread.php?t=1090643)

---

### Post by paradigm2 on 2009-04-19
Update:

Upgrading pulseaudio to 9.0.15 along with the new alsa

+

Installing the new 2.6.30 rc2 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc2/) (Warning: Obviously this kernel isn't the official Ubuntu sanctioned release for Jaunty.  It may screw things up for you.)

Seems to have really helped a lot with this.  Sound also seems infinitely more stable now (even testing multiple streams at once with volume control)

:)

I trust that the 2.6.30rc2 probably incorporated crimson's latest fixes as well?

Nice job developers!

---

