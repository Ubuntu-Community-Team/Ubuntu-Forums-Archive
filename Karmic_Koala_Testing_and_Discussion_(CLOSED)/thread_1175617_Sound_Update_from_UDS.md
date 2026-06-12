---
title: "Sound Update from UDS"
date: 2009-06-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-06-01
Ubuntu developer [Dan Chen]("https://launchpad.net/~crimsun") recently made [a post summarizing much of the audio work discussed at the recent UDS]("http://drowninginbugs.blogspot.com/2009/06/action-items-from-uds-barcelona.html").  There is definitely some promising news - some highlights:> On the audio front, a slew of bugs have been resolved in Karmic simply by upgrading the entire stack.> Glitch-free PulseAudio likely will not be enabled in Karmic.> As part of an improved battery life objective, powering down HDA controller amps when no sound is being played [has already been enabled.]("https://lists.ubuntu.com/archives/ubuntu-devel/2009-May/028264.html")He also linked to [the slides from a presentation he made at UDS]("http://kernel.ubuntu.com/~dtchen/UDS-Barcelona/Audio_Madness.odp") on the state of Linux sound.  Be sure to check it out!

---

### Post by davideotape on 2009-06-01
Best bit is attached :D

---

### Post by seeker5528 on 2009-06-01
If libcaberra is an implementation of the XDG Sound Theme and Name Specifications, how come the diagram only shows a path through PulseAudio? Alsa and Gstreamer backends exist so shouldn't the diagram include those paths, or is the plan going forward to pretend ALSA doesn't exist, except when it makes a good scapegoat for some problem PulseAudio is having?

Later, Seeker

---

### Post by ghindo on 2009-06-01
> **davideotape said:**
> Best bit is attached :D

[removed image]I much prefer the fixed version.

---

### Post by seeker5528 on 2009-06-01
> **ghindo said:**
> I much prefer the fixed version.

:lolflag:

OK, that makes for a much nicer image, but what about those of us who prefer to skip PulseAudio all-together?

If my hardware can do mixing I would much rather use that than have PulseAudio injected into the mix in a way that doesn't fully let me use the capabilities of my hardware. Vista all ready went down that road and I don't see it as a good tradeoff.

If I can use PulseAudio for specific applications and at the same time use ALSA directly for specific applications, there is no problem.

Later, Seeker

---

### Post by mdurham on 2009-06-03
ghindo wrote:
> As part of an improved battery life objective, powering down HDA controller amps when no sound is being played has already been enabled.
Thanks for your post ghindo, this was really annoying me. Do you know the value that I should change the entry "HDA power_save=10" to in /etc/modprobe.d/alsa-base.conf in order to disable this feature? I set it to -1 which seems to work but I just wondered what would be the correct value. Or maybe comment out the line?
Cheers, Mike

---

### Post by psyke83 on 2009-06-03
> **mdurham said:**
> ghindo wrote:

Thanks for your post ghindo, this was really annoying me. Do you know the value that I should change the entry "HDA power_save=10" to in /etc/modprobe.d/alsa-base.conf in order to disable this feature? I set it to -1 which seems to work but I just wondered what would be the correct value. Or maybe comment out the line?
Cheers, Mike

Rather than disabling it, I'm sure Daniel would appreciate if you file a bug as he requested: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

---

### Post by Slug71 on 2009-06-03
> **ghindo said:**
> I much prefer the fixed version.

Looks much better.

---

### Post by mdurham on 2009-06-03
> **psyke83 said:**
> Rather than disabling it, I'm sure Daniel would appreciate if you file a bug as he requested: [https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

You're quite right psyke83, I'll do that. I'd still like to know how to disable it correctly as I'm using a desktop and have no need for it. Should it have been enabled on a desktop anyway?
Cheers, Mike

---

### Post by zekopeko on 2009-06-03
> **mdurham said:**
> You're quite right psyke83, I'll do that. I'd still like to know how to disable it correctly as I'm using a desktop and have no need for it. Should it have been enabled on a desktop anyway?
Cheers, Mike

why not? lower electric bills aren't a bad thing. they are doing some cool stuff with server (on demand power on/off).

---

