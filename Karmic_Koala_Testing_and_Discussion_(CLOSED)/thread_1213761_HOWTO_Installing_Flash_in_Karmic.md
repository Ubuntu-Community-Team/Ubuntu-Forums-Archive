---
title: "HOWTO: Installing Flash in Karmic"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-07-15
Since adobe-flashplugin messed up my Karmic install (it was a daily build, 14-July-09), I reinstalled the OS and headed for gnash. I successfully set gnash up and got it working, *with sound*, on YouTube.

This is a guide on installing gnash, not swfdec. I could never get swfdec working, but if you're up to it, go for it and tell us if it works.

**Installing Packages**

First, you've got to install the packages. The list is quite long, so make sure to copy and paste this command verbatim/word-for-word.

```

sudo apt-get install gnash mozilla-plugin-gnash libavutil49 freepats libgsm1 libavcodec52 libpostproc51 libswscale0 gstreamer0.10-ffmpeg libenca0 libass3 libcdaudio1 libcelt0 libdc1394-22 libdca0 libdvdread4 libdvdnav4 libfaad0 libgmyth0 libiptcdata0 libxml++2.6-2 libffado0 libfreebob0 libjack0 libmodplug0c2 libmpcdec3 libneon27-gnutls libofa0 libfftw3-3 libopenspc0 libsoundtouch1c2 libwildmidi0 gstreamer0.10-plugins-bad -y

```

The -y suffix makes it so APT assumes yes on installing packages.

Wait for the packages to install, then...

**Create a Link Between Plugin Files**

For some reason, I've never been able to get Firefox or Shiretoko to recognise an alternative flash plugin such as gnash or swfdec. So, you must create a symbolic link.

```

sudo ln -s /usr/lib/gnash/libgnashplugin.so /usr/lib/mozilla/plugins/flashplugin-alternative.so 

```

Then you're done. Restart Firefox/Shiretoko and voila, it should work flawlessly.

---

### Post by descendent87 on 2009-07-15
I've been using gnash for a while, it works quite often but theres still a lot it doesnt work with. Also occasionally you have to reload a page 4 or 5 times before the videos will show up. Still not ready to replace flash from adobe (which i've had no problems with)

---

### Post by b3n87 on 2009-07-15
Intersting, didnt realise it worked with YouTube.

Is it stable? Any sites it doesnt work with?

---

### Post by iaskedalice09 on 2009-07-15
If ANYONE knows how to get adobe's flash to work, please let me know. It works a lot better than gnash!

As far as sites it doesn't work with, the only site i really have problems with is Aish.com. The video loads but it says no data, rather than loading the video. With Adobe, it loads the video.

---

### Post by Slug71 on 2009-07-15
Its working for me on 64bit. I downloaded the 64bit Flash and put the .so file in usr/lib/mozilla/plugins.

---

### Post by tad1073 on 2009-07-15
some good information

[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by iaskedalice09 on 2009-07-15
Of course I'm on i386 or 32-bit system. And it doesn't work. :(

---

### Post by iaskedalice09 on 2009-07-15
If anyone has any resources on making Adobe Flash work on 32bit Karmic, please share. Thanks so much, for now I'll use gnash. :) / :(

---

### Post by descendent87 on 2009-07-15
> **b3n87 said:**
> Intersting, didnt realise it worked with YouTube.

Is it stable? Any sites it doesnt work with?

Doesnt work with myspace music, youtube works for some videos but a lot don't work for me

---

### Post by Reiger on 2009-07-15
A i386 Kubuntu here, aptitude says I installed:
[list]
[*]adobe-flashplugin
[*]flashplugin-installer
[/list]

But I can only remember installing adobe-flashplugin... (And youtube works just fine, including its JavaScript API.)

---

### Post by iaskedalice09 on 2009-07-15
I did some digging in the repositories. Here's another fix that works for me that doesn't break apt.

```

sudo apt-get install flashplugin-installer flashplugin-nonfree -y && sudo apt-get remove gnash mozilla-plugin-gnash -y --purge

```

Restart Firefox and it works wonderfully. Lesson I learned today: if it's in the repositories, use that. Don't use something outside the repositories if you don't have to.

---

