---
title: "mpd daemon asks libx11"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by superbike on 2012-03-15
I am a linux newbie so please have patience with me!
I built a ubuntu headless machine as a downloader and media server from hardy. apache2, mysql, sqlite3, mt-daapd, mediatomb, webmin, pyload, transmission. I was not keen on installing extra dependencies to keep the installation small but then I saw mpd and decided to install it but the apt-get install command shows that i also have to libx11 and some dependencies. Could anyone tell me why even though it is not listed in mpd dependencies.
Thanks

---

### Post by raja.genupula on 2012-03-15
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

in that read "Package Dependencies" 

and you wanna install it now do as 
```
sudo apt-get install -f
```

---

### Post by superbike on 2012-03-16
> **raja.genupula said:**
> [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

in that read "Package Dependencies" 

and you wanna install it now do as 
```
sudo apt-get install -f
```

OK! but you see x11 is not a dependency or should not be:
[http://packages.ubuntu.com/hardy/mpd]("http://packages.ubuntu.com/hardy/mpd"):mad:
also see:
[http://mpd.wikia.com/wiki/Dependencies]("http://mpd.wikia.com/wiki/Dependencies"):mad:

also after a lot of search i found a link for workaround in gentoo,
[http://www.linuxquestions.org/questions/linux-software-2/mpd-dependencies-333991/]("http://www.linuxquestions.org/questions/linux-software-2/mpd-dependencies-333991/"):KS
any hope in ubuntu? thanks a lot!

---

### Post by papibe on 2012-03-16
Hi superbike.

I was curious and tried a simulate install of mpd in my home server. This is what I got:
```
sudo apt-get -s install mpd
[sudo] password for ...: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libao2 libasound2 libaudiofile0 libavcodec52 libavformat52 libavutil49 libcue1 libfaad2 libflac8 libgsm1 libice6 libid3tag0 libjack0 libmad0 libmms0
  libmpcdec3 libogg0 liboil0.3 libpulse0 libresid-builder0c2a libsamplerate0 libschroedinger-1.0-0 libshout3 libsidplay2 libsm6 libsndfile1 libspeex1
  libtheora0 libvorbis0a libvorbisenc2 libvorbisfile3 libwavpack1 libxi6 libxtst6
Suggested packages:
  libaudio2 libesd0 libesd-alsa0 libasound2-plugins jackd pulseaudio speex mpd-client icecast2
The following NEW packages will be installed:
  libao2 libasound2 libaudiofile0 libavcodec52 libavformat52 libavutil49 libcue1 libfaad2 libflac8 libgsm1 libice6 libid3tag0 libjack0 libmad0 libmms0
  libmpcdec3 libogg0 liboil0.3 libpulse0 libresid-builder0c2a libsamplerate0 libschroedinger-1.0-0 libshout3 libsidplay2 libsm6 libsndfile1 libspeex1
  libtheora0 libvorbis0a libvorbisenc2 libvorbisfile3 libwavpack1 libxi6 libxtst6 mpd
...
```
You are kind of right! I wonder why that be?

There are 2 X11 libraries as dependencies: libxi6 libxtst6. Here's more information about them:
```
apt-cache search libxtst6
libxtst6 - X11 Testing -- Resource extension library

apt-cache search libxi6
libxi6 - X11 Input extension library
```
As you, my first reaction was surprise. However, note that you are not installing the whole X Windows system, but just a couple of libraries. As a test, check how long the list libraries that Xorg would install:
```
sudo apt-get -s install xorg
```

Just some thoughts.
Regards.

---

### Post by superbike on 2012-03-16
> **papibe said:**
> Hi superbike.

I was curious and tried a simulate install of mpd in my home server. This is what I got: .....


Here is my output:

```
apt-get install mpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libao2 libasound2 libaudiofile0 libcue1 libfaad2 libice6 libjack0 libmad0 libmms0 libmpcdec3 libpulse0 libresid-builder0c2a libsamplerate0 libshout3 libsidplay2 libsm6 libsndfile1 libwavpack1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxi6 libxtst6 x11-common
Suggested packages:
  libaudio2 libesd0 libesd-alsa0 libasound2-plugins jackd pulseaudio mpd-client icecast2
The following NEW packages will be installed:
  libao2 libasound2 libaudiofile0 libcue1 libfaad2 libice6 libjack0 libmad0 libmms0 libmpcdec3 libpulse0 libresid-builder0c2a libsamplerate0 libshout3 libsidplay2 libsm6 libsndfile1 libwavpack1 libx11-6 libx11-data libxau6 libxcb1 libxdmcp6 libxext6 libxi6 libxtst6 mpd x11-common
0 upgraded, 28 newly installed, 0 to remove and 67 not upgraded.
Need to get 4875kB of archives.
After this operation, 12.8MB of additional disk space will be used.
Do you want to continue [Y/n]

```

But the problem is not just with installing the X but what bothers me is that graphics system is being asked for by a gui-less audio player!:mad:. 

I will have to take up source codes for light reading.:lolflag:
every single package sends the size of the installation funnily high ... i wonder what the reason could be.
i started with an absolute stripped down version 380mb and only with the above declared packages mt-daapd et al it now is above
1gig.:mad: (will try with a stripped down fedora:idea:).

---

