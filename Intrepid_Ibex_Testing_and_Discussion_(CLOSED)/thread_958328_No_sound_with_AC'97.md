---
title: "No sound with AC'97"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kasio on 2008-10-25
Since upgrading from Hardy to Intrepid, I have had no sound at all. I've tried changing the sound system in GNOME, but to no avail.

Here's the output from lshw:

```

        *-multimedia
             description: Multimedia audio controller
             product: AC'97 Sound Controller
             vendor: Silicon Integrated Systems [SiS]
             physical id: 2.7
             bus info: pci@0000:00:02.7
             version: a0
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=Intel ICH latency=32 maxlatency=11 mingnt=52 module=snd_intel8x0

```

I''m using an up to date Intrepid. Also, it seems Compiz to slower than before. The desktop cube used to work extremely smoothly, but now it sort of jerks.

---

### Post by zorkerz on 2008-10-25
Many peoples sound is getting muted in alsamixer. Open a terminal at type 'alsamixer -Dhw' then check that your PCM volume is turned up. Hope that helps. This thread has many people discussing their sound issues as well. [http://ubuntuforums.org/showthread.php?t=942529&highlight=sound](http://ubuntuforums.org/showthread.php?t=942529&highlight=sound)

---

### Post by kasio on 2008-10-25
I have a slight problem with alsamixer, it won't work. Here's the output:

> 
ALSA lib conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw

alsamixer: function snd_ctl_open failed for hw: No such file or directory


---

### Post by zorkerz on 2008-10-25
Man im sorry I don't know how to help. You could file a bug at launchpad. To make sure it gets looked at faster put in as much info as possible. I would start here [https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

good luck

---

### Post by kasio on 2008-10-25
OK, I'll try that

---

### Post by kasio on 2008-10-26
It was the wrong version of the alsa packages, from a ppa. Update manager hadn't changed them. I got the official Intrepid ones, and all is fine.

---

