---
title: "why does ubuntu show my HDMI port on video card as a digital sound device?"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2010-12-17
I was investigating sound and noticed ubuntu reports I have 2 sound devices, one labelled as HDMI so the only HDMI connection I have is on the video card.  But if I go into terminal and detect my sound modules, they appear to me to be identical - How is this?

[HTML]$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel
[/HTML]

---

### Post by daqron on 2010-12-18
HDMI is a digital sound device. Also, /proc/asound/modules is a list of drivers, not devices. It is likely that you have two sound devices on your system, and they are both using the HDA Intel driver. 

If you go into your sound preferences, or alsamixer on the command line then F6, do you see two different devices to select from?

---

### Post by alvinmoneypit on 2010-12-18
yes, they show them both.  I thought HDMI was a video device only.

So should I disable it?  I wonder if it can conflict sometimes with my onboard 5.1 sound.

---

### Post by daqron on 2010-12-18
> **alvinmoneypit said:**
> I thought HDMI was a video device only. [HDMI is both video and audio]("http://en.wikipedia.org/wiki/Hdmi"). 

> **alvinmoneypit said:**
> So should I disable it?  I wonder if it can conflict sometimes with my onboard 5.1 sound.
Probably not necessary to disable it unless it's actually causing problems, especially if that is your active video card. I have a similar setup and use both cards without any issues.

---

