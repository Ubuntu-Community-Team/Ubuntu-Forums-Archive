---
title: "[ubuntu-intrepid] slow performance h264 videos"
date: 2008-05-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by XoRDy on 2008-05-24
Hello,

I've got an Sanyo HD1000, an HD camera that record in h264/AC3 (or ACC, I don't know)
I play this h264 videos with totem, installing the codecs from the metapackage "ubuntu-restricted-extras"

With the codecs of the package gstreamer0.10-ffmpeg 0.10.3-6 (from hardy) I can play my videos recorded at 480p and 720p faster than in windows, but I can't play 1080i files.

I've tried to update gstreamer0.10-ffmpeg to version 0.10.3.3-1 (from intrepid) and now I can play 1080i videos, but its about one frame per 3 seconds... And 720p goes very slow, plays one second, and does one second of pause... 480p are fine, but they get more resources

I've downgraded the gstreamer0.10-ffmpeg package, and everything is as before

I've read in the changelog that in the first version of intrepid, they updated the ffmpeg codecs included to version 0.svn20080206, I've tried to search in ffmpeg page, but I can't find anything...

Any idea of what's that huge performance loss?

Thank you

---

### Post by sdennie on 2008-05-24
I'm not sure what the performance problems are but, there is no telling what you are getting if you grab something from a pre-alpha release.  I would see if you can use vlc or mplayer to play 1080i stuff.  I only have 720p video files so I can't say if vlc or mplayer will work but, they are very good alternatives to totem.

---

### Post by XoRDy on 2008-05-25
I've tried mplayer and vlc, and none of them works with my 1080i videos... other 1080p and 1080i works, but the ones recorded with my cam doesn't, I can only play them on windwos (with a pity performance) and Mac OS (without sound, lan and wlan drivers, so it's useless)

---

### Post by Cresho on 2008-06-25
just to let you know, avidemux can open it.  BUT!  there is a but!  have you tried using command lines to convert the 1080i b frames to something more readable?

---

### Post by Cresho on 2008-07-01
here is another update.  you can open up sanyo xacti hd1000 videos in xbmc

it runs superbly under linux [http://xbmc.org/](http://xbmc.org/)

---

