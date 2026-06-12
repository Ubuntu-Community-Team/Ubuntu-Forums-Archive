---
title: "sound problems after upgrade"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by knavarathna92 on 2009-12-06
Hey so I upgraded from Jaunty to Karmic today because I thought the bugs would have been patched by now, but after I upgraded, I had no sound. 

In a nutshell, here's what happens: I log in, I hear the log in sound perfectly. I play any video, the sound plays nicely in the beginning but maybe 10 seconds after goes down to very low levels until it's essentially muted. I followed the tutorial here ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) and looking at volume control, nothing's muted and the bars for each program on the playback tab are moving. My only input and output devices are internal analog stereo (don't know what this means, I don't have speakers but I use headphones). Alsamixer shows PCM is at 100% but there is no option to mute/unmute shown (maybe it's muted? Can't tell)

I'm pretty confused and have extremely limited computer skills so any help would be appreciated.

Funny thing is, a couple of moments later after I stop playing sound, it comes back only to die down a couple of seconds later (this process repeats itself).

IMPORTANT : Pulse Audio device chooser won't run (in the teminal,I run the command and nothing shows up)

---

### Post by knavarathna92 on 2009-12-06
OK, so I SOLVED IT!!!:popcorn:

Well, I worked around it, but I'm just happy to have my sound back.

What I did was:
1) Remove Pulse Audio (I've been annoyed with Pulse back when it first came about)
2)
open up a terminal
Code:
sudo gedit /etc/modprobe.d/alsa-base.conf
Add this line at the end of the file
Code:
options snd-hda-intel model=3stack

Note: your model differs based on your comp, but I think there is a list floating around on the forums.

---

