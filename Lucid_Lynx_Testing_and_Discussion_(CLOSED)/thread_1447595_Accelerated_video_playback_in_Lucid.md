---
title: "Accelerated video playback in Lucid?"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by stelekpl on 2010-04-05
Hi,
I'm just a regular Ubuntu user who sometimes tries to update a package or two. I'm currently on Karmic and today I decided to enable Nvidia HiDef video playback acceleration in VLC. It took me some hours but I managed to do it in the end and it works just fine.
The problem is that achieving that was not simple. Not only I had to download and install two additional libraries (libvaapi) but I also had to re-compile the whole FFmpeg and VLC. The FFmpeg recompilation was most problematic, since I failed to simply "update" the existing package and I had to remove many libraries from my system to install custom FFmpeg. This resulted in removal of all application dependant on FFMpeg and basically broke my Ubuntu, since now I have to compile all these applications by myself... Perhaps there was a better way to do that but with my level of knowledge this was all I could get...

Soon I'm going to upgrade to Lucid and I was wondering whether the GPU video acceleration is considered for this release at all. It would be really convenient if we could have this feature working out-of-the-box without the need of creating any custom packages. It is an important feature and currently is not reachable for "normal people" at all. Is this considered for this release?

To be honest I'm asking because I have some doubts about it. I've checked the packages of Lucid today:
[http://packages.ubuntu.com/search?keywords=nvidia&searchon=names&suite=lucid&section=all](http://packages.ubuntu.com/search?keywords=nvidia&searchon=names&suite=lucid&section=all)
and it seems that the latest NVidia drivers are not even in this release. I have a graphic card that requires drivers 190/195 and if they're not included, I will have to keep updating them manually after each kernel fix. This is another serious issue for "normal people" and I hope that Ubuntu developers are aware how important the graphic chipset support is. Karmic is basically unusable for "normal people" with latest NVidia graphic cards, because there's only support for driver 185.* in this release.

I really hope this gets better in Lucid :)

---

### Post by deankovell on 2010-04-05
don't know the answer to your lucid question, but you might try using  checkinstall instead of make install. I believe checkinstall can be  gotten from synaptic. what checkinstall does is instead of just  installing the program you've compiled, it'll create a .deb that is  recognised by synaptic as an upgrade to vlc or whatever. that should help with all of the other programs that depend on vlc, ffmpeg etc. sorry I can't answer your question, but hopefully this will keep you from having to recompile everything else by yourself.

---

### Post by stelekpl on 2010-04-06
> **deankovell said:**
> don't know the answer to your lucid question, but you might try using  checkinstall instead of make install. I believe checkinstall can be  gotten from synaptic. what checkinstall does is instead of just  installing the program you've compiled, it'll create a .deb that is  recognised by synaptic as an upgrade to vlc or whatever. that should help with all of the other programs that depend on vlc, ffmpeg etc. sorry I can't answer your question, but hopefully this will keep you from having to recompile everything else by yourself.

I did use checkinstall. The problem was that my .deb contained not only the ffmpeg program but also all the A/V libs which are separate debs on Ubuntu. I failed miserably with solving this conflict and had to replace it completely :(

---

### Post by Linuxforall on 2010-04-06
Why not install mplayer which does native vdpau instead vlc, mplayer is also easy to compile and integrate it into system thanks to andrew46's excellent instructions here on the forum. Also the SMPLAYER front end is excellent and does vdpau quite well, if you intend to compile mplayer, I would also suggest compiling x264 and ffmpeg as per Fake Outdoorsman's instructions here.

---

### Post by stelekpl on 2010-04-06
> **Linuxforall said:**
> Why not install mplayer which does native vdpau instead vlc, mplayer is also easy to compile and integrate it into system thanks to andrew46's excellent instructions here on the forum. Also the SMPLAYER front end is excellent and does vdpau quite well, if you intend to compile mplayer, I would also suggest compiling x264 and ffmpeg as per Fake Outdoorsman's instructions here.

I do have mplayer installed too, but there are two problems with the movies from my camcorder:
1) mplayer shows some strange "juddering" - probably caused by the fact that my video is 50fps and the monitor is 60Hz
2) smplayer does not work with them at all :)

Besides - I have nothing against mplayer. I simply believe that VLC is better. But of course it would be best to have many players supported in Ubuntu, and of course all of them with hardware decoding. I really hope that some day we'll reach that goal :)

---

### Post by mc4man on 2010-04-06
I've checked the packages of Lucid today:
[http://packages.ubuntu.com/search?ke...id&section=all](http://packages.ubuntu.com/search?ke...id&section=all)
and it seems that the latest NVidia drivers are not even in this release. I have a graphic card that requires drivers 190/195 and if they're not included

scroll down and look under nvidia-current (195.36.15

---

### Post by cariboo on 2010-04-06
I'm using the latest current driver, 195.36.15. See screenshot.

---

### Post by djchandler on 2010-04-06
To the OP:

I have been using Ubuntu to some degree for almost four years, beginning with 6.06. I have compiled programs before with Ubuntu, but it certainly isn't necessary. The only times I have had serious problems were due to hardware issues, as in failing hardware, and using the video drivers downloaded directly from ATI or Nvidia and installing those from their executable binary or building my own .deb.

In regard to the current state of proprietary drivers in Ubuntu Lucid, those are just now becoming integrated. Nouveau is now the open source driver for Nvidia cards. I don't use Nvidia now, but the xorg FOSS ATI Radeon driver is pretty good. Depending on the raw processing power of your GPU, it may still feel slow compared to the proprietary drivers in Karmic. (Watching video with my lower end laptop is less than fully satisfying, but it was purchased in lieu of a netbook because there was only a $100 US difference after rebate. It has actually surpassed my expectations.)

What graphics card are you using? The latest driver [Nvidia]("http://www.nvidia.com/object/unix.html") has released is 195.36.15. Whether or not it gets included in Lucid soon is a matter of completion of testing by Canonical. The Nvidia release date was March 19. The current beta 1 release was March 18. The Beta 2 is due in two days, April 8. Here is the official [release schedule]("http://ubuntuforums.org/showthread.php?t=1304172"). So far it is holding form. If the new Nvidia driver makes it into beta 2, that will be a good sign for you.

[nV News Forums      ]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14")[> Linux  Support Forums]("http://www.nvnews.net/vbulletin/forumdisplay.php?s&forumid=14") has posts that very directly address your concerns. How reliable its members are is left to your judgment. Nvidia links to that forum from the Unix driver page referenced above. If I had an Nvidia card, that's where I would be looking. 

One last question. If you had issues with an Nvidia card driver while running Windows, where would you look for support?;)

---

### Post by stelekpl on 2010-04-06
OK, so the latest nVidia driver is in. I did not notice it - my fault:) Good news, by the way... :) But the issue of applications supporting hardware acceleration still stands. In order to get GPU acceleration on Karmic I had to do everything that is described here:
[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)
and here:
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)
and THAT is A LOT of messing with Linux for "normal" people. I would really expect that all this stuff is already prepared in the default Ubuntu packages. It should not be a problem for the maintainers to compile the applications with support enabled, right?

Even if Lucid comes without this support by default, I will manage to fix it for me but... my aunt will not. And once she buys an HD camcorder she will have to either move to Windows or ask me for help... So it would really be better if it was working out-of-the-box... (not only for her but for thousands of other people like her)

@djchandler - You're right, on Windows I do not have a place to look for support - Linux is much, much better here. The problem is that on Windows you need support only when something is really broken, since all the basic features (like accelerated video playback) are already in and on "standard" hardware they work right away... And that's what non-geeks expect - they don't want a good place for getting support, they want an OS that does not need one. When I was switching from Slackware to Ubuntu I had a feeling that it was the direction Ubuntu wants to go... But the stuff I had to do yesterday to get my videos to play nicely, really reminded me of my Slackware days...

---

### Post by Luke has no name on 2010-04-14
It seems getting (s)mplayer to work in Lucid with VDPAU is as easy as installing this PPA:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid](https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid)

I know you said you can't use mplayer, but it's still handy for others to get.

What I don't understand is why mplayer can't be in the official repos with VDPAU support. 

1) Why does it need to be recompiled? Why isn't VDPAU just a plugin?

2) Why can't it be compiled officially to support VDPAU? Why make us go through a PPA?

---

### Post by mc4man on 2010-04-15
> on Karmic I had to do everything that is described here:
[http://wiki.videolan.org/VLC_VAAPI](http://wiki.videolan.org/VLC_VAAPI)

When or if you do this again (lucid), then don't use "--enable-shared", just do a ffmpeg build specifically for vlc and statically link.

This way you won't impact your current ffmpeg shared libs.

The other decent way is to build ffmpeg as shared but as a .deb package set - with some care it will not regress current repo apps that depend on the shared libs. Relativity easy to do, but the former method is certainly  preferred. (though I always replace the shared ffmpeg lib packages once per install, no advantage after that.

---

### Post by jocko on 2010-04-15
> **Luke has no name said:**
> It seems getting (s)mplayer to work in Lucid with VDPAU is as easy as installing this PPA:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=lucid]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa?field.series_filter=lucid")

I know you said you can't use mplayer, but it's still handy for others to get.

What I don't understand is why mplayer can't be in the official repos with VDPAU support. 

1) Why does it need to be recompiled? Why isn't VDPAU just a plugin?

2) Why can't it be compiled officially to support VDPAU? Why make us go through a PPA?
The mplayer version in the lucid repos already support vdpau. There's no need to recompile anything or install from ppa's.
Just install mplayer (plus any additional frontend you like, like mplayer-gui, gnome-mplayer, smplayer), the nvidia driver (nvidia-current) and libvdpau. All in the repos.

---

### Post by Longinus00 on 2010-04-15
> **jocko said:**
> The mplayer version in the lucid repos already support vdpau. There's no need to recompile anything or install from ppa's.
Just install mplayer (plus any additional frontend you like, like mplayer-gui, gnome-mplayer, smplayer), the nvidia driver (nvidia-current) and libvdpau. All in the repos.

Do you know if mplayer in the repos have the patches for multithreaded decoding of h264 content?

---

