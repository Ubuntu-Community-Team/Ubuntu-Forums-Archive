---
title: "What extra packages are installed if you select 'Install this third-party software'?"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by Cheesemill on 2012-12-27
This question arose in [this]("http://ubuntuforums.org/showthread.php?t=2098781") thread but I've started this new one so as to not take the original off-topic.

Does anyone know exactly which extra packages are installed if you check the 'Install this third-party software' option in the installer, specifically are any restricted video drivers installed? My coding isn't really good enough to check out the source code for Ubiquity and the only machines I have available have Intel graphics so I can't test for myself.

I'm about to do a couple of VM installations and diff the lists of installed packages so this will tell me all of the extra packages installed *except* the video drivers, can anyone fill in the blanks for me?

---

### Post by Cheesemill on 2012-12-27
It's not just the mp3 decoder, it installs flash as well as other software.

If you read the linked thread MG&TL and I were discussing whether or not it installs video drivers as well, I am looking for a definitive answer.

---

### Post by haqking on 2012-12-27
> **Cheesemill said:**
> ok :)

is it not the restricted extras package ?

such as this for quantal [http://packages.ubuntu.com/quantal/ubuntu-restricted-extras](http://packages.ubuntu.com/quantal/ubuntu-restricted-extras)

---

### Post by haqking on 2012-12-27
yes its the restricted-addons

[http://askubuntu.com/questions/22285/clarification-of-the-third-party-software-options-during-system-installation](http://askubuntu.com/questions/22285/clarification-of-the-third-party-software-options-during-system-installation)

packages found here [http://packages.ubuntu.com/search?keywords=ubuntu-restricted-addons](http://packages.ubuntu.com/search?keywords=ubuntu-restricted-addons)

---

### Post by Cheesemill on 2012-12-27
That's what I presumed but in the thread I linked to in the first post MG&TL said it installed the restricted Nvidia drivers on his machine. This is what I'm trying to clarify.

---

### Post by haqking on 2012-12-27
> **Cheesemill said:**
> That's what I presumed but in the thread I linked to in the first post MG&TL said it installed the restricted Nvidia drivers on his machine. This is what I'm trying to clarify.


Well it says on that link i posted

> It asks the Additional Drivers (jockey) program to enable any drivers that can be automatically installed

Which of course would do Nvidia, and it says in post below.  Though initially it says only includes Broadcom.

I am guessing that Nvidia is included as they are catered for with jockey

---

### Post by Cheesemill on 2012-12-27
> **haqking said:**
> Well it says on that link i posted



Which of course would do Nvidia, and it says in post below.  Though initially it says only includes Broadcom.

I am guessing that Nvidia is included as they are catered for with jockey

From the research I've just done it would seem that it installs ubuntu-restricted-addons (not ubuntu-restricted-extras which is a superset of ubuntu-restricted-addons) and ***only*** Broadcom if needed (just as your linked post specifies). I don't believe that any other packages are ever installed as my testing with VM's doesn't install the VirtualBox guest additions which are flagged by jockey.

This makes me believe that video drivers are never installed as part of the 'Install this third-party software' process, I think we can call this closed.

Just in case anyone is interested here is the diff of extra packages installed when the option is checked:
```
flashplugin-installer
freepats
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
liba52-0.7.4
libass4
libavcodec53
libavformat53
libavutil51
libcdaudio1
libcelt0-0
libdc1394-22
libdca0
libdirac-encoder0
libdirectfb-1.2-9
libdvdnav4
libdvdread4
libenca0
libfaad2
libfftw3-3
libflite1
libgme0
libgsm1
libgstreamer-plugins-bad0.10-0
libkate1
libmad0
libmimic0
libmms0
libmodplug1
libmp3lame0
libmpcdec6
libmpeg2-4
libnspr4-0d
libnss3-1d
libofa0
liboil0.3
libopenal-data
libopenal1
libopencore-amrnb0
libopencore-amrwb0
libpostproc52
libschroedinger-1.0-0
libsidplay1
libslv2-9
libsoundtouch0
libspandsp2
libswscale2
libts-0.0-0
libtwolame0
libva1
libvo-aacenc0
libvo-amrwbenc0
libvpx1
libwildmidi-config
libwildmidi1
libx264-120
libxvidcore4
libzbar0
libzvbi-common
libzvbi0
tsconf
ubuntu-restricted-addons
```

---

### Post by MG&amp;TL on 2012-12-27
Interesting stuff, nice digging guys!

This was the one install I checked that option on, and I wasn't exactly paying attention (anyone else find you can do that these days?) so I wouldn't worry about it too much.

Did some digging myself, went through the jockey commit logs. Eventually the trail goes cold, but I keep finding references to "ubuntu-drivers-common", which a quick google search brings me to: [https://launchpad.net/ubuntu/quantal/+package/ubuntu-drivers-common](https://launchpad.net/ubuntu/quantal/+package/ubuntu-drivers-common)

...which is interesting, particularly:

> [...]some NVidia specific support code to find the most appropriate driver version[...]So no, it probably doesn't, but I think it's trying to at some point. The install was an alpha build if I recall, so it may simply have malfunctioned and called the as-yet-unfinished auto-detect functions.

IDK. Was fun finding out about though, thanks Cheesemill!

---

