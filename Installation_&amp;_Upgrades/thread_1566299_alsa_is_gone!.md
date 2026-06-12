---
title: "alsa is gone!"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by adpads on 2010-09-02
Hi all!
Just setting up a brand new Acer TimelineX 3820TG laptop. I had everything running smoothly (despite the fact that the hardware took a lot of twiddling) - and then I managed to break the sound while trying to fix it.

I had upgraded to alsa 1.0.23-2 using this script:
[HTML]http://ubuntuforums.org/showthread.php?p=6589810#post6589810[/HTML]

and everything was working fine, except that firefox and other browsers would grab the alsa device, and were not able to share it with other programs. In an effort to fix this, I made the mistake of adding the ubuntu-audio-dev PPA, and installing the linux-alsa-drivers package from there.
Result: No hardware appearing in the sound settings, no sound, and no alsamixer: 

```
$ alsamixer
cannot open mixer: No such file or directory

$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory

$ ls /dev/snd/control
ls: cannot access /dev/snd/control: No such file or directory

$ cd /proc/asound
bash: cd: /proc/asound: No such file or directory
```

But

```
$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] (rev ff)

```

So the sound cards are there and enambled in the BIOS. I have added my user to the audio group (which it hadn't been before) - but even running alsaconf only delivers snd-hda-intel, and no change in the state of sound.

I have since removed the package from the ubuntu-audio-dev-PPA, but I am afraid that may have made the situation worse.

Help!

---

### Post by adpads on 2010-09-03
I didn't solve this problem, but I reinstalled fresh - so for the moment, never mind..

---

