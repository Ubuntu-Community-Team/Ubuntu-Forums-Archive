---
title: "Removing all audio related packages"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by ArnoM on 2012-10-29
I'm currently in the process of creating a custom live CD based on Lubuntu 12.04 (as part of my internship).
Since we won't be using any audio and due to possible license and patent issues, the company I'm working for would like to have all the audio codecs and such removed (like ffmpeg, lame mp3, mplayer, etcetera etcetera).
Can this be done without breaking stuff?
(I tried to remove them using apt-get, but it wanted to remove other programs like Chromium as well.)

And, since we won't be using any audio, is it also possible to completely remove ALSA, esound, etcetera?

---

### Post by dino99 on 2012-10-29
if these packages are owned by main/universe/multiverse, then you does not need to worry about patents etc.
but trying to remove "pulse" for example, beeing part of a bunch of crossed dependencies, will give you much more work than you are thinking :(

---

### Post by ArnoM on 2012-10-29
> **dino99 said:**
> if these packages are owned by main/universe/multiverse, then you does not need to worry about patents etc.
Unfortunately the IP department has a different opinion about this.
Apparently some packages make use of some patents and that use isn't licensed.

But you strongly advice not to remove the "drivers" like pulse / ALSA, cause it's likely to break stuff quickly?

---

### Post by dino99 on 2012-10-29
> **ArnoM said:**
> Unfortunately the IP department has a different opinion about this.
Apparently some packages make use of some patents and that use isn't licensed.

But you strongly advice not to remove the "drivers" like pulse / ALSA, cause it's likely to break stuff quickly?

As you might know, despite the IT opinion (but it seems to test your knowledge) ubuntu (lubuntu) is an open-source distro and does not use closed sources into the core packages. These non patent free packages are all found into additional ppa (medibuntu) or via partner repo (canonical partner) like adobe flash; thats all.

[https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound)

---

### Post by ArnoM on 2012-10-29
I've actually been given a list of rejected software by the Intellectual Property & Standards department, which has several libraries on it that I'm not allowed to use.
To name a few: GNU database management lib (GDBM), ffmpeg, LAME MP3, MPlayer.

I removed most of them, but apparently I'm unable to install Chromium from the official repositories without installing ffmpeg.
Do you know a way around that perhaps?

---

### Post by dino99 on 2012-10-29
a quick glance at ffmpeg package properties (synaptic) let you know:

This package contains the deprecated ffmpeg program. This package also serves
as a transitional package to libav-tools. Users are advised to use avconv from
the libav-tools package instead of ffmpeg.

so chromium needs to take care of that change; ready for compiling the chronium source with avconv dependency instead of ffmpeg ?

[https://code.google.com/p/chromium-source-browsing/source/detail?spec=svn.third-party--ffmpeg.f8d71c394e071249f26703669baf1093009620d7&repo=third-party--ffmpeg&r=4778783160fb8d7aa39dafdabc756f1691b830f7](https://code.google.com/p/chromium-source-browsing/source/detail?spec=svn.third-party--ffmpeg.f8d71c394e071249f26703669baf1093009620d7&repo=third-party--ffmpeg&r=4778783160fb8d7aa39dafdabc756f1691b830f7)

note: what is called "ffmpeg" into ubuntu has nothing in common with the official ffmeg patented package 
 [http://askubuntu.com/questions/162740/how-do-i-uninstall-ffmpeg-in-12-04](http://askubuntu.com/questions/162740/how-do-i-uninstall-ffmpeg-in-12-04)

---

### Post by FakeOutdoorsman on 2012-10-29
> **dino99 said:**
> note: what is called "ffmpeg" into ubuntu has nothing in common with the official ffmeg patented package 
 [http://askubuntu.com/questions/162740/how-do-i-uninstall-ffmpeg-in-12-04](http://askubuntu.com/questions/162740/how-do-i-uninstall-ffmpeg-in-12-04)

Also see: [Who can tell me the difference and relation between ffmpeg, libav, and avconv](http://stackoverflow.com/a/9477756/1109017).

---

