---
title: "Lucid-VLC (Multimedia Player) - Anyone else getting freezing system"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-22
Attempting to run a 40 meg 720p MP4 video last night and after this morning's this morning update, and on loading, the video loads and then my system freezes.  The mouse cursor moves, but clicks do not work; I have to reset the system to get back to Ubuntu. 
Can any one test and confirm this?

---

### Post by mc4man on 2010-02-22
While the lucid vlc 1.0.5 is lacking a few things overall it works well here on a tester. 

Occasionally vlc locking up can be audio related, maybe run htop and see if anything is occurring there

Vlc's pulseaudio plugin can at times have an issue though it does work best using it ( vs. alsa or sdl depending on hardware

You could try setting a specific audio output in tools -> preferences, (if audio related

---

### Post by HarshReality on 2010-02-22
I had a few freezes and stutters on my lappy but found it was related to streaming.. local works flawlessly so far.

---

### Post by emarkay on 2010-02-22
How would I use htop ( an interactive process viewer for Linux) for this?

This is a saved, (HDU based) file of: 
[http://www.youtube.com/watch?v=SsDEfu8s1Lw](http://www.youtube.com/watch?v=SsDEfu8s1Lw)
"Solar Dynamics Observatory Launch, Feb 11, 2010 "

---

### Post by moviemaniac on 2010-02-23
This might not be a VLC bug - I've been getting these kinds of freezes with other applications as well - programs using OpenGL or Flash-streamed internet videos. The machine itself is not dead, it can still be accessed via ssh, but X is somehow semi-dead and can't be reset with the keyboard.

Removing plymouth(!) fixed these problems for me.

---

### Post by emarkay on 2010-02-23
> **moviemaniac said:**
> This might not be a VLC bug - I've been getting these kinds of freezes with other applications as well - programs using OpenGL or Flash-streamed internet videos. The machine itself is not dead, it can still be accessed via ssh, but X is somehow semi-dead and can't be reset with the keyboard.
Removing plymouth(!) fixed these problems for me.

This is not a steamed video - it's saved onto my Hard Disk, and I have already permanently eliminated Plymouth!

---

