---
title: "Video lagging behind audio"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dude2425 on 2009-09-21
One of the updates this week has made watching video a pain on my Asus Eee PC 1000h running Karmic. About half way into the video the video slows or stops completely, leaving the audio to continue on. The video will eventually catch up and stop again. I had no trouble last week watching regular television shows.

So far the only video codec I've tried to watch has been XVID MPEG-4.

---

### Post by andrewabc on 2009-09-21
What video player are you using? VLC? Totem?
How big is the video file? high quality or bad quality?

---

### Post by dude2425 on 2009-09-21
I have made an attempt to try all video players that I could. I tried Totem, VLC, Xine, and Mplayer, all with the same issue. The first video that I noticed the problem with is 41 minutes and 51 seconds. The second is 24:29. 350mb and 232.1mb respectively. Both video's were standard quality, 624x352 and 704x400 respectively. Same encoding I've always watched with the same hardware with no trouble at all. XVID MPEG-4 video, standard MP3 audio.

---

### Post by andrewabc on 2009-09-21
Do you have compiz enabled?

---

### Post by dude2425 on 2009-09-21
I do, but I have attempted to disable it, reboot fresh, and then watch the same video and still the same results. Despite that, if it were compiz that were causing trouble, I would still consider that a regression. I have full compiz enabled on my netbook, and never had problems before.

I have noticed that my swap partition is not being used.

```
$ free -m
             total       used       free     shared    buffers     cached
Mem:          2005       1293        711          0         64        701
-/+ buffers/cache:        527       1477
Swap:         2863          0       2863

$ cat /proc/sys/vm/swappiness 
60

```

I'm not sure if this would cause the trouble or not, but it could have something to do with it. Any clue how to make swap work again to see if it's an issue?

---

