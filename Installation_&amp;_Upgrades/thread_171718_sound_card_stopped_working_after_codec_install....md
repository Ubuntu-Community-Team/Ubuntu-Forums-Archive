---
title: "sound card stopped working after codec install..."
date: 2006-05-07
forum: Installation &amp; Upgrades
---

### Post by pyromidget on 2006-05-07
Hey all - bit stumped.

Finally managed to get Breezy installed (had to use LILO as GRUB just hated me), but after doing all the updates etc and installing the win32 and gstreamer0.8 codec packs my sound has stopped working!

Whenever I try to even *open* volume control it comes up with:

> No volume control elements and/or devices found
I'm still firmly in the land of the newbie, so any suggestions would be appreciated! :)

---

### Post by pyromidget on 2006-05-07
Looks like the error fairy has paid a visit again...

Now i'm getting:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

Anyone got a clue?

---

### Post by christhemonkey on 2006-05-07
What sound card do you have?

Did you have sound working before getting the codecs?

---

### Post by Sef on 2006-05-07
> What sound card do you have?

To find what sound card or cards you have , type this from the terminal

lspci | grep audio

---

### Post by pyromidget on 2006-05-07
> **Sef]To find what sound card or cards you have , type this from the terminal

lspci | grep audio[/QUOTE]
Thanks man - was wondering  said:**
> root@nerthus:/home/martin# lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 05)

I used Automatrix and now card seems to be recognised, but i don't get any sound out from it...

When i try to open audio files i get:

> Totem could not play 'file:///home/martin/Desktop/Halo Soundtrack/03 - Brothers In Arms.mp3'.

This is an audio-only file, and there is no audio output available.

---

