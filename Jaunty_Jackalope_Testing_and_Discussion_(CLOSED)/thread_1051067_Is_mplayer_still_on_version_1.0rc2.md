---
title: "Is mplayer still on version 1.0rc2?"
date: 2009-01-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-01-26
What version of mplayer is in the Jaunty repos? I'm still on Intrepid, but mplayer is version 1.0rc2 which is very, very out dated. Mplayer is a very popular media player.

---

### Post by x33a on 2009-01-26
add this line to your sources.

deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) intrepid main

it's a repository from the creator of smplayer, and contains the latest mplayer as well.

---

### Post by Slug71 on 2009-01-26
Yep still 1.0-RC2

---

### Post by taavikko on 2009-01-26
There hasn't been any major upstream release for mplayer, so yes, it's stuck at rc2.

All the proper patches for mplayer will be submitted to ubuntus version of it.

More info [http://www.mplayerhq.hu/design7/news.html](http://www.mplayerhq.hu/design7/news.html)

---

### Post by Jeroen Vernooij on 2009-01-26
You can verify such information very easily on [this website]("http://packages.ubuntu.com/jaunty/")

---

### Post by phenest on 2009-01-26
> **x33a said:**
> add this line to your sources.

deb [http://ppa.launchpad.net/rvm/ubuntu](http://ppa.launchpad.net/rvm/ubuntu) intrepid main

it's a repository from the creator of smplayer, and contains the latest mplayer as well.

Cheers! That saves me a shed load of compiling.

---

### Post by forcecore on 2009-01-26
download new builds in deb installers from smplayer page, those are best.

---

### Post by Nullack on 2009-01-28
Its a mistake to discount the benefit of specific cpu optimizations during compilation - in certain cpus is makes decoding significantly faster.

---

### Post by Starks on 2009-01-28
deb [http://ppa.launchpad.net/](http://ppa.launchpad.net/)**rvm4000**/ubuntu intrepid main

this is the newer ppa.

---

### Post by andrew.46 on 2009-01-28
It must surely be time that the Ubuntu / Debian developers consider using an svn snashot for MPlayer, much as is done with FFmpeg.

Andrew

---

### Post by andrew.46 on 2009-01-28
It must surely be time that the Ubuntu / Debian developers consider using an svn snapshot for MPlayer, much as is done with FFmpeg.

Andrew

---

### Post by RAOF on 2009-01-28
> **andrew.46 said:**
> It must surely be time that the Ubuntu / Debian developers consider using an svn snapshot for MPlayer, much as is done with FFmpeg.

Andrew

We package ffmpeg svn snapshots because the ffmpeg project is actively hostile to releasing.  If so much stuff didn't depend on ffmpeg it would drop from the archive like a stone.

Nothing depends on mplayer (and it's in multiverse), so developers care about it a lot less.  You could petition mplayer devs to release something more regularly :).

---

### Post by rvm4000 on 2009-01-28
> **RAOF said:**
> We package ffmpeg svn snapshots because the ffmpeg project is actively hostile to releasing.  If so much stuff didn't depend on ffmpeg it would drop from the archive like a stone.

Nothing depends on mplayer (and it's in multiverse), so developers care about it a lot less. 

Well, smplayer (and other frontends) depend on it. And for me it's a pain that many linux distros (not only ubuntu) still include the old 1.0rc2, as then I have to try to keep compatibility with it, which sometimes is not easy or even impossible. Also some bug reports for smplayer are actually bugs in mplayer 1.0rc2 fixed a long time ago in svn...

> **RAOF said:**
> 
You could petition mplayer devs to release something more regularly :).

AFAIK they don't have anybody to make a new release. Also it seems they don't believe much in releases. They recommend everyone to use svn (because it's stable). For them 1.0rc2 is obsolete and unsupported, and blame distro's maintainers for keeping such an old version.

See for instance [this thread](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-October/074650.html) in mplayer-users.

---

### Post by RAOF on 2009-01-28
> **rvm4000 said:**
> Well, smplayer (and other frontends) depend on it. And for me it's a pain that many linux distros (not only ubuntu) still include the old 1.0rc2, as then I have to try to keep compatibility with it, which sometimes is not easy or even impossible. Also some bug reports for smplayer are actually bugs in mplayer 1.0rc2 fixed a long time ago in svn...

Yeah.  Sorry about this, but you've written a frontend for a project that basically doesn't want to be used.  The best I can offer is to suggest that you drop mplayer, and write a frontend for something that isn't deliberately difficult to use.

> **rvm4000 said:**
> 
AFAIK they don't have anybody to make a new release. Also it seems they don't believe much in releases. They recommend everyone to use svn (because it's stable). For them 1.0rc2 is obsolete and unsupported, and blame distro's maintainers for keeping such an old version.

See for instance [this thread](http://lists.mplayerhq.hu/pipermail/mplayer-users/2008-October/074650.html) in mplayer-users.

That's pretty much the mplayer/ffmpeg devs in a nutshell.  Sure, the rest of the world does releases, and every distribution is packaging an old mplayer release, but that *doesn't matter*.  Multimedia applications shouldn't release, ever, and the world is wrong to expect it!
</exasperated sarcasm>

They *have* had people volunteer to do releases.  They're actively hostile to it, basically demanding that
[list]
[*] It cannot impact any current developer in any way
[*] It can't be done unless it's done perfectly.
[/list]

---

### Post by Starks on 2009-01-28
RAOF. Chill.

MPlayer (svn or stable) is pretty much unrivaled for what it does. Unless you have the time or ability to replace the enduring standard for playback on Linux, we simply will just have to make do with it.

Besides, without MPlayer and libass, styled assa/ssa subtitles on Linux would be nothing more than a pipe dream.

---

### Post by andrew.46 on 2009-01-28
Hi RAOF,

My apologies for accidentally releasing a small storm here.

> **RAOF said:**
> We package ffmpeg svn snapshots because the ffmpeg project is actively hostile to releasing.  If so much stuff didn't depend on ffmpeg it would drop from the archive like a stone.

Then I guess it is fortunate that FFmpeg is used by so many programs :-).

> Nothing depends on mplayer (and it's in multiverse), so developers care about it a lot less.  You could petition mplayer devs to release something more regularly :).

Well it might be a better plan, and perhaps more achievable, to petition the *Ubuntu* devs to use a newer version. The other possibility of course is for individuals to make their own package from the subversion repositories of both FFmpeg and MPlayer but this is perhaps not typical behaviour for the average Ubuntu user. I firmly believe that a subversion 'snapshot' would be the best possible solution for the average Ubuntu user.

My apologies again for inadvertently stirring things up a little :-).

Andrew

---

### Post by rvm4000 on 2009-01-29
I'd really like that mplayer developers would make releases more often, but aren't linux distros supposed to include recent versions of the applications they provide instead of including the same old version year after year?

---

### Post by plun on 2009-01-29
> **andrew.46 said:**
>  I firmly believe that a subversion 'snapshot' would be the best possible solution for the average Ubuntu user.



Yup...  I took the time and build it....

- build-dep for mplayer is broken for Jaunty


- Your howto

libglide2 and libxcb-xlib0-dev broken

Builds Ok without those this morning...  broke yesterday.


nVidias build script works just fine  (180.25 installed driver)

[http://www.nvnews.net/vbulletin/showpost.php?p=1914226&postcount=4](http://www.nvnews.net/vbulletin/showpost.php?p=1914226&postcount=4)


Cannot see any problem with using SVN snapshots, just to maybe let users with a little more knowledge decide good ones......

I don't think they will release more often...;)

---

### Post by RAOF on 2009-01-29
> **rvm4000 said:**
> I'd really like that mplayer developers would make releases more often, but aren't linux distros supposed to include recent versions of the applications they provide instead of including the same old version year after year?

We can't provide a more recent release if they don't *have* a more recent release, and are demotivated to work out whether the particularl svn revision they're on now is a good candidate to cut a pseudo release.

---

### Post by rvm4000 on 2009-01-29
> **RAOF said:**
> We can't provide a more recent release if they don't *have* a more recent release

The do have a more recent version in their download page:

[http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2](http://www.mplayerhq.hu/MPlayer/releases/mplayer-export-snapshot.tar.bz2)

Yes, it's not a "release", but isn't that better than keeping to distribute a version more than a year old?

---

### Post by andrew.46 on 2009-01-29
> **RAOF said:**
> We can't provide a more recent release if they don't *have* a more recent release, and are demotivated to work out whether the particularl svn revision they're on now is a good candidate to cut a pseudo release.

But this same trouble *is* taken with FFmpeg and development of MPlayer appears to be taking the same course, so...

Andrew

---

### Post by Starks on 2009-01-29
"Release" is a dirty word. Take Debian and its rolling development for example.

---

### Post by phenest on 2009-01-29
Personally, I only have one use for mplayer:
```
mplayer dvd://1 -dumpstream -dumpfile video.mpg
```
I know no other way to do this. If I thought there was another way, I'd drop mplayer.

But that's diversing a little from why mplayer needs updating. I'm not expecting the Ubuntu devs (or anyone for that matter) to keep it constantly updated, but just to do a one off, up-to-date package, maybe once for each new release of Ubuntu, or at least for Intrepid.

---

### Post by taavikko on 2009-01-29
> **phenest said:**
> Personally, I only have one use for mplayer:
```
mplayer dvd://1 -dumpstream -dumpfile video.mpg
```
I know no other way to do this. If I thought there was another way, I'd drop mplayer.



IIRC: this should do the trick,
```
cat /dev/dvd > ~/video.mpg
```

---

### Post by Starks on 2009-01-29
> **taavikko said:**
> IIRC: this should do the trick,
```
cat /dev/dvd > ~/video.mpg
```

Shhh. Let the man enjoy his mplayer.

---

### Post by plun on 2009-01-29
> **phenest said:**
> Personally, I only have one use for mplayer:
```
mplayer dvd://1 -dumpstream -dumpfile video.mpg
```
I know no other way to do this. If I thought there was another way, I'd drop mplayer.

But that's diversing a little from why mplayer needs updating. I'm not expecting the Ubuntu devs (or anyone for that matter) to keep it constantly updated, but just to do a one off, up-to-date package, maybe once for each new release of Ubuntu, or at least for Intrepid.

You can also use smplayer as frontend... just great !

With mplayer there are many hidden "secrets" and one challenge is software patents within USA and Australia...:rolleyes:

Another is nVidias VDPAU....8)

I live in a software patent free country so I just compile **"the real thing"**...;)  

[http://ubuntuforums.org/showthread.php?t=1024592&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=1024592&highlight=mplayer)

A little broken for Jaunty....


Beats Windows 7 .....:D

---

### Post by Starks on 2009-01-29
Speaking of VDPAU, I saw someone in the mplayer channel talking about a patch last night.

Links: 
[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)
[ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3076399.tar.bz2](ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3076399.tar.bz2)

---

### Post by plun on 2009-01-29
> **Starks said:**
> Speaking of VDPAU, I saw someone in the mplayer channel talking about a patch last night.

Links: 
[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)
[ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3076399.tar.bz2](ftp://download.nvidia.com/XFree86/vdpau/mplayer-vdpau-3076399.tar.bz2)

Well....

Please read all messages within the thread....;)

[http://www.nvnews.net/vbulletin/showthread.php?t=123091](http://www.nvnews.net/vbulletin/showthread.php?t=123091)

**Last message** includes **_latest VDPAU_** build script and patches.

Tested it last night without any trouble.

---

### Post by phenest on 2009-01-29
> **taavikko said:**
> IIRC: this should do the trick,
```
cat /dev/dvd > ~/video.mpg
```

That doesn't allow ripping of 1 title only, more like everything in one file.

---

### Post by andrew.46 on 2009-01-29
Hi plun,

> **plun said:**
> 
I live in a software patent free country so I just compile **"the real thing"**...;)  

[http://ubuntuforums.org/showthread.php?t=1024592&highlight=mplayer](http://ubuntuforums.org/showthread.php?t=1024592&highlight=mplayer)

A little broken for Jaunty....


I believe that there will be a Jaunty version of that guide written up when Jaunty becomes beta.

Andrew

---

### Post by plun on 2009-01-30
> **andrew.46 said:**
> Hi plun,



I believe that there will be a Jaunty version of that guide written up when Jaunty becomes beta.

Andrew

Ok.. just 2 packages which are wrong, libglide and a xlib package.
Builds without those.

Debian can probably discuss stripping ffmpeg as a "never ending discussion" and for sure also Ubuntu...;)

MS and Windows 7 really likes this sort of "doing nothing"....

---

### Post by pt123 on 2009-01-30
> **andrew.46 said:**
> But this same trouble *is* taken with FFmpeg and development of MPlayer appears to be taking the same course, so...

Andrew
On Hardy using the medibuntu packages one was able to create thumbnails from an xvid file

ffmpeg -i "testfile.avi" -r .01 -y ~/ss_%d_yy.jpg

now this doesn't work on Intrepid using the unstripped ffmpeg libraries in Intrepid because medibuntu doesn't provide ffmpeg versions

but png files work
ffmpeg -i "testfile.avi" -r .01 -y ~/ss_%d_yy.png

I prefer jpg to png as the filesizes are much smaller.

Am I doing something wrong, or is this the way it is:(

---

### Post by Starks on 2009-01-30
What is the major difference between unstripped and vanilla?

Why does mplayer like unstripped and gstreamer like vanilla?

---

### Post by plun on 2009-01-30
> **Starks said:**
> What is the major difference between unstripped and vanilla?

Why does mplayer like unstripped and gstreamer like vanilla?

Just some facts and this is "sensitive".....

Latest ffmpeg is probably rather OK.
[http://packages.ubuntu.com/jaunty/ffmpeg](http://packages.ubuntu.com/jaunty/ffmpeg)


Just took a discussion about this >   Debian/Ubuntu
[http://www.mail-archive.com/debian-devel@lists.debian.org/msg264951.html](http://www.mail-archive.com/debian-devel@lists.debian.org/msg264951.html)


Mplayer is heavily outdated and I am rather sure that Mplayers devs not are going to release more often....:---)

[http://packages.ubuntu.com/jaunty/mplayer](http://packages.ubuntu.com/jaunty/mplayer)

RC2-17

Debian Sid is at RC2-20

[http://packages.debian.org/sid/mplayer](http://packages.debian.org/sid/mplayer) 


This years mplayer-svn gives nVidia a big advantage with VDPAU....:-\"8-)


Lets see whats happens.....     W7 will include everything !!!](*,):^o

---

### Post by Starks on 2009-01-30
ffmpeg. proof that the free software debate is serious ****ing business. </half-sarcasm>

---

### Post by plun on 2009-01-30
> **Starks said:**
> ffmpeg. proof that the free software debate is serious ****ing business. </half-sarcasm>

Well... it is a sensitive area and as I wrote I live in a patent free country so I just compile whatever I want.

The challenge is mainly USA and Australia....

No chance that it will be software patents in Europe so its more like a  "As Is" problem which just makes a Linux newbie frustrated....


This thread is also a reminder for this mess...
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)


;)

---

### Post by andrew.46 on 2009-01-30
> **plun said:**
> 
Just took a discussion about this >   Debian/Ubuntu
[http://www.mail-archive.com/debian-devel@lists.debian.org/msg264951.html](http://www.mail-archive.com/debian-devel@lists.debian.org/msg264951.html)


Just to add another distro: Slackware does not carry FFmpeg and MPlayer at all rather than carry outdated or crippled versions. But most slackware users will build their own or take guidance for such building from slackbuilds.org.

Andrew

---

### Post by plun on 2009-01-30
> **andrew.46 said:**
> Just to add another distro: Slackware does not carry FFmpeg and MPlayer at all rather than carry outdated or crippled versions. But most slackware users will build their own or take guidance for such building from slackbuilds.org.

Andrew

Yup... as also Gentoo and a few Ubuntu users which finds a good howto :D 

The main reason is just this for me and we must fix this "mess" for all newbies, despite of deep "religious" thoughts...

[http://www.istartedsomething.com/20081115/windows-7-new-decoders-encoders-transcoding/](http://www.istartedsomething.com/20081115/windows-7-new-decoders-encoders-transcoding/)

When we maybe reaches 5% of all users its maybe possible to have developers for all demands...;)

---

### Post by Nullack on 2009-01-31
As always, much respect for the solid work Andrew does. For me personally, I find gnome mplayer to be lighter than smplayer; as well as being actively developed like smplayer.

Until gstreamer gets vdpau support Im mainly using mplayer and for those who dont want to compile:

[https://launchpad.net/~rvm4000/+archive/ppa](https://launchpad.net/~rvm4000/+archive/ppa)

The SMPlayer dev has regular svn builds on his ppa. Just add his key to software sources under authentication and add the ppa to sources.

Compiling your own is ultimately better because it allows you to control the compile options such as DVD support and best optimises the build for your specific cpu.

---

### Post by Starks on 2009-01-31
Nully. Don't you have to use the 'intrepid' tag for the ppa?

---

### Post by Nullack on 2009-01-31
He doesnt have a jaunty build, and when I tried the intrepid tag synaptic accepts it but fails on dependencies not being met so for right now, its broken on his ppa.

---

### Post by Starks on 2009-01-31
> **Nullack said:**
> He doesnt have a jaunty build, and when I tried the intrepid tag synaptic accepts it but fails on dependencies not being met so for right now, its broken on his ppa.

the intrepid dist has always worked for me on jaunty.

---

### Post by plun on 2009-01-31
> **Nullack said:**
> He doesnt have a jaunty build, and when I tried the intrepid tag synaptic accepts it but fails on dependencies not being met so for right now, its broken on his ppa.

Well... I just tested to build a package out of nVidias script and the challenge is the d--ned **[libconfhelper]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libconfhelper")**  (also Ubuntu bugs about it)

```
dpkg-buildpackage -rfakeroot 

```


It builds a package just fine.....

I don't know the consequence for not including this function but maybe Andrew.46 knows ???


Andrew.46s [guide]("http://ubuntuforums.org/showthread.php?t=1024592") also works except that libglade and a xlib package must be excluded from dependencies.

---

### Post by Starks on 2009-01-31
I want to cry.

```
eric@kingfisher:~$ sudo apt-get build-dep mplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Build-dependencies for mplayer could not be satisfied.
```

No details. No reason whatsoever. Great job packagers!

I have all the repo and ppa sources enabled.

---

### Post by rvm4000 on 2009-02-02
Maybe will there be a new release very soon? :p

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060064.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060064.html)

---

### Post by Starks on 2009-02-02
I saw that this morning and almost **** bricks.

---

### Post by meborc on 2009-02-02
> **rvm4000 said:**
> Maybe will there be a new release very soon? :p

[http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060064.html](http://lists.mplayerhq.hu/pipermail/mplayer-dev-eng/2009-February/060064.html)

wow... i guess that is good news :D

---

### Post by RAOF on 2009-02-02
Synchronised with *FFmpeg* releases?  Hurray!

---

### Post by Starks on 2009-02-02
(Does that mean that mplayer will continue to be released once in a blue moon?)

The release schedule is giving me so much angina. My proposition for libass enhancements may not make it in.

---

