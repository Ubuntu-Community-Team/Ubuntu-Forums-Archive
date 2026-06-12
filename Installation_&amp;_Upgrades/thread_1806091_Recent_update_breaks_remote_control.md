---
title: "Recent update breaks remote control"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by declanmullen on 2011-07-17
My mythbuntu 10.10 system including its lirc managed remote control has been working fine. I've recently done some updates (see below) and now the remote doesn't work correctly (only some of its keys seem to work). I suspect that lirc is no longer managing the remote and now instead the remote is now being treated like a keyboard.

How do I get lirc managing my remote control correctly again, thanks ?

Before the updates the kernel was:
```

$ uname -a
Linux pvr 2.6.35-28-generic-pae #50-Ubuntu SMP Fri Mar 18 20:43:15 UTC 2011 i686 GNU/Linux

```

I suspect that one or more of the below updates are to blame (extracted from /var/log/apt/history.log):
```
Install: 
linux-headers-2.6.35-30:i386 (2.6.35-30.54), 
linux-headers-2.6.35-30-generic-pae:i386 (2.6.35-30.54), 
linux-image-2.6.35-30-generic-pae:i386 (2.6.35-30.54)

Upgrade:
linux-image-generic-pae:i386 (2.6.35.28.36, 2.6.35.30.38),
linux-libc-dev:i386 (2.6.35-1028.50, 2.6.35-1030.54),
linux-generic-pae:i386 (2.6.35.28.36, 2.6.35.30.38),
linux-headers-generic-pae:i386 (2.6.35.28.36, 2.6.35.30.38)

Install: 
linux-headers-2.6.35-30:i386 (2.6.35-30.54),
linux-headers-2.6.35-30-generic-pae:i386 (2.6.35-30.54),
linux-image-2.6.35-30-generic-pae:i386 (2.6.35-30.54)

Upgrade:
initramfs-tools-bin:i386 (0.98.1ubuntu6, 0.98.1ubuntu6.1),
initramfs-tools:i386 (0.98.1ubuntu6, 0.98.1ubuntu6.1),
libimobiledevice1:i386 (1.0.1-1, 1.0.1-1ubuntu0.1), 

```   

Current LIRC:
```
$ dpkg -l | grep -i lirc
ii  liblircclient0                       0.8.7~pre3-0ubuntu1                                infra-red remote control support - client library
ii  lirc                                 0.8.7~pre3-0ubuntu1                                infra-red remote control support
ii  lirc-x                               0.8.7~pre3-0ubuntu1                                infra-red remote control support - X utilities
ii  mythbuntu-lirc-generator             0.25-0ubuntu1                                      Mythbuntu Lirc Configuration Generator

```   

Current modules: 
```

$ lsmod
Module                  Size  Used by
snd_hda_codec_nvhdmi    13615  1 
snd_hda_intel          22299  0 
nvidia               9331115  28 
snd_hda_codec          87552  2 snd_hda_codec_nvhdmi,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71603  2 snd_hda_intel,snd_hda_codec
tda18271               52053  1 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
af9013                 19970  2 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49038  8 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
dvb_usb_af9015         24754  19 
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm
dvb_usb                14597  1 dvb_usb_af9015
dvb_core               88505  1 dvb_usb
agpgart                32075  1 nvidia
serio_raw               4022  0 
lp                      7342  0 
joydev                  8767  0 
i2c_piix4               8795  0 
k10temp                 2607  0 
parport                31492  1 lp
usbhid                 36978  0 
hid                    67742  1 usbhid
ahci                   19198  1 
libahci                21792  1 ahci
r8169                  36777  0 
mii                     4425  1 r8169
pata_atiixp             3288  0 

```

BTW, booting off the previous kernel 2.6.35-28 does not fix the problem.

The remote control receiver is the one that is built in to the Leadtek WinFast DTV2000DS DVB-T TV card. The remote control is the Y04G0051 model. [http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS]("http://www.linuxtv.org/wiki/index.php/Leadtek_WinFast_DTV2000DS")

I'm using the generic "devinput" configuration file with lirc. [http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput]("http://lirc.sourceforge.net/remotes/devinput/lircd.conf.devinput")

---

### Post by declanmullen on 2011-07-17
It wouldn't have anything to do with this topic would it ?
[http://wilsonet.com/?page_id=95]("http://wilsonet.com/?page_id=95")

---

### Post by declanmullen on 2011-07-17
Problem solved. It turned out that the updates had resulted in a change to the name of the device file thru which the remote's events were being made available. 

Prior to the above updates the device file was /dev/input/event4
After the above updates the device file was /dev/input/event6

I just had to update the /etc/lirc/hardware.conf file to specify the new file name and then restart lirc.

---

