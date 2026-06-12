---
title: "no video output in KDE 4.4 RC1"
date: 2010-01-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by biasquez on 2010-01-16
hi, i have problems with video and kde 4.4 rc1: exactly, if i try to see a video, for example xvid, with all players don't show video output but only audio output. moreover with vlc i have this error: vlc doesn't support video or audio XVID...
only with smplayer/mplayer video works fine. 
i think that problem is phonon and xine backend...how can i fix it?
do you have this problem?

EDIT:
purging all xine packages installed from ppa and reinstalling default packages fix problem.

P.S. i'm learning that it's not good idea using ppa repository with kubuntu :(

---

### Post by seeker5528 on 2010-01-16
Make sure that libxine1-plugins is installed.

Don't know if it's necessary for the xvid/divx support, but there is also a libxvidcore4 package, seems odd the VLC would say the play back support was not there if mplayer can play it.

Looks like I was a bit slow to respond. Good to hear you got it fixed. 

Later, Seeker

---

