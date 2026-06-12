---
title: "Sound problem when running 2 X server"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by creatorlarryli on 2008-10-10
Hi,

I've been running games using wine on another X server for better performance. But since I upgraded to intrepid, the sound never worked in another X server.
It always gave the error message:
```
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: Permission denied
```
The commands I used:
```
sudo X :3 -ac
cd "/home/larry/.wine/drive_c/Program Files/Warcraft III"
sleep 2
DISPLAY=:3 WINEDEBUG=-all wine "C:/Program Files/Warcraft III/Frozen Throne.exe" &
```

I also noticed that in hardy if I was playing music in my first X server using amarok or alike and then I switched to ttyn or another X server, the music would stop right the way, but now the music just goes on. 

I don't know if this is a bug or rather more likely a change of the settings of the sound server. But I really don't think it is a bug of wine because other programs like totem or xine also won't play any sound in another X server. (Just try something like DISPLAY=:3 xine /usr/share/sounds/question.wav and you should see it.)

Does anyone know how to solve this?

---

