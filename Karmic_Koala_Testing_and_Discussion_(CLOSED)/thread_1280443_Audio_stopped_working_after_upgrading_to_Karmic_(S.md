---
title: "Audio stopped working after upgrading to Karmic (SB Audigy)"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Lazy123 on 2009-10-02
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/440260](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/440260)

Upgrading from Jaunty went pretty well except sound stopped working. Any tips would be appreciated.

---

### Post by ljrmorgan on 2009-10-02
Try running alsamixer in a terminal to see the different levels, try turning up the PCM values.

Also, maybe check to see if your onboard sound is disabled.

My audigy 2 works OK on Karmic.

---

### Post by Lazy123 on 2009-10-02
> **ljrmorgan said:**
> Try running alsamixer in a terminal to see the different levels, try turning up the PCM values.

Also, maybe check to see if your onboard sound is disabled.

My audigy 2 works OK on Karmic.

[IMG]http://img143.imageshack.us/img143/450/screenshotalsa.png[/IMG]

I have disabled my onboard audio from BIOS so that shouldn't be the problem. Maybe I should try the Live CD and see if audio works with it.

---

### Post by ljrmorgan on 2009-10-02
> **Lazy123 said:**
> I have disabled my onboard audio from BIOS so that shouldn't be the problem. Maybe I should try the Live CD and see if audio works with it.

I suppose trying with the live CD is worth a shot, I'd still double check that nothing is trying to use the onboard sound - I disabled mine in the BIOS, but I had to make some tweaks on ubuntu too. Make sure the audigy card is selected under hardware in system>preferences>sound.

When I run alsamixer my card is listed as SB Audigy 2 ZS and the chip as sigmatel something. Not sure why yours is just displaying "pulseaudio"

EDIT - also check the levels & card etc under the ouput tab once you've opened up sound preferences
EDIT 2 - I also have loads and loads of different levels in alsamixer, not just 4, though I think we have a similar card,

---

### Post by Lazy123 on 2009-10-02
> **ljrmorgan said:**
> When I run alsamixer my card is listed as SB Audigy 2 ZS and the chip as sigmatel something. Not sure why yours is just displaying "pulseaudio"

EDIT - also check the levels & card etc under the ouput tab once you've opened up sound preferences
EDIT 2 - I also have loads and loads of different levels in alsamixer, not just 4, though I think we have a similar card,

Maybe my alsa settings got corrupted by the upgrade. Do you have any idea how can I get my  Audigy to show up in alsamixer instead of pulseaudio?

Below is ~/.asoundrc.asoundconf 
```

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
pcm.!default { type pulse }
ctl.!default { type pulse }

```

---

### Post by Jonie on 2009-10-02
I have the same card. It seems that the lower level hardware controls for alsa interface are gone for good from gnome applet. You can install alsamixergui or alsamixer and start it from commandline with the option -c 0 (to specify first available sound interface, in my case its the SB Audigy). The devs should bring back the ability to choose the device in gnome sound applet or the settings like capture feedback, selection for some recording sources will not be available.

---

### Post by ljrmorgan on 2009-10-02
> **Lazy123 said:**
> Maybe my alsa settings got corrupted by the upgrade. Do you have any idea how can I get my  Audigy to show up in alsamixer instead of pulseaudio?

Below is ~/.asoundrc.asoundconf 
```

# ALSA library configuration file managed by asoundconf(1).
#
# MANUAL CHANGES TO THIS FILE WILL BE OVERWRITTEN!
#
# Manual changes to the ALSA library configuration should be implemented
# by editing the ~/.asoundrc file, not by editing this file.
pcm.!default { type pulse }
ctl.!default { type pulse }

```

I don't even have this file - is there anything I can post that might help? I haven't mucked around with editing files, mine just worked after using the GUI sound preferences thing and alsamixer.

---

### Post by Lazy123 on 2009-10-02
> **ljrmorgan said:**
> I don't even have this file - is there anything I can post that might help? I haven't mucked around with editing files, mine just worked after using the GUI sound preferences thing and alsamixer.

Hmm... I'm not home at this moment but maybe I should delete these old files and reboot. Over SSH-connection I could change lots of SB Audigy settings with "alsamixer -c 0" command but "alsamixer" still shows those pulseaudio settings. Later tonight I will test deleting those alsa files and if that Live CD has audio.

---

### Post by Lazy123 on 2009-10-02
I tried removing those .asoudrc files but that did nothing. After that was Live CDs turn, but audio didn't work with Live CD either.

There are some clicks from the speakers at startup (as there are when the system is starting up and something is trying to initialize audio), but maybe something fails after that?

[EDIT] Something positive has happened. "alsamixer" now shows my Audigy instead of Pulseaudio.

[EDIT2] 
[http://img88.imageshack.us/img88/8996/screenshotalsa1.png](http://img88.imageshack.us/img88/8996/screenshotalsa1.png)
[http://img225.imageshack.us/img225/8981/screenshotalsa2.png](http://img225.imageshack.us/img225/8981/screenshotalsa2.png)
[http://www.alsa-project.org/db/?f=e01bacdd794cca6132fd8e3d2bfd9b2afab55d44](http://www.alsa-project.org/db/?f=e01bacdd794cca6132fd8e3d2bfd9b2afab55d44)

[EDIT3]
Solved: I enabled all the settings from alsa mixer and sound started to work. Some of those settings must have disabled audio by default in Karmic.

---

