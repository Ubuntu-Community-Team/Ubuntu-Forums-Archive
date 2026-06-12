---
title: "VLC does not detect channels on my TV card"
date: 2016-01-19
forum: MINT
---

### Post by hermit2 on 2016-01-19
My TV card is a Compro Videomate DVB-T300. I have recently ditched M$ Windows XP and installed Mint 17.1. I know very little about Linux. The card worked perfectly in the former OS, but in Mint VLC does not find a single channel when it scans for them.

This is what I have found out so far:

**lspci -vnn**
 ```
03:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder [1131:7134] (rev 01)
    Subsystem: Compro Technology, Inc. Videomate DVB-T300 [185b:c900]
    Flags: bus master, medium devsel, latency 32, IRQ 21
    Memory at fdcff000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
```

**dmesg | grep -i saa713**
```
[   11.275144] saa7130/34: v4l2 driver version 0, 2, 17 loaded
[   11.275271] saa7134[0]: found at 0000:03:07.0, rev: 1, irq: 21, latency: 32, mmio: 0xfdcff000
[   11.275276] saa7134[0]: subsystem: 185b:c900, board: Compro Videomate DVB-T300 [card=70,autodetected]
[   11.275289] saa7134[0]: board init: gpio is 843f00
[   11.309683] input: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/rc/rc0/input4
[   11.309747] rc0: saa7134 IR (Compro Videomate DV as /devices/pci0000:00/0000:00:14.4/0000:03:07.0/rc/rc0
[   11.461610] saa7134[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   11.461616] saa7134[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   11.461620] saa7134[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[   11.461624] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461628] saa7134[0]: i2c eeprom 40: ff 02 00 c2 86 10 ff ff ff ff ff ff ff ff ff ff
[   11.461631] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   11.461635] saa7134[0]: i2c eeprom 60: 34 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461639] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461642] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461646] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461650] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461653] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461657] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461660] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461664] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.461668] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.617767] saa7134[0]: registered device video0 [v4l2]
[   11.617808] saa7134[0]: registered device vbi0
[   11.619904] saa7134 ALSA driver for DMA sound loaded
[   11.619923] saa7134[0]/alsa: saa7134[0] at 0xfdcff000 irq 21 registered as card -2
[   11.645711] DVB: registering new adapter (saa7134[0])
[   11.645717] saa7134 0000:03:07.0: DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
```

I have created a file named saa7134.conf in /etc/modprobe.d. It contains a single line: option saa7134 card=70 tuner=67

Rebooted.

VLC lists the card under Devices ---> Video Capture as "Compro Videomate DVB-300 without a problem. In fact it lists it twice. My guess is that it recognises the digital and analogue capabilities separately. Under Devices --->Audio capture it itemises "Compro Videomate DVB-300 Analogue Stereo." among others.

I followed [these instructions]("http://www.mrs.monash.edu.au/oncampus/it/vlc-instructions.pdf"). All went well, except for the very last step. At that point it was supposed to discover and itemise all available free to air digital TV channels. I have the card connected via the standard coax cable to the digital / analogue TV antenna on the roof. Under the Windows OS it found about 20 of them. Now the little "Hang on while I'm scanning" disc rotates for a minute or two, then just stops without finding anything at all.

VLC still won't detect channels. The card is connected to a digital antenna on the roof via a coax cable.

Help appreciated.

---

### Post by howefield on 2016-01-19
Thread moved to the "*MINT*" sub forum.

---

### Post by deadflowr on 2016-01-19
Your PDF linked seems to have nothing to do with using a capture/tuner card.
It shows how to use vlc for live streams, which do not need a capture/tuner card.

For use of the capture card, vlc's wiki is probably better,
[https://wiki.videolan.org/How_to_Use_a_Capture_Card](https://wiki.videolan.org/How_to_Use_a_Capture_Card)

---

