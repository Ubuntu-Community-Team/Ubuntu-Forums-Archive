---
title: "error installing ffmpeg and x264"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by prkhr4u on 2013-11-12
I am trying to install ffmpeg and x264 on my ubuntu(precise) system.I am using Ubuntu Compilation guide.
When i am executing the following line 
```
[COLOR=#000000]git clone --depth 1 git://git.videolan.org/x264.git[/COLOR]
```
i get the following error:
```
Cloning into 'x264'...fatal: unable to connect to git.videolan.org:
git.videolan.org[0: 88.191.250.118]: errno=No route to host
git.videolan.org[1: 2a01:e0d:1:3:58bf:fa76:0:1]: errno=Network is unreachable
```

pl tell how to clone git repository

---

### Post by FakeOutdoorsman on 2013-11-12
Are you behind a firewall that may be interfering? Have you tried again recently? Perhaps the server was down or maybe there were network issues. Alternatively, if you can't use git you can download the [nightly x264 source snapshot](ftp://ftp.videolan.org/pub/x264/snapshots/last_x264.tar.bz2). Each section that uses git in [How To Compile FFmpeg and x264 on Ubuntu](https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide) provides an alternative to git.

---

### Post by prkhr4u on 2013-11-12
I have also tried to do the same after disabling the firewall by :
```
sudo ufw disable 
```
Then also the same problem exists.

An alternative was also given,which required me to add a PPA,but i am unable to add PPA as given in my post:
[http://ubuntuforums.org/showthread.php?t=2187425](http://ubuntuforums.org/showthread.php?t=2187425)

I have tried it many times,and do not think that there are any network issues
Earlier also i had tried to do the same,but was unable to clone git.

I am now forced to go with the nightly snapshot

---

### Post by prkhr4u on 2013-11-13
I have been able to install x264 and ffmpeg using the nightly snapshots and then compiling them.
Still the problem for git cloning is remaining..
anyways thanks for your help

---

### Post by FakeOutdoorsman on 2013-11-13
Maybe you can contact videolan and see if your IP address is banned. Other than that I don't have any more ideas.

---

