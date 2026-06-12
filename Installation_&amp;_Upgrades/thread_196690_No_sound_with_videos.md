---
title: "No sound with videos"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by isterios on 2006-06-14
I recently installed xubuntu. Everything seems to work except the sound on videos.

The videos play but no sound... (avi, mpeg).

The sound works with MP3 (xmms)

I tried an alsaconf but this option doesn't exist anymore.

So I tried to reinstall alsa but I can't:
v   alsa                            -

With XFCE 4.2, the sound worked perfectly with alsa.

What's the problem with xubuntu?

---

### Post by emperor on 2006-06-14
Here's a few things to check:
==================

check volumes with "alsamixer"

If you did an upgrade from 5.10, the gstreamer-0.8 plugins need to be removed and the gstreamer-0.10 plugins installed.  (good, bad, ugly and etc)

Are the win/qtime/rp codecs installed? If not get from mplayer.hq or "Ubuntu PLF" 
(Penguin Liberation Front)

---

### Post by isterios on 2006-06-15
Thanks Emperor.

So I checked the volume which is ok (40%)

It is not an upgrade but I installed gstreamer-plugins (just in case).

And I would like to install codecs (I downloaded the package essential) but impossible to find a clear doc: so:
I extracted this package
I created a directory codecs in /usr/lib
I copied the extracted files in /usr/lib/codecs.

And after, I don't know... (I think I have to create a link somewhere but I am not sure)

Just for information I work with Xubuntu and gxine.

---

### Post by emperor on 2006-06-15
The codecs have been said to belong in on of these 3 directories:

/usr/local/lib/codecs
/usr/lib/codecs
/usr/lib/wiin32

The xine FAQ says they must be in "/usr/lib/win32".

You can install in one directory and make a symbolic link to others if needed. for example:

sudo ln -s /usr/lib/codecs /usr/lib/win32

gxine or xine has sound settings within it's menus that might need tweaking as well. 

[http://www.xinehq.de/index.php/faq#NOAUDIO]("http://www.xinehq.de/index.php/faq#NOAUDIO")

Is the problem viewing trailers in the browser or when just playing a video that has been downloaded or on a CD/DVD.

I just installed Xubuntu on a PIII 500Mhz machine last night for use as a MythTV frontend in my bedroom. I'll be working on it again tonight and will get some hands on checking out the sound. I'll let you know what I learn later tonight or tomarrow.

---

