---
title: "Pulse Audio 0.9.14 and Bluetooth headset"
date: 2009-04-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2009-04-20
According to the [Bluez Audio HowTo]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices#Pulseaudio"), you should be able to use a bluetooth headset with bluez 4.27-33 and pulse 0.9.14 (both in Jaunty).  My headset connects fine now in Jaunty and I'd like to get my BT headset audio working (either with ALSA or Pulse, but preferably Pulse).  However, I played with the suggestions on the Bluez Wiki for a while and couldn't figure out why things aren't working.  Has anyone had any luck?  I know that PA 0.9.15 came out recently with improved BT audio support, but I'm wondering if I can't make the one installed by default in Jaunty work with my headset.  I tried uncommenting the line "load-module module-bluetooth-discover" in /etc/pulse/default.pa (according to the Bluez wiki) and upon restarting my computer, I think PA even detect my headset (I could hear a slight hiss and I got a confirmatory *beep* when my headset connected), but it subsequently froze up the system and made it unusable.  Any attempt to play audio was futile.  

Has anyone had any luck with this or do you care to play around?

---

### Post by jblackhall on 2009-04-20
Looks like it's no use: [http://identi.ca/notice/3584083](http://identi.ca/notice/3584083)

---

