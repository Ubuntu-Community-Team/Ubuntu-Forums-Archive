---
title: "AWFUL HD .mkv playback performance"
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NCLI on 2009-10-11
I understand why flash still sucks quite hard, but why is my Gigabyte T1028 netbook(Intel 945GM) incapable of playing HD matroska files in Ubuntu, when it can do so in Windows?

---

### Post by LittleKoy on 2009-10-11
> **NCLI said:**
> I understand why flash still sucks quite hard, but why is my Gigabyte T1028 netbook(Intel 945GM) incapable of playing HD matroska files in Ubuntu, when it can do so in Windows?

Have you tried MPlayer? Also, I find it faster without the GUI

---

### Post by NCLI on 2009-10-11
I use SMplayer, and no, I haven't tried it without the GUI but I don't think I should have to.

I'll try it regardless though, thanks for the advice :)

---

### Post by manuelb on 2009-10-11
Are you using cpu frequecy scaling?
If so, try set it to "Performance" and try again?

---

### Post by philinux on 2009-10-11
> **manuelb said:**
> Are you using cpu frequecy scaling?
If so, try set it to "Performance" and try again?

+1 this works on my desktop. Setting it to conservative seems better than ondemand too.

---

### Post by Tich666 on 2009-10-11
I would also recommend compiling the latest version of mplayer yourself using this guide: [http://ubuntuforums.org/showthread.php?t=1280543](http://ubuntuforums.org/showthread.php?t=1280543)

(if you haven't already done so)

else it might be a driver problem

---

### Post by hikaricore on 2009-10-11
Crappy OpenGL support on your hardware would be my guess.

---

### Post by perfectska04 on 2009-10-11
I use gnome-mplayer (with a very recent mplayer grabbed from a PPA) and "lavdopts=skiploopfilter=all:fast=yes" option. It plays .mkv's well, even in Jaunty - where the Intel drivers for my netbook are just plain bad.

---

### Post by NCLI on 2009-10-13
> **manuelb said:**
> Are you using cpu frequecy scaling?
If so, try set it to "Performance" and try again?
Where do I find that setting?

---

### Post by manuelb on 2009-10-13
> **NCLI said:**
> Where do I find that setting?

Add the "CPU Frequency Scaling Monitor" to your Gnome panel, right or left (can't remember) click to choose the mode.

---

### Post by NCLI on 2009-10-13
> **manuelb said:**
> Add the "CPU Frequency Scaling Monitor" to your Gnome panel, right or left (can't remember) click to choose the mode.
Thanks, though I didn't really improve things :(

I'll try building my own mplayer next.

---

### Post by Longinus00 on 2009-10-13
If you're playing a really high quality HD video, it's likely that it's saturating one of your cpus. To test if this is the case, try playing the video while you have system monitor open in the background. Add the two numbers for your cpu load together and if it's equal to about 100% then this is your problem.

Currently, the mainstream decoders for linux are all single threaded. The only way I know of to fix this is to compile mplayer/ffmpeg with the multithreaded patches.
[http://ubuntuforums.org/showthread.php?t=1049449](http://ubuntuforums.org/showthread.php?t=1049449)

If you run a newer nvidia card then you could also use mplayer with vdpau support but I don't know much about that.

---

### Post by manuelb on 2009-10-13
> **Longinus00 said:**
> If you run a newer nvidia card then you could also use mplayer with vdpau support but I don't know much about that.

The latest SMPlayer+MPlayer does support vdpau and it's working really really good for me, just add these PPA and install/update both SMPlayer and MPlayer:

```

https://launchpad.net/~rvm/+archive/smplayer
https://launchpad.net/~rvm/+archive/mplayer

```

That should do it.

---

### Post by vinutux on 2009-10-13
> **manuelb said:**
> The latest SMPlayer+MPlayer does support vdpau and it's working really really good for me, just add these PPA and install/update both SMPlayer and MPlayer:

```

https://launchpad.net/~rvm/+archive/smplayer
https://launchpad.net/~rvm/+archive/mplayer

```

That should do it.

...Thanks

---

### Post by doas777 on 2009-10-13
I've been told in past that the CoreAVC codec for MKV is far superior to those available for free. it is only 8$ so may be worth a try.

---

### Post by Longinus00 on 2009-10-13
> **doas777 said:**
> I've been told in past that the CoreAVC codec for MKV is far superior to those available for free. it is only 8$ so may be worth a try.

I don't believe you can turn off the image quality compromises in the CoreAVC codec (pleaes correct me if I'm mistaken). The main benefit of CoreAVC is that it has supported multithreaded decoding for awhile now. 

With mplayer-mt I'm able to watch 1080p videos even on my 1.6 ghz core duo (t2300). The same video is jerky if I try to play it using only one core on my overclocked e8400 (3.5ghz).

---

### Post by xOrphenochx on 2009-10-13
> **perfectska04 said:**
> I use gnome-mplayer (with a very recent mplayer grabbed from a PPA) and "lavdopts=skiploopfilter=all:fast=yes" option. It plays .mkv's well, even in Jaunty - where the Intel drivers for my netbook are just plain bad.

This degrades the quality of the video and should not be used indefinitely. Most causes for these issues are related to Compiz and OpenGL and can also be attributed to CPU Scaling.

As suggested before, compiling the latest SVN code from Mplayer is a good idea, they also have support for nVidia's new hardware acceleration feature if you have a supported chipset.

---

### Post by tom56 on 2009-10-13
> **manuelb said:**
> The latest SMPlayer+MPlayer does support vdpau and it's working really really good for me, just add these PPA and install/update both SMPlayer and MPlayer:

```

https://launchpad.net/~rvm/+archive/smplayer
https://launchpad.net/~rvm/+archive/mplayer

```

That should do it.

You don't need a PPA. Just install Gnome Mplayer, go to Edit->Preferences and set Video Output to vdpau :popcorn:

---

### Post by manuelb on 2009-10-20
> **tom56 said:**
> You don't need a PPA. Just install Gnome Mplayer, go to Edit->Preferences and set Video Output to vdpau :popcorn:

Right, but for some reason i experience a lot less cpu usage by using SMPlayer :P

---

