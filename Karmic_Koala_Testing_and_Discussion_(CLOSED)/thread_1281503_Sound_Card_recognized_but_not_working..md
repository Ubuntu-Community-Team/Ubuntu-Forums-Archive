---
title: "Sound Card recognized but not working."
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Chesh on 2009-10-03
I am having issues with sound playback in the Karmic beta, no sound at all.

lspci output:

```
0:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Lenovo Device 20f2
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fc220000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

aplay  output:

```
aplay: device_list:223: no soundcards found...

```

When I try to run alsamixer I get:

```
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

I have tried reinstalling the also packages, removing my .pulse and pulse-cookie directories and restarting pulseaudio with no efect.

This is a thinkpad W500, it only had some very minor issues in jaunty.

---

### Post by abhiroopb on 2009-10-25
I am having the EXACT same problem. Did you manage to find a solution?

Thanks!

---

### Post by Chesh on 2009-10-25
I never found a definitive answer, but after a couple of kernel upgrades the problem disappeared, I would just double check and make sure the grub menu updated (I had problems with that too) and that you're booting with the latest one.

---

### Post by abhiroopb on 2009-10-25
I am definitely booting with the latest one.

Actually, I made a mess of things. Basically, I added some repo's that totally destroyed my dependencies and I had to re-install a lot of packages (including alsa and pulse). I also had to re-install my kernel and numerous other things.

In between doing all this my configuration got messed up. Before adding the repo everything was fine. So, I assume if I were to re-install jaunty at this point everything would work fine. But, of course I'd rather not re-install everything.

What the basic commands show me:

```

$ aplay -l
aplay: device_list:217: no soundcards found...

```

```

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

[code]
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Hewlett-Packard Company Device 30a5
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
[code]

I've done everything in these guides: 
http://ubuntuforums.org/showthread.php?t=205449
http://ubuntuforums.org/showthread.php?t=1130384
http://ubuntuforums.org/showthread.php?t=1043568
http://ubuntuforums.org/showthread.php?t=843012

Nothing has worked for me. In fact I've done everything twice I think!

Please help!!

---

### Post by Ulsak on 2009-10-25
and what happens when ( in Terminal)
[B]
sudo alsa force-reload[/B]?

---

### Post by abhiroopb on 2009-10-25
```

$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
Terminating processes: 16943lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/abhiroop/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-usb-lib snd-hwdep snd-pcsp snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.
Loading ALSA sound driver modules: snd-hda-intel snd-usb-audio snd-usb-lib snd-hwdep snd-pcsp snd-pcm-oss snd-mixer-oss snd-pcm snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

```

Also:

```

$ speaker-test

speaker-test 1.0.18

Playback device is default
Stream parameters are 48000Hz, S16_LE, 1 channels
Using 16 octaves of pink noise
ALSA lib confmisc.c:768:(parse_card) cannot find card '0'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
ALSA lib pcm.c:2205:(snd_pcm_open_noupdate) Unknown PCM default
Playback open error: -2,No such file or directory

```

Obviously before I had these problems this would work fine and I'd hear "left speaker", "right speaker" etc.

---

### Post by abhiroopb on 2009-10-25
Instead of completely hijacking this thread I started a new one:

[http://ubuntuforums.org/showthread.php?t=1300743](http://ubuntuforums.org/showthread.php?t=1300743)

Thanks for the help!

---

