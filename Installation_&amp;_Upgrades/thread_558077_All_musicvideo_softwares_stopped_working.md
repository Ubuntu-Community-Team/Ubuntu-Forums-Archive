---
title: "All music/video softwares stopped working"
date: 2007-09-23
forum: Installation &amp; Upgrades
---

### Post by Glaucous on 2007-09-23
Hi.

Recently all my video and music softwares have stopped working every time I try to play a video or music-file. Doesn't answer and so on.

I've tried VLC, Rhythmbox and the default videoplayer, but none of them works.

The only program that works is Audacity, and when I hover a file with my mousecrusor.

Anyone who might know how to fix this?

---

### Post by cowkiller on 2007-09-23
> Hi.

Recently all my video and music softwares have stopped working every time I try to play a video or music-file. Doesn't answer and so on.

I've tried VLC, Rhythmbox and the default videoplayer, but none of them works.

The only program that works is Audacity, and when I hover a file with my mousecrusor.

Anyone who might know how to fix this?

Maybe, but not with so few info....

could you give some specifications like graphic and sound card model, ubuntu version, lspci output, etc....?
did you use automatix to install the media codecs?

---

### Post by Glaucous on 2007-09-23
I've got Nvidia 6600 GT with the drivers enabled.
Ubuntu 7.04 Feisty Fawn.
Realtek 880 or Intel Corporation 82801FB

> 00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:01.0 PCI bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600] (rev a2)
03:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:05.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)


I did not use Automatix to install the codecs, I think it did automatically when I tried to start an AVI file the first time. 
But I did uninstall the drivers and install them with Automatix, but nothing changed.

I'm quite new to Ubuntu/Linux, I got it yesterday, so.
And the sound works on Windows XP (dual boot).

EDIT: **Okay, this is weird, but it works now, I don't know how, but it might have something to do with that I reinstalled the codecs and then restared.**

---

### Post by cowkiller on 2007-09-24
Hi there... I just started with it like 6-7 months ago. Sound problems used to happen to me too. Sometimes it just doesn't works and it does after rebooting or something alike.... anyway... it seems to me like any of these random problems. 
But anyway... since automatix seems to have some problems with these codecs when upgrading, I'd recommend you to manually remove and reinstall all the media codecs, included the w32codecs, without using automatix.

this way:

```

sudo apt-get remove gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-pitfdll libquicktime0 libxine-main1 libxine-extracodecs libquicktime0 libdvdread3 flashplugin-nonfree totem-gstreamer-firefox-plugin unrar
```

and then...
```

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-pitfdll libquicktime0 libxine-main1 libxine-extracodecs libquicktime0 libdvdread3 flashplugin-nonfree totem-gstreamer-firefox-plugin unrar
```

( I dunno if it's a very ortodox way anyway.... :lolflag: )

also install the .deb with the [w32codecs]("http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20061022-0.1_i386.deb") 

the command was taken from [ubuntulife]("http://ubuntulife.net/wordpress/?p=1877")

I can't do much more, I just can tell you that I had these problems and they finally get solved with new upgrades, just have a little patience and good luck.

---

### Post by Omegabyte on 2007-09-24
I've had the same problem and don't know what to do about it.  I have a Toshiba Satellite M115-S1061 with an ATI driver.  I had some problems with getting the sound to work with ATI, but I got that taken care of and DVD's would play fine on the default media player. Then recently it would just stop working when I put a DVD in.  It would say, "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.  Please install the necessary plugins and restart Totem to be able to play this media."  When I tried to go through the Synaptic Package Manager and add the plugins, it would download them, but the player still wouldn't work and I would go back and it showed that the plugins were never downloaded.  I've tried this several times and they say that they're installed, but I'd go back and check, and they weren't.  If you could help, I would really appreciate it.

---

### Post by cowkiller on 2007-09-25
Hi Omegabyte, I couldn't fully understand what you pointed, but I think that once you've solved your sound problem, just DVD can't be played. Googling around a bit I've read that the totem-gstreamer developers didn't include DVD support due to legal reasons. I think that installing the **VLC **player will solve that problem with DVDs.

Anyway, if that wouldn't work, check out the solution given [here]("https://answers.launchpad.net/ubuntu/+question/11904")

---

