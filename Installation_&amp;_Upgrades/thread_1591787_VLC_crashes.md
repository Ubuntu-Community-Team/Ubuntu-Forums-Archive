---
title: "VLC crashes"
date: 2010-10-09
forum: Installation &amp; Upgrades
---

### Post by kroq-gar78 on 2010-10-09
Hello Ubuntu Forums Community,

I recently upgraded to Ubuntu 10.10RC. I tried to use VLC 1.1.4 (from official repos) and it crashes ~0.5-2 secs right after I run it (gui). When I say it crashes, it logs me out and sends me to the login screen. When I log back in, everything seems to have closed (apps, that is). I'm not sure how to get the terminal output since it immediately logs me out.

Tell me if you need more info. Thanks in advance.

---

### Post by andrewthomas on 2010-10-09
I would try a purge and reinstall.  I am on 64-bit 10.10 since may and have not had a single problem with VLC.

---

### Post by kroq-gar78 on 2010-10-10
sorry for the noob question but how do i "purge"? is it "sudo apt-get purge"?

---

### Post by andrewthomas on 2010-10-10
```
sudo aptitude purge vlc 
```followed by
```
sudo aptitude update && sudo aptitude install vlc
```

---

### Post by kroq-gar78 on 2010-10-10
I did what you said and it still doesn't work. I ran from terminal (just for fun) and wait a few seconds. Apparently, it is me putting the MOUSE  in the window. I do have a custom cursor installed and would be fine removing it. It changes back to DMZ-BLACK (maybe white) and THEN crashes. SHould I remove my cursor and replace w/ default? Thanks in advance.

---

### Post by KrisWillis on 2010-10-11
I am also experiencing this, though it also happens when I launch Opera, MusicBrainz Picard, VirtualBox (non-OSE), or Skype.

---

### Post by alphacrucis2 on 2010-10-11
Try running vlc from the terminal. The messages it outputs might provide a clue as to what is going on. I upgraded from 10.4 (64 bit) to 10.10 final yesterday and vlc is working fine for me so it doesn't seem to be a general problem.

---

### Post by KrisWillis on 2010-10-12
I have done some searching on Launchpad and it looks like this reported bug may be relevant.

[http://bugs.launchpad.net/ubuntu/+source/xorg/+bug/657966](http://bugs.launchpad.net/ubuntu/+source/xorg/+bug/657966)

---

### Post by kroq-gar78 on 2010-10-15
KrisWillis,

The bug is pretty much what's wrong with my comp. I have xinerama on, and skype nor vlc will start. Last I checked, there was no solution in the bug thread. Does anyone else know?

---

### Post by Auweia on 2010-10-16
I had success in running vlc after resetting the plugins cache:
```
vlc --reset-plugins-cache
```

---

### Post by kroq-gar78 on 2010-11-04
Auwela,

Thanks for the suggestion but it didn't help. I have a strong feeling its a problem with QT and Maverick. Virtualbox, skype, musescore, vlc, and some other programs all crash on 10.10 and use QT. Anybody got any other ideas?

---

### Post by mjarrod82 on 2010-11-22
I had a similar problem, VLC would not load when opening either from the Applications menu or when just double-clicking on a movie file. I tried marking for re-installation (then applying of course)in the synaptic package manager, no luck. Then the command to reset plugins listed previously in this thread. Nothing. 
I was able to get VLC to run from terminal, so just for the heck of it, I tried changing the skin arbitrarily and restarting VLC. Success!
This seemed to work for me. Now it loads as expected. 
I'm not experienced enough to know just why this worked, but I'm learning... I'll get there someday. 

Thanks to all the others that posted here, your inputs helped me get to my solution. Hope this works for someone else as well.

---

### Post by kroq-gar78 on 2010-11-26
oops meant to mark this thread solved a long time ago.

anyway, I fixed the bug through a fix in this bug report: [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/650539)

---

