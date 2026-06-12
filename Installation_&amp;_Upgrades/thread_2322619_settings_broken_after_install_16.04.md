---
title: "settings broken after install 16.04"
date: 2016-04-29
forum: Installation &amp; Upgrades
---

### Post by ronron2613 on 2016-04-29
Hi everyone,

I installed ubuntu 16.04 on my notebook but soundcontrol seems not to be working properly.
No possible to change any settings.
If I play music, video the sound comes tru.
So my guess is that sound is bypassing pulseaudio en connects directly to alsa.

A second misbehaviour I see that the contextmenu is very slow to react.

The notebook is a HP pavillion dv8 (1000eb)
Soundcontrol in live
[IMG]https://drive.google.com/open?id=0B7bkXQl-ri-HSjNZam1ER1hvSEk[/IMG]

Soundcontrol after install
[IMG]https://drive.google.com/open?id=0B7bkXQl-ri-HbDNrQTlwc2tTclU[/IMG]


greetings,
Ronald

---

### Post by ronron2613 on 2016-04-30
Soundcontrol within Live
[IMG]https://www.dropbox.com/s/pru3tcftaadw3d7/Screenshot.sound.live.png?dl=0[/IMG][https://www.dropbox.com/s/pru3tcftaadw3d7/Screenshot.sound.live.png?dl=0](https://www.dropbox.com/s/pru3tcftaadw3d7/Screenshot.sound.live.png?dl=0)


Soundcontrol after installation
[IMG]https://www.dropbox.com/s/67rv5d2gn073uw7/Screenshot.sound.png?dl=0[/IMG][https://www.dropbox.com/s/67rv5d2gn073uw7/Screenshot.sound.png?dl=0](https://www.dropbox.com/s/67rv5d2gn073uw7/Screenshot.sound.png?dl=0)

---

### Post by msschambach on 2016-05-28
I got the answer to this from [http://askubuntu.com/questions/460089/system-settings-wont-load-after-ubuntu-14-04-installation](http://askubuntu.com/questions/460089/system-settings-wont-load-after-ubuntu-14-04-installation)

I just ran ```
sudo apt install unity-control-center
``` and everything was OK after that.

---

