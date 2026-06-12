---
title: "karmic update: sound not working with music players"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ittiam on 2009-10-24
After karmic update, there is no sound output while trying to play songs from any music player. I tried banshee, amarok, VLC, rhythymbox. But content from flash play fine. 

Initially I saw this error in syslog and the time progress bar for the song is stuck at 0:00

```
pulseaudio[2307]: alsa-sink.c: Error opening PCM device front:0: Device or resource busy
```

So I check my sound perferences and I do not see any ALSA specific thing there, nothing.

All I see under the Hardware tab under Choose a device to configure frame is Internal Audio. So in that tab the profile was initially set to Analog Stereo duplex and I changed it to Digital Stereo duplex.

After this I do not see the error mentioned above and I also see the progress bar for each song advancing but no sound. 

But I see this in the log, not sure even if it is an error or something.

```
pulseaudio[2307]: ratelimit.c: 106 events suppressed
```

I remember in jaunty I used to see some preferences and settings specific to ALSA in System->Preferences->Sound. But I dont see it at all in karmic.

I reinstalled pulseaudio but nothing changed.

Any help appreciated. It is so important to have songs playing, otherwise just cant work, just cant.

---

### Post by ittiam on 2009-10-24
The solution is do the following

```

pulseaudio --kill
rm ~r ~/.pulse
rm ~/.pulse-cookie
pulseaudio --startZ
```

as mentioned [here]("http://ubuntuforums.org/showthread.php?t=1158939&page=2")

---

