---
title: "screwed sound in Lucid"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Linux-Djihad on 2010-03-14
Since I upgraded to Ubuntu 10.04 Lucid Lynx, I have weird problems with the sound. First of all I thought it's related to mplayer because I only had sound problems there, but it seems that it affects not only mplayer.

First I got in mplayer the following output:
bt_audio_service_open: connect() failed: Connection refused (111)

I solved this with removing alsa-bluez. But then mplayer still doesn't have sound. Then I remove .pulse from my home directory and logged in again. After that I tried player an avi file. It worked. Then I player an mp3 with Audacious2. It worked. But as I started a wmv-file, sound was gone. I tried the first avi file again, but still no sound. Suddendly the sound didn't work in Audious2 either. After short time I played an mpg file, I was able to hear the sound again. Then the sound in Audacious2 worked again. Fact is that mplayer is not able to play sound from media files due to any reason. Sometimes it works, sometimes not. I don't have problems in other programs. 

In mplayer.conf my sound is set to pulse,alsa,... so it's not a configuration issue. (And I never had problems in Karmic). dmesg doesn't show anything. 

What's going on here?

---

### Post by overdrank on 2010-03-14
Hi and moved to Lucid Lynx Testing and Discussion

---

### Post by Linux-Djihad on 2010-03-14
I think it is related to ffmpeg, because when I extract audio from an avi, I hear nothing. Does mplayer use ffmpeg as well or is this another bug? (By the way: the avi works correctly in VLC so I hear sound there)

---

### Post by Linux-Djihad on 2010-03-14
Ok, the issue with ffmpeg was a misunderstanding, because there seemed to be a conflict between VLC and pulseaudio which led to the problem that I can't listen to any mp3 in audacious2. I reinitialized pulseaudio and can listen to the mp3. So there is only the problem with mplayer I already described.

---

### Post by Linux-Djihad on 2010-03-15
It's probably a pulseaudio issue, because when I telephone in Skype by webcam and meanwhile write a message in the chat box of skype, the soundserver has been knocked out of its stride.

---

