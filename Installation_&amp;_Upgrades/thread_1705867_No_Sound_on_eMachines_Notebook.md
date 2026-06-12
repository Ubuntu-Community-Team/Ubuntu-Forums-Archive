---
title: "No Sound on eMachines Notebook"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by TeKurtz on 2011-03-12
I just installed Ubuntu 10.4.2 on a M622 eMachines notebook. I have no audio what-so-ever even after installing an ALSA mixer and updating everything.  I can control every option as if the sound drivers were functioning fine. I've made sure nothing is muted and I've checked the headphones as well. What's strange is that the microphone input works and I'm able to record with sound recorder (according to the audio in level meter). 
The only thing I can think of is that the wrong drivers are installed but I'm not sure how about changing them or what to change them to. Here is a copy of my ALSA report:

```
!!Linux Distribution
!!------------------

Ubuntu 10.04.2 LTS \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"


!!DMI Information
!!---------------

Manufacturer:      Gateway
Product Name:      MX4625
Product Version:   67.09.00


!!Kernel Information
!!------------------

Kernel release:    2.6.32-29-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.21
Library version:    1.0.22
Utilities version:  1.0.22


!!Loaded ALSA modules
!!-------------------

snd_atiixp
snd_atiixp_modem


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [IXP            ]: ATIIXP - ATI IXP
                      ATI IXP rev 2 with Cx20468-31 at 0xd0503400, irq 17
 1 [Modem          ]: ATIIXP-MODEM - ATI IXP Modem
                      ATI IXP Modem rev 2 at 0xd0503800, irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)


!!Advanced information - PCI Vendor/Device/Subsystem ID's
!!--------------------------------------------------------

00:14.5 0401: 1002:4370 (rev 02)
    Subsystem: 107b:0301


!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-usb-caiaq: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2


!!Loaded sound module options
!!--------------------------

!!Module: snd_atiixp
    ac97_clock : 48000
    ac97_codec : -1
    ac97_quirk : <NULL>
    enable : N
    id : <NULL>
    index : -1
    spdif_aclink : Y

!!Module: snd_atiixp_modem
    ac97_clock : 48000
    enable : N
    id : <NULL>
    index : -2


!!AC97 Codec information
!!---------------------------
--startcollapse--

0-0/0: Conexant Cx20468-31

PCI Subsys Vendor: 0x107b
PCI Subsys Device: 0x0301

Flags: 8
Revision         : 0x00
Compat. Class    : 0x00
Subsys. Vendor ID: 0x0000
Subsys. ID       : 0x0000

Capabilities     : -reserved1- -headphone out-
DAC resolution   : 18-bit
ADC resolution   : 18-bit
3D enhancement   : No 3D Stereo Enhancement

Current setup
Mic gain         :  0dB [ 0dB]
POP path         : pre 3D
Sim. stereo      : off
3D enhancement   : off
Loudness         : off
Mono output      : MIX
Mic select       : Mic1
ADC/DAC loopback : off
Extended ID      : codec=0 rev=2 AMAP DSA=0 SPDIF
Extended status  : PRL PRK PRJ PRI SPCV SPDIF=7/8
SPDIF Control    : Consumer PCM Copyright Category=0x0 Generation=0 Rate=48kHz
Extended modem ID: codec=0 LIN1
Modem status     : GPIO
Line1 rate       : 48000Hz

```
Does anything stand out as an issue?

---

### Post by Dutch70 on 2011-03-12
Hi, and welcome to UF.

I think this link works for notebooks  also.

[https://help.ubuntu.com/community/SoundTroubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting")

Ps. Please edit your post & highlight the info you posted. Then tick the "#" sign in the toolbar. This puts code tags around it so people that are trying to help, don't have to scroll that entire post every time someone views your thread. ;)

---

### Post by TeKurtz on 2011-03-12
Thanks....
Ah yes, I figured there had to be better way. Thank you

---

### Post by Dutch70 on 2011-03-13
Your quite welcome. Did you get your sound problem figured out?

---

