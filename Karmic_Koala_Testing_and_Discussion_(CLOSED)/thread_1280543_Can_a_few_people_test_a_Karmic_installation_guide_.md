---
title: "Can a few people test a Karmic installation guide for the svn MPlayer?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrew.46 on 2009-10-02
Hi,

Looks like Karmic will be out soon so could I please have a few people test the following guide for the svn MPlayer under Karmic? There are a few new ideas there that I would appreciate some extra eyes on:


==================================================================
**Howto: Improve the 'mplayer-nogui' package under Karmic Koala**
==================================================================

Over the last few years I have written several guides for the installation of the development version of MPlayer under Ubuntu. This particular version of that long series of guides is intended to bring the benefits of the cutting edge svn MPlayer to users of Karmic Koala by concentrating on upgrading the mplayer-nogui package. I should mention at this time that the mplayer-nogui package from the Karmic Repository is an immense improvement over packages seen in previous versions of Ubuntu and if the information below looks a little too much you will still be well served by simply installing the repository package. This guide is perhaps for those who want a little more...

============================
**Some requirements...**
============================

There is a little preparation work required before we actually lay hands on the MPlayer application and this will probably take about 30 minutes and involve a download of about 100 megabytes of extra software. First then for some necessary software:

------------------------
Required tools:
------------------------

Some compiling will be required for this guide so we will be downloading some compiling sotware as well as software to access subversion and git repositories and finally the utility checkinstall which will be used to keep the installation within the Ubuntu package management system. Copy the following and paste into a Terminal window, exclude the '$' marks which among other things demonstrates a *new line* of commands in this guide:

```
$ sudo apt-get install build-essential gcc-4.3 g++-4.3 subversion checkinstall
```

Next to collect some development files:

---------------------------
Development files:
---------------------------

MPlayer works by automatically gathering functionality from various development files installed on your computer. The following list of files has been winnowed out from the standard *sudo apt-get build-dep mplayer-nogui* command in the interests of maintaining a cleaner system:

```

$ sudo apt-get install ladspa-sdk libaa1-dev libasound2-dev libatk1.0-dev \
libaudio-dev libaudio2 libaudiofile-dev libavahi-client-dev libavahi-common-dev \
libcaca-dev libcairo2-dev libcdparanoia-dev libcelt0 libdbus-1-dev libdc1394-22 \
libdca-dev libdca0 libdirectfb-dev libdirectfb-extra libdts-dev libesd0-dev \
libexpat1-dev  libffado1 libfontconfig1-dev libfreebob0 libfreetype6-dev \
libfribidi-dev libgif-dev libgl1-mesa-dev libglib2.0-dev libglu1-mesa-dev \
libgsm1 libgtk2.0-dev libice-dev libjack-dev libjack0 libjpeg62-dev liblzo2-2 \
liblzo2-dev libmail-sendmail-perl libncurses5-dev libogg-dev liboil0.3-dev \
libopenal-dev libopenal1 libpango1.0-dev libpixman-1-dev libpng12-dev \
libpthread-stubs0 libpthread-stubs0-dev libpulse-dev libruby1.8 \
libschroedinger-dev libsdl1.2-dev libslang2-dev libsm-dev libsmbclient-dev \
libspeex-dev libsvga1 libsvga1-dev libsys-hostname-long-perl libsysfs-dev \
libtheora-dev libvorbis-dev libvorbisidec-dev libvorbisidec1 libx11-dev libxau-dev \
libxcb-render-util0-dev libxcb-render0-dev libxcb1-dev libxcomposite-dev \
libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxft-dev \
libxi-dev libxinerama-dev libxml++2.6-2 libxrandr-dev libxrender-dev libxt-dev \
libxv-dev libxvidcore4 libxvidcore4-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev \
mesa-common-dev vstream-client-dev x11proto-composite-dev x11proto-core-dev \
x11proto-damage-dev x11proto-fixes-dev x11proto-input-dev x11proto-kb-dev \
x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev \
x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev \
zlib1g-dev libopencore-amrwb-dev libopencore-amrnb-dev

```

This guide does not deal with vdpau so if you have an appropriate NVidia graphics card you will need to now add in the necessary development files to enable vdpau output from MPlayer, no extra *./configure* flags are necessary as MPlayer will pick up these files automagically. We will also add another useful packages here, a current set of Live555 libraries to enable playback of some streaming audio:

```

$ sudo apt-get remove liblivemedia-dev
$ cd $HOME
$ wget http://www.live555.com/liveMedia/public/live555-latest.tar.gz
$ tar xvf live555-latest.tar.gz
$ cd live
$ ./genMakefiles linux
$ make
$ sudo cp -r $HOME/live /usr/lib

```

These libraries are in constant development so come back here from time to time to repeat the process and pick up the updated libraries. Or if you have no interest in streaming audio simply omit this step, many streams will be processed *natively* by MPlayer anyway.

Next however to install a codec package:

-------------
Codecs:
-------------

MPlayer has the ability to use and external library of codecs to playback some media files. Conveniently Medibuntu holds these files and I would suggest that you now read over the following page and enable the Medibuntu repository for Karmic Koala:

Medibuntu - Community Ubuntu Documentation
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Once this is in place users of a 32bit system will need to run the following:

```
$ sudo apt-get install w32codecs
```

while users of a 64bit system will need to run the following instead:

```
$ sudo apt-get install w64codecs
```

Now that all of this is done it is time to actually lay hands on the MPlayer files themselves:

==============================
**Downloading & Compiling**
==============================

The development version of MPlayer is held in a subversion repository that allows read access by users, which is to say that you can *download* files from the repository but not *alter* files in this repository. To download our copy of the MPlayer files the following commands are required:

```

$ cd $HOME
$ svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer

```

Now to compile and install the source code, especially note the use of gcc-4.3 in this command. The MPlayer developers believe that there are a few issues compiling under gcc-4.4.1 which is the default under Karmic. If you wish to use gcc-4.4.1 anyway simply omit *--cc=gcc-4.3* and cross your fingers while compiling:

```

$ cd $HOME/mplayer
$ ./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-mencoder
$ make
$ sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/Desktop" \
   --pkgname mplayer-nogui --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "3:1.0~svn-`grep "#define VERSION" version.h | cut -d"-" -f2`"
$ make distclean

```

And that just about does it for mplayer-nogui. It is best to now leave $HOME/mplayer undisturbed as you can return at a later date to run the command *svn up* to download the latest changes in the MPlayer source code and then recompile. And I wish you all the best with your improved copy of Karmic Koala's mplayer-nogui!

===========================
**Some Resources...**
===========================

[LIST]
[*][MPlayer-users]("https://lists.mplayerhq.hu/mailman/listinfo/mplayer-users") MPlayer mailing list for usage questions, feature requests, bug reports. I would advise lurking for  while on this list before posting, breaches of posting etiquette are dealt with harshly at times.
[*][MPlayer - The Movie Player]("http://www.mplayerhq.hu/DOCS/HTML/en/index.html") The html documentation for MPlayer. Usually kept up to date and well worth reading if problems arise and certainly will need to be read before requesting help on MPlayer-users.
[*] [MPlayer FAQs]("http://wiki.multimedia.cx/index.php?title=MPlayer_FAQ") This page attempts to list all of the frequent questions from the #mplayer irc channel on irc.freenode.net. 
[*][Top 10 Tricks and Tips for the svn MPlayer]("http://ubuntuforums.org/showthread.php?t=1154431") A guide on the Ubuntu Forums that demonstrates some of the magic that can be accomplished with the commandline MPlayer. Written by the author of this guide.
[/LIST]

---

### Post by andrew.46 on 2009-10-02
On closer examination 2 gcc versions should not be a problem. Looks like a default installation has a 'gcc' soft-link to gcc-4.4.1, both in /usr/bin while gcc-4.3 sits quietly in /usr/bin waiting for a *specific* call, such as I have made in this guide.

Andrew

---

### Post by slakkie on 2009-10-02
WIth regards to the wXXcodecs, you could do this:

```

sudo apt-get install w$(getconf LONG_BIT)codecs

```

This is 32/64 bit compatible, since the getconf LONG_BIT will actually tell you whether the system is 32/64 bit.

---

### Post by happyhamster on 2009-10-02
I had a few problems getting the codecs to install. When trying to install from the Medibuntu repo:
> 
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783


And when trying to install the w64codecs_20071007-0medibuntu2_amd64.deb file manually:
> dpkg: unable to read filedescriptor flags for <package status and progress file descriptor>: Bad file descriptor


From the same page you can get the source file though:
w64codecs_20071007.orig.tar.gz

Extract it, and copy the 3 .so files to /usr/local/lib/codecs/, as written in the corresponding README file. In my case I first had to create the folder:
sudo mkdir /usr/local/lib/codecs/

And then, from within the extraction folder:
sudo cp *.so /usr/local/lib/codecs/

When following the guide, I initially was confused about the line:
> 
It is best to leave $HOME/mplayer undisturbed as you can return at a later date to run the command 'svn up' to download the latest changes in the MPlayer source code.
Because next thing to do is actually make changes to $HOME/mplayer. Perhaps you could add something like "After compilation is done, it is best ...". Yeah, I know I'm dense :)

Anyway, mplayer compiled fine, and it appears to work fine too, but I haven't thrown all media-formats at it yet.

Thanks for the guide!



edit: The install problems are related to this bug:
[https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953](https://bugs.launchpad.net/ubuntu/+source/vte/+bug/388953)

---

### Post by mc4man on 2009-10-02
Only minor difference noticed off of a configure is when using gcc-4.3 that autodection is not quite as good.
The most notable would be a live555 installed to /usr/lib/live, gcc-4.3 fails to find. gcc-4.4 will detect

---

### Post by andrew.46 on 2009-10-02
Hi slakkie,

> **slakkie said:**
> WIth regards to the wXXcodecs, you could do this:

```

sudo apt-get install w$(getconf LONG_BIT)codecs

```

Thanks for that idea!!

Andrew

---

### Post by andrew.46 on 2009-10-02
Hi happyhamster,

> **happyhamster said:**
> I had a few problems getting the codecs to install.

I will admit that it is my normal practice to place these codecs manually and to download the entire pack from MPlayer itself, in part to avoid some of the errors that come from a Medibuntu installation. But in the interests of a more 'user-friendly' guide I have gone the Medibuntu way...

> When following the guide, I initially was confused about the line:

Because next thing to do is actually make changes to $HOME/mplayer. Perhaps you could add something like "After compilation is done, it is best ...". 

Good point, I have altered the sequence a little so it makes more sense.

> Thanks for the guide!

Thanks for testing it out :). After the release of Karmic I will be placing it in the 'Tutorials and Tips' section.

All the best,

Andrew

---

### Post by andrew.46 on 2009-10-02
Hi mc4man,

> **mc4man said:**
> Only minor difference noticed off of a configure is when using gcc-4.3 that autodection is not quite as good.
The most notable would be a live555 installed to /usr/lib/live, gcc-4.3 fails to find. gcc-4.4 will detect

You have noticed of course that I have omitted the libopencore-amr, Live555, x264 and mencoder material. I am hoping that a lesser level of complication will allow more people to successfully get a working copy. More advanced users can then add what they please.

Seems odd as regards the live555 libraries, slackware 13.0 uses gcc 4.3.3 wih no detection problems, I shall investigate on Karmic. Have you had trouble with usage of MPlayer compiled with gcc-4.4.1? I see that there have been some big problems elsewhere:

[https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-October/000626.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-October/000626.html)

Andrew

---

### Post by Milos_SD on 2009-10-02
Why do you disable mencoder in that configure command? :S

---

### Post by kansasnoob on 2009-10-02
I normally don't use mplayer but, since I find the latest changes to Totem somewhat unpalatable, I'd like to give this a try once the Ubuntu servers free up a bit.

I do have a couple of questions though:

(1)If I install it how do I remove it?

(2)Will this work with the smplayer front-end? Other front-ends?

(3)Does this also automatically install the mozilla mplayer plugin? (I'd dislike that because I'm quite happy with vlc and totem in their current configuration).

---

### Post by andrew.46 on 2009-10-02
Hi Milos,

> **Milos_SD said:**
> Why do you disable mencoder in that configure command? :S

There are a couple of reasons. The main reason is that I am getting a little closer to Ubuntu practice where MPlayer is carved up into several different packages. This guide, when complete, will be replacing *only* the package 'mplayer-nogui' and of course this does not actually contain MEncoder, the default MPlayer gui or the MPlayer html documenation. All of these have *their own packages* under Ubuntu.

Another reason is that I am removing several layers of complexity by creating only mplayer-nogui thus hopefully allowing less technically able Ubuntu users to still successfully use the svn MPlayer. Thus without MEncoder there will be no issues with compiling the git x264 vs the repository x264 and there will be no issues of repository software unable to find a single MEncoder package and a few other smaller problems that have surfaced over the years I have been writing these guides.

Mind you if you are keen to add MEncoder it would be fairly straightforward. Simply change the build-dep line to drag a few extra packages in, grab a copy of x264, alter the ./configure line and twiddle a little with the checkinstall syntax. But that would be a different guide :).

Andrew

---

### Post by mc4man on 2009-10-02
> Have you had trouble with usage of MPlayer compiled with gcc-4.4.1?

only in regards to .mkv as you mentioned previously.

want to retry on a fresh beta install i have (was previously a straight up a6
Unfortunately now isn't a great time to get build-deps, the servers are slow ( as in very

so I tried on my 'real install' which as been modded slightly 

Ex. w/ 4.3
> Disabled optional drivers:
    Input: radio tv-dshow live555 nemesi 
    Codecs: libdirac x264 toolame 
    Audio output: sun arts ivtv dxr2 


4.4
> Disabled optional drivers:
    Input: radio tv-dshow nemesi 
    Codecs: x264 toolame 
    Audio output: sun arts ivtv dxr2 

( currently have the 75 libx264-dev installed so no x264 which is no big loss

A small note
the build-deps will install the -devs for the ffmpeg libs, no big deal though possibly should be removed if those using this guide were also inclined to use FO's for ffmpeg

---

### Post by mc4man on 2009-10-02
As far as mencoder

edit 
doesn't seem possible, will recheck

re edit 
was my orig.  mplayer build which created the separate mencoder .deb

---

### Post by andrew.46 on 2009-10-02
Hi kansasnoob,

> **kansasnoob said:**
> 

(1)If I install it how do I remove it?

It can be removed from Synaptic. I attach a screenshot to demonstrate this.

```
(2)Will this work with the smplayer front-end? Other front-ends?
```

It certainly works with SMPlayer and that is how I have been using it, and should also work with other software that looks for the Ubuntu package mplayer-nogui.

> (3)Does this also automatically install the mozilla mplayer plugin? (I'd dislike that because I'm quite happy with vlc and totem in their current configuration).

It does not install the plugin. 

Bear in mind that this guide is still only in the testing phase, as is Karmic Koala of course, so there will be numerous small changes over the next few weeks until the release of Karmic.

All the best,

Andrew

---

### Post by andrew.46 on 2009-10-02
Hi mc4man,

> **mc4man said:**
> the build-deps will install the -devs for the ffmpeg libs, no big deal though possibly should be removed if those using this guide were also inclined to use FO's for ffmpeg

It is a bit of a pain that build-dep installs files not actually used to build mplayer-nogui, also it brings in libdvdread and a few others that are redundant with the svn MPlayer. Which is why I have not used build-dep before of course, this is a slighly new direction.

As to why liblivemedia-dev is not working with gcc-4.3 I am not sure, I would like this one picked up if possible.....

Andrew

---

### Post by mc4man on 2009-10-02
What may be interesting is if there was a common 'problem' file or 2.

Went ahead and built off of your commands but used 4.4.1

the .mkv that previously failed now plays

 Noting that this .mkv is terribly unsuited to the machine I'm on, a p4. being a hd video w/ high bitrate  ac3,  eac3 audio

( a curiosity is mplayer refuses to play the eac3 audio track, but ffplay and vlc will play it
> avcodec decoder debug: ffmpeg codec (A/52 B Audio (aka E-AC3)) started

Edit: resolved the issue with mplayer and eac3, was an issue with the file, not mplayer, though vlc and ffplay ignored so to speak

But that's besides the point

I grabbed a few from mplayer samples but don't know if they represent where the problems may lie (they also play fine

---

### Post by kansasnoob on 2009-10-02
> **andrew.46 said:**
> Hi kansasnoob,



It can be removed from Synaptic. I attach a screenshot to demonstrate this.

```
(2)Will this work with the smplayer front-end? Other front-ends?
```

It certainly works with SMPlayer and that is how I have been using it, and should also work with other software that looks for the Ubuntu package mplayer-nogui.



It does not install the plugin. 

Bear in mind that this guide is still only in the testing phase, as is Karmic Koala of course, so there will be numerous small changes over the next few weeks until the release of Karmic.

All the best,

Andrew

Sounds good, I'll give it a whirl in the next day or two!

Many thanks for the effort!

---

### Post by mc4man on 2009-10-02
Also noting that there is a large update to karmic beta now avail., what it may bring on who knows
( not inclined to try till after midnight

---

### Post by mc4man on 2009-10-02
andrew
from the configure log with 4.3 concerning live
> gcc-4.3: error trying to exec 'cc1plus': execvp: No such file or directory

(exactly the same as build error if you enable and link the live libraries in the configure, in other words it does find it in the configure but rejects and if forced then fails

---

### Post by Longinus00 on 2009-10-02
Does the subversion repository listed have the mt patches?

NM, i'm almost certain it doesn't.

---

### Post by andrew.46 on 2009-10-03
Hi mc4man,

> **mc4man said:**
> (exactly the same as build error if you enable and link the live libraries in the configure, in other words it does find it in the configure but rejects and if forced then fails

It is c++ compiler problem I suspect.... hmmmm... I have a few ideas

Andrew

---

### Post by mc4man on 2009-10-03
just curious if the main (or only ..?) issue with gcc-4.4.1 was with mkv?

If so you may want to rebuild and see how it fares now

( I only have a few on hand and they're now playing fine, though I wouldn't know if they're representative of ones that are a problem

---

### Post by andrew.46 on 2009-10-03
Hi mc4man,

> **mc4man said:**
> just curious if the main (or only ..?) issue with gcc-4.4.1 was with mkv?

No, there were dire warnings on #mplayer that the earth would crack the sun explode etc etc if MPlayer was compiled with this version of gcc. I experienced some odd video effects as well with backgrounds showing through videos. Hmmmm.... I shall try 4.4.1 again, it would certainly make life a lot easier, I assume you have had no trouble with this except for those rogue mkvs?. BTW adding g++-4.3 enabled the Karmic liblivemedia.

Andrew

**Edit: ** Well, I believe gcc-4.3 is the way to go based on my own experiments with both and a brief foray onto #mplayer where 4.4.1 is being given the thumbs down. Interesting!!

---

### Post by mc4man on 2009-10-03
> BTW adding g++-4.3 enabled the Karmic liblivemedia.
there you go. ( was looking in same section earlier due to the dirac error which pointed to libstdc++, but decided not to install libstdc++6-4.3-dev, which would have installed g++-4.3

Now
> Config files successfully generated by ./configure --cc=gcc-4.3 --confdir=/etc/mplayer --disable-lirc --disable-mencoder
............
Disabled optional drivers:
    Input: radio tv-dshow nemesi 
    Codecs: x264 toolame 

and
> Checking for LIVE555 Streaming Media libraries ... yes (using /usr/lib/live)

Edit
plus dirac is now enabled for what that's worth ..?
suggest removing the liblivemedia package after build-deps

---

### Post by slakkie on 2009-10-03
Followed the guide, works for me. Now need to figure out a way to remove all the build-deps packages.

---

### Post by andrew.46 on 2009-10-03
Hi slakkie,

> **slakkie said:**
> Followed the guide, works for me. Now need to figure out a way to remove all the build-deps packages.

I have a deep suspicion that there is no automatic procedure for this. Perhaps a list might be better than the build-dep approach? I think this may very well be the go and I shall add this in on my next spare days....

Andrew

---

### Post by slakkie on 2009-10-03
I found a way:

```

sudo aptitude markauto $(apt-cache showsrc mplayer-nogui | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g')

```

Based on comments made here: [https://answers.launchpad.net/apt/+question/8366](https://answers.launchpad.net/apt/+question/8366)

Put it in a function ala:

```

purge_build_deps () {
        [ -n "$1" ] && sudo aptitude markauto $(apt-cache showsrc $1 | grep Build-Depends | perl -p -e 's/(?:[\[(].+?[\])]|Build-Depends:|,|\|)//g')
}

```

Put that function in your bashrc or whatever rc file your shell uses and reload the shell/source the rc file and you can run purge_build_deps APPNAME and you will remove the build dependencies.

---

### Post by plun on 2009-10-03
Thank you Andrew....

Followed the guide and it just works !

---

### Post by Nullack on 2009-10-03
Andrew with the way ffmpeg is these days people dont need the 64bit codecs. The guide is good.

---

### Post by andrew.46 on 2009-10-03
Hi plun,

> **plun said:**
> Thank you Andrew....

Followed the guide and it just works !

Glad it is working ok :). I intend fine-tuning a little more, particularly with the dependencies once the load on the Ubuntu servers dies down a little!

Andrew

---

### Post by andrew.46 on 2009-10-03
Hi Nullack,

> **Nullack said:**
> Andrew with the way ffmpeg is these days people dont need the 64bit codecs. The guide is good.

This is my thought, but somebody I am sure will ask or them alhough from memory there are 3 codecs there and probably libavcodec covers these mostly? Still some fine-tuning to go...

Andrew

---

### Post by andrew.46 on 2009-10-04
Hi mc4man,

> **mc4man said:**
> suggest removing the liblivemedia package after build-deps

Actually I have gone a little further and used some of my previous work and used the current live555 libraries again. liblivemedia-dev is in fact quite old and bears a little tag to say that Canonical will not update it. Plus I guess for those who wish to build vlc this will be handy?

build-dep has gone as I had a long hard look at all the extras dragged in: libdvdread, x264, ffmpeg development libraries, tools for generating deb packages, tools for generating documentation and it all started looking a little silly. Plus as you mentioned this might very well impact on FakeOutdoorsman's FFmpeg work.

Left gcc-4.3 in but explained how to compile with 4.4.1 so non-believers can use whichever version they want :).

All in all it is taking shape nicely and should be a nice well-tested guide by release-time...

Andrew

---

### Post by mc4man on 2009-10-04
> left gcc-4.3 in but explained how....
I'm currently using the 4.3 off of the guide even though didn't see a diff., figure you and the mplayer guys know much better (plus what's on my new karmic install video wise is sparse

> Plus I guess for those who wish to build vlc this will be handy?
Very handy, been doing that since you first posted the way (added as --with-live555-tree=/usr/lib/live

---

### Post by andrew.46 on 2009-10-04
Hi mc4man,

> **mc4man said:**
> I'm currently using the 4.3 off of the guide even though didn't see a diff., figure you and the mplayer guys know much better

Well not *me* so much :). I know there has been historically some professional disagreements between FFmpeg/MPlayer devs and the gcc devs with a reasonable amount of robust discussion! And I have certainly been assured on #mplayer that there is a problem although specifics are often hard to find... Anyway I had no idea it was so easy to switch compilers so I am happy to have picked up something new.

Andrew

---

### Post by mc4man on 2009-10-04
edit:
did a quick build here on hardy using the checkinstall command from this thread, must of been a local issue - won't install a mplayer-nogui in presense of a mplayer install

ignore

( amazing how quick a core2duo is, 5 -6 min from checkout to finish, need to get a new desktop one of these days

---

### Post by happyhamster on 2009-10-04
When testing a gcc4.4.1 build, mplayer occasionally crashes on me. 

> 
 MPlayer interrupted by signal 11 in module: video_read_frame
ID_SIGNAL=11
- MPlayer crashed by bad usage of CPU/FPU/RAM.


Doesn't seem to be any pattern, the crashes aren't tied to any particular video file at least. On average, about 1 in 20 sessions triggers a crash. Haven't seen a crash with gcc4.3 yet.

---

### Post by ikt on 2009-10-04
everything running well, only the gui for smplayer isn't that fantastic and there are no eq presets.

first issue:

> [AO_ALSA] pcm pause error: File descriptor in bad state
[AO_ALSA] pcm resume error: File descriptor in bad state

?

was clicking around different parts of a video and all of a sudden the video stopped playing and wouldn't start :s

does have a lot of potential though, good work :)

---

### Post by mc4man on 2009-10-04
While i don't see it listed yet at packages.ubuntu there appears to be the libopencore libs availble now in the karmic repos.
( got an update notice today to ver. 0.1.2-1 which only could of come from there ( *initial release

---

### Post by andrew.46 on 2009-10-04
Hi mc4man,

> **mc4man said:**
> While i don't see it listed yet at packages.ubuntu there appears to be the libopencore libs availble now in the karmic repos.
( got an update notice today to ver. 0.1.2-1 which only could of come from there ( *initial release

I did not expect to see this is Karmic:

```

andrew@andrew-laptop:~$ apt-cache search libopencore-amr
libopencore-amrnb-dev - Adaptive Multi Rate speech codec - development files
libopencore-amrnb0 - Adaptive Multi Rate speech codec - shared library
libopencore-amrnb0-dbg - Adaptive Multi Rate speech codec - debugging symbols
libopencore-amrwb-dev - Adaptive Multi-Rate - Wideband speech codec - development files
libopencore-amrwb0 - Adaptive Multi-Rate - Wideband speech codec - shared library
libopencore-amrwb0-dbg - Adaptive Multi-Rate - Wideband speech codec - debugging symbols

```

Thanks for the heads-up!

Andrew

---

### Post by mc4man on 2009-10-04
I'm wondering if this is a precursor to a ffmpeg update, ( the current repo ffmpeg only enables the non-free

If so, it will be interesting to see if they use the same -r source (which can be configured for either the  non-free or opencore) or update to a newer source ( maybe one that enables the native aac encoding

---

### Post by andrew.46 on 2009-10-04
Hi ikt,


> **ikt said:**
> 

```

[AO_ALSA] pcm pause error: File descriptor in bad state
[AO_ALSA] pcm resume error: File descriptor in bad state 

```
was clicking around different parts of a video and all of a sudden the video stopped playing and wouldn't start :s

A search for this error showed in fact that it had [been reported for SMPlayer]("https://bugs.launchpad.net/ubuntu/+source/smplayer/+bug/414171") but not for the commandline oddly enough. I suspect rvm's advice is the best for the moment: use a different -vo, perhaps oss or pulse?

Andrew

---

### Post by andrew.46 on 2009-10-04
Hi mc4man,

> **mc4man said:**
> I'm wondering if this is a precursor to a ffmpeg update, ( the current repo ffmpeg only enables the non-free

If so, it will be interesting to see if they use the same -r source (which can be configured for either the  non-free or opencore) or update to a newer source ( maybe one that enables the native aac encoding

They are making some big changes fairly late in the development cycle. I would lay bets that the release of Karmic Koala will be delayed.

Andrew

---

### Post by Tich666 on 2009-10-09
I had mplayer already compiled and working with the instructions for jaunty, but today I recompiled it with the updated instructions.

Just wanted to report everything worked without a hitch. Thanks for the guide. :)

---

### Post by andrew.46 on 2009-10-09
Hi Tich,

> **Tich666 said:**
> Just wanted to report everything worked without a hitch. Thanks for the guide. :)

Great news! I suspect that for the most part this Karmic guide is complete so I shall test it on the actual release version and then put it in the Tutorials and Tips section shortly after.

All the best,

Andrew

---

### Post by jbernardo on 2009-10-15
To fix the issues with gcc 4.4.x, you need to add the following to the configure line:
```
 --extra-cflags=-fno-strict-aliasing
```
I've done that, and now everything works well, including mkv.

---

### Post by andrew.46 on 2009-10-15
Hi bernardo,

> **jbernardo said:**
> To fix the issues with gcc 4.4.x, you need to add the following to the configure line:
```
 --extra-cflags=-fno-strict-aliasing
```
I've done that, and now everything works well, including mkv.

Thanks for that :). I suspect for the first month or so of the Karmic release I will leave the compiling with gcc 4.3 and just watch the forums for any fallout from the repository MPlayer, which I gather has been compiled with 4.4.1.

Thanks for your trouble,

Andrew

---

### Post by piousp on 2009-10-19
Hi andrew, i too had mplayer already compiled and working on jaunty, and right now i'm compiling it under karmic with the new instructions. Just one question:

Will i'll still get nvidia VDPAU support?? Thanks in advance!

Uh-Oh, something went wrong! :o

Here, the last few lines of the make process:

```

-ldirectfb -lXext -lX11 -lpthread -lXv -lXinerama -lXxf86vm -lXxf86dga -laa -lcaca -lvga -lGL -ldl -lSDL -lesd -laudio -lXt -lpulse -ljack -lopenal                                                                 
libavcodec/libavcodec.a(dsputil.o): In function `dsputil_init':                                           
dsputil.c:(.text+0x1c236): undefined reference to `ff_lpc_compute_autocorr'                               
collect2: ld returned 1 exit status                                                                       
make: *** [mplayer] Error 1  

```

I'm using vanilla up-to-date kubuntu karmic x64

---

### Post by FakeOutdoorsman on 2009-10-19
> **piousp said:**
> Hi andrew, i too had mplayer already compiled and working on jaunty, and right now i'm compiling it under karmic with the new instructions. Just one question:

Will i'll still get nvidia VDPAU support?? Thanks in advance!

Uh-Oh, something went wrong! :o

Here, the last few lines of the make process:

```

-ldirectfb -lXext -lX11 -lpthread -lXv -lXinerama -lXxf86vm -lXxf86dga -laa -lcaca -lvga -lGL -ldl -lSDL -lesd -laudio -lXt -lpulse -ljack -lopenal                                                                 
libavcodec/libavcodec.a(dsputil.o): In function `dsputil_init':                                           
dsputil.c:(.text+0x1c236): undefined reference to `ff_lpc_compute_autocorr'                               
collect2: ld returned 1 exit status                                                                       
make: *** [mplayer] Error 1  

```

I'm using vanilla up-to-date kubuntu karmic x64

I too got this same error on 32-bit Arch Linux today.  Looks like a bit of a wait is in order for MPlayer svn.  I bet this error will be resolved in a few revisions/days.  Such is the life of a bleeding-edge user!

---

### Post by andrew.46 on 2009-10-20
Hi piousp,

> **piousp said:**
> Will i'll still get nvidia VDPAU support?? Thanks in advance!

I believe so as the appropriate dev file is installed but I will admit upfront that I know next to nothing about vdpau. If it all works with your installation could you post the info?

> Uh-Oh, something went wrong! :o

Here, the last few lines of the make process:

```

-ldirectfb -lXext -lX11 -lpthread -lXv -lXinerama -lXxf86vm -lXxf86dga -laa -lcaca -lvga -lGL -ldl -lSDL -lesd -laudio -lXt -lpulse -ljack -lopenal                                                                 
libavcodec/libavcodec.a(dsputil.o): In function `dsputil_init':                                           
dsputil.c:(.text+0x1c236): undefined reference to `ff_lpc_compute_autocorr'                               
collect2: ld returned 1 exit status                                                                       
make: *** [mplayer] Error 1  

```

There have been quite a few changes recently and hopefully this is the product of some of these changes, similar error seen on the arch forums. I have just compiled r29787 with no error, could you svn up and try again?

**Edit:** Oops talking crap again :). Compilation is fine on my *Slackware* partition but breaks with this error message on *Karmic*...

All the best,

Andrew

---

### Post by andrew.46 on 2009-10-20
Hi akeOutdoorsman,

> **FakeOutdoorsman said:**
> I too got this same error on 32-bit Arch Linux today.

But oddly enough not on my Slackware partition, while Karmic bombs out on the same revision... 

**Edit:** I think I see the problem, try compiling* without* disabling either MEncoder or MPlayer and the compilation will succeed.

Andrew

---

### Post by piousp on 2009-10-20
> **andrew.46 said:**
> Hi akeOutdoorsman,



But oddly enough not on my Slackware partition, while Karmic bombs out on the same revision... 

**Edit:** I think I see the problem, try compiling* without* disabling either MEncoder or MPlayer and the compilation will succeed.

Andrew

Nice! I'll try to compile it again. 
vdpau works really well on my home computer... i can watch 720p videos and the cpu barely notices it.

I just updated my work copy to revision 29787.
Now, lets compile this beast :)

Edit 2-
Alright! We have a successful compilation here! As you said, i did this:

./configure --cc=gcc-4.3 --confdir=/etc/mplayer  (without disabling mencoder)
Now, last step and i'll try it out ;)

Edit 3-
Have a look:

```

piousp@BOSON:~/Mis_cosas$ mplayer earthwormjimmp3.mp3
MPlayer SVN-r29787-4.3.4 (C) 2000-2009 MPlayer Team

Playing earthwormjimmp3.mp3.
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: Device or resource busy
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:  29.9 (29.9) of 60.0 (01:00.0)  0.9%

```

Now, lets get SMplayer and i'm done here! Thanks again!

By the way, i still have my home computer with jaunty, so we'll have to wait to see if vdpau still rocks in karmic!

---

### Post by jbernardo on 2009-10-20
I am building this mplayer, but with vaapi. I built libva from [here]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/"), and then got the vaapi patches from [here]("http://www.splitted-desktop.com/%7Egbeauchesne/mplayer-vaapi/"), applied them, and just followed this guide. Now my gma500 netbook can play 720p videos... :)

---

### Post by piousp on 2009-10-20
> **jbernardo said:**
> I am building this mplayer, but with vaapi. I built libva from [here]("http://www.splitted-desktop.com/%7Egbeauchesne/libva/"), and then got the vaapi patches from [here]("http://www.splitted-desktop.com/%7Egbeauchesne/mplayer-vaapi/"), applied them, and just followed this guide. Now my gma500 netbook can play 720p videos... :)

How did you applied them?? :o

---

### Post by cor2y on 2009-10-20
Ok a bit off topic, i followed the guide got mplayer-nogui installed.
So i decided why the heck not and attempted to compile a straight package of only mencoder so i did this
```
./configure --prefix=/usr --disable-mplayer  --extra-cflags=-fno-strict-aliasing
```
Everything worked but when i get to creating a deb package i get this error.
> checkinstall error trying to overwrite '/usr/share/man/man1/mplayer.1.gz', which is also in package mplayer-nogui
Anyway to fix this?

---

### Post by jbernardo on 2009-10-20
> **piousp said:**
> How did you applied them?? :o

I expanded the tarball with the patch in the dir above the mplayer svn dir, changed to the mplayer dir, and did ```
patch -p 1 < ../mplayer-vaapi.patch
```

Not that complicated... :)

---

### Post by andrew.46 on 2009-10-21
Hi piousp,

> **piousp said:**
> 

```
./configure --cc=gcc-4.3 --confdir=/etc/mplayer  (without disabling mencoder)
```


Just keep in mind that your copy of mencoder will be a little skimpy as I have not included the appropriate dev files for this. The break in compilation with *--disable-mencoder* is [an acknowledged problem]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-October/078017.html"), just a matter of waiting for a fix, this is usually only a couple of days in the making.

All the best,

Andrew

---

### Post by andrew.46 on 2009-10-21
Hi cor2y,

> **cor2y said:**
> Everything worked but when i get to creating a deb package i get this error.
```
checkinstall error trying to overwrite '/usr/share/man/man1/mplayer.1.gz', which is also in package mplayer-nogui 
```
Anyway to fix this?

This is a difficult one and I am not sure about the solution. There is only one set of man pages and programs like MEncoder and gmplayer have symlinks to it, this is set in the MPlayer Makefile. I could not see how to get around this issue at the moment.

Looks like the guide is on hold at the moment anyway as the ability to compile MPlayer without MEncoder is broken, hopefully only temporarily. But I cannot publish the guide away from the 'Karmic Koala Testing and Discussion' thread until this is resolved. Plus I guess the issue of the clashing man pages :).

Andrew

---

### Post by mc4man on 2009-10-21
while I don't use mencoder and I'm still in the habit of building mplayer as a package set (mplayer, mencoder, docs's ....

was thinking that if one was to build as here (checkinstall) with mencoder enabled and wanted mencoder to be seen as installed then maybe **[equivs]("http://packages.ubuntu.com/karmic/equivs")** could be used to build a dummy mencoder package with same version as the mplayer-gui built

So quickly built/installed a checkinstall mplayer-nogui and a dummy mencoder (**an equivs build**) , guess I'd have to test with something that uses mencoder, does show up as installed though 

Was also wondering if there's a reason for libswscale0 and -dev as build dep?

( am starting to find a couple of karmic apps that depend on mplayer or mplayer-nogui instead of mplayer | mplayer-nogui 
Will cause some people some aggravation

---

### Post by cor2y on 2009-10-22
While i dont know anything about building dummy packages with checkinstall , i was crudely able to get around the install problem by configuring mencoder's doc/man pages to /usr/local/share/man its not elegant and if you do "man mencoder" after the install you get these warnings
```
man: warning: /usr/local/share/man/man1/mencoder.1 is a dangling symlink
man: warning: /usr/local/share/man/man1/mencoder.1.gz is a dangling symlink
``` but the man page displays correctly.

---

### Post by andrew.46 on 2009-10-22
Hi mc4man,

> **mc4man said:**
> Was also wondering if there's a reason for libswscale0 and -dev as build dep?

Absolutely no reason at all, and I have removed them :). Some 2nd thoughts about this guide I will admit, at times I tire a little of battling with the package management system.....

Andrew

---

### Post by andrew.46 on 2009-10-22
Hi cor2y,

> **cor2y said:**
> 
```
man: warning: /usr/local/share/man/man1/mencoder.1 is a dangling symlink
man: warning: /usr/local/share/man/man1/mencoder.1.gz is a dangling symlink
``` 

I suspect you may be able to correct these warnings as follows:

```
$ sudo mv /usr/local/share/man/man1/mencoder.1 /usr/local/share/man/man1/mencoder.1_bak
$ sudo mv /usr/local/share/man/man1/mencoder.1.gz /usr/local/share/man/man1/mencoder.1.gz_bak
$ ln -s /usr/share/man/man1/mplayer.1.gz /usr/local/share/man/man1/mencoder.1.gz
```

and this would not be a problem if you have used the same MPlayer revision for *both* packages. It is a cumbersome way to do it but should work well enough. If this does not work for some reason you can of course restore the *_bak files and delete the symlink.

All the best,

Andrew

---

### Post by mc4man on 2009-10-23
Went ahead and used equivs, actully quite simple, takes about 30 secs
Tested by installing devede, worked out fine, it used the mencoder installed from the mplayer-nogui checkinstall
At it's simplest just install equivs
```
sudo apt-get install equivs
```

After the checkinstall is done, leave the terminal open to copy the version number
Ex. from build yesterday using this howto
Using a new terminal

```
mkdir dummymencoder && cd dummymencoder
```
```
equivs-control mencoder && gedit ./mencoder
```

edited the default control to this, matching blue to the mplayer-nogui version


> ### Commented entries have reasonable defaults.
### Uncomment to edit them.
Section: misc
Priority: optional
Standards-Version: 3.6.2

Package: mencoder
Version: [COLOR="Blue"]3:1.0~svn-r29789-1[/COLOR]
Depends: mplayer-nogui (=[COLOR="Blue"]3:1.0~svn-r29789-1[/COLOR])
Description: dummy mencoder 



Saved and closed gedit, then
```
equivs-build mencoder -a i386
```

(the -a i386  or -a amd64 probably isn't necessary, nor is making it a depend of specific mplayer-nogui, though a bit cleaner and easy to redo if building a new mplayer down the road

And then just install the .deb created

As far as the mencoder man deal I'd just remove those 2 links and then this if following the howto (mplayer-nogui installed to /usr/local

```
sudo ln -s /usr/[COLOR="Blue"]local[/COLOR]/share/man/man1/mplayer.1.gz /usr/local/share/man/man1/mencoder.1.gz
```

---

### Post by Kraust on 2009-10-23
I get

```
kraust@ubuntu:~$ mplayer
mplayer: error while loading shared libraries: libdirectfb-1.0.so.0: cannot open shared object file: No such file or directory
```

I've been trying to fix this for a while. Now. I just recompiled mplayer with your guide and I had no errors or anything. I also get this error if I get mplayer with Synaptic.

---

### Post by andrew.46 on 2009-10-23
Hi Kraust,

> **Kraust said:**
> I've been trying to fix this for a while. Now. I just recompiled mplayer with your guide and I had no errors or anything.

Good news :). I have just used this guide on a fresh copy of Karmic release candidate and all seems to be working well, the *--disable-mencoder* compilation error has been rectified with the current svn. So with any luck this guide will be ready for the avalanche of new karmic users in less than a week.

All the best,

Andrew

---

### Post by Kraust on 2009-10-23
No, no. I still have that problem. I'm trying to fix it.

I'm on an Upgrade from 9.04 (8.10 was the initial install if that matters). I haven't beeb able to get mplayer to work properly since I updated to 9.10.

Sorry, I have issues with explaining myself sometimes.

---

### Post by piousp on 2009-10-23
> **andrew.46 said:**
> Hi piousp,



Just keep in mind that your copy of mencoder will be a little skimpy as I have not included the appropriate dev files for this. The break in compilation with *--disable-mencoder* is [an acknowledged problem]("http://lists.mplayerhq.hu/pipermail/mplayer-users/2009-October/078017.html"), just a matter of waiting for a fix, this is usually only a couple of days in the making.

All the best,

Andrew

> **andrew.46 said:**
> Hi Kraust,



Good news :). I have just used this guide on a fresh copy of Karmic release candidate and all seems to be working well, the *--disable-mencoder* compilation error has been rectified with the current svn. So with any luck this guide will be ready for the avalanche of new karmic users in less than a week.

All the best,

Andrew

Excellent! I dont use mencoder, so its ok on my work box. So, when my home box gets karmic, i'll compile everything for it!!

Kudos for this guide Andrew!:KS

---

### Post by Zorael on 2009-10-23
The checkinstall line greps the svn revision from version.h, but that file isn't created until you run version.sh.

Other than that, it seems to be working so far. :3

---

### Post by andrew.46 on 2009-10-23
Hi Kraust,

> **Kraust said:**
> No, no. I still have that problem. I'm trying to fix it.

I'm on an Upgrade from 9.04 (8.10 was the initial install if that matters). I haven't beeb able to get mplayer to work properly since I updated to 9.10.

OIC :). Perhaps the upgrade path is the problem? For this guide the version of libdirectfb that you quote is wrong, this version is installed on an up to date Karmic:

```
/usr/lib/libdirectfb.so
/usr/lib/libdirectfb-1.2.so.0
/usr/lib/libdirectfb-1.2.so.0.7.0
```

So your copy is looking for an older version for some reason. I wonder if your /etc/apt/sources.list contains some mixed repositories. Can you post the terminal output of:

```
cat /etc/apt/sources.list
```

I will admit that I have never used the upgrade path, always a clean installation.

Andrew

---

### Post by Kraust on 2009-10-23
Here you go:

```
kraust@ubuntu:~$ cat /etc/apt/sources.list
# 

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ karmic main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ karmic-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ karmic universe
deb http://archive.ubuntu.com/ubuntu/ karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb http://archive.ubuntu.com/ubuntu/ karmic-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ karmic-security restricted main multiverse universe #Added by software-properties
deb http://archive.ubuntu.com/ubuntu/ karmic-security universe
# deb http://wine.budgetdedicated.com/apt karmic main #WineHQ - Ubuntu 9.10 "Karmic Koala"
deb http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu karmic main #Mozilla Repository - Ubuntu 9.10 "Karmic Koala"
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main

```

Neglect the Wine one, I totally half-edited that for when they actually put up a Karmic Repo.

**EDIT:** The 3 libdirectfb files mentioned are located in /usr/lib and the symbolic links aren't broken or anything. libdirectfb.so and libdirectfb-1.2.so.0 are symbolic links where the other isn't

---

### Post by andrew.46 on 2009-10-23
Hi Zorael,

> **Zorael said:**
> The checkinstall line greps the svn revision from version.h, but that file isn't created until you run version.sh.

But version.h *should* be created by the Makefile in the normal course of compilation and is subsequently deleted by *make distclean* which should be performed after the package is created and installed. I thought this was kind of neat actually :). This did not work in your case?

All the best,

Andrew

---

### Post by mc4man on 2009-10-23
@ Kraust
Seems there was some confusion in your other post on this, when I asked about upgrade vs. fresh I meant Karmic, I guess you thought mplayer..

As a small test of something, if you wish, go into synaptic, search mplayer and mark mplayer **and or** mplayer-nogui for complete removal. After applying then go mplayer in a terminal.
If anything shows up other than saying mplayer is not installed then post.

If it says there is no mplayer installed then install the mplayer-nogui .deb you built following this guide and then again run mplayer from a terminal.

---

### Post by Kraust on 2009-10-23
I Completely Removed mplayer-nogui, and tried to run mplayer. Said I needed to install mplayer (like it Should have)

I reinstalled the .deb from compiling the svn, I STILL get this error. I'm just going to give up for now until someone else gets it.

I don't think installing / removing mplayer is going to fix it as I've done it 100 times already, I think it's a problem with it looking for the older lib file when it should be looking for the newer one. My only thoughts is that I'd have to do a fresh install, which I'm not going to do until I get a new computer later this year (hopefully).

---

### Post by andrew.46 on 2009-10-24
Hi pious,

> **piousp said:**
> By the way, i still have my home computer with jaunty, so we'll have to wait to see if vdpau still rocks in karmic!

In a small management decision I have removed the repository vdpau libraries as on my non-NVidia system they were causing a few odd error messages on playback with MPlayer. It is a simple matter to add them in if you have the appropriate card or indeed get the newest drivers from NVidia. MPlayer will automagically pick up the libraries and enable vdpau output.

Andrew

---

### Post by andrew.46 on 2009-10-24
Hi Kraust,

I see you have rvm's PPA here:

> **Kraust said:**
> 
```
deb http://ppa.launchpad.net/rvm/mplayer/ubuntu karmic main
```


and to tell the truth rather than compiling up a storm here you might be better to download your MPlayer from there. It will be frequently updated and fits well with SMPlayer. I would suggest removing the mplayer-nogui package created in this guide and then simply running:

```
sudo apt-get install mplayer
```

Then can you run:
```

andrew@skamandros~$ **[COLOR="Red"]mplayer | head -n 1[/COLOR]**
MPlayer SVN-r29794-4.3.3 (C) 2000-2009 MPlayer Team
```

and this should show rvm's version. If the errors persist rvm may be able to assist with some resolution.

All the best,

Andrew

---

### Post by moreje on 2009-10-25
Hi all,
I have the rvm mplayer-mt (but the issue is the same with mplayer) installed on my new Karmic Koala.
I can't decode any movie using the command mplayer.... no video output , and the following errors:

```

[mkv] Track ID 1: video (V_MPEG4/ISO/AVC) "MPEG-4/AVC, 9222 kbps", -vid 0
[mkv] Track ID 2: audio (A_DTS) "DTS, 5.1, 1536 kbps (transcoded from LPCM)", -aid 0, -alang eng
[mkv] Track ID 3: subtitles (S_TEXT/***) "Hungarian", -sid 0, -slang und
[mkv] Track ID 4: subtitles (S_TEXT/***) "Italian", -sid 1, -slang und
[mkv] Track ID 5: subtitles (S_TEXT/***) "Polish", -sid 2, -slang pol
[mkv] Track ID 6: subtitles (S_TEXT/***) "Portuguese", -sid 3, -slang por
[mkv] Track ID 7: subtitles (S_TEXT/***) "Romanian", -sid 4, -slang rum
[mkv] Track ID 8: subtitles (S_TEXT/***) "Serbian", -sid 5, -slang scc
[mkv] Track ID 9: subtitles (S_TEXT/***) "Slovenian", -sid 6, -slang slv
[mkv] Track ID 10: subtitles (S_TEXT/***) "Spanish", -sid 7, -slang spa
[mkv] Track ID 11: subtitles (S_TEXT/***) "Swedish", -sid 8, -slang swe
[mkv] Track ID 12: subtitles (S_TEXT/***) "Turkish", -sid 9, -slang tur
[mkv] Track ID 13: subtitles (S_TEXT/***) "Brazilian", -sid 10, -slang por
[mkv] Track ID 14: subtitles (S_TEXT/***) "Croatian", -sid 11, -slang scr
[mkv] Track ID 15: subtitles (S_TEXT/***) "Czech", -sid 12, -slang cze
[mkv] Track ID 16: subtitles (S_TEXT/***) "Danish", -sid 13, -slang dan
[mkv] Track ID 17: subtitles (S_TEXT/***) "Dutch", -sid 14, -slang dut
[mkv] Track ID 18: subtitles (S_TEXT/***) "English", -sid 15, -slang eng
[mkv] Track ID 19: subtitles (S_TEXT/***) "Finnish", -sid 16, -slang fin
[mkv] Track ID 20: subtitles (S_TEXT/***) "French", -sid 17, -slang fre
[mkv] Track ID 21: subtitles (S_TEXT/***) "German", -sid 18, -slang ger
[mkv] Will play video track 1.
Matroska file format detected.
VIDEO:  [avc1]  1920x800  24bpp  23.976 fps    0.0 kbps ( 0.0 kbyte/s)
Can't open /dev/fb0: No such file or directory
[fbdev2] Can't open /dev/fb0: No such file or directory
VO: [v4l2] No such file or directory
vo_cvidix: No vidix driver name provided, probing available ones (-v option for details)!
[cyberblade] Error occurred during pci scan: Operation not permitted
[mach64] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[mga] Error occurred during pci scan: Operation not permitted
[nvidia_vid] Error occurred during pci scan: Operation not permitted
[pm3] Error occurred during pci scan: Operation not permitted
[radeon] Error occurred during pci scan: Operation not permitted
[rage128] Error occurred during pci scan: Operation not permitted
[s3_vid] Error occurred during pci scan: Operation not permitted
[SiS] Error occurred during pci scan: Operation not permitted
[unichrome] Error occurred during pci scan: Operation not permitted
[VO_SUB_VIDIX] Couldn't find working VIDIX driver.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Requested audio codec family [dts] (afm=libdca) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 1536.0 kbit/100.00% (ratio: 192000->192000)
Selected audio codec: [ffdca] afm: ffmpeg (FFmpeg DTS)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 2.40:1 - prescaling to correct movie aspect.
VO: [null] 1920x800 => 1920x800 Planar YV12 


```sound is OK... but no video.
Smplayer works...vlc works...
Any ideas?
Thanks for your help
J.

---

### Post by Kraust on 2009-10-25
For some reason, I had to install libdirectfb-1.0,so I don't know why but that worked, (Even if I had 1.2)


So if anyone ever gets this problem from upating Jaunty to Karmic (becayse Karmic uses 1,2 and Intrepid / Jaunty use 1.0) than that's the answer.

Not this keep on uninstalling / reinstalling crap.

---

### Post by viking_maniac on 2009-10-27
Thank you so much, andrew.46, for your kind contributions! :)

You mentioned in _[COLOR=Red][this thread]("http://ubuntuforums.org/showthread.php?t=1287143&page=2")[/COLOR]_ that in Karmic the relevant libopencore-amr libraries are held in the repository. Could this mean that my problem is solved regarding playback of amr files *with* sound?

---

### Post by andrew.46 on 2009-10-27
Hi viking,

> **viking_maniac said:**
> You mentioned in _[COLOR=Red][this thread]("http://ubuntuforums.org/showthread.php?t=1287143&page=2")[/COLOR]_ that in Karmic the relevant libopencore-amr libraries are held in the repository. Could this mean that my problem is solved regarding playback of amr files *with* sound?

The libraries are certainly there but as far as I know no software in the Karmic repository has been compiled against libopencore-amr, although I am ready to be proved wrong :). Certainly this guide enables amr sound.

Andrew

---

### Post by viking_maniac on 2009-10-28
> **andrew.46 said:**
> Certainly this guide enables amr sound.

I don't doubt it. It just looks a bit frighting to a newcomer like me.

---

### Post by andrew.46 on 2009-10-28
Hi viking,

> **viking_maniac said:**
> I don't doubt it. It just looks a bit frighting to a newcomer like me.

This section of the forums will be read-only shortly (Karmic comes out today) but there is a short window of time to mention that I believe RVM's MPlayer also enables amr sound, but don't quote me on this one :). This would be a far easier option than compiling as I describe.

All the best,

Andrew

---

