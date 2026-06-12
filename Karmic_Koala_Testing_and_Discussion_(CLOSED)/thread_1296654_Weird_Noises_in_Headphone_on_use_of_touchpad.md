---
title: "Weird Noises in Headphone on use of touchpad"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by adempewolff on 2009-10-20
When I am wearing headphones after maybe 10 seconds everytime I touch or move a finger on the touchpad, and weird noise (low static) will come out of the headphones.  It stops when I stop moving my finger on the touchpad.  If I unplug the headphones and plug them back in this effect stops for about 10 seconds then starts again.  This has startted after rebooting from a kernel panic (they are happening pretty regularly, but I believe the problem is related with wireless, bugs in launchpad already).  While looking in my log files I found these entries which I don't think are too important but do provide the model for my touchpad and headphone jack (in bold), if that helps at all.  I can provide more information as needed, I just thought I'd throw this problem out there to see if I am crazy or if this has ever happened to someone else.

Oct 20 22:08:28 austin-laptop kernel: [    7.206733] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
Oct 20 22:08:28 austin-laptop kernel: [    7.227424] input: **AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input8**
Oct 20 22:08:28 austin-laptop kernel: [    7.295624] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input9
Oct 20 22:08:28 austin-laptop kernel: [    7.377962] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
Oct 20 22:08:28 austin-laptop kernel: [    7.378043] input: **HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11**

Turning the volume up or down (via the hardware buttons) also will stop this sound (and lock the touchpad but I think this is because Karmic by default locks the touchpad on keyboard use).  Just typing on the keyboard while move the touchpad does not produce this effect.  wierd.

---

### Post by adempewolff on 2009-10-20
restarted and it is still occurring.  however when I start playing a file in rhythmbox the effect stops...   I can't decide whether to file this as a bug against pulseaudio or whatever driver is managing the touchpad (much less would I know how to find the later...).

---

### Post by NRDNick on 2009-10-21
try unplugging the laptop from the charger, does the sound go away? If so the sound you hear is most likely some sort of ground loop problem. I have the same issue when I send sound from my laptop to the input on my pc.

---

### Post by adempewolff on 2009-10-21
unplugging the laptop does nothing.  I think it is a software problem.  This problem went away for day and then just started again when I just had another kernel panic and rebooted.

It is hard to describe the sound.  When I moved my finger on the touchpad fast or at normal speeds, it just sounds like static.  When I slow down how fast I move the finger though... it resolves into individual ticks, that happen at a frequency corresponding to the speed my finger moves on the touchpad.

It seems as if the input of the touchpad is somehow being read by pulseaudio as another mic or something.

Also, opening up "Sound Preferences" from the sound icon on the panel stops this effect.  It resumes about 15 seconds or so after closing the preferences window (you can hear a slight sound on opening the preferences, and then 15 seconds after closing it, as if it is switching channels or something).

---

### Post by adempewolff on 2009-10-21
bug filed against pulseaudio [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/457710](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/457710)

hopefully that is the right package...

---

