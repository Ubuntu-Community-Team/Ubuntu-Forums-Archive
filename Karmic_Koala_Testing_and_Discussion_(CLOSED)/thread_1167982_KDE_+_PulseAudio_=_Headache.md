---
title: "KDE + PulseAudio = Headache"
date: 2009-05-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Darkshade on 2009-05-23
...at least for me.

I had perfect sound by default - no issues at all but I needed pulseaudio to get sound from my 2 audio cards at the same time with the simultaneous output option (as far as I know using PA is the only way to do this, please correct me if I'm wrong!).

The good news are that I have sound in both my 5.1 speakers on one card and headphones in the other, as expected and as I had it working flawlessly in Ubuntu Jaunty with Gnome.

The bad news are that audio playback is driving me crazy. When listening to music in Amarok (and not only, same thing happens with Juk) every once in a while it starts playing almost twice faster and really distorted. Then starts playing slower (still distorted) and then faster again.

I remember seeing a forum post some time ago saying that PA shouldn't be used in KDE for some reason (doesn't make much sense, although seeing the results might be correct).


What I want to know after all is:
- how can I fix PulseAudio?
- is there another (better) way to get sound from both audio cards at the same time in Kubuntu?


I'm really enjoying KDE4.3 (I used Gnome for the whole Jaunty dev cycle) but music is the one thing I can't live without and this is really driving me crazy after spending 2 days trying to fix it myself :S

---

### Post by ranch hand on 2009-05-23
Try this, it may help;

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Darkshade on 2009-05-23
Thank you. I'm going out now but I'll check it when I'm back and I'll post the results.

---

### Post by Darkshade on 2009-05-23
Hmm interesting... When I got back home after a few hours (I left Amarok playing with my speakers turned off) I turned them on and everything seemed ok. Then I restarted my PC and I'm back to fast/slow/fast/distorted playback. :-s

The guide you posted didn't help me either. Also it said:
> Note 4: Kubuntu users: Don't follow this guide - PulseAudio isn't used in your distribution.
:confused:

---

### Post by ranch hand on 2009-05-23
But it is in your distro.  I would try and see what the Jaunty stuff woud do.  WTF, this is an alpa.  If you screw it up, what isthere to loose?  If it fixes it you can file a bug and say what helped.  If it just makes a difference you can discribe that.

Alphas are put out to play with.  That is the purpose.  HAVE FUN or else.

---

### Post by Darkshade on 2009-05-24
> **ranch hand said:**
> But it is in your distro.  I would try and see what the Jaunty stuff woud do.  WTF, this is an alpa.  If you screw it up, what isthere to loose?  If it fixes it you can file a bug and say what helped.  If it just makes a difference you can discribe that.

Alphas are put out to play with.  That is the purpose.  HAVE FUN or else.

Please don't get me wrong - I totally agree with you. Thing is, I did try it but it didn't change anything.

---

### Post by ranch hand on 2009-05-24
Rats - foiled again.

Beats me.

I use Gnome, KDE and I are not compatible so I am probably no help.  Sorry.  I need my tunes too.

Good Luck.  Have Fun anyway.

---

### Post by BwackNinja on 2009-05-24
Do you have tsched=0 in your default.pa ?
its should be on the line load-module module-hal-detect

I'd also try turning off flat-volumes (assuming you're using 0.9.15) in daemon.conf

---

### Post by Darkshade on 2009-05-24
Yes I do. Is that how it's supposed to be or shall I change it to something else?

---

### Post by BwackNinja on 2009-05-24
That's how its supposed to be. If you missed my post edit:

I'd also try turning off flat-volumes (assuming you're using 0.9.15) in daemon.conf

I think I get this too, whenever I change my volume or another application starts playing sound.

---

### Post by Darkshade on 2009-05-24
Same behavior after turning off flat-volumes and restarting. The only difference was that I had no sound when I logged in and had to kill and restart PA. :(

---

### Post by xerosis on 2009-05-25
I had no end of problems, namely I could either have sound in KDE or flash sound, never both. All I did to fix it in the end was to change Phonon to output to the PulseAudio device and things work great now.

---

### Post by super.rad on 2009-05-25
I was getting errors about default playback device (pulseaudio) failing when I logged into KDE and then certain programs wouldn't play sound and others would but were playing up. After a bit of reading on the PulseAudio wiki I edited **~/.asoundrc** and added the following
```

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```
Then went to multimedia in system settings and made sure the default output was PulseAudio and after a restart (not sure if that piece is necessary) I have no more errors and no problems with sound from any application (had amarok, smplayer, dragon and kaffeine all playing sound at once)
[http://pulseaudio.org/wiki/PerfectSetup#KDE](http://pulseaudio.org/wiki/PerfectSetup#KDE)

---

### Post by psyke83 on 2009-05-26
> **super.rad said:**
> I was getting errors about default playback device (pulseaudio) failing when I logged into KDE and then certain programs wouldn't play sound and others would but were playing up. After a bit of reading on the PulseAudio wiki I edited **~/.asoundrc** and added the following
```

pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

```
Then went to multimedia in system settings and made sure the default output was PulseAudio and after a restart (not sure if that piece is necessary) I have no more errors and no problems with sound from any application (had amarok, smplayer, dragon and kaffeine all playing sound at once)
[http://pulseaudio.org/wiki/PerfectSetup#KDE](http://pulseaudio.org/wiki/PerfectSetup#KDE)

Don't follow the upstream wiki, 99% of the advice is unnecessary. Ubuntu's libasound2 libraries have been patched to automatically use the "pulse" ALSA plugins by default - they're in the file /usr/share/alsa/pulse-alsa.conf which is parsed by default.

Listen, I think we're all suffering from PulseAudio problems - KDE, GNOME, everyone. There are issues with the ALSA libraries and PA 0.9.15, but the problems are being worked on and things will certainly improve.

---

### Post by ranch hand on 2009-05-26
psyke83
I agree, I actually had mine working great and then updated today.  The alsa upgrade did not work (installation script error), but my volume level has dropped a bunch.

This does not worry me, I am actually shocked by the performance of 9.10, just a lot better than I expected at this point.

---

### Post by seeker5528 on 2009-05-27
> **psyke83 said:**
> Listen, I think we're all suffering from PulseAudio problems - KDE, GNOME, everyone. There are issues with the ALSA libraries and PA 0.9.15, but the problems are being worked on and things will certainly improve.

I'm too impatient for that, eliminating as much PulseAudio stuff as I can, without eliminating stuff I actually want to use works for me, YMMV. :p

Later, Seeker

---

### Post by caryb on 2009-05-27
I booted up today to find 1 no sound at all & 2 the kmixer speaker icon is missing from my taskbar:(


Cary

---

### Post by seeker5528 on 2009-05-28
First does kmix show up in the multimedia section of the menu and can you run it from there?

If it runs from there.....

Plan A: 

With the full view of the mixer open, go into 'settings --> configure kmix', are the 3 boxes in the behaviour section checked? If they are not checked, try checking them, logging out and logging in again.

Plan B:

For me personally since I normally prefer to use kmix in whatever desktop environment I happen to be running, I often will just put it in the autostart ('system settings --> advanced --> autostart' in KDE) using the command:

```
/usr/bin/kmix --keepvisibility
```

: to run it. So any dekstop environments that look in '~/.config/autostart' for things to run at log in should start it.

Later, Seeker

---

