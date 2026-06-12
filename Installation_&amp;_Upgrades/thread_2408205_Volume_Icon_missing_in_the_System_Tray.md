---
title: "Volume Icon missing in the System Tray"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by artist-wavenet on 2018-12-15
The volume icon, which looks like a loudspeaker with sound waves emanating from it, and is normally in the system tray to the upper right of the screen near the clock, is missing. The OS was recently installed, but I did not get any audio. I do not know excalty when it disappeared in my effort to get audio working, but suspect it  disappeared when I attempted to get audio working by the commands:
 
```
sudo apt-get remove --purge alsa-base pulseaudio
sudo apt-get install alsa-base pulseaudio
sudo alsa force-reload
```

because it disappeared around that time.

What do I need to do to get this icon back and get audio working?

I am using headphones plugged into the analog output jack.

System information:
```
$ lsb_release -a
LSB Version:    core-9.20170808ubuntu1-noarch:printing-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

$ sudo hwinfo | grep -A7 -i "audio"
Can play audio:    
Can write CD-R:    
Can write CD-RW:
Can read DVD:    
Can write DVD-R:
Can write DVD-RAM:
Can read MRW:    
Can write MRW:    
--
  E: ID_MODEL_FROM_DATABASE=GP102 HDMI Audio Controller
  E: ID_PCI_CLASS_FROM_DATABASE=Multimedia controller
  E: ID_PCI_SUBCLASS_FROM_DATABASE=Audio device
  E: ID_VENDOR_FROM_DATABASE=NVIDIA Corporation
  E: MODALIAS=pci:v000010DEd000010EFsv00001043sd000085E2bc04sc03i00
  E: PCI_CLASS=40300
  E: PCI_ID=10DE:10EF
  E: PCI_SLOT_NAME=0000:01:00.1
  E: PCI_SUBSYS_ID=1043:85E2
  E: SUBSYSTEM=pci
--
  E: ID_PCI_SUBCLASS_FROM_DATABASE=Audio device
  E: ID_VENDOR_FROM_DATABASE=Advanced Micro Devices, Inc. [AMD/ATI]
  E: MODALIAS=pci:v00001002d00004383sv00001458sd0000A182bc04sc03i00
  E: PCI_CLASS=40300
  E: PCI_ID=1002:4383
  E: PCI_SLOT_NAME=0000:00:14.2
  E: PCI_SUBSYS_ID=1458:A182
  E: SUBSYSTEM=pci
--
34: PCI 100.1: 0403 Audio device
  [Created at pci.378]
  Unique ID: NXNs.xEnIxzt3m06
  Parent ID: _Znp.mxGZ4sT7tg6
  SysFS ID: /devices/pci0000:00/0000:00:02.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "nVidia GP102 HDMI Audio Controller"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x10ef "GP102 HDMI Audio Controller"
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x85e2 
  Revision: 0xa1
  Memory Range: 0xfe080000-0xfe083fff (rw,non-prefetchable,disabled)
  IRQ: 7 (no events)
  Module Alias: "pci:v000010DEd000010EFsv00001043sd000085E2bc04sc03i00"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
--
35: PCI 14.2: 0403 Audio device
  [Created at pci.378]
  Unique ID: 5Dex.oj7atcdzLmC
  SysFS ID: /devices/pci0000:00/0000:00:14.2
  SysFS BusID: 0000:00:14.2
  Hardware Class: sound
  Model: "ATI SBx00 Azalia (Intel HDA)"
  Vendor: pci 0x1002 "ATI Technologies Inc"

```

---

### Post by again? on 2018-12-15
```
sudo apt install indicator-sound
```
Logout.

If no sound, in terminal run...
```
alsamixer
```

Check controls make sure not muted.
Use arrow keys to navigate.
Toggle muting of selected control with the "m" key

If a control is muted it will show as "MM".
[ATTACH=CONFIG]281935[/ATTACH]

Also try to toggle mute with....
```
amixer -D pulse set Master toggle
```

---

### Post by artist-wavenet on 2018-12-15
Thanks for you reply :)

The command "sudo apt install indicator-sound" did work to put the volume icon in the System Tray. But ti does not do anything until I do the command "pulseaudio" in the Terminal Emulator. After that the volume icon does get me a sound volume slider, Btu there is still no sound. Under that slider the "Sound Settings...." option appears. When clicked on I get and expanded volume control with three tabs. In the "Output Devices" tab the only device I see is the "Dummy Output" one and its slider.

My OS does not recognize the commands: "amixer" and "alsamixer". These are not installed, and I do not know right now how to get them installed.

In the Software Center I was able to install "GNOME ALSA Mixer". But doing so did not install the above two commands.

I suspect my OS is missing the driver "snd_hda_intel" because the command "inxi -A" does not output anything. How is this installed?

---

### Post by CatKiller on 2018-12-15
OK, it looks like you've got rid of a bunch of stuff that you need. It's ALSA that talks to the hardware, and pulseaudio talks to ALSA. Pulseaudio can't start automatically because it can't find ALSA.

The package **alsa-utils** has those programs we know you don't have. I have no idea if there's more that you need to replace.

---

### Post by artist-wavenet on 2018-12-16
[B]I attempted this installation apt-get told me alsa-utils was already installed.

I am able to hear audio now though. The final key to it was to get pulseaudio running, and to get the module  snd-hda-intel running with the command: 

sudo modprobe snd-hda-intel 

As described in: 
[https://askubuntu.com/questions/57810/how-to-fix-no-soundcards-found](https://askubuntu.com/questions/57810/how-to-fix-no-soundcards-found) 

The modprobe command had to be executed after every reboot. So I set  this up to do so automatically by creating the soundcardfix bash script  file as Fred describes in his posting near the bottom of that webpage. 

The only thing left to do is to also execute the pulseaudio command  automatically on boot up. I attempted to do so by adding this as the  last command in the soundcardfix script. But this did not work. I still  have to execute this manually. Why is this? How can it be executed  automatically at boot time?
[/B]

---

