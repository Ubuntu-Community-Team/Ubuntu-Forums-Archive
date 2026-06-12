---
title: "Totem playback falls over after end of file"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bobince on 2009-10-20
Anyone having this trouble in Karmic? Started occurring for me this morning.

When Totem gets to the end of a file it is playing (seemingly any filetype, audio or video), it won't play anything more for an indeterminate amount of time. If you have a playlist it will move to the next item and claim to be playing it, but with no AV output or timeline progression. Often, several minutes later it will suddenly burst into life and start playing the track.

Clicking pause/play, changing track or loading a new file in doesn't help in this state; nothing will play until Totem randomly wakes up, or you quit/reload it.

---

### Post by LittleKoy on 2009-10-20
Just installed Karmic and yes, same problem here.

---

### Post by JanDM on 2009-10-20
Same problem here.. It's really annoying :(

---

### Post by Sandsound on 2009-10-20
> **jandm said:**
> same problem here.. It's really annoying :(

+1

---

### Post by MentalNotes on 2009-10-21
Same here. However, if I wait for a while (~20 seconds) it starts to play. I'm also getting a lot of "pulseaudio[1955]: protocol-native.c: Failed to push data into queue" in /var/log/messages.

---

### Post by cor2y on 2009-10-21
yes both totem and rhythmbox seem to have problems playing back mp3 audio when it moves to a new file. I noticed this for some video that has mp3 audio tracks and plain mp3 music.
It seems to be a pulse audio thing.

---

### Post by morryis on 2009-10-21
It also happens when totem/rhythmbox repeats a video/audio file. Has anyone created a bug report yet?

This is what I found in syslog:
> Oct 21 14:44:31 morryis-laptop pulseaudio[3941]: protocol-native.c: Failed to push data into queue

I've created a bug report: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/457165](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/457165). Please confirm!

---

### Post by zika on 2009-10-21
Boy am I glad. I thought I messed up something by installing various xine parts. Thank You for letting me know that it is not my fault. Annoying bug for us that love to listen to the music ... But xine proved admirable substitution whatsoever ...

---

### Post by EmmEff on 2009-10-21
Yup, same here...  somebody tell me again why PulseAudio was a good idea?  ALSA worked perfectly fine for me :(

---

### Post by zika on 2009-10-21
> **EmmEff said:**
> Yup, same here...  somebody tell me again why PulseAudio was a good idea?  ALSA worked perfectly fine for me :(I do not think that PulseAudio has anything to do with this problem. It is totally isolated and repeatable just and only for Totem. PulseAudio is not the ultimate peril.

---

### Post by EmmEff on 2009-10-21
> **zika said:**
> I do not think that PulseAudio has anything to do with this problem. It is totally isolated and repeatable just and only for Totem. PulseAudio is not the ultimate peril.

Is this a gstreamer problem or specific to Totem?  I thought I'd seen similar issues with Rhythmbox but I might be mistaken.

---

### Post by ikt on 2009-10-21
> pulseaudio[2343]: protocol-native.c: Failed to push data into queue

absolute boatload of these in syslog, going to investigate.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433865](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433865)

Bug report.

---

### Post by Sandsound on 2009-10-21
> **EmmEff said:**
> Yup, same here...  somebody tell me again why PulseAudio was a good idea?  ALSA worked perfectly fine for me :(

I just removed Pulse, and now Totem won't play audio at all, VLC, Rythmbox and other players I have tried works fine(both with and without Pulse).
Perhaps it's a configuration in Totem that depends on Pulse ?

I would not recommend removing Pulse from your system unless you are ready for some breakage, but if you like fiddling with your system, then go for it, it's a learning experience ;-)

---

### Post by zika on 2009-10-21
> **EmmEff said:**
> Is this a gstreamer problem or specific to Totem?  I thought I'd seen similar issues with Rhythmbox but I might be mistaken.I've just checked (even though I was pretty sure already) Rbox is not having any problems, at least related to this topic.

---

### Post by zika on 2009-10-21
[quote=SandSound]I just removed Pulse, and now Totem won't play audio at all, VLC,  Rythmbox and other players I have tried works fine(both with and without  Pulse).
Perhaps it's a configuration in Totem that depends on Pulse ?[/quote]Did You change settings in MultiMediaSelector after You removed PA?

---

### Post by Sandsound on 2009-10-21
> **zika said:**
> Did You change settings in MultiMediaSelector after You removed PA?

Yes, still no sound in Totem.

---

### Post by digbigbrotherjenson on 2009-10-21
Totem stops for 20sec after playing one file and continuing to the next.
Instant time-scrolling after the pause has the same effect, it takes 20sec to load ...

A bug in pulseaudio ... ? 
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433865](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433865)		
Is this symptom reproducible after installing
linux-backports-modules-alsa-karmic and rebooting?

YES ... totem still stops and takes a pause ...

... bump

---

### Post by cor2y on 2009-10-22
Its a gstreamer/pulse audio bug (which explains the similar problem in rhythmbox with some mp3 files).
Still unconfirmed but a hack was recommended in bugzilla
[https://bugzilla.gnome.org/show_bug.cgi?id=599105](https://bugzilla.gnome.org/show_bug.cgi?id=599105)

So hopefully a bug fix of the gstreamer plugins (either base or good) will take care of the problem.

---

### Post by bobince on 2009-10-23
Fixed for me with today's gstreamer updates.

---

### Post by zika on 2009-10-23
> **bobince said:**
> Fixed for me with today's gstreamer updates.Looks like it is.

---

### Post by Sandsound on 2009-10-23
> **bobince said:**
> Fixed for me with today's gstreamer updates.

Not for me using ALSA :-(

But actually I don't mind that much... I have been trying VLC for the last couple of days, and it's amazing how far this player have come since I last tried it, the new skins are SO cool \\:D/

---

