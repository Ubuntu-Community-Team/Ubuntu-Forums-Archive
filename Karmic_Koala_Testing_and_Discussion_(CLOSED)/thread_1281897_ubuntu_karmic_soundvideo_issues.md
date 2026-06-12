---
title: "ubuntu karmic sound/video issues"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Tenn lynx on 2009-10-03
Hey

the problem is that sound stops working or is jerky in totem, firefox+adobe flash, vlc... in totem the picture will freeze and sound will get jerky, after that the movie starts skipping or playing too fast...

pretty much the same thing happens in flash, picture freezes and sound goes on while the picture starts skipping and freezing. Firefox also freezes totally when the picture freezes.

vlc has sound issues when I'm moving my mouse(maybe an unrelated problem) while the mouse is moving the sound is gone. Vlc also looses sound after a while.

the system is an HP laptop pavilion dv7, intel ICH9 sound card, usb mouse.

anyone experienced anything similar?

---

### Post by overdrank on 2009-10-03
Moved to Karmic Koala Testing and Discussion

---

### Post by Tenn lynx on 2009-10-04
ok so edited /etc/modprobe.d/alsa-base.conf
and did this:
#options snd-hda-intel power_save=10
options snd-hda-intel enable_msi=1 model=hp-dv5

not sure if the power saving feature has anything to do with it, but since the problems start after a while it seemed suspicious, so I commented it out.
The other line used to be vital to enable audio on my laptop, but audio "works" out of the box in 9.10. I added it just in case.

anyway, one or the other thing fixed my issues. Vlc still has some problems, but I think they're not really related. Totem and flash work just fine now.

regards
tenn

---

### Post by moster on 2009-10-04
Install first ubuntu restricted extras from ubuntu software center. Also look up for gstreamer, he is dealing with codecs too.

If you enabled proprietary drivers in menu system/administration/hardware drivers you should not have any problems with video.

---

### Post by anoxi on 2009-10-06
i've got ubuntu-restricted-extras and the gstreamer plugins installed. sound is working fine but any video (wmv,xvid,divx) is just showing a black picture in totem or vlc. anyone else experienced this ?

---

### Post by Revage on 2009-10-09
Yep, I can confirm this. 
Any videos playing in Totem (also stream in Firefox via Totem) are playing ok, though they are rediculously fast.

Using VLC the speed of the video is back to normal, but the sound is stuttering.

Using Flash inside Firefox, both, the sound and the video stutters. 
I am not using an Intel card though. Do not ask me what it is exactly, just some retail soundcard from the store.

---

### Post by Taijitu on 2009-10-09
I have this problem as well, and can inform you that it is related to pulseaudio. If you remove the pulseaudio package in synaptic, video and flash and everything else audiorelated will work just fine... But you will lose the traditional volume control. You can control the volume by installing xfce4-mixer and opening it, but the old mixer applet with the volume key bindings is not included in karmic :-(.

Problem is also posted in [this]("http://ubuntuforums.org/showthread.php?t=1284219") thread.

---

