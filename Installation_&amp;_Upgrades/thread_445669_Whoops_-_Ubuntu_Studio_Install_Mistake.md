---
title: "Whoops - Ubuntu Studio Install Mistake"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by zheepeez on 2007-05-16
Hey all,

I just installed Ubuntu Studio dual-booting with Windows (have to have my games) and overall i like it - except, uh, i accidentally *embarassed cough* didn't install any of the audio, visual, or video packages that come with it... they came up with install options during the OS install, but I accidentally didn't select them... If I want to install those now, do I just reboot from the DVD (its not a LiveCD, it's an install disc), or do I have to manually select the packages from Synaptic? Cheers...

If need be, I can always just format the partition and reinstall clean, as I only just installed it, but that's kinda a lengthy process.

Much appreciated.

---

### Post by Tom Mann on 2007-05-17
You need to do the following

sudo apt-get install ubuntustudio-audio
sudo apt-get install ubuntustudio-audio-plugins
sudo apt-get install ubuntustudio-graphics
sudo apt-get install ubuntustudio-video

Each line is self explainable. Pick the ones you need. I found if you do an apt-get remove on one of the above followed by a 'sudo apt-get autoremove' would remove it's associated packages cleanly, so if you fancy trying one of the other parts you can go for it :)

---

