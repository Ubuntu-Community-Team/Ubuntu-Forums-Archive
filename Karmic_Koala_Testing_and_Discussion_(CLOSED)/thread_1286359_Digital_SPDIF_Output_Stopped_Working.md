---
title: "Digital SPDIF Output Stopped Working"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by seanUSXIII on 2009-10-08
After upgrading to Karmic Beta, my digital audio output stopped working. If I set the audio preferences to any of the analog settings under "Hardware", it works just fine through the headphones, but no output through the coaxial cable. Is this a known bug? Is Karmic fully based on Pulseaudio, because I had to edit my .asoundrc file to get this working in other releases. My guess is that if it's using Pulseaudio now, the .asoundrc file is irrelevant. Am I right? If so, how can I input these options elsewhere? Here's some relevant information

lspci:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

lsmod:

```
Module                  Size  Used by
binfmt_misc             8356  1 
xt_limit                2176  8 
xt_tcpudp               2780  35 
ipt_LOG                 5344  8 
ipt_MASQUERADE          2204  0 
xt_DSCP                 2844  0 
ipt_REJECT              2812  1 
nf_conntrack_irc        4992  0 
nf_conntrack_ftp        6880  0 
xt_state                1820  6 
iptable_nat             5500  0 
nf_nat                 17808  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      13352  9 iptable_nat,nf_nat
nf_conntrack           67608  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1756  1 nf_conntrack_ipv4
iptable_mangle          3452  0 
snd_atiixp             15720  1 
snd_ac97_codec        101216  1 snd_atiixp
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_atiixp,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  12 snd_atiixp,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_atiixp,snd_pcm
iptable_filter          3100  1 
nvidia               9586376  36 
ati_agp                 6760  0 
agpgart                34988  2 nvidia,ati_agp
ip_tables              11692  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16544  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,ip_tables
i2c_piix4               9932  0 
ppdev                   6688  0 
k8temp                  4188  0 
psmouse                56180  0 
serio_raw               5280  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52544  0 
usbhid                 38208  0 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
```

aplay -l:

```
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Any help is appreciated!!!

---

### Post by hofsmo on 2009-10-09
I get sound through my headset no matter what settings I choose under hardware. However in earlier ubuntu releases choosing digital would give me sound from my speakers through toslink to a receiver. I would really appreciate if anyone have a solution to this.

---

### Post by rtalcott on 2009-10-09
I have one machine...an eVga motherboard with working digital out...but have to ecs boards with only analog...all the boards have nVidia chip sets...I can see volume on the PA volume Control when it's set to the digital hardware and the outputs are not muted but I get no digital out.
rt

---

### Post by hofsmo on 2009-10-09
I managed to fix it, installing gnome-alsamixer and activating the appropriate switch for digital output, in my case IEC958 Output. However it shouldn't be necessary to install additional software to get digital output.

---

### Post by rtalcott on 2009-10-09
I check the digital sources in gnome-alsa-mixer but they never STAY checked...
rt

---

### Post by seanUSXIII on 2009-10-11
I tried gnome-alsamixer, and it checking any of the boxes does not solve the problem. It really is no different that going into alsamixer in the command line. Still no results...

---

### Post by aVirulence on 2009-10-12
I have the same problem... No sound, although the digital output shows up, is selected in the Pulsaudio volume control program *and* I tried gnome-alsamixer..

---

### Post by yelo3 on 2009-10-12
Go to
System->Preferences->Sound
Hardware->Profile

What's selected?

---

### Post by aVirulence on 2009-10-12
Digital Stereo (IEC958) Output + Analog Stereo Input

---

### Post by seanUSXIII on 2009-10-13
> **aVirulence said:**
> Digital Stereo (IEC958) Output + Analog Stereo Input

Same here... Although I have tried all those options. I've pretty much exhausted the GUI options. Is there a conf file I can toy with? :confused:

---

### Post by aVirulence on 2009-10-14
After a sudo apt-get update && sudo apt-get upgrade everything is working again!

---

### Post by seanUSXIII on 2009-10-21
I've tried pretty much everything I could think of to fix this, and nothing I did helped. I had it working for a few minutes, but then it stopped working again...

I eventually got sick of this problem and went back to 9.04. Hopefully this problem isn't also in the final release of 9.10

---

