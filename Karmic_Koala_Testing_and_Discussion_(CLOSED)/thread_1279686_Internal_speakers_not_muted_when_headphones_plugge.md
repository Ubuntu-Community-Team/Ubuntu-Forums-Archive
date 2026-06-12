---
title: "Internal speakers not muted when headphones plugged"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kungfutse on 2009-10-01
Hi,

I have an older Dell Precision 390 machine to play around with and I decided to put Karmic Alpha6 to the test but ran into following problem.

Audio is outputted through both the internal speaker and headphones and there is now way to select any options for it either through pulseaudio volume control or alsamixer to remedy this.

I tried running alsactl init, but got the following errors:
```

$ alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9200" "HDA:83847690,102801de,00102201" "0x1028" "0x01de"
Hardware is initialized using a guess method
/usr/share/alsa/init/default:51: control element not found
/usr/share/alsa/init/default:52: missing closing brace for format
/usr/share/alsa/init/default:52: error parsing CTL attribute
/usr/share/alsa/init/default:52: invalid rule

```

After fixing the typos I still get the following to errors:
```

alsactl init
Unknown hardware: "HDA-Intel" "SigmaTel STAC9200" "HDA:83847690,102801de,00102201" "0x1028" "0x01de"
Hardware is initialized using a guess method
/usr/share/alsa/init/default:51: control element not found
/usr/share/alsa/init/default:52: control element not found

```

So I'm guessing for some reason alsa is no longer recognizing the card where as in Jaunty it worked perfectly.

Here are the outputs of lspci -v and aplay -l
```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Dell Device 01de
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at efffc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
-----------------------------------------------------------------------
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by raiwo on 2009-10-01
i had similar problem with my toshiba satellite laptop & solution was:

> fixed by adding following line:

options snd-hda-intel position_fix=1 model=lenovo

in /etc/modprobe.d/alsa-base.conf

don't know if this works for dell but you get the idea what to do...

---

### Post by kungfutse on 2009-10-01
> **raiwo said:**
> i had similar problem with my toshiba satellite laptop & solution was:



don't know if this works for dell but you get the idea what to do...
Tried the position fix with all the possible Dell models I could find from the ALSA documentation for the STA9200 but no help.

I also tried without the model but no help.

Looking at dmesg the different output/input jacks are detected correctly, but for some reason the internal speakers aren't muted.

---

### Post by raiwo on 2009-10-01
did you do reboot between tries? for this to work had to reboot my machine to get it working. Also try other models as dell as you can see i use lenovo while my laptop is made by toshiba...

---

### Post by kungfutse on 2009-10-01
> **raiwo said:**
> did you do reboot between tries? for this to work had to reboot my machine to get it working. Also try other models as dell as you can see i use lenovo while my laptop is made by toshiba...
Yes, I did reboot between changes. Thankfully Karmic boots really fast. 

I guess I'll start trying out different model options for the STAC9200 to see if there's any help.

---

### Post by kungfutse on 2009-10-01
Tried a few different model settings: auto, ref, 3stack, lenovo and none worked :/

I finally just opened the chassis and disconnect the internal speaker wire from the motherboard.

I guess the jack sensing in either pulseaudio or alsa is just broken with this particular audio codec.

---

### Post by fut21 on 2009-10-02
Why not bug it in launchpad?

---

