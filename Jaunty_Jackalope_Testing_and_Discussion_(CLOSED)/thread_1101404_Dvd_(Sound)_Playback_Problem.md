---
title: "Dvd (Sound) Playback Problem"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2009-03-20
I have installed the Ubuntu-restricted-extras(30) and have the following problem with sound from DVD Discs, the video is ok but there is no sound playback. MP3 playback fine with no probs.

From Totem movie player 2.25.92

When playing back dvds i have these options from sound menu:
[I]Sound>Auto
      Audio0[/I]

While playing MP3's I have these;
[I]Sound>Auto
      MPEG1 Audio Layer 3 (MP3)[/I]

I am right in assuming that the dvd sound menu should have an entry instead of *Audio0*, either way does anyone know how i can resolve this issue?

If this is down to pulseaudio what do i do to kill it?

---

### Post by Nightstrike2009 on 2009-03-20
Bump. Anyone got any ideas?

---

### Post by taavikko on 2009-03-20
> **Nightstrike2009 said:**
> Bump. Anyone got any ideas?

Don't bumb messages after 15 minutes.
Thumb rule is to wait at least a day.

Set Audio to "auto-detect" in "gstreamer-properties"
Try different player and play with audio-output modules.

---

### Post by Nightstrike2009 on 2009-03-20
Sorry taavikko,

If you mean in Totem movie player 2.25.92, selecting auto in sound menu I've tried that it didn't make any difference, thanks for your advice anyhow though it appreciated.


PS: Sorry about the bump thing i am still relatively new to ubuntu will bear that in mind in future. :( Yeah I am a newbie with an Alpha 6 version I've heard all the warnings, but I chose to learn this way and I am enjoying it too and learning fast, I must be insane LOL ;)

---

### Post by taavikko on 2009-03-20
No worries ;)

Open terminal
```
gstreamer-properties
```

Set audio output to "autodetect" 
And test (you should hear a beep?)

And switch to using main-server for repositories,
Totem has been upgraded to 2.26

If totem fails, try a different mediaplayer, like VLC or mplayer etc.
Almost every player has preferences incorporated in their menu, so you should be able to test with various audio-plugins

---

### Post by Nightstrike2009 on 2009-03-20
Think I may have found the answer:
[COLOR="Red"]faad_2.6.1-3.1_i386[/COLOR] was missing i had [COLOR="SeaGreen"]libfaad0_2.6.1-3.1_i386[/COLOR] installed this maybe the problem. Will update my system later and retry. :)

> **Nightstrike 2009's Signature**:I don't have internet on my Linux PC and use a Windows PC to download and install .deb files onto my linux PC, which works fine for me. Its an unusual way but it works for me, I'd like to use Synaptic but its not an option for me.

I don't use synaptic to install repositories, I install manually with .deb files, I realise this is unconventional but its my only way to learn linux at the moment. Thanks once again for trying to help me out.:)

---

### Post by Nightstrike2009 on 2009-03-20
Yeah It worked [COLOR="Red"]libdvdread3[/COLOR] was missing to thought because I had libdvdread4 it didn't matter (probably wrongly). The disc i am using plays audio on the main film but not on the intro part before it, must be in a daft format or something, I am happy with it now anyhow. :) 

Thanks for the advice. :)

---

