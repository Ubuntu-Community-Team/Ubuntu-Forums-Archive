---
title: "Is anyone running Teamspeak with Ubuntu 8.04?"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by weee on 2008-05-08
Hello, I was wondering if anyone knows how or if you can run Teamspeak with Ubuntu 8.04.

---

### Post by LordVeovis on 2008-05-12
I am having problems myself as well. I can ghet the program to launch and run fine, but I cant get it to let me use my headset for the mic or for the incomming audio.  How does linux map these so I can manuallt tell TS that I want to use my USB headset?

Is your problem that u cant even get it to launch? or what? more info pls...

---

### Post by LordVeovis on 2008-05-12
HAHA!!! YES!! I now have it working, respond when you can I think I can walk you thru it, but here is where I learned:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Sound)

---

### Post by netjunk1e on 2008-06-29
Any way you can walk me through that post?

I tried to do it my self and didnt get anywhere.

---

### Post by ex.hav0k on 2008-06-29
here's what let me use my logitech usb headset, already configured with alsa for the system, as in, i could get audio from everything else, like youtube and system sounds.

open teamspeak
settings>options

choose other, and put /dev/dsp1 in there.

then it works!
but you can't hear anything else... like system sounds or anything else, like youtube.  sucks.  if someone knows how to fix that, i'd love to be able to hear other things while using teamspeak.

ps, i read somewhere that ts3 will have alsa support and it'll just work better.

---

### Post by quanumphaze on 2008-07-01
If it's using OSS for sound you can try to use the padsp wrapper that lets it play through PulseAudio without hogging the whole sound card.```
padsp teamspeak
```

---

### Post by Ryan Marcus on 2008-07-04
If padsp does not work for you (it did not for me) you can give good ol' ALSA a shot with a little help from WINE. My guide: [http://rmarcus.wordpress.com/2008/07/01/teamspeak-in-linux-with-logitech-or-other-usb-desktop-microphone-on-ubuntu/](http://rmarcus.wordpress.com/2008/07/01/teamspeak-in-linux-with-logitech-or-other-usb-desktop-microphone-on-ubuntu/)

---

### Post by SmilerUK on 2008-07-24
Hi

I followed a post I found here and I downloaded it through Synaptic Package Manager and it worked first time, no problems. Just go to Synatic Package Manager search for Teamspeak and download and install. It appears in Applications / Internet

Hope this helps

---

