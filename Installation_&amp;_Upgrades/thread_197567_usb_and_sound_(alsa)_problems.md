---
title: "usb and sound (alsa) problems"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by dparadinha on 2006-06-15
hello forum,

after upgrade to dapper (from breezy) , (at least) two problems appear - sound is not initializated (alsa does not recognize sound card) and usb pen drives are not being mounted (at least my verbatim 1 gb; i could try with others later)!
these are annoying disturbances! in breezy both sound and usb worked great!

casa@casaubuntu:~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333]
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
0000:00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:00:0b.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:00:0b.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
0000:00:0b.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
0000:00:0b.3 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8233 PCI to ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.4 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1b)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 30)0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 11)

---

### Post by dparadinha on 2006-06-15
i've noticed that my usb scanner is not working either! i'm beginning to think that the problem is far bigger than just the pen drive...
i've one Via pci board with 4 usb 2.0 and 2 firewire, where i attach the pen and scanner to; if i attach the scanner or the pen to the usb 1.1 ports of my motherboard it won't work either...
in breezy everything was fine!
and the sound continues dead! as if there was not one onboard!

---

### Post by dparadinha on 2006-06-16
hello again,

tonight i've reinstalled dapper, this time using the install/live cd iso (and not by the upgrading alternate way);

the good news are that both sound and usb work as they should!
(very) bad news are that when win xp is initializated (i've dual boot) an error message appears and i cannot start xp now!!!
message is:
stop: c000021a {fatal system error}
the session manager initialization system process terminated unexpectedly with a status of 0xc0000034 (0x00000000 0x00000000)
the system has been shut down.

what should i do now?

i'm beginning a new post...

---

