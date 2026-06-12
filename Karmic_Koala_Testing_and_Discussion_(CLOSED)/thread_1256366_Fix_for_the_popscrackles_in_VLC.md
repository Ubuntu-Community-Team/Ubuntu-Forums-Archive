---
title: "Fix for the pops/crackles in VLC"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BobCFC on 2009-09-02
VLC has stuttering audio in Karmic for videos that play fine in other programs such as Totem.

INSTALL:

```
sudo apt-get install vlc-plugin-pulse
```


This adds an entry for Pulse Audio in VLC audio preferences and fixes the pops/crackles.

---

### Post by miegiel on 2009-09-02
Thanks, works great here. Of the 8 vids I just watched the audio was out of sync once, but I think that was just a case of bad encoding.

---

### Post by bear24rw on 2009-09-02
Thanks, I'll have to try this i started using totem to watch movies because vlc was popping and crackeling like crazy

---

### Post by tahina on 2009-09-03
Thanks!
=D>

---

### Post by ELD on 2009-09-03
Should that not be a dependancy?

---

### Post by miegiel on 2009-09-03
> **ELD said:**
> Should that not be a dependancy?I guess, though there might be a good reason, that I can't think of, not to. :shrug:

---

### Post by Jim March on 2009-09-03
I found something else that fixes it.  Abandon Gnome, switch to LXDE.

Kind of a radical solution but, right now it might be the best option.  There's some kind of a weird interaction going on between Nautilus and Pulseaudio.  At early Alpha4, I could crash any playing sound by doing file-related things.  They're obviously working on it, it's getting better, but it still ain't quite right.

---

### Post by eltoozero on 2009-09-03
> **BobCFC said:**
> VLC has stuttering audio in Karmic for videos that play fine in other programs such as Totem.

INSTALL:

```
sudo apt-get install vlc-plugin-pulse
```


This adds an entry for Pulse Audio in VLC audio preferences and fixes the pops/crackles.

Hi guys, workarounds are awesome but it really helps everyone if the bug is reported and eliminated.

I reported this bug as [LaunchPad Bug #402018]("https://bugs.launchpad.net/bugs/402018") in the hopes this can be fixed in time for the final of Karmic.

The skipping for me was correlated to incrementing "lost buffers" as shown in the statistics tab of the media information screen (CTRL-I) in VLC.

You guys know and love VLC, lets make it perfect for Karmic.

---

