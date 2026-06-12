---
title: "Restricted Extras issue"
date: 2010-02-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-02-26
Went to set up Lucid for multimedia. Tried to install ubuntu-restricted-extras. It wants to remove pulse audio and ubuntu desktop???

[IMG]http://i50.tinypic.com/2zsmd91.jpg[/IMG]

---

### Post by doas777 on 2010-02-26
that is not normal. what package are you installing exactly?
try this instead:
```
sudo apt-get install ubuntu-restricted-extras
```

ultimately removing ubuntu-desktop is not a big deal (it doesn't remove gnome or anything), but besure that if you upgrade to lucid next month, that you do a clean install. never perform a dist upgrade on a system if ubuntu-desktop has been removed.

---

### Post by morryis on 2010-02-26
This should be fixed with the latest update of libsdl1.2debian-pulseaudio

---

### Post by Uncle Spellbinder on 2010-02-26
> **doas777 said:**
> that is not normal. what package are you installing exactly?

ubuntu-restricted-extras via Synaptic.



> **doas777 said:**
> try this instead:
```
sudo apt-get install ubuntu-restricted-extras
```
This worked. Should have done that first. Odd that Synaptic wanted to remove pulseaudio and ubuntu-desktop

---

### Post by coffeecat on 2010-02-26
> **Uncle Spellbinder said:**
> This worked. Should have done that first. Odd that Synaptic wanted to remove pulseaudio and ubuntu-desktop

I did a "sudo apt-get install ubuntu-restricted-extras" an hour or so ago in a fresh install of Alpha3 and it **did** take out ubuntu-desktop and the pulseaudio package, without me noticing until too late - I wasn't paying sufficient attention. :oops:

So I marked ubuntu-desktop for installation in Synaptic and it reinstalled the pulseaudio package as well in place of an alsa package which had been sneaked in, again without me noticing.

Note to self: pay attention when using a development version. :wink:

---

### Post by BilliShere on 2010-02-27
Hey I experienced the same bug. the problem lies with the libdsl-alsa plugin: so use this code instead: works flawlessly!
```
sudo apt-get install ca-certificates-java cabextract flashplugin-installer freepats gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea-6-jre-cacao icedtea6-plugin java-common lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libaccess-bridge-java libaccess-bridge-java-jni libass4 libavcodec-extra-52 libavformat52 libavutil-extra-49 libc6-i386 libcdaudio1 libcelt0-0 libdc1394-22 libdca0 libdirac-encoder0 libdvdnav4 libdvdread4 libenca0 libfaac0 libfaad2 libfftw3-3 libgme0 libgsm1 libid3tag0 libiptcdata0 libkate1 libmad0 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libopencore-amrnb0 libopencore-amrwb0 libopenjpeg2 liborc-0.4-0 libpostproc51 libquicktime1 libschroedinger-1.0-0 libsdl1.2debian libsdl1.2debian-pulseaudio libsidplay1 libsoundtouch1c2 libswscale0 libtwolame0 libwildmidi0 libx264-67 libx264-85 libxvidcore4 nspluginwrapper openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib ttf-mscorefonts-installer tzdata-java ubuntu-restricted-extras unrar
```

---

