---
title: "Can't record Audio (Karmic Beta)"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CulleyS on 2009-10-22
Hello,

I recently upgrade from Intrepid to Karmic Beta (64bit version).  I have an SB Audigy sound card.  Sound sounds great.  All of my audio inputs are working as I set them in Gnome-alsa-mixer.  However, even though I can hear sound, I am not able to record.  This includes inputs, sound from a CD, streaming sound, etc.  That is, no sounds are being recorded.  I tested this in Audacity, Ardour, and Ubuntu Sound Recorder.

I added my Ubuntu user to the audio group.  Cleared the contents of ~/.pulse and rebooted.  That didn't solve my problem.

I opened up Audacity (1.3.9) and cycled through all available devices under Edit -> Preferences -> Devices (Recording).  None of them enabled recording.  I only receive a flat level.  Input level is up, like I said, I can hear it.

I checked in Ubuntu under System -> Preferences -> Sound.  Under Hardware (Profiles), I cycled through every profile, but still couldn't get recording to work. I checked the Input and Output levels here as well, both are up near Max.

In previous versions of Ubuntu, the Volume Preferences had two separate areas for Playback and Recording.  Under Gnome-alsa-mixer, I only see one set.  Perhaps there is another way to enable recording in Karmic?

I find it odd that I can hear sound, but no sound is being captured.

Any advice would be appreciated.

Thanks,
Culley

---

### Post by CulleyS on 2009-10-22
Bah, I should have just read down further in this forum.

I ran alsamixer at the command line, and upped the "capture" levels there.

Problem solved.  This can be closed.

---

### Post by diafanos on 2009-10-22
Hello CulleyS

As your problem solved, you better tag this thread as solved.

Just go to 'Thread Tools' (upper right corner) and select 'Mark this thread as solved'

---

