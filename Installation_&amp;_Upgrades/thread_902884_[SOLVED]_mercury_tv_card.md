---
title: "[SOLVED] mercury tv card"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by smolty on 2008-08-27
Hi
I'm new to Linux/Ubuntu and love it but the one thing dragging me back to Windows is the fact that I cant get my Mercury TV card to work (i think it uses the Philips 7130 Chip but im not 100% on this). It's an analogue card with a video input on it, I only use the video input on it as I have an external Freeview box. I've tried most things on all the other threads but cant get anything to work. dmesg result (or the bit I think is useful) is 

[   53.569493] Linux video capture interface: v2.00
[   53.683286] saa7130/34: v4l2 driver version 0.2.14 loaded
[   53.683354] ACPI: PCI Interrupt 0000:01:0b.0[A] -> GSI 21 (level, low) -> IRQ 21
[   53.683365] saa7130[0]: found at 0000:01:0b.0, rev: 1, irq: 21, latency: 64, mmio: 0xcfeffc00
[   53.683374] saa7130[0]: subsystem: 18d0:2100, board: LifeView/Typhoon FlyVIDEO2000 [card=3,insmod option]
[   53.683383] saa7130[0]: board init: gpio is 38500
[   53.683386] saa7130[0]: there are different flyvideo cards with different tuners
[   53.683388] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   53.683390] saa7130[0]: option to override the default value.
[   53.683488] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:1e.0/0000:01:0b.0/input/input8
[   53.864396] saa7130[0]: i2c eeprom 00: d0 18 00 21 10 28 ff ff ff ff ff ff ff ff ff ff
[   53.864410] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.864421] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.864432] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.864444] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.864455] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.864466] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.864477] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   53.905313] tuner 0-0061: chip found @ 0xc2 (saa7130[0])
[   53.905342] tuner-simple 0-0061: type set to 39 (LG NTSC (newer TAPC series))
[   53.905346] tuner 0-0061: type set to LG NTSC (newer TAPC
[   53.905349] tuner-simple 0-0061: type set to 39 (LG NTSC (newer TAPC series))
[   53.905352] tuner 0-0061: type set to LG NTSC (newer TAPC
[   53.907791] saa7130[0]: registered device video0 [v4l2]
[   53.907823] saa7130[0]: registered device vbi0
[   53.907851] saa7130[0]: registered device radio0
[   53.965183] saa7134 ALSA driver for DMA sound loaded
[   53.965218] saa7130[0]/alsa: saa7130[0] at 0xcfeffc00 irq 21 registered as card -2
[   54.067636] Adding 3028212k swap on /dev/sdb5.  Priority:-1 extents:1 across:3028212k

This has changed from a couple of days ago when I was getting information listed around [58.xxxx]. This has disappeared from dmesg now though.

I've been trying to get my head round Ubuntu for a few weeks and I did have TV Time working but showing no images or anything, just loading up. Now however I get this messages:

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/smolty/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Aside from the tv time problem I know a lot of the threads are saying to enter 
"sudo rmmod saa7134
sudo modprobe saa7134 card=2"

I either get an error message for these or it doesn't appear to do anything. I've tried with saa 7130 instead of 7134 but this doesn't work either. 

Like I say this is the only thing from stopping me using Ubuntu all the time as I don't have a stand alone TV.

Any help would be appreciated but I've only been using Ubuntu for a short time so I'm not that great following all the technical talk!! I'm pretty good at following instructions though whether I understand it or not!!!

Hope someone can help me!

---

