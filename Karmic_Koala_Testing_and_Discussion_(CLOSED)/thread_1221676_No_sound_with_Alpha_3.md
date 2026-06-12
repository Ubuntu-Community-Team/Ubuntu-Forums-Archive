---
title: "No sound with Alpha 3"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by theozzlives on 2009-07-24
On my test computer is a Cirrus Logic  CS 4614/22/24/30 sound card. I can get sound with Jaunty and XP, but not with Alpha 3. May it be known that Alpha 3 plays sound on my laptop in a virtual box. Any ideas?

---

### Post by ranch hand on 2009-07-24
Try installing gnome-alsamixer and using it.  I think this will work.

---

### Post by taavikko on 2009-07-24
> **ranch hand said:**
> Try installing gnome-alsamixer and using it.  I think this will work.

It's just a GUI for alsamixer, so installing it should solve anything.
just like alsamixergui.

does sound work with a new user?
Is some levels muted? (check with alsamixer and alsamixer -Dhw)

---

### Post by Regenweald on 2009-07-24
Try adding yourself to the 'audio' group. A while back that was the problem.

---

### Post by BCurtisWX on 2009-07-24
Not to sound condescending, but the pulseaudio volume starts off muted (im sure its noted in a bug somewhere).  Could this be your problem?

---

### Post by theozzlives on 2009-07-25
Alsamixer has Master and Capture, volume is up and nothing muted. I can hear the speakers initialize/de-initialize when I boot/shutdown, but no sound in the GUI. I want the old alsamixer, I bet PCM needs adjusted. I also want alsa, not pulseaudio if any devs are reading.

---

### Post by ranch hand on 2009-07-25
PCM is on the gnome-alsamixer and yes, it may need adjusted.

Check the setting on whatevercomes up from the sound applet today too.  It seems to change quite often recently.  I think they are hard at it on the sound issues.

---

### Post by taavikko on 2009-07-25
You were aware that you can scroll the alsamixer window horizontally?
If there's <> on side of the window...

usually speaker is set to low levels. (at least on my laptop)

---

### Post by taavikko on 2009-07-25
> **ranch hand said:**
> PCM is on the gnome-alsamixer and yes, it may need adjusted.


alsamixer has the same controls as the gnome-alsamixer you so eagerly advertize ;)

But wait for the gnome-volume-manager to mature to be included everything users need.

---

### Post by ranch hand on 2009-07-25
> **taavikko said:**
> alsamixer has the same controls as the gnome-alsamixer you so eagerly advertize ;)

But wait for the gnome-volume-manager to mature to be included everything users need.
The reason that I suggest gnome-alsamixer is because using it has fixed the no sound problem, for me, on 8.10, 9.10 and Mandriva2009 (both KDE and Gnome).

I, by no means, think of this as a long term fix in 9.10.  I think great things are ahead.  It is nice to be able to hear your tunes while you wait.

---

### Post by theozzlives on 2009-07-25
Gnome-alsamixer didn't work, everything is up and not muted. This is on my test box/fax machine so sound's really not a big deal. I just wanted to put Amarock14 and my Christian playlist on there. I just remember Jaunty's Alphas when there's no sound.

---

### Post by ubername on 2009-07-25
I can understand why anyone struggles - I mess with all these (see attachment) , and other settings / monitors to get my sound to work. It is far from clear how the whole pulse/alsa/sound setup works (to me).

---

### Post by zika on 2009-07-25
> **ubername said:**
> I can understand why anyone struggles - I mess with all these (see attachment) , and other settings / monitors to get my sound to work. It is far from clear how the whole pulse/alsa/sound setup works (to me).You have mute on output ... ? (upper right corner ...)

---

### Post by wayne_cat on 2009-07-25
> **zika said:**
> You have mute on output ... ? (upper right corner ...)

zika = man with eagle eyes :biggrin:

---

### Post by zika on 2009-07-25
> **wayne_cat said:**
> zika = man with eagle eyes :biggrin:In my country we say: even a sight-challenged chicken do find a corn eventually ... :)

---

### Post by theozzlives on 2009-07-25
> **zika said:**
> You have mute on output ... ? (upper right corner ...)

I said nothing's muted in an earlier post.

---

### Post by ranch hand on 2009-07-25
> **theozzlives said:**
> I said nothing's muted in an earlier post.
Your output control in the upper right corner of you picture is checked "Mute".

Maybe you have changed this?

---

### Post by zika on 2009-07-26
> **theozzlives said:**
> I said nothing's muted in an earlier post.I made a comment on a picture posted by **ubername**.

---

### Post by ubername on 2009-07-26
> **zika said:**
> You have mute on output ... ? (upper right corner ...)

I know my output was muted - I was just trying to show how many different GUI ways there were to get at the controls, and how it could be confusing.

---

### Post by theozzlives on 2009-07-26
Back to me, I want to play my Christian music while I sleep. I have insomnia and I think that'll help. Using my server for anything but is not the wisest thing to do. I'd like to use my test machine for that, and play my Rock on my laptop when I'm awake.

GNOME ALSA Mixer reports a different card than lspci. It says it's a Cirrus Logic CS4297 rev 3 if that helps any. Also it's onboard.

---

### Post by theozzlives on 2009-07-28
Bump

---

