---
title: "HD Playback with Nouveau without VDPAU"
date: 2010-02-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tito_torrisi on 2010-02-27
Because of Nouveau now beeing able to provide great 3D support, but not yet VDPAU, some of us can't switch from nvidia drivers completely. 

I recommend switching to nouveau for everyone who just needs compositing (compiz, mutter/gnome-shell) enabled for e.g. docky/cairo-dock/rgba/awn. With xorg-edgers ppa Gallium3d is working. The only thing missing is VDPAU support. 
To resolve that, I switched to mplayer-mt (multithreading). Unfortunately the rvm ppa (Launchpad) is outdated (won't install on Lucid due to dependency conflicts), but thanks to that thread (at the end) I found a new version working great with lucid: 

[http://smplayer.berlios.de/forums/viewtopic.php?id=1179&p=2](http://smplayer.berlios.de/forums/viewtopic.php?id=1179&p=2)

you can get it from [http://debian-multimedia.org/dists/unstable/main/binary-amd64/package/mplayer-mt.php](http://debian-multimedia.org/dists/unstable/main/binary-amd64/package/mplayer-mt.php)

missing dependencies from: [http://www.debian.org/distrib/packages#search_packages](http://www.debian.org/distrib/packages#search_packages)

for Lucid I had to download and install: ibartsc0 libbs2b0 libcaca0 libcaca-dev libfaac0

It would be great if someone could provide a ppa for mplayer-mt version.

In SMPlayer you can set your cores and change the executable to mplayer-mt. So this works side by side with your current mplayer!

On my ION/Atom 330 dual core Nettop, 720p mkv files play great, CPU usage @ 50-80%. You should use alsa instead of pulse.

There may be more to tweak, please post your results. I couldn't find any information on VDPAU support in nouveau.

Sorry for my language :)

---

### Post by t.alex on 2010-02-27
> **tito_torrisi said:**
> 
It would be great if someone could provide a ppa for mplayer-mt version.


[https://launchpad.net/~ripps818/+archive/coreavc](https://launchpad.net/~ripps818/+archive/coreavc)

that's mplayer from git, which already uses ffmpeg-mt

---

### Post by tito_torrisi on 2010-02-27
Great, thank you, I didn't find it myself because it is hard to search for in Launchpad, the package has the same name as the most ones without ffmpeg-mt!

It also works great. Is someone already using it with an Atom CPU?

---

