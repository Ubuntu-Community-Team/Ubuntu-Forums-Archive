---
title: "Audio but no video in multiple applications"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CFBauer on 2009-10-26
Hello,

After upgrading to Karmic RC, I cannot play videos. I have universe and medibuntu as repositories, tried installing restricted-extras, tried reinstalling mplayer, and gstreamer, still no luck. I've also updated and upgraded.

VLC and Totem play audio but there is no video.

In **SMPlayer**, I get this error:

"MPlayer has finished unexpectedly. Exit code 127"

```
/usr/bin/mplayer -noquiet -nofs -nomouseinput -sub-fuzziness 1 -identify -slave -vo xv -ao alsa -nokeepaspect -framedrop -nodr -double -input conf=/usr/share/smplayer/input.conf -stop-xscreensaver -wid 69206031 -monitorpixelaspect 1 -*** -embeddedfonts -***-line-spacing 0 -***-font-scale 1 -***-styles /home/chris/.config/smplayer/styles.*** -fontconfig -font Arial -subfont-autoscale 0 -subfont-osd-scale 20 -subfont-text-scale 20 -subcp ISO-8859-1 -subpos 100 -cache 2000 -osdlevel 0 -vf-add screenshot -slices -channels 2 -af equalizer=0:0:0:0:0:0:0:0:0:0 /home/chris/Videos/King of the Hill - S05E15 - Luanne 2.0.avi -loop 0

/usr/bin/mplayer: error while loading shared libraries: libx264.so.67: cannot open shared object file: No such file or directory
```

I did check, libx264.so.67 is installed, but there is no file in usr/bin called "mplayer".

**VLC** does this:

```
No suitable decoder module:
VLC does not support the audio or video format "XVID". Unfortunately there is no way for you to fix this.
```

**Totem** searches for plugins, but does this:

```
No packages with the requested plugins found

The requested plugins are:

XVID MPEG-4 decoder
```

Ive tried all types of video types. The "requested plugin" from Totem changes, but it is never found.

Any tips would be appreciated. Thanks.

-Chris

---

### Post by CFBauer on 2009-10-27
Bamp :)

---

### Post by CFBauer on 2009-10-27
If there's any more information I could provide, I will certainly oblige. :)

---

### Post by CFBauer on 2009-10-28
Mods, I wonder if this would get a better response in the "Multimedia and Video" section?

---

### Post by CFBauer on 2009-10-28
:(

---

### Post by mc4man on 2009-10-28
i don't use any of the repo versions of vlc, mplayer or the shared ffmpeg libs but on a tester have had no issue with most formats using the stock repo packages.

copying from a recent post I made this allows playback with repo versions vlc, mplayer and Movie Player to the extent they can.

> Search ffmpeg in synaptic and mark the 'extra' versions of the ffmpeg libs for install and apply. (don't mark the current ones for removal

There are up to 7 available, the key ones would be libavcodec-extra-52 ; libavformat-extra-52 ; libswscale-extra-0 ; libpostproc-extra-51

(if you wish a fairly full gstreamer plugins then search gstreamer and install these gstreamer plugins

bad (1st listed
bad multiverse (4th listed
ugly (1st
ugly multiverse ( 4th
gstreamer0.10-ffmpeg
pitfdll (allows limited use of w32codecs in gstreamer - somewhat broken in karmic atm


Note this is on both a fresh install and a live cd (usb).

If installing these has no effect and you upgraded from jaunty to karmic the problem may lie there.

( you could also try to install an mplayer from here, and possibly an smplayer from last link.

[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

[https://launchpad.net/~rvm/+archive/smplayer](https://launchpad.net/~rvm/+archive/smplayer)

---

### Post by CFBauer on 2009-10-28
Thanks mc4man. I tried your suggestions. No luck yet.

---

