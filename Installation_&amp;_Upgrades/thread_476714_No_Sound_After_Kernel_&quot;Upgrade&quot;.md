---
title: "No Sound After Kernel &quot;Upgrade&quot;"
date: 2007-06-17
forum: Installation &amp; Upgrades
---

### Post by Gibran on 2007-06-17
Hello everyone,

I did the latest kernel *upgrade*, after which I had lost sound and all audio apps would freeze. I could load the previous kernel and everything would work fine, until yesterday I *upgraded* again, still got no sound but now x server fails to load on the older kernel. I tried

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

sudo apt-get install linux-sound-base alsa-base alsa-utils

sudo apt-get install gdm

```

as suggested in another post and when I rebooted I got the same problem. What do I need to do to restore my sound card??

EDIT: I can't open alsamixer on the terminal now, either :(

---

### Post by 5-HT on 2007-06-17
Is your sound card module getting loaded in the new kernel? You can find out which one you're using in the old kernel by doing a lsmod -l  grep snd. Is that module getting loaded in the new kernel? If not, load it manually and see if you get sound working.
About the alsamixer issue: what error message are you getting?
If you're running ubuntu, try reinstalling ubuntu-desktop in case any alsa related packages got removed. What's the error when you try to start X on the old kernel?

---

### Post by highcliff on 2007-06-17
High..I upgrade kernel and the wireless card not shown in network setting ,i go to system-administration -restricted device manager then i download the drive and it's OK... try this.

---

### Post by Gibran on 2007-06-26
sorry for taking so long, I was in the process of moving to another city... When I try opening alsamixer from the terminal it tells me the command is not recognized, and the problem with xserver is that it "could not find any screens" or something like that. I am replying from work, since I still don't have internet set up at home. If I could load xserver on my old kernel I'd be happy, at least for now.

How can I enable the sound card manually? If I try as much as opening the volume control it tells me I have no sound card installed. I don't have internet at home yet, so I guess that would be a problem. I should also note that video and audio players crash when I open any media files on them... I would reinstall but I don't think it would help too much and I would be devoid of applications and everything until my ISP feels like restoring my service.

Please help!

---

