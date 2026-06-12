---
title: "Sound only crackling now?"
date: 2009-03-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nixie Pixel on 2009-03-24
Hi, I am sorry for the noobish question, but something broke my sound recently, I think it may have been a recent update.  Where I used to play sound just fine, now I get only crackling, and no sound, no matter what I do (crackling instead of a song at load, youtube videos, etc).

Based on other messages on this forum, I tried enabling Intel HD Conexant Audio (Digital) ALSA for each setting, except for the capture device set to analog.  I also enabled and checked the IEC958 switch and PLM? checkbox.  Neither worked.  I updated to a more recent version of 2.6.8-11, but it didn't help.  I also marked everything labelled "ALSA" in Synaptec for reinstallation, but it did nothing...

Is there anything else I can try to fix this?

Thanks!

---

### Post by danwood76 on 2009-03-24
It will be a pulseaudio issue.
Check the first sticky regarding it.

In a recent update glitch free audio was disabled this may have caused issues with your alsa drivers.
You can re enable it by editing the /etc/pulse/default.pa and changing this line:
```

load-module module-hal-detect tsched=0

```
to:
```

load-module module-hal-detect

```
If that doesnt work I would change it back though

---

### Post by Nixie Pixel on 2009-03-24
Didn't work, thanks though.  I'll check the thread!

---

### Post by danwood76 on 2009-03-24
I forgot to say once that is changed its necessary to restart pulseaudio.

so first do:
```

pulseaudio -k

```
to kill it then:
```

pulseaudio -D

```
to restart (deamonise)

---

### Post by awam66 on 2009-03-24
I remember having this issue some time ago with intrepid, it was caused by the PCM volume control being set to zero.
Try turning it up in volume control.

---

### Post by crimsun on 2009-03-24
> **danwood76 said:**
> In a recent update glitch free audio was disabled this may have caused issues with your alsa drivers.

There is no way that PulseAudio can cause issues with the ALSA drivers. PulseAudio uses whatever the kernel driver provides.

I have linked to a test kernel in the sticky thread that resolves the majority of audible audio aberrations (though not the initial mute state) apparent in PulseAudio. See bug 330814.

---

### Post by Roger E Critchlow Jr on 2009-03-24
Ah, I had the same problem, same symptoms.  One day, the login sounds went away, replaced by crackling, and every other audio source came out as crackling.  Thank you for bringing it to the top of the forum.

When I attempted the "load-module module-hal-detect tsched=0" hack suggested above, I got a bunch of messages about missing privileges when I ran "pulseaudio -k" or "pulseaudio -D".  The messages mentioned the pulse-rt group, that would be pulse-real-time as in low latency audio.  I added myself to the pulse-rt group, ie appended my user name to that line in /etc/group, and rebooted.  (I'm never sure when group membership changes take effect, and a reboot should never hurt when figuring these things out.)

After the boot, still cracking, but I can "pulseaudio -k" and "pulseaudio -D" without the nasty messages, so I drop the "load-module module-hal-detect tsched=0" hack as a non-starter.

Then I open up the volume control and notice that the PCM volume is turned all the way down, again.  Furthermore, when I open the Preferences on the volume control, I notice that the displayed controls are not the ones that are checked.  So I fuss with the preferences until the checked controls are the ones that are displayed.  This probably rewrites my alsa configuration somewhere and alters the list of saved controls so they agree with the ones that the driver is using.

I go back to my shell window and try "aplay /usr/share/sounds/question.wav", again, and it works.  Earlier aplay reported that it couldn't open a connection, so it's apparently no longer the alsa player but the alsa player rerouted through pulse.  But as a quick check it works, and SongBird is working again.

So try that: add yourself to pulse-rt in /etc/group; fuss with the volume control until the checked preferences and the volume controls agree.

-- rec --

---

### Post by Nixie Pixel on 2009-03-26
Thank you Roger, this worked like a charm!

---

