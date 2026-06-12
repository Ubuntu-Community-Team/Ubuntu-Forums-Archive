---
title: "Sound is too loud"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Labus on 2010-03-20
When I set my sound at the lowest possible without muting it's still way to loud. Im worried my speakers will break, or my ears for that matter.
Is there a way to change this?

---

### Post by efflandt on 2010-03-20
You have given no details about your sound card/chip, so it is anybody's guess whether it is fully supported or some setting that could help.

Are you using amplified speakers (or built-in speakers in a laptop) and do the speakers have any external volume control, or are they connected to a headphone jack vs. audio output jack (although the headphone jack is audio output from a laptop).

---

### Post by Labus on 2010-03-20
I just realised that Im using Lucid Lynx so it's probably a bug or something like it. It worked before I upgraded and I just haven't required any sound since, so I didn't make the connection at first.
But thank you :)
I'll report the bug now.

---

### Post by linden940 on 2010-03-20
it could or could not be a bug...cant just think its a bug if u dont look into it first..

---

### Post by Labus on 2010-03-20
Yes, I agree. But what could it be.
Sound works perfect --> Upgrades Ubuntu to beta release --> sound doesn't work well

---

### Post by lidex on 2010-03-20
It's probably pulseaudio, some in karmic have same issues. Got to this section: "Volume range anomalies" of this page:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by Labus on 2010-03-21
I've tried both things stated on that page and none of them helped.

---

### Post by Labus on 2010-03-21
It seems that something have happened.Now I can't change the volume with the normal volume controls. When I run alsamixer I see that the volume controls effect the master sound but nothing happens. If i change the "front" level in alsamixer the sound changes as normal.
Is there  a way to change "front" audio without opening alsamixer every time?

---

### Post by kansasnoob on 2010-03-21
I've installed gnome-alsamixer and made my tweaks there:

[ATTACH]150858[/ATTACH]

I recall some things not being muted that should have been, etc. I just started fiddling while I had sound playing. So far it seems to stay where I set it on reboot.

It's in the repos so you can just:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video.

---

### Post by Labus on 2010-03-21
Thank you :D
It's much easier to change volume now.

---

### Post by lidex on 2010-03-21
Hopefully gnome-alsamixer will save your settings. For alsamixer I believe you need to save the settings manually in some cases:
```
sudo alsactl store
```

Once you get it configured ^

---

