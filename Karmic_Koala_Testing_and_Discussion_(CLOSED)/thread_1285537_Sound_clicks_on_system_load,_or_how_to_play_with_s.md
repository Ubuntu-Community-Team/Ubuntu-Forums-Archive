---
title: "Sound clicks on system load, or how to play with schedulers on the fly?"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-10-07
Probably during last week or so I have noticed audio players click on system high loading (I deal with JVM apps and it is common situation both core of Core 2 Duo are busy with java tasks). The problem is not related to audio players: the issue takes place both with, say Amarok and MPD. Last ones use absolutely different audio chains (phonon-xine-alsa and alsa directly).

I have never had the problem before starting from A4, so, a regression takes place.

BTW, X11 resposivity seem also slightly degraded in sync with this sound problem.

I have tried - in accordance with [http://www.linuxhowtos.org/System/iosched.htm](http://www.linuxhowtos.org/System/iosched.htm) - to play with another schedulers, but echo'ing to scheduler is forbidden even for 'sudo'-started command:

```
sudo echo noop > /sys/block/sda/queue/scheduler
bash: /sys/block/sda/queue/scheduler: Permission denied
```

Up to date Kubuntu Karmic is in use.

Help!

---

### Post by FuturePilot on 2009-10-07
> **ilna said:**
> Probably during last week or so I have noticed audio players click on system high loading (I deal with JVM apps and it is common situation both core of Core 2 Duo are busy with java tasks). The problem is not related to audio players: the issue takes place both with, say Amarok and MPD. Last ones use absolutely different audio chains (phonon-xine-alsa and alsa directly).

I have never had the problem before starting from A4, so, a regression takes place.

BTW, X11 resposivity seem also slightly degraded in sync with this sound problem.

I have tried - in accordance with [http://www.linuxhowtos.org/System/iosched.htm](http://www.linuxhowtos.org/System/iosched.htm) - to play with another schedulers, but echo'ing to scheduler is forbidden even for 'sudo'-started command:

```
sudo echo noop > /sys/block/sda/queue/scheduler
bash: /sys/block/sda/queue/scheduler: Permission denied
```

Up to date Kubuntu Karmic is in use.

Help!

Try
```
echo noop | sudo tee /sys/block/sda/queue/scheduler
```

sudo can't be redirected. If it could that would be a big security risk. That's where the tee command comes in.

---

### Post by ilna on 2009-10-07
FuturePilot,

Thanks! - 'tee' helps. Are there other recommendations wrt the problem (wrt io schedulers and beyond them)? - say, do I need 1000HZ and how to set it, and such...

---

### Post by FuturePilot on 2009-10-07
> **ilna said:**
> FuturePilot,

Thanks! - 'tee' helps. Are there other recommendations wrt the problem (wrt io schedulers and beyond them)? - say, do I need 1000HZ and how to set it, and such...

Sorry I don't know a whole lot about schedulers. Hopefully someone else here is more knowledgeable in this area and can help you. :)

---

### Post by ilna on 2009-10-08
Have tried all schedulers - noop, anticipatory, deadline and cfq - there isn't luck in the world :(  - deadline and noop are better than anticipatory and cfq, but still stutters takes place.

Has anybody other suggestions except for io schedulers?

---

