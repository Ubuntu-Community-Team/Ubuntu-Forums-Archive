---
title: "No HDMI audio after upgade to 13.04"
date: 2013-04-26
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2013-04-26
Just upgraded to 13.04

HDMI audio was working in 12.10 with the radeon.audio=1 flag in /etc/default/grub

Flag is still in grub but i've no audio over HDMI

anyone else had a problem with audio on 13.04? 
Or is it just my bad luck ^_^

any help is gratefully welcomed

```


bill@zotac:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
 
bill@zotac:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, HDMI 0
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, HDMI 0
    Hardware device with all software conversions
sysdefault:CARD=SB
    HDA ATI SB, ALC892 Analog
    Default Audio Device
front:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Front speakers
surround40:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample mixing device
dmix:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct sample snooping device
hw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=SB,DEV=0
    HDA ATI SB, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=SB,DEV=1
    HDA ATI SB, ALC892 Digital
    Hardware device with all software conversions

```

---

### Post by Alan.Brown on 2013-04-26
I have just upgraded to Xubuntu 13.04 and I have no sound.   **gnome-alsamixer** crashes each time I try to use it.   No sound output from VLC and other players.

---

### Post by jelies on 2013-04-26
I'm also having exactly the same issue with Ubuntu 13.04. radeon.audio=1 is being ignored. I have tried to install latest ATI propietary drivers (13.4) but problem still persist.

---

### Post by tmette on 2013-04-26
Same thing here, it's not even recognizing it as a selection in the Sound Settings.

It's already a bug and should be fixed in the next kernel update:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984)

---

### Post by Alan.Brown on 2013-04-26
I found the solution here - **> [http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)**

In Terminal I entered **alsamixer** then I found the PCM setting muted - unmuted it and everything now works

I have found many settings have been changed after upgrading to 13.04

---

### Post by j2bv16 on 2013-04-26
Sometimes the problem solve itsef. Sometimes you must go to alsamixer and un-mute the outputs

---

### Post by blackdalek on 2013-04-26
I would suggest that the issue some are experiencing of the audio being muted (fixable through alsamixer) is totally unrelated to the issue of there being no HDMI audio after upgrade to 13.04.

I too have no HDMI audio at all in 13.04. i.e., it no longer exists as an available device in sound settings - NOT a muted device.

The device existed in 12.10, now it is gone.

---

### Post by Alan.Brown on 2013-04-27
In my case the only thing that had changed after the upgrade was that the **alsamixer** settings had changed (so had the settings for several other things).

---

### Post by jaykumar_2001 on 2013-04-27
This will fix it....[http://askubuntu.com/questions/285920/no-sound-through-hdmi-out-13-04]("http://askubuntu.com/questions/285920/no-sound-through-hdmi-out-13-04")

---

### Post by jelies on 2013-04-27
> **blackdalek said:**
> I would suggest that the issue some are experiencing of the audio being muted (fixable through alsamixer) is totally unrelated to the issue of there being no HDMI audio after upgrade to 13.04.

It's totally unrelated. The audio is not muted for me, alsamixer is OK, but after upgrading to 13.04 HDMI audio is gone and the HDMI entry at sound settings selection has dissapeared.

---

### Post by solitaire on 2013-04-27
The no HDMI audio is a bug.
They didn't add the correct modules in to the kernel for some types of HDMI audio support. ( [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761) & [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169984) )

Workaround / Fix is to install a new kernel:
 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.8-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.8.8-raring/)

This kernel works for me. HDMI is now in the list of available devices and I have sound.

---

### Post by SeijiSensei on 2013-08-30
I finally broke down and installed the 3.8.0-29 kernel on my Kubuntu 13.04 system.  The HDMI audio device is no longer detected, and the option is greyed out in System Settings > Multimedia > Phonon.  It was working on 3.8.0-25.

I have a Radeon 6770M and am running the fglrx proprietary driver.

These are the kinds of things that must drive less-experienced users up the wall!

Update:  Jockey told me that it was using the "FireGL" driver.  I tried the alternative proprietary driver; the HDMI interface is still greyed out.

---

