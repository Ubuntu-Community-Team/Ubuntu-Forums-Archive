---
title: "gma 965 - choppy video playback"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stats on 2008-10-06
Video playback is choppy and uses cpu even though mplayer is set to use xv. I have textured video(video on faces of the cube while rotating), which was not possible using the intel drivers in hardy, which gives me the feeling the video isnt hardware accelerated

I get 600~ fps in glxgears, however with compiz on the overlay flickers continuously.
glxinfo gives
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2

(this is on intel gma 965 (x3100))

---

### Post by mordanda on 2008-10-06
I think this is related to an issue I'm having in Kubuntu.  When watching a DVD in anything (Dragon Player, Kaffeine, KMPlayer, VLC) the playback hitches every five seconds or so.  If I'm in fullscreen mode the mouse cursor will disappear as it's supposed and reappear after 2 seconds.  I think something's going on on the desktop that refreshing every 5-10 seconds but I'm unable to figure it out.  I too am running on Intel video hardware, 945GM.

D

---

### Post by adam on 2008-10-07
Same problem here. kubuntu, x3100 chipset. Choppy playback over all players tried--vlc, mplayer, totem-xine, totem-gstreamer... 

Have noticed the mouse re-appearing in fullscreen as well.

Edit: Should also say that the problem exists regardless of the output setting (although I've only tried different output settings in vlc).

---

### Post by stats on 2008-10-09
I found out some more details. the new xserver-xorg-video-intel package uses texturedvideo by default which does not work well on some cards. 
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278318]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/278318")
by running xvinfo i can get the port of video overlay
then using mplayer -vo xv: port={port} i can work arouund this

however this is quite unstable and causes the the display to go blank and the system freezes. The only thing i can do is switch off the power

---

### Post by nystire on 2008-10-09
> **stats said:**
> Video playback is choppy and uses cpu even though mplayer is set to use xv. I have textured video(video on faces of the cube while rotating), which was not possible using the intel drivers in hardy, which gives me the feeling the video isnt hardware accelerated

I get 600~ fps in glxgears, however with compiz on the overlay flickers continuously.
glxinfo gives
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2

(this is on intel gma 965 (x3100))

I think that the line in glxinfo's output about no direct rendering says that you don't have hardware acceleration for your video card, but I could be wrong.

---

### Post by psyke83 on 2008-10-09
> **stats said:**
> Video playback is choppy and uses cpu even though mplayer is set to use xv. I have textured video(video on faces of the cube while rotating), which was not possible using the intel drivers in hardy, which gives me the feeling the video isnt hardware accelerated

I get 600~ fps in glxgears, however with compiz on the overlay flickers continuously.
glxinfo gives
direct rendering: No (LIBGL_ALWAYS_INDIRECT set)
server glx vendor string: SGI
server glx version string: 1.2

(this is on intel gma 965 (x3100))

That's probably to be expected. If you're using textured video and compiz, then the video is composited as well (whereas in the past, the video was not). You're getting choppy playback simply because compiz doesn't have enough horsepower to render this content on-screen.

An earlier posts mentions XV ports - this is the way to workaround the problem. You can also change the port for GStreamer applications via gstreamer-properties.

---

### Post by adam on 2008-10-09
I'm thinking we may have different problems.

```
glxinfo |grep direct
```

returns: direct rendering: yes

Changing the output setting does nothing. Changing from Textured Video to Video Overlay does nothing.

This may be a separate KDE bug...

It looks like every time there's a "hiccup" in the video (every 5 seconds or so), Plasma seems to spike up in CPU usage. Though honestly I have no idea if this is causing the problems, caused by the problem (or perhaps completely unrelated).

This also seems to go beyond media players, as I've noticed the same effects while watching flash videos.

Any ideas on how to properly diagnose the problem?

Thanks.

Edit: Should also add that I've tried shutting off compositing, which also does nothing.

---

### Post by elcman on 2008-10-09
I'm having this problem, too.

I have a computer that I've attached to an LCD HDTV and I use it to playback movies and TV shows. This is *really* distracting.

I first though it was a networking issue where my wireless network card loses signal briefly, but the connection was stable for the time the video was running. I find that the smaller I keep the video, the less often it happens.

Using VLC, I changed the output to XVideo, X11 and OpenGL with no difference. (I thought it made a difference at first, but alas, no.)

OpenGL output was very glitchy, but I kinda expected that.

I have an old ATI Radeon AGP video card in there. Everything else works dandy. Compiz functions without a hitch. Video playback should be smooth as can be, but no... it isn't.

In cases where there is a lot of processing going on--such as unzipping in the background or file copying--the artifacting happens more often.

It seems like it happens often around keyframes in videos, too. It seems that when the keyframe is processed, it freezes the screen while the audio is being played and then catches up.

I think this is not a driver problem, though I don't know the guts of Linux well enough to pinpoint it. But, from a complete guess, I believe it is the way that codec processing is handled. It should be considered a fulltime process.

Anyway... I'll keep playing around. I'm hoping that if I keep updating my Intrepid Ibex distro that it'll eventually be resolved. :)

---

### Post by plun on 2008-10-09
DRI2 is missing within Xorg 7.4 and therefore these problems

About DRI2 and the future
[http://www.phoronix.com/scan.php?page=news_item&px=NjYzNw](http://www.phoronix.com/scan.php?page=news_item&px=NjYzNw)


Use **fusion-icon** and switch to Metacity before whatching a movie or playing a game

[http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)


.

---

### Post by adam on 2008-10-09
Shutting off compositing doesn't solve the problem. At least not in KDE...

---

### Post by adam on 2008-10-09
elcman: Which desktop environment are you using?

---

### Post by elcman on 2008-10-09
> **adam said:**
> elcman: Which desktop environment are you using?

Using the default Gnome but I piggy backed 8.10 Edubuntu on top of my 8.10 Ubuntu install. This shouldn't affect any of the video handling stuff, though. My hardware is pretty weak. It's a P4 with 512MB of SDRAM, but when using it with Windows XP before this upgrade, it worked just fine with only 256MB of SDRAM.

Would Gnome be bogging things down? The video response with Compiz is pretty smooth, so my ATI card was correctly installed and Direct Rendering is working like a dream...

Just video playback... and it doesn't seem to be overtaxing the system. I don't get it.

---

### Post by adam on 2008-10-09
elcman: If you haven't already, you should try what plun suggested a few posts up. It may be that compositing video is overtaxing your hardware.

Shutting off compositing has no effect on the problem I'm having though. I think it may be a kwin/plasma/[etc] bug, but I'm not sure how to find out exactly what's causing the problem. I guess I'll install ubuntu-desktop to see if the problem persists in gnome...

---

### Post by adam on 2008-10-09
The bug appears to be in KDE, as video in gnome plays perfectly even with compiz enabled.

How can I find out exactly what's causing the problem so I can file a useful bug report?

---

### Post by elcman on 2008-10-10
I'll turn off compositing and see what happens. I think that there may be something else underlying the stuttering.

I'll try it, though! Worth a shot! I did an update and it seemed to work a little better with the lastest update.

---

### Post by Bou on 2008-10-17
I'm about to buy a laptop with this card. Are you still having trouble with it? Would you recommend me against buying it?

---

### Post by stats on 2008-10-17
the card has no problems at all on hardy, and considering intrepid is still in beta these problems may be ironed out in the next few  months.

---

### Post by adam on 2008-10-17
The problem in KDE can be solved by going to:

System Settings > Advanced Tab > Service Manager

And shutting off "Detecting RANDR (monitor) changes".

Doing so gives me flawless video playback in KDE. Without changing anything, I've never had anything but perfect playback in Gnome. It's not even necessary to shut off compositing.

---

### Post by andrewabc on 2008-10-17
> **Bou said:**
> I'm about to buy a laptop with this card. Are you still having trouble with it? Would you recommend me against buying it?

I've had this video card on a desktop for 1.5 years. Decent, and compiz worked decent with hardy, and from what I saw on the intrepid beta it worked even better. There is better support now than a year ago. Yes compiz did not work on gutsy that good (it was blacklisted). But with hardy it was not blacklisted and it worked (the only problem I have is with scrolling causes massive CPU usage). With intrepid live cd the CPU issue appeared to be gone.

Is the version you are getting x3100?

the problems mentioned earlier with video would have mostly related to compiz being turned on. With compiz turned off everything should work. With compiz turned on there may be a small problem or so with possible solutions.

See
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/177492)
But don't reply about whether to purchase one there.

---

