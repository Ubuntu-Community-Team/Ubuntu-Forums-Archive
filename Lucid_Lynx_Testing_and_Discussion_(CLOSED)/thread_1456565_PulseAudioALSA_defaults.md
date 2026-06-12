---
title: "PulseAudio/ALSA defaults"
date: 2010-04-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jkxx on 2010-04-17
(I'm not sure if this is the proper place for suggestions so if not, mods, feel free to move this elsewhere..)

One of the issues I have had with *buntu for a while has been the sound support. I have an M-Audio Revolution 5.1 card which is officially supported, but has been troublesome to properly configure (as exemplified by threads such as [http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525").

So while the card has 6 channels available, only 2 are enabled by default and no tool is immediately available to configure it. In Kubuntu, KDE's "sound output device" settings section (System Settings->Multimedia) always errors out when trying to select anything but the front out.

I did some digging and found the problem can be fixed by opening
/etc/pulse/daemon.conf and adding the line

default-sample-channels = 6

along with installing the 'pavucontrol' app. Given this is all it takes, the current defaults don't seem to make much sense.

Could this be suggested as an essential defaults change somewhere?

---

### Post by sirkeith on 2010-04-17
There is a place for suggestions. I don't know where but this will give you a bump and maybe someone with the answer will see your post.

---

### Post by Yellow Pasque on 2010-04-17
> no tool is immediately available to configure it.
What about the gnome volume control? It has different audio profiles.

---

### Post by psyke83 on 2010-04-18
> **jkxx said:**
> 
I did some digging and found the problem can be fixed by opening
/etc/pulse/daemon.conf and adding the line

default-sample-channels = 6

along with installing the 'pavucontrol' app. Given this is all it takes, the current defaults don't seem to make much sense.

Could this be suggested as an essential defaults change somewhere?

I certainly agree that this should be fixed by default, but to modify everybody's daemon.conf by setting default-sample-channels=6, it would break all other types of speaker setups.

The unmodified daemon.conf file does not specify a default sample channel amount at all, so the required autodetection fix should be made within the pulseaudio code itself, somehow. There may be a bug filed on this issue already.

---

### Post by jkxx on 2010-04-18
That was the second thought that crossed my mind here, what happens if there aren't at least 6 channels. Hardcoding a value would not be the best solution.

Perhaps an algorithm that tries to detect 8 channels, then 6, then 4, and finally 2 for stereo and set channels accordingly as part of autodetection would work best.

> What about the gnome volume control? It has different audio profiles. 

That is not installed by default with kubuntu, although I suspect it would be a good idea to have it. However, it will fail too unless PulseAudio knows to use more than 2 audio channels.

I would post a bug, however launchpad has always prevented me from doing so in the past. Might still check to see if anyone else has done this already.

---

