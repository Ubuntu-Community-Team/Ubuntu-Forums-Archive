---
title: "No sound in new Koala installation"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by EulaMHorn on 2010-03-30
I have read everything I can get my hands on, and there seem to be many people without sound.  However, I can't seem to find anything from the suggestions that will work.  Please help a noob.:confused:

Thanks.

---

### Post by mörgæs on 2010-03-31
Sound was indeed the weak spot in 9.10. There has been many important improvements in the sound in 10.04, and rather than fighting with 9.10 I would go for the new one:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Though being in beta it is a very stable release, at least on all machines where I have tried it.

---

### Post by tommcd on 2010-03-31
> **EulaMHorn said:**
> I have read everything I can get my hands on, and there seem to be many people without sound.  However, I can't seem to find anything from the suggestions that will work.  Please help a noob.:confused:

First, open a terminal (applications > accessories > terminal) and run the **alsamixer** command. Use the arrow keys to turn all the sound levels all the way up. Then hit the **Esc** key twice to exit alsamixer. Then see if you have sound.
Second, try going to: system > preferences > sound, and try different options there, including using alsa instead of pulse audio if that is available as an option. Then hit the "test" button and see if you get sound.

If that does not work, then we need more info to try to solve your sound problem. What sound card do you have? Do you have more than one sound card (onboard, and a separate sound card)?
While in the terminal, report back the output of these commands:
```
aplay -l
```
This will tell us what sound card you have that is seen by Ubuntu.
```
lspci -k
```
This will list your hardware, including your sound card (probably listed as "Multimedia audio controller: ..."). The -k switch will tell us what driver is being used by each piece of hardware, including the sound card.
```
lsmod | grep -i snd
```
This will list all audio drivers in use on your system.

For reference, see this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
Write back if you need more help.

And welcome to the Ubuntu forums!

---

### Post by EulaMHorn on 2010-03-31
aplay -l returns the following:

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

And lspci -k returns the following:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
    Kernel modules: ati-agp
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Kernel modules: shpchp
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
    Kernel modules: shpchp
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
    Kernel driver in use: ohci_hcd
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
    Kernel driver in use: ohci_hcd
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
    Kernel driver in use: ehci_hcd
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
    Kernel driver in use: piix4_smbus
    Kernel modules: i2c-piix4
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
    Kernel driver in use: pata_atiixp
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
    Kernel driver in use: ATI IXP MC97 controller
    Kernel modules: snd-atiixp-modem
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
    Kernel driver in use: k8temp
    Kernel modules: k8temp
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
    Kernel modules: radeon, radeonfb
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5789 Gigabit Ethernet PCI Express (rev 21)
    Kernel driver in use: tg3
    Kernel modules: tg3
03:07.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
    Kernel driver in use: yenta_cardbus
    Kernel modules: yenta_socket
03:07.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394
03:07.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
    Kernel driver in use: tifm_7xx1
    Kernel modules: tifm_7xx1
03:07.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
03:09.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb


And lsmod | grep -i snd returns the following:

snd_atiixp_modem       11940  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
snd_atiixp             15720  2 
snd_ac97_codec        101216  2 snd_atiixp_modem,snd_atiixp
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_rawmidi            22176  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_pcm                75296  4 snd_atiixp_modem,snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  15 snd_atiixp_modem,snd_seq_oss,snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  3 snd_atiixp_modem,snd_atiixp,snd_pcm

I have already turned up all the volume slides in alsamixer, and when I go to system > preferences > sound there doesn't seem to be any choice.  The only thing I see is Internal Audio Analog Stereo Duplex.

Thank you so much for your reply.  Does this information clear up the problem for you?  Because I can't make any since of it. I really appreciate any assistance.

---

### Post by tommcd on 2010-03-31
> **EulaMHorn said:**
> 
 Does this information clear up the problem for you?  Because I can't make any since of it. I really appreciate any assistance.
It would seem that your sound card is now supported. It looks like you have the proper drivers loaded. This thread is a bit old, but try the suggestions posted here:
[http://ubuntuforums.org/archive/index.php/t-365342.html](http://ubuntuforums.org/archive/index.php/t-365342.html)

---

### Post by EulaMHorn on 2010-04-02
I tried all the suggestions at the sound troubleshooting page.  Nothing worked.  Then I tried running Ubuntu 10.04.  THAT was a disaster.  pages kept flickering and disappearing for no reason.  And there was STILL no sound at all.

I'm getting pretty discouraged.

---

### Post by mörgæs on 2010-04-03
> **EulaMHorn said:**
> pages kept flickering and disappearing for no reason.

Sorry, I don't understand. Which pages are you talking about?

---

### Post by Jose Catre-Vandis on 2010-04-03
> **EulaMHorn said:**
> I have read everything I can get my hands on, and there seem to be many people without sound.  However, I can't seem to find anything from the suggestions that will work.  Please help a noob.:confused:

Thanks.

Check you are a member of the audio group: See here
```
http://ubuntuforums.org/showthread.php?p=9041450
```

---

### Post by tommcd on 2010-04-03
> **EulaMHorn said:**
> aplay -l returns the following:

**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am not sure about this, but I think your problem may be that "aplay -l" lists 2 devices as sound cards, the second one is the modem listed there.
Can you post the output of:
```
cat /proc/asound/modules
```
If you only have 1 sound card (and you really do since the modem is not a sound card) then there should only be 1 device listed in the output from cat /proc/asound/modules.
If there are 2 devices listed, then we may need to blacklist the modem to get your sound to work. 
Try installing **alsamixergui** from the Ubuntu repos. This provides a graphical interface for using alsamixer that may make it easier for you to correctly select the proper sound device.
You sound card should be supported afaik. I can't think of anything else. Have you tried using alsa instead of pulse audio when you go to: system > preferences > sound?

**EDIT**
Also, see the suggestions posted here about sound in Ubuntu 9.10:
[http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)
and in the link posted there:
[http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html](http://drowninginbugs.blogspot.com/2009/10/caveats-for-audio-in-910.html)

---

