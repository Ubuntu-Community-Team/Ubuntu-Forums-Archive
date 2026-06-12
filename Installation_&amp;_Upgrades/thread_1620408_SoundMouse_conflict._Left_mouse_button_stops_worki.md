---
title: "Sound/Mouse conflict. Left mouse button stops working."
date: 2010-11-13
forum: Installation &amp; Upgrades
---

### Post by Sykes2222 on 2010-11-13
Hello all,

I recently upgraded to Ubuntu Maverick from Lucid. Now when I play music (from mpd,amarok,audacious etc) the left mouse
button doesn't get "released". That is it acts as if the left button is held down. I can usually use the keyboard for navigation (I have had the keyboard and mouse completely lock up) but the only way to free the mouse is to restart X.

I have tested this in Gnome, KDE, Enlightenment and a few others. I have tried jumping out to a virtual console and
back, unloading and reloading different mouse modules, unplugging the mouse, but the only way i can find is to restart
GDM.

This seems to happen only when the music is first started. For example if I play a song via mpd and it continues to
play, I can use the mouse fine when X restarts even the the song is still playing. 

Anyone out there have any ideas?

---

### Post by The_Eddster on 2010-11-13
Bump. This is really annoying me as I have to restart the computer everytime I play a track from amarok. Sometimes the right-mouse button stops working as well.

---

### Post by The_Eddster on 2010-11-13
By the way, this just started after I installed kubuntu 10.10 Maverick Meerkat.

---

### Post by gulmer on 2010-11-13
> **Sykes2222 said:**
> Hello all,

I recently upgraded to Ubuntu Maverick from Lucid. Now when I play music (from mpd,amarok,audacious etc) the left mouse
button doesn't get "released". That is it acts as if the left button is held down. I can usually use the keyboard for navigation (I have had the keyboard and mouse completely lock up) but the only way to free the mouse is to restart X.

I have tested this in Gnome, KDE, Enlightenment and a few others. I have tried jumping out to a virtual console and
back, unloading and reloading different mouse modules, unplugging the mouse, but the only way i can find is to restart
GDM.

This seems to happen only when the music is first started. For example if I play a song via mpd and it continues to
play, I can use the mouse fine when X restarts even the the song is still playing. 

Anyone out there have any ideas?



I've got the same problem, in a way. My left button appears to get stuck,doesn't work after I use the keyboard shortcuts to open the music player,pause,play or even to raise or lower or mute the volume,otherwise the mouse is OK. To get the mouse to work again,I just need to unplug it for 3 seconds and plug it back in.It's a wireless mouse and keyboard combo.I've got an AMD 64bit processor with Ubuntu 64bit 10.10 running.
If you find a solution,let me know here and same for me.

---

### Post by The_Eddster on 2010-11-14
Yeah it's not amarok that's causing it, it happens everytime I press one of the media buttons on my wireless keyboard. It doesn't happen when I use the media buttons on my laptop though, just on the wireless keyboard. I'm gonna see if this bug has been reported.

---

### Post by The_Eddster on 2010-11-14
Here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311?comments=all)

---

### Post by Sykes2222 on 2010-11-14
> **The_Eddster said:**
> Here's the bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311?comments=all](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/636311?comments=all)

Thanks so much for this. I added the ppa:raof/aubergine patch and that fixed it. I can listen to music again. :)

---

