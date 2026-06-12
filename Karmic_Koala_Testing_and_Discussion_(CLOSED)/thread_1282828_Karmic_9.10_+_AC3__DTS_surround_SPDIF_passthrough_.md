---
title: "Karmic 9.10 + AC3 / DTS surround SPDIF passthrough (pulseaudio)"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by davewantsmoore on 2009-10-04
Sorry if this is already solved, however my search didn't show anything authoritive for Karmic.


[B]I wish to have AC3 and DTS audio passed directly to my SPDIF and notice there are some issues doing this with pulseaudio.

Is the correct solution in 9.10 still to disable pulseaudio and use ALSA ?[/B]


I am happy to disable pulseaudio (don't need it's features, and only use one application at a time, ie. I am using a HTPC) ...but I would also like to keep things "standard Ubuntu" if possible.


So, Karmic SPDIF passthrough for AC3/DTS audio... fix pulseaudio or remove/disable pulseaudio?

---

### Post by davewantsmoore on 2009-10-04
I notice the wiki ([https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)) mentions removing all the pulseaudio packagaes if you don't want pulseaudio.

Does this apply to 9.10 ? ... asking to remove the pulseaudio packages wants to remove ubuntu-desktop  :-/



I found this ([http://ubuntuforums.org/showpost.php?p=7341138&postcount=2](http://ubuntuforums.org/showpost.php?p=7341138&postcount=2)) for Jaunty.   Which says it disables pulse (without removing).   Is it the right thing to do in Karmic?

---

### Post by unimatrix on 2009-10-19
PulseAudio doesn't support AC3 passthrough, and the developers are happily ignoring the problem.

---

### Post by Peter09 on 2009-10-19
Install gnome-alsamixer, this lets you turn the spdif output on.

---

### Post by davewantsmoore on 2009-10-19
Sorry guys I should have updated... problem solved, it was to do with the amp, not linux audio

---

### Post by davewantsmoore on 2009-10-19
> **unimatrix said:**
> PulseAudio doesn't support AC3 passthrough, and the developers are happily ignoring the problem.

Not true.

... and why don't you go and help them?  huh!?

EDIT:  Well... it's true that it doesn't do passthrough... but they aren't ignoring the issue... it's also not high on their priority list either.

You don't have to use Pulse. You don't have to use Ubuntu... You can also help fix Pulse if there is something you need.

---

### Post by RDV on 2009-10-24
> **davewantsmoore said:**
> ...You don't have to use Pulse. You don't have to use Ubuntu... You can also help fix Pulse if there is something you need.

What I find difficult to accept is that since pulseaudio has been added to Ubuntu every upgrade breaks my WORKING audio configuration and it usually takes days to fix. The use of SPDIF is just too common to not prioritize, if pulseaudio is going to continue to pretend to be an encompassing solution for Linux audio.

Hours ago I have upgraded to 9.10 RC and once again have to enjoy the sound of silence (PCM and AC3/DTS passthrough) as I only have my audio through a SPDIF connection. This just should not be such a hassle.

Yes there are choices but why should I abandon such a great distro just because of pulseaudio. That does not make sense. 

The proper solution is a choice at install or upgrade time to install Pulse or not.

---

### Post by davewantsmoore on 2009-10-24
> **RDV said:**
> Yes there are choices but why should I abandon such a great distro just because of pulseaudio. That does not make sense. 

You are talking about a Ubuntu problem, not a pulseaudio problem.  It's Ubuntu's choice to use Pulse when there is no passthrough AC3/DTS/etc. support... and it's Ubuntu's choice to break your configuration each upgrade.

---

### Post by imaca on 2009-10-24
Hi, I'm using the Karmic with pulse audio and spdif passthrough works.
I have Logitech z-5500 and I can play DVDs using xine (plug to use for pulse audio: plug:spdif) with dolby digital/DTS and also flash video sound now comes through (on gutsy I had to switch the speakers to analogue input for flash)
Amarok also outputs to spdif using "Pulse audio sound server"
I don't have any technical understanding of the sound system, I only know I've got it working.

The only thing I now have to use analogue for is Tvtime.

PS. : the ALSA mixer doesn't seem to affect spdif anymore. There is a bug which sets ALSA volume to minimum on every reboot, I have to turn the master and line in up to get sound out of Tvtime but spdif is unaffected even though IEC958 is set to minimum in ALSA mixer panel.

---

### Post by davewantsmoore on 2009-10-25
I can also get SPDIF working using pulse (karmic).

Passthough (AC3/DTS) works when no other sound is a playing and no volume control is in use (ie.  volume is @ 100%).

The 'problem' with pulse is that is has no way of identifying 'bitstream' audio (such as DTS/AC3) and doesn't know not to change the digital bit stream  (eg.  mixing in other audio, applying volume control, etc.)

So, in short, pass through is "possible" with pulse... just not reliable (or coded for).

The pulse guys certainly know about this issue, and will be addressing it at some stage.... however it's not a major priority for them.

Any machines I need pass-through audio (eg. media centers) for... i am removing pulseaudio.

---

