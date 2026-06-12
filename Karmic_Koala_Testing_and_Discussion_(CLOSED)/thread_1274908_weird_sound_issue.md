---
title: "weird sound issue"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-09-25
I have a strange sound issue. On boot up the sound doesn't work. The login sound is played but when I am in the desktop I can't playback anything regardless of the player.

When I issue this command (as mentioned in a previous thread)

sudo rm -rf ~/.pulse ~/.pulse-cookie && sudo killall pulseaudio

It gets the players working again but I have to go and uncheck then recheck the options in the gnome-alsa mixer to get the sounds working again

Headphone (checked)
ICE958 (checked)
IEC958 Default PCM (checked)
Channel Mode (unchecked)
Input Source (unchecked)

Does anyone know how I can get this permanently fixed? Every time I reboot I have to go through this arduous process all the time.

I am using

 82801H (ICH8 Family) HD Audio Controller

IN digital mode.

---

