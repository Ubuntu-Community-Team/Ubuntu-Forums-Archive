---
title: "My Intrepid experience so far"
date: 2008-07-07
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by z0idberg on 2008-07-07
I've been running Intrepid (64-bit) since alpha 1 was released and so far, it's been completely stable for me (maybe there is still major breakage to come, I don't really know the development process). Anyway, I thought I'd write down some of my observations so far. Why? Hmm... "For your consideration"? Naah... not really. "Because I want to"? Yeah, that's probably it! :)

The new theme--It has kind of grown on me... I'd really like more contrast between window decorations (mostly titlebar, I suppose) on active and inactive windows. At least this theme is way more usable than most of the see-through glassy goodness everyone is suggesting for Intrepid default!

The dangerously devious developers have put the Administration menu above the Preferences menu instead of vice versa. As a result of this, hundreds of poor, innocent users just trying to change their theme to aforementioned glassy goodness are reported lost in various administration applications! The search for survivors will continue as soon as the resque team stop playing with their wobbly windows.

When I try to change my keyboard layout from the default one (USA), the application crashes (in an enthusiastic display of typographical patriotism, perhaps). Is the problem simply that no other keyboard layouts are included yet? Anyway, I'm starting to get quite used to the USA layout. Subtle brainwashing in progress!

Sound... well, my E-MU 0404 USB soundcard isn't known for working perfectly in Linux (in the same way Dan Quayle isn't known for his eloquence and rhetoric). It kind of works in Intrepid... that is; sometimes, a little. Let me explain:

In the Sound Preferences window, I get a dropdown list of available devices that looks like this:

Autodetect
pcsp
USB Audio #1
USB Audio
pcsp
USB Audio
pcsp
USB Audio
USB Audio
ALSA - Advanced Linux Sound Architechture
OSS - Open Sound System 
PulseAudio Sound Server

As anyone who has ever used a computer would guess, choosing the *second* "USB Audio" alternative gives me working sound. When playing music in Rhythmbox. Of course, trying to play a movie gives me completely distorted sound and sometimes it isn't possible to use two programs that use sound at the same time. I vaguely remember reading about this happening because one of the programs isn't using PulseAudio or something similar. Anyway, I don't really understand why PulseAudio is included in Ubuntu 1. in it's current state and 2. at all. It seems to be the cause of a whole lot of audio issues, not only in Intrepid and the benefits it provides don't seem to be of very much importance to the desktop user. But I really don't know enough about it to whine (which doesn't seem to deter me at all) and I guess everything will turn out nice and shiny in the end!

Hmm... that's probably it for now. I haven't bothered trying to get NVIDIA drivers to work, but I got the resolution right (1680x1050) after some messing around with xorg.conf (try to realize the truth: There is no xorg.conf!) and things seem to work quite well. For Flash, I tried Swfdec and Gnash with varying degrees of success... that sound didn't work with either of them did not surprise me as much as one might have expected :). 

All in all, I didn't expect Intrepid to work as well as it did already, and I think it will be a great release when it's finished. For me, the one big thing that will win me over if they get it right is sound; music and movies as well as Flash movies, and of course support for my soundcard. If any of you know how I could contribute to that, please tell me!

---

### Post by galileon on 2008-07-07
its funny, but I felt a chill down my spine when I read "no xorg.conf", lol

---

### Post by Gina on 2008-07-08
Well there IS an xorg.conf and if you use the default when installing the proprietry nVidia driver it will only give low resolution.  I replaced it with my Hardy xorg.conf and got correct res.  xorg.conf is used less though.

PulseAudio is broken and a real pain in the neck!!  Set everything to ALSA until PulseAudio is fixed - sound then works!

Yes, there are a few things that need fixing and I gather a fair bit of new stuff.  So you can expect breakages later on.  But that's the fun of development :lol:

---

### Post by z0idberg on 2008-07-08
> **Gina said:**
> Well there IS an xorg.conf and if you use the default when installing the proprietry nVidia driver it will only give low resolution.  I replaced it with my Hardy xorg.conf and got correct res.  xorg.conf is used less though.
I meant getting the right resolution without the proprietary NVIDIA driver, which I'm not using at all at the moment. If I remember correctly, there is no xorg.conf unless you generate one or install some drivers which create one for you.
> 
PulseAudio is broken and a real pain in the neck!!  Set everything to ALSA until PulseAudio is fixed - sound then works!

Except switching to ALSA in Sound Preferences doesn't help... Switching to the second of several identically named devices helps :).
> 
Yes, there are a few things that need fixing and I gather a fair bit of new stuff.  So you can expect breakages later on.  But that's the fun of development :lol:
Of course :).

galileon:
Do not try to bend the xorg.conf; that's impossible. Instead, only try to realize the truth. There is no xorg.conf. Then you'll see, that it is not the xorg.conf that bends, it is only yourself.

---

### Post by galileon on 2008-07-08
> **z0idberg said:**
> 
galileon:
Do not try to bend the xorg.conf; that's impossible. Instead, only try to realize the truth. There is no xorg.conf. Then you'll see, that it is not the xorg.conf that bends, it is only yourself.

sorry, I'm not a native speaker, and I don't *quite* get it, lol. Anyways I have a copy of my old xorg.conf that I emailed myself, so I'll always have one to stick back in place when my wacom tablet doesn't work!

---

### Post by aamukahvi on 2008-07-08
> **galileon said:**
> sorry, I'm not a native speaker, and I don't *quite* get it, lol. Anyways I have a copy of my old xorg.conf that I emailed myself, so I'll always have one to stick back in place when my wacom tablet doesn't work!

Watch Matrix, it's a good movie. In the mean time:
[http://www.neoandtrinity.net/spoonboy.html](http://www.neoandtrinity.net/spoonboy.html)

Sorry about OT :D

---

### Post by caryb on 2008-07-08
Just installed xorg 1:7.4 so far so good no breakages:lolflag:


Cary

---

### Post by uBeer on 2008-07-08
> **z0idberg said:**
> 

galileon:
Do not try to bend the xorg.conf; that's impossible. Instead, only try to realize the truth. There is no xorg.conf. Then you'll see, that it is not the xorg.conf that bends, it is only yourself.

Brilliant! And maybe someday it will come true...

---

### Post by jwsawyer on 2008-07-08
Intrepid was fine when I left for work this morning.  I have to turn off my computer when I leave.  When I turned it on and logged on this evening, after loading gnome, it went to a blank white screen.

Has this happened to anyone else and does anyone have a fix?

---

### Post by z0idberg on 2008-07-09
Mr. morningcoffee is right, of course, it's a quote from The Matrix. I've sunk that low :).

In other words: This is my xorg.conf. There are many like it, but this one is mine. My xorg.conf is my best friend. It is my life. I must master it as I must master my life. My xorg.conf without me is useless. Without my xorg.conf, I am useless.

Oh well... Moving right along: will there be any changes/upgrades in ALSA too, or will only PulseAudio be fixed. I'm asking because my soundcard doesn't play well with ALSA either :).

---

### Post by marijus on 2008-07-09
> **jwsawyer said:**
> Intrepid was fine when I left for work this morning.  I have to turn off my computer when I leave.  When I turned it on and logged on this evening, after loading gnome, it went to a blank white screen.

Has this happened to anyone else and does anyone have a fix?

press alt-f2 and type: ```
metacity --replace
``` than press enter...

the new xorg doesn't play nice with compiz... i have to start mine with: ```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
``` to make it work...

regards! marijus

ps: im using intel i810 gfx driver

---

### Post by caryb on 2008-07-09
I just had the dreaded KDE4 white screen of death again after going into system settings desktop effects & putting the tick in the box & bingo no desktop. Rebooting does absolutely nada! I found this fix on another post, edit /home/username/.kde4/share/config/kwinrc & change compositing from true to false.


All is good again! I really dislike lynx lol


Cary

---

### Post by damis648 on 2008-07-09
> The dangerously devious developers have put the Administration menu above the Preferences menu instead of vice versa. As a result of this, hundreds of poor, innocent users just trying to change their theme to aforementioned glassy goodness are reported lost in various administration applications! The search for survivors will continue as soon as the resque team stop playing with their wobbly windows.

:lolflag::lolflag::lolflag:

Anyway, great "review". I have liked pulseaudio, not that it always worked, but I like it. Hopefully they will fix these pulseaudio bugs... they should put that as a high priority, as new users AT LEAST expect their sound to work out of the box.

---

### Post by jwsawyer on 2008-07-09
> **marijus said:**
> press alt-f2 and type: ```
metacity --replace
``` than press enter...

the new xorg doesn't play nice with compiz... i have to start mine with: ```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
``` to make it work...

regards! marijus

ps: im using intel i810 gfx driver

Thanks.  I tried that but it still didn't work.

---

### Post by jwsawyer on 2008-07-11
Finally fixed it.  Completely removed compiz.

---

