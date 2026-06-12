---
title: "unable to find drivers"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by mark102461 on 2008-08-16
:confused: I installed Ubuntu 8.04 LTS desktop edition.  Unable to find drivers restricted or otherwise. please, help. Graphics are messed up and cpu shutsdown when I try to put system in sleep mode.

---

### Post by NIKOLCE77 on 2008-08-16
Try with this:
sudo apt-get install ubuntu-restricted-extras

---

### Post by mark102461 on 2008-08-16
Where do I type that in at? How do you get a command line to come up?

---

### Post by NIKOLCE77 on 2008-08-17
Open Applications then go to Accessories and click on Terminal
Then copy paste the line below and press Enter

sudo apt-get install ubuntu-restricted-extras

---

### Post by Sef on 2008-08-17
> Where do I type that in at? How do you get a command line to come up?

sudo apt-get install ubuntu-restricted-extras

That's the wrong code.  That is for installing Java, Flash, and codecs for playing music.

Instead try this:

System > Administration > Hardware Drivers

Also what are you system specs, especially your graphics card.

---

### Post by manishtech on 2008-08-17
Please mention your Hardware config esp Graphics card, motherboard ,processor and some more nice information which you can furnish

---

### Post by NIKOLCE77 on 2008-08-17
Hi Im sorry for not helping with my answer, I have problem with drivers with my TV TUNER card Match I have tried with post but didnt get answer , my card is Match MpegTV-Station with TV FM and remote control and works with Conexant drivers in Windows XP SP2 and has a Philips chip PAL BG, I dont know what drivers to install for Linux.

Here is what I get with dmesg:

[   52.402804] bttv0: Bt878 (rev 17) at 0000:02:02.0, irq: 5, latency: 32, mmio: 0xda100000
[   52.402831] bttv0: using:  *** UNKNOWN/GENERIC ***  [card=0,autodetected]
[   52.402874] bttv0: gpio: en=00000000, out=00000000 in=003fffff [init]
[   52.404182] tveeprom 0-0050: Huh, no eeprom present (err=-121)?
[   52.404189] bttv0: tuner type unset
[   52.404195] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[   52.404795] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[   52.405384] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[   52.406083] bttv0: registered device video0
[   52.406158] bttv0: registered device vbi0
[   52.490106] bt878: AUDIO driver version 0.0.0 loaded
[   52.490280] bt878: Bt878 AUDIO function found (0).
[   52.490316] ACPI: PCI Interrupt 0000:02:02.1[A] -> Link [LNKC] -> GSI 5 (level, low) -> IRQ 5
[   52.490328] bt878_probe: card id=[0x0], Unknown card.
[   52.490331] Exiting..
[   52.490339] ACPI: PCI interrupt for device 0000:02:02.1 disabled
[   52.490353] bt878: probe of 0000:02:02.1 failed with error -22
[   53.982491] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   56.023570] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[   56.023581] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 11 (level, low) -> IRQ 11
[   56.023614] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   56.342768] intel8x0_measure_ac97_clock: measured 52184 usecs
[   56.342778] intel8x0: clocking to 48000
[   56.946457] parport_pc 00:0a: reported by Plug and Play ACPI
[   56.946555] parport0: PC-style at 0x378 (0x778 ), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[   60.101604] Bluetooth: Core ver 2.11

And with every program that I've tried I get message that I have no tuner card but in windows it works both with program from the manufacturer and with Win DVR 3 which is for recording from TV. I think that I need some drivers but I dont know which ones and where to find.

Can anyone help please

---

### Post by manishtech on 2008-08-17
I cant figure it out, but do you have windows drivers for the same. Try using ndiswrapper for installing, but am still not sure whether it will work with ndiswrapper. Frankly, I dont have a TV Tuner card, so cant help much, only suggestions.

---

### Post by mark102461 on 2008-09-02
:confused:under (System > Administration> Hardware Drivers) there is nothing there.  Please, Help!!!!!!:

---

### Post by cariboo on 2008-09-03
mark102461 please give us your hardware specs, in a Applications-->Accessories-->Terminal type:

```
lspci
```

Post the output in your next post. We can't help you if we don't know hwat hardware you are running.

Jim

---

