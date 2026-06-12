---
title: "Lucid 10.04b2 and Amarok - No sound on dloaded podcast or stream."
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by tehowe on 2010-04-21
Hi - So I grabbed Amarok off Synaptic since it's the only full featured media player I could find with OPML import, audio and video podcasting, etc. (Sorry, audio-only Rhythmbox - any other suggestions? I want to sync podcasts to my iPod classic as well, and cut the ties to Win 7)

Anyways on Amarok I was able to successfully import my 20+ podcast feeds in a couple of clicks with the OPML import, and I then downloaded a test audio podcast.

On trying to play this podcast, however, the progress bar just shot across the screen, no audio was produced, and the podcast ended right away.

I tried playing a radio stream as well from the Internet/Radio feature and no audio there either. It definitely was not muted.

Is this an Ubuntu problem? Something with this 'GStreamer' thingy? - I don't know what that is, but I need to pretend I know something about this here fancy Ubuntu jargon. :) Amarok played a test .ogg I recorded using Sound Recorder but that's all I've gotten to work so far.

Thanks. And if this is worth reporting as a bug, could someone please let me know what additional logs or info I should submit to launchpad. (Since there's no crash, there's no automatic submit popup.)

---

### Post by corneliuscrab on 2010-04-24
Try installing libxine1-ffmpeg and ubuntu-restricted-extras packages

---

### Post by tehowe on 2010-04-24
> **corneliuscrab said:**
> Try installing libxine1-ffmpeg and ubuntu-restricted-extras packages

I will and let the forum know, thanks.

---

### Post by tehowe on 2010-04-26
> **corneliuscrab said:**
> Try installing libxine1-ffmpeg and ubuntu-restricted-extras packages

Crazy, that worked. Now why wouldn't Amarok just do that or if there's some legality involved, gently suggest it? :confused:

Anyways - closed, thank you!

---

### Post by cmcanulty on 2010-04-29
Doesn't work for me still no sound on podcasts

---

### Post by jonny163 on 2010-04-29
I have ubuntu-restricted-extras and regular .mp3s didn't play in either Amarok or Banshee but they do in VLC. Not muted. Any suggestions?

---

### Post by cmcanulty on 2010-05-11
I just got it fixed by installing Gnome alsa mixer and seeing it had external amplifier checked, I unchecked it and my sound works! I saw nothing like that in alamixer from terminal but the gnome alsamixer is much easier to configure.Thanks

---

### Post by saurabh42 on 2010-05-30
I have the same problem. Fixed it by downloading the specie-ed packages but the problem reoccurred on reboot.

---

