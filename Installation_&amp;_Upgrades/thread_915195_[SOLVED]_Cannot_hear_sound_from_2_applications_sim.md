---
title: "[SOLVED] Cannot hear sound from 2 applications simultaneously"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by steak-sandwich on 2008-09-09
I installed Ubuntu 8.04 and everything works. My sound works as well but there is only one problem which I didn't have with all the previous versions. 
For instance, when I open skype I get sound but if I open mplayer or watch a video on youtube I don't get sound from this source. Then I have to close skype and re-open mplayer, firefox.....to watch a video or listen to some music. 
It's independent of the applications, I just can't get sound from 2 different programs. Why? This used to work. And it even works with Windows!! :-) 

Thanks,

BEN

---

### Post by mikewhatever on 2008-09-09
The problem is pulseaudio. Go to System ->Preferences->Sounds and change everything to alsa in the first tab.

---

### Post by Vivaldi Gloria on 2008-09-09
The following guide fixes pulseaudio bugs:

[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

### Post by steak-sandwich on 2008-09-12
okay thanks, I have already seen this thread about the pulseaudio bug. I thought I can avoid it but it seems like this is the problem.

---

