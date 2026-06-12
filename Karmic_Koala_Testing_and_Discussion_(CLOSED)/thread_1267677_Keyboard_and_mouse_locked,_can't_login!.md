---
title: "Keyboard and mouse locked, can't login!"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by simmeson on 2009-09-16
Been using karmic since alpha 5 now and everything has been just fine so far. But today after some updates I can't login because my keyboard and my mouse are locked, it's just like theyve been unplugged. KDM is loading fine but I can't write or move the mouse cursor. If I change to CLI mode I can type, but I don't wanna be stuck with commands when I have my lovely KDE desktop ;)

My thoughts have been to try boot in to recovery mode, but how am I doing this in GRUB2?

Help are appreciated!

/Simon

---

### Post by slakkie on 2009-09-16
I've had the same problem. I've tried updating via chroot, but that b0rked more then it fixed: Cursor of death, like mentioned here [http://ubuntuforums.org/showthread.php?t=1267040](http://ubuntuforums.org/showthread.php?t=1267040) and in other threads.

The irritating thing is that I could not find anything in the logs.

---

### Post by simmeson on 2009-09-16
Anyone have an idea? Atleast how I can get internet access from the CLI?

---

### Post by Eestlane on 2009-09-16
You could try
```
sudo dhclient eth0
```
This will try to autoconnect to eth0 interface.

---

### Post by meborc on 2009-09-16
my advice is: get internet... wait a few days and keep apt-get upgrade'ing until the problem is solved

if the problem did not come from upgrade and you messed your system up by yourself, then it is a different story :D

@Eestlane: tervitus!

---

### Post by simmeson on 2009-09-16
> **Eestlane said:**
> You could try
```
sudo dhclient eth0
```
This will try to autoconnect to eth0 interface.

THANKS! Now I managed to download the latest updates and now my system works like a charm :)

---

