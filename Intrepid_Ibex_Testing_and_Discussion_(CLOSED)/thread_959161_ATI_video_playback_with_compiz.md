---
title: "ATI video playback with compiz"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Firestrider on 2008-10-26
Currently I'm having problems with video playback with compiz active. The problems are the video will flicker with black screens frequently in any media player (totem, vlc, mplayer). If I disable compiz + emerald the problems will go away. I'm using the fglrx proprietary driver. [ This is in Ubuntu 8.10 ]

Also I'm looking for an all in one media player... video, music, radio streams, media libary + sorting, burning, and ripping... kind of like windows media player

Also can OpenOffice open accdb and docx formats?

---

### Post by jcmorris on 2008-10-26
If you install Gnome Mplayer it seems to work very well with compiz. I get no flicker with it. I used [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) to install and set it as my media player in Firefox. I'm using a X1900XT and get the same flicker except for gnome mplayer.

---

### Post by sdowney717 on 2008-10-26
just switch video output module to x11

---

### Post by Najmudin on 2008-10-26
I have the same problem ,I noticed that visualisation also flickers when compiz is on.
Is it possible to change the video output module in totem movie player to x11? or can i change it completely in all video and media players?

---

### Post by deresh on 2008-10-27
use gstreamer-properties, you have 2nd tab Video where you can change video output to X11,Xv or whatever you have available...

---

### Post by Longinus00 on 2008-10-27
Is the X11 video path accelerated in any way or is it completely relying on the cpu to draw the image?

---

### Post by Radeky on 2008-10-27
I didnt have the black screen flickering issue, but some tearing, etc... until I just switched to X11.

Longinus:  Not sure about other players, but in VLC... it is checked for 'accelerated video'

---

### Post by olskar on 2008-10-27
> **Longinus00 said:**
> Is the X11 video path accelerated in any way or is it completely relying on the cpu to draw the image?

I think it is not accelerated in any way and you get very poor quality compared to xv, I wouldn't even call it a solution to this problem..

---

