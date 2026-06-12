---
title: "Nautilus gnome-session problem"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nyarnon on 2009-02-05
I'm using compiz with wallpapers so Nautilus is in the way. I solved this by disabeling Nautilus in gconf-editor by setting show-desktop to false. This week after an update gnome-session started spawning nautilus till the machine died. After a few hours debugging I now can control the problem. It seems to occur if you set the show-desktop bit to false. Even while setting it to true you see it stop spawning immidiatly to restart as soon as you set the bit to false. Does anybody else notice this if so I will file a bugreport.

---

### Post by marmuta on 2009-02-06
Yes, I can easily reproduce this with clearing show_desktop and I had filed a bug report here [#324925]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/324925"), but it has been marked as invalid. So feel free to report it again and I'll confirm.
There is a workaround too. It doesn't seem to happen when there is a file browser window open at all times.

---

### Post by nyarnon on 2009-02-06
> **marmuta said:**
> Yes, I can easily reproduce this with clearing show_desktop and I had filed a bug report here [#324925]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/324925"), but it has been marked as invalid. So feel free to report it again and I'll confirm.
There is a workaround too. It doesn't seem to happen when there is a file browser window open at all times.

I don't see it marked invalid, only the crashreport, the bug is open and filed as medium. I will have a look later this evening as there is also a message that their should be a new nautilus. Pitty it doesn't state a version?

---

### Post by nyarnon on 2009-02-06
Just updated to alpha 4 and the problem persists with Nautilus 2.25.4

---

### Post by taavikko on 2009-02-07
> **nyarnon said:**
> Just updated to alpha 4 and the problem persists with Nautilus 2.25.4

Then report it. Or Use marmuta's bug, and change the status to "confirmed"

btw. apport marked it invalid, maybe bug within apport :)

---

### Post by nyarnon on 2009-02-07
I jjust confirmed it. Wonder why there are not more reactions? Are we the only testers who use this option. Can become a real mess after the release IMHO.

---

### Post by nyarnon on 2009-02-15
Hmmm this is funny, I renamed nautilus to nautilus.bak and guess what I found after a restart. The wallpaper still appears. Double checked that there is no other Nautilus available. It does make me wonder if the new wallpaper mechanism could be the culprit?

---

### Post by nyarnon on 2009-02-24
Found a better bugreport for the issue with more info
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325973](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/325973)

---

### Post by nyarnon on 2009-03-03
Todays update reset the nautilus.desktop file rendering marmuta's solution useless I had to reset it manualy to false again as gnome started spawning happely again :-)

As Marmuta's solution isn't shown here and the original launchpad thread featuring it was closed I quote it here:

Marmuta says:
Fwiw, the one workaround I found was that I can stop gnome-session from respawning nautilus by setting X-GNOME-AutoRestart=false in /usr/share/applications/nautilus.desktop.

---

### Post by nyarnon on 2009-03-11
And today again the nautilus.desktop file was updated, the problem still exist. Aplied marmuta's patch again.

---

### Post by nyarnon on 2009-03-16
And again a major update but the problem persists stop gnome-session from respawning nautilus by setting X-GNOME-AutoRestart=false in /usr/share/applications/nautilus.desktop.

---

### Post by drs305 on 2009-03-28
Same result in the initial Jaunty beta - *new install for me (other than VM)*. Patch still works though.

---

### Post by nyarnon on 2009-03-28
nautilus.desktop didn't change in the update to beta. Lot's of other stuff broke though, thank god we have something to play with :-)

---

