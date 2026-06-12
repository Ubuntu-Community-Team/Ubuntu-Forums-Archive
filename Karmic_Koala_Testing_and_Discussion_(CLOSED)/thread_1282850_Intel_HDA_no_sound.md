---
title: "Intel HDA no sound"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by canadianwriterman on 2009-10-04
With yesterday's updates, sound disappeared on my laptop with onboard Intel HDA sound. Complete silence throughout the system. Anyone else experience that?

---

### Post by rogerdean on 2009-10-05
I've had no sound on Intel HDA since Alpha 5...

---

### Post by Dusal on 2009-10-05
I installed ALSA from source and now with sound. But there is problem with serious system crash. :( I submitted bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442799](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442799).

---

### Post by wizard10000 on 2009-10-05
> **rogerdean said:**
> I've had no sound on Intel HDA since Alpha 5...

Mine comes and goes and the problem has almost always been policykit.  Try this in a terminal window -```
aplay -l
```
If you see a "no soundcards detected" try this -```
**sudo** aplay -l
```If your soundcard shows up it's because your user account doesn't have permission to access the soundcard.

Hope this helps -

---

### Post by soro2005 on 2009-10-05
@rogerdean: On my Thinkpad X32, [this]("https://answers.launchpad.net/ubuntu/+question/73060") may have been the relevant lead. Not quite sure, but all of the sudden, sound came back after I'd enabled the hardware hotkeys.

---

### Post by canadianwriterman on 2009-10-05
Output from:

```
aplay -l
```

is:

```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

So the device is seen. However, there is no sound from the speakers at all.

---

### Post by wizard10000 on 2009-10-05
Last night's updates fixed sound for me.

Again.

:)

---

### Post by slacklin on 2009-10-05
I also lost sound after upgrading from 9.04 to 9.10. Ive got intel hda onboard with a biostar mobo.

---

### Post by sparta644 on 2009-10-06
> **canadianwriterman said:**
> So the device is seen. However, there is no sound from the speakers at all.

Same here. Identical output, no sound at all...

Ubuntu 9.10 on ZaReason UltraLapSR (Asus S37E).
And I'm a bloddy newbie in here (jftr)

Cheers
Peter

---

### Post by sparta644 on 2009-10-06
> **sparta644 said:**
> Same here. Identical output, no sound at all...


The workaround explained in [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/421250/comments/15") worked for me. Sound is back. :)

Cheers
Peter

---

### Post by jou770d on 2009-10-08
I was about to post a new thread and found this.
I'm having the same problem, I have also been using the workaround mentioned in the previous post:
```
sudo alsa force-reload
```

But I have to do that each time I start the device. So, I was hoping to find an actual solution.
I've thought about making a startup script to automate this, but it's still just a messy workaround.

I'm (dual)booting 64bit Karmic (with Win7) on an Asus M51va, these are the audio devices:

```

amarus@Zeus-Ubuntu:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]

```
```

amarus@Zeus-Ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```

amarus@Zeus-Ubuntu:~$ sudo lshw -C Multimedia
  *-multimedia            
       description: Audio device
       product: RV635 Audio device [Radeon HD 3600 Series]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:01:00.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:34 memory:fdfec000-fdfeffff
  *-multimedia
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:33 memory:fdef8000-fdefbfff

```

alsamixer can normally see the existence of two devices, but pulseaudio won't see the Intel device.

And one last thing, I can't get the built-in mic to work no matter what I do. However, I couldn't get it to work with Jaunty either, it only worked on Vista and 7 so far.

I would appreciate any ideas, thanks in advance.

---

### Post by rogerdean on 2009-10-08
Hmmm... when I try that command I get this...

```
roger@roger-laptop:~$ sudo alsa force-reload
[sudo] password for roger: 
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
Terminating processes: 1794lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
 6498lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
 6512lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
 6545lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
 (with SIGKILL:) 6586lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
 (failed: processes still using sound devices: 6600(pulseaudio)).
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/roger/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 6600(pulseaudio). 
Unloading ALSA sound driver modules: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-pcm snd-timer snd-page-alloc).
Loading ALSA sound driver modules: snd-hda-codec-analog snd-hda-intel snd-hda-codec snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
roger@roger-laptop:~$ 


```

Can anyone suggest what on earth this means? :)

Cheers

---

