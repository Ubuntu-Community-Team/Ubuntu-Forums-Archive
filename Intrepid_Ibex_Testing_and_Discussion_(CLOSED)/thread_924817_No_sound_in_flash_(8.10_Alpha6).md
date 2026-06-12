---
title: "No sound in flash (8.10 Alpha6)"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by malfist on 2008-09-19
I just made a fresh install of Alpha6 and have no sound in flash with pulseaudio. How can I fix this?

Malfist

---

### Post by G-Dub on 2008-09-19
I've had this problem before in 8.04. I have 2 sound cards (integrated and add-on) which i switch between. Whenever i switch, it fixes it. Just something you might want to try if you have 2 sounds cards.

---

### Post by mb_webguy on 2008-09-20
It may also be due to the well documented incompatibility problems between the Flash 9 plugin and PulseAudio.  Installing the Flash 10 plugin from the backports repository (see my signature for instructions) may fix the problem.

---

### Post by Sef on 2008-09-20
moved to intrepid ibex.

---

### Post by psyke83 on 2008-09-20
I had to search through your posting history to get an idea of your system specs, you may want to volunteer more information in the future.

Version 2.2ubuntu13 of ia32-libs has removed libflashsupport (which is what allowed flash 9 to work with PulseAudio at the cost of some instability).

Flash 10 is in Intrepid and can work with PulseAudio without the need for libflashsupport, so this library was removed in order to improve stability. However, in order for flash to work correctly with PulseAudio, you must enable the PulseAudio ALSA plugins:

```
$ asoundconf set-pulseaudio
```

P.S. From your posting history I also see that you experimented with OSSv4 and you've had problems with ALSA, so your difficulties could be due to problems in ALSA. I don't recommend you try OSSv4 on Ubuntu again - you're only asking for trouble, especially since it's not compatible with PulseAudio.

---

### Post by malfist on 2008-09-20
I have disabled Flash 10 and am using Flash 9 because of this bug: [https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251700](https://bugs.launchpad.net/ubuntu/+source/firefox-3.0/+bug/251700) I visit Facebook often, and if causes my quad-core to become fully utilized, that's unacceptable.

As for my posting history, my computer has been upgraded, but the sound card is the same. Of course, pulseaudio doesn't work with OSS, I know that. OSSv4 worked where ALSA and Pulse was failing. Usually I could get alsa to work by itself without pulse but one time, I rebooted and lost all sound and had to switch back to OSSv4.

I'll try your fix, and see what happens.

---

### Post by malfist on 2008-09-20
Switched back to Flash 10 and tried the fix with no luck.

Edit: System Specs:
AMD 9850 Black Edition
1.2TB in 3 HDD's
4 GB RAM
GeForce 6800
C-media (supported chipset) sound card

---

### Post by ajeetraj on 2008-09-20
I had the same problem with Flash after a fresh install of Intrepid. When I tried to play Youtube or Google videos or any other videos online, it would play but there was no sound. 

I knew that Skype had some problems with the audio playback. I quit skype and then I closed firefox and then I restarted firefox and the sound was working. I think there is a problem with skype and firefox. 

For me whenever I am playing any video in firefox and if I start skype and try to make a call, I get a messages saying "problem with audio-playback" in skype. If I close firefox and restart skype the the problem with audio playback is fixed. 

I hope that either skype or ubuntu people will fix this. 

I don't know if it is going to help you but then I thought I should share my experience related to it. Hope that you find a solution soon. 

all the best!

---

### Post by gjoellee on 2008-09-20
Install Flash 10 .deb....download here: [http://www.kshoster.net/?c=downloads&h=deb](http://www.kshoster.net/?c=downloads&h=deb)

Hope it helps:)

---

### Post by ajeetraj on 2008-09-20
after installing the new flash, the sound is still not working :P

---

### Post by malfist on 2008-09-20
> **gjoellee said:**
> Install Flash 10 .deb....download here: [http://www.kshoster.net/?c=downloads&h=deb](http://www.kshoster.net/?c=downloads&h=deb)

Hope it helps:)

Now I have neither audio or visual :(

---

### Post by SeePU on 2008-09-21
I installed Flash 10 in Kubuntu Intrepid 8.10 with no problem.  I had sound and audio.  This probably doesn't help you but I'm just saying that it should work.  I wasn't using Pulse Audio as far as I know.

---

### Post by psyke83 on 2008-09-21
> **malfist said:**
> Now I have neither audio or visual :(

Who runs that kshoster.net site, is the flash package safe? Judging from the filename it seems to be a custom deb. It's much better to test packages that are compatible with the official releases. I suggest you try the packages in my PPA (they'll be official soon, pending testing). You can find the information in the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=866965") thread.

---

### Post by malfist on 2008-09-22
> **psyke83 said:**
> Who runs that kshoster.net site, is the flash package safe? Judging from the filename it seems to be a custom deb. It's much better to test packages that are compatible with the official releases. I suggest you try the packages in my PPA (they'll be official soon, pending testing). You can find the information in the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=866965") thread.

After following those instructions I lose sound system wide.

---

### Post by malfist on 2008-09-22
Sounds reports this when I attempt to play the test sound:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect: Connection refused

```

---

