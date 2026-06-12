---
title: "Sound : webcam at main sound device instead soundcard"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by cosmocat on 2005-04-23
Hello,

*edit : this message is a repost because I have posted in the wrong part of the forum...*

I have installed ubuntu Hoary (good ;) ) and I still have sound with totem.
After a lot of time of reinstall alsa package, modify config files (with not too mutch knowledge), I find that I have not sound with all the application exept totem (rhytmbox, amarok,juk,cdplayer,...) because my webcam (on usb) is detected like my first soundcard instead of my sound blast live.

cat /proc/asound/cards
```
0 [Camera         ]: USB-Audio - Camera
                     Camera at usb-0000:00:1d.2-2, full speed
1 [Live           ]: EMU10K1 - Sound Blaster Live!
                     Sound Blaster Live! (rev.8) at 0xdf40, irq 22
```

Someone on the french forum tell me to add this line :
options snd-usb-audio index=-2
at the of the config file /etc/modutils/alsa-base but it changed nothing.

it seems it is a bug on ubuntu : [https://bugzilla.ubuntu.com/show_bug.cgi?id=1467](https://bugzilla.ubuntu.com/show_bug.cgi?id=1467)

and I can have sound if I don't use my webcam but it's not what I want.

I also try to edit the file /usr/share/alsa/alsa.conf to change all the file like this one :
defaults.ctl.card 0
by 
defaults.ctl.card 1
expecting to use the sound card detected by the numer '1'.
But nothing change too.

Have you got a solution for me??? You can imagine how I will be happy!

thanks in advance.
cosmocat

---

