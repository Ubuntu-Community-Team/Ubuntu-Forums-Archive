---
title: "can't configure sound.."
date: 2005-08-01
forum: Installation &amp; Upgrades
---

### Post by fargoth on 2005-08-01
i got C-Media's CMI9880 as the onboard sound chip (giga-byte 915P DOU mobo).
 lspci -v :
[B]0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Giga-byte Technology: Unknown device a005
        Flags: bus master, fast devsel, latency 0, IRQ 5
        Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] #10 [0091][/B] 

i see 
[B]alsa-base 1.0.8-4ubuntu
alsa-utils 1.0.8-lubuntu1
gstreamer0.8-alsa 0.8.8-lubuntu4
libpt-plugins-alsa 1.8.4-1[/B]
installed.

but it seems my soundcard wasnt found... how do i install it?

[B]aplay -l
aplay: device_list:200: no soundcards found...[/B]

-more info from me typing things =P-

the command:** lsmod **
yields:

[B]Module                  Size  Used by
snd_pcm_oss            47652  0
snd_pcm                84872  1 snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  1 snd_pcm
snd_mixer_oss          16768  1 snd_pcm_oss
snd                    50276  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  1 snd
[/B]
the command :
**# alsamixer**

yields:

**alsamixer: function snd_ctl_open failed for default: No such device**

alsaconf doesnt work:
**bash: alsaconf: command not found**



any suggestions?

---

### Post by fargoth on 2005-08-01
i got more debugging =P

copied the script from [http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
and ran it.
it says:
[B]ALSA Audio Debug v0.0.9 - Mon Aug  1 09:18:05 BST 2005
[http://alsa.opensrc.org/?page=aadebug](http://alsa.opensrc.org/?page=aadebug)

Kernel ----------------------------------------------------
Linux ubuntu 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_pcm_oss            47652  0
snd_pcm                84872  1 snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd_page_alloc          9604  1 snd_pcm
snd_mixer_oss          16768  1 snd_pcm_oss
snd                    50276  4 snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.6 (Sun Aug 15 07:17:53 2004 UTC).
Compiled on Jun 24 2005 for kernel 2.6.10-5-386.
--- no soundcards ---
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  hwC2D3    midiC1D2  midiC3D1  pcmC0D4c  pcmC1D3p  pcmC2D3c  pcmC3D2pcontrolC1  hwC3D0    midiC1D3  midiC3D2  pcmC0D4p  pcmC1D4c  pcmC2D3p  pcmC3D3ccontrolC2  hwC3D1    midiC1D4  midiC3D3  pcmC0D5c  pcmC1D4p  pcmC2D4c  pcmC3D3pcontrolC3  hwC3D2    midiC1D5  midiC3D4  pcmC0D5p  pcmC1D5c  pcmC2D4p  pcmC3D4chwC0D0     hwC3D3    midiC1D6  midiC3D5  pcmC0D6c  pcmC1D5p  pcmC2D5c  pcmC3D4phwC0D1     midiC0D0  midiC1D7  midiC3D6  pcmC0D6p  pcmC1D6c  pcmC2D5p  pcmC3D5chwC0D2     midiC0D1  midiC2D0  midiC3D7  pcmC0D7c  pcmC1D6p  pcmC2D6c  pcmC3D5phwC0D3     midiC0D2  midiC2D1  pcmC0D0c  pcmC0D7p  pcmC1D7c  pcmC2D6p  pcmC3D6chwC1D0     midiC0D3  midiC2D2  pcmC0D0p  pcmC1D0c  pcmC1D7p  pcmC2D7c  pcmC3D6phwC1D1     midiC0D4  midiC2D3  pcmC0D1c  pcmC1D0p  pcmC2D0c  pcmC2D7p  pcmC3D7chwC1D2     midiC0D5  midiC2D4  pcmC0D1p  pcmC1D1c  pcmC2D0p  pcmC3D0c  pcmC3D7phwC1D3     midiC0D6  midiC2D5  pcmC0D2c  pcmC1D1p  pcmC2D1c  pcmC3D0p  seq
hwC2D0     midiC0D7  midiC2D6  pcmC0D2p  pcmC1D2c  pcmC2D1p  pcmC3D1c  timer
hwC2D1     midiC1D0  midiC2D7  pcmC0D3c  pcmC1D2p  pcmC2D2c  pcmC3D1p
hwC2D2     midiC1D1  midiC3D0  pcmC0D3p  pcmC1D3c  pcmC2D2p  pcmC3D2c

CPU -------------------------------------------------------
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
cpu MHz         : 3014.979

RAM -------------------------------------------------------
MemTotal:       516500 kB
SwapTotal:      248968 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)[/B]

---

### Post by heimo on 2005-08-01
What happens if you run
 ```
sudo modprobe snd_hda_intel

```

---

### Post by fargoth on 2005-08-01
FATAL: Module snd_hda_intel not found.

---

### Post by fargoth on 2005-08-01
ive just noticed that there is more appropriate place for this isssue on the hardware section... sorry for posting it here, if there a moderator around kindly move this thread to that section, i don't want to double post and spam this forum...
anyway, untill this post has moved please help  :-)

---

### Post by varunus on 2005-08-01
Hoary doesn't include Intel HDA sound support out of the box.  However, its easy to set up.  

Here you go:
[http://wiki.ubuntu.com/HdaIntelSoundHowto](http://wiki.ubuntu.com/HdaIntelSoundHowto)

Follow the second method to install the driver instead of the first, the second one is cleaner.  Make sure you have the "build-essential" package installed from synaptic.

---

### Post by fargoth on 2005-08-01
thanks, ive found the wiki before i saw this post, and followed the first one..
sound works!!!
but i cant seem to play mp3's it says i dont have the codec...
i tried installing 
[B]development files for libavcodec
This is the codec library from the ffmpeg project. It supports most existing
encoding formats (MPEG, DivX, MPEG4, AC3, DV, ...).

This package contains the header files and static libraries needed to
compile applications or shared objects that use libavcodec.[/B] 
but it doesnt affect anything...

how do i get mp3's to play (and divX movies...)

---

### Post by fargoth on 2005-08-01
well, i figured out a workaround... can't use totem or music player, but ive installed bplayer and mplayer instead... works fine under esd

---

### Post by varunus on 2005-08-02
Here's howto install all codecs you should ever need (makes rhythmbox, totem, etc. play MP3s and more):

[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

Make sure to enable extra repositories as stated on that site.

---

