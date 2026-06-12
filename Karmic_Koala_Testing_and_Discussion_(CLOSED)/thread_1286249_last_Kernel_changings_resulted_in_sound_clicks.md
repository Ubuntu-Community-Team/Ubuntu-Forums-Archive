---
title: "last Kernel changings resulted in sound clicks"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ilna on 2009-10-08
Borrowing symptoms from here [http://ubuntuforums.org/showthread.php?p=8070908](http://ubuntuforums.org/showthread.php?p=8070908)
[I]
"... Probably during last week or so I have noticed audio players click on system high loading (I deal with JVM apps and it is common situation both core of Core 2 Duo are busy with java tasks). The problem is not related to audio players: the issue takes place both with, say Amarok and MPD. Last ones use absolutely different audio chains (phonon-xine-alsa and alsa directly).

I have never had the problem before starting from A4, so, a regression takes place."[/I]

Ok, I have played with io schedulers without any luck. Does anybody know which kernel configuration changes were made approximately week or two ago, which (theoretically) can result in the issue?

---

