---
title: "HDA Intel ICH8 Family : No Sound through speaker &amp; Almost No Sound through Headphone"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by pooh14 on 2007-10-22
Hi Guys,

I am kinda sick and tired of this problem and really hope somebody can help me over here :)

I am having Acer Aspire 4730 Laptop with HDA Intel ICH8 Family (rev 03)(Realtek 268 ) sound card.
My sound never worked in Ubuntu Feisty (it is fine with Windows), although i have time numerous methods suggested by the forum .

I then tried with Gusty, and the same problem occurred. However, after downloading and installing the linux-backports-modules, i have extremely soft sound (almost unheard) if i use headphone and external speaker. No sound coming from the normal speaker though. 

I even added the following line added s line to /etc/modprobe.d/alsa-base (according to suggestions from this link : [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller):](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller):)
options snd-hda-intel model=acer.

It did not help either. I have tried downloading the latest alsa driver, ALSA 1.0.15rc3, and installed it, did not help either.

I had a Warning Message :CAT:sound might be muted by default.However, I don't find any sound muted in my alsa-mixer.


```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
0a:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

```

Under the volume control I have 2 device :
1) HDA Intel (Alsa Mixer)
2) Realtek 268 (OSS Mixer)

I have tried both, and both do not work.

Under the Sound Setting, it is under AutoDetect for all option. If i tried to change to ALSA, and click Test, I get the following error :
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

```

I would really appreciate if someone could help me out in this problem. I have been trying for a month already. I have attached my alsa-mixer window if it might help

*Note : My Linux skills isn't too good, so would appreciate more detail help :):KS

---

### Post by pooh14 on 2007-10-22
Hi Guys,

Actually I manage to get the sound working FINALLY!.

However my mic isn't working, whether internal or external mic.

Hope somebody could help o nthat :)

---

### Post by xfred on 2007-10-26
You got it working - cool.

Mind if I ask how :) ?

I started with the soundcard allegedly detected, but no sound.  This on a toshiba A200 with gutsy.

I've tried following the HdaIntelSoundHowto instructions... failed at step:

cat /proc/asound/card0/codec#* | grep Codec

and now sound didn't even pretend to work anymore.  After much head scratching and googling I tried doing this:

sudo apt-get install module-assistant
sudo m-a update
sudo m-a prepare
sudo m-a a-i alsa 

and that got be back to where I started... everything seems fine in software, but no sound.  So I tried the codec command thingy again and I get:

Codec: Realtek ID 268
Codec: Generic 11c1 Si3054

which after some more googling indicates that I may or may not be boned, depending on which source I believe.  The best lead seems to be patching alsa, but when I tried compiling alsa previously... well, see step 1 above.

HEEEeeeelp.  I'm not a linux guru, I'm a dabbler, and I'm lost.  Any suggestions??

---

### Post by Pumalite on 2007-10-26
Maybe this would help:
[http://ubuntuforums.org/showpost.php?p=3588321&postcount=5](http://ubuntuforums.org/showpost.php?p=3588321&postcount=5)

---

