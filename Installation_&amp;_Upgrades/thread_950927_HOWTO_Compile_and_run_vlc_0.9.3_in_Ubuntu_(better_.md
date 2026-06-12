---
title: "HOWTO: Compile and run vlc 0.9.3 in Ubuntu (better than 0.9.4)"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by Neo_The_User on 2008-10-17
**_PLEASE NOTE: THIS IS VERY SIMILAR TO [http://ubuntuforums.org/showthread.php?t=924887](http://ubuntuforums.org/showthread.php?t=924887) EXCEPT THIS IS A MUCH MORE CLEAN GUIDE MAKING IT SIMPLY BETTER ALONG WITH NO VIOLATIONS OF THE GNU LICENSE! I DEEPLY APOLOGIZE FOR NOT FOLLOWING THROUGH WITH THE GNU PUBLIC LICENSE!_**

You might be tired of vlc 0.9.4 and up with the extended video pop-up instead of built-in embedded video with no external screen. It is simple, quick, and easy to change it all back the way it was. Follow my numbered instructions in this little step-by-step guide on compiling, making, and running VLC 0.9.3 the way it was. **_DO NOT_**type what is in parenthesis :lolflag:

(I am currently building a debian package for vlc 0.9.3)

1.) Download the tar.bz2 source for vlc 0.9.3 here:

[http://download.videolan.org/pub/videolan/vlc/0.9.3/vlc-0.9.3.tar.bz2](http://download.videolan.org/pub/videolan/vlc/0.9.3/vlc-0.9.3.tar.bz2)

2.) Extract the folder within the tar.bz2 file to a directory of your choice. :guitar:

3.) Open up a Terminal

```

sudo apt-get build-dep vlc

sudo apt-get install cvs build-essential subversion git git-core automake1.9 libtool libgcrypt-dev libfaad-dev libtwolame-dev libqt4-dev libjack-dev libxpm-dev libcddb2-dev liblua5.1-0-dev libzvbi-dev libshout-dev

```

Now for the fun part (sureeeeeee)

4.) Make sure you are in the root directory of the vlc-0.9.3 folder

```

./bootstrap

cd extras/

git clone git://git.videolan.org/x264.git

cd x264

make

sudo make install

cd ..

cd ..

mkdir build

cd build

```

(If it says that ../configure is not a directory or something then replace "../configure --prefix=/usr \" with "./configure --prefix=/usr \" except without quotes)

```

../configure --prefix=/usr \

```

```

--enable-snapshot --enable-debug \
--enable-dbus-control --enable-musicbrainz \
--enable-shared-libvlc --enable-mozilla \
--enable-lirc \
--with-ffmpeg-tree=../extras/ffmpeg \
--enable-x264 --with-x264-tree=../extras/x264 \
--enable-shout --enable-taglib \
--enable-v4l \
--enable-dvb \
--enable-realrtsp --disable-xvmc \
--enable-svg --enable-dvdread \
--enable-dc1394 --enable-dv \
--enable-theora --enable-faad \
--enable-twolame --enable-real \
--enable-flac --enable-tremor \
--enable-skins2 --enable-qt4 \
--enable-ncurses \
--enable-aa --enable-caca \
--enable-esd --disable-portaudio \
--enable-jack --enable-xosd \
--enable-galaktos --enable-goom \
--enable-ggi \
--disable-cddax --disable-vcdx \
--disable-quicktime --enable-lua \
--disable-live555

```

Now open up a graphical file browser such as nautilus and go inside the vlc-0.9.3. Browse to the modules folder. Now inside the codec folder, there should be an x264.c file (the speex.c file actually became messed up in vlc 1.0 making it a pain in the arsenal as in my other thread but luckily, vlc 0.9.3 doesn't require a re-programmed speex.c file as well)

Replace the x264.c file with the code on this pastebin.ca link located here:

[http://pastebin.ca/1313703](http://pastebin.ca/1313703)

Copy and paste all the source code in the box and save it in the modules/codec folder as x264.c and click "replace" or you can replace the x264.c file many different ways of your choice. It doesn't matter.

After replacing the x264.c file with the partially re-programmed file, go back into the terminal (or open a new one if you closed it up) and cd to the directory located in /vlc-0.9.3/build

```

make
sudo make install

```

***YOU ARE NOW DONE WITH COMPILING***

To launch vlc, go inside the vlc folder you compiled everything in yada yada yada. Inside the build folder, double click on vlc. Click on run. Boom!

*****END OF GUIDE*****

If you have any problems related to compiling vlc and need a specific .c file to be fixed, please post your exact problem and all make errors so I can make a fix. It will take 1 - 3 days depending on the amount of files and the amount of complexity for a complete fix to be made to meet your expectations. Please leave feedback, comments, and or questions and I will do my best to assist you. Thank you for your patience.

---

### Post by The_OMFG on 2008-10-17
WTF:confused:

---

### Post by Neo_The_User on 2008-10-17
> **The_OMFG said:**
> WTF:confused:

Is there a problem?

---

### Post by The_OMFG on 2008-10-17
It looks like vlc 0.9.3 will never be the way it was. I just compiled it and ran it, noticed a lot of bugs.

---

### Post by Neo_The_User on 2008-10-17
> **The_OMFG said:**
> It looks like vlc 0.9.3 will never be the way it was. I just compiled it and ran it, noticed a lot of bugs.

I am making a .deb package for this. Who wants to compile anything anyway? I'll be making a .deb package shortly of vlc 0.9.3 and let gedbi install it for you. Debian package will be avaliable to all users of vlc 0.9.3 shortly. Thank you The_OMFG for stating your problem. I have noticed some bugs myself. After all, it is a shell script rather than a full actual program. Debian package will be made. Thanks again! :)

---

### Post by slumbergod on 2008-10-17
I'd be grateful for some debs for 0.9.3

The upgrade to 0.9.4 broke so much and, unfortunately, I no longer have the 0.9.3 debs. Nor can I find them on the net. 

I really liked 0.9.x and when I can get a stable 0.9.3 installed I will lock that version!

---

### Post by Neo_The_User on 2008-10-17
> **slumbergod said:**
> I'd be grateful for some debs for 0.9.3

The upgrade to 0.9.4 broke so much and, unfortunately, I no longer have the 0.9.3 debs. Nor can I find them on the net. 

I really liked 0.9.x and when I can get a stable 0.9.3 installed I will lock that version!

I'm still working on it. It might be a few days for me to figure out how to generate one. Sit tight for a few days. This is my first time making a .deb package so any assistance for generating .deb packages would be helpful for me and as a result, help everybody who wants the good old stable version of vlc (0.9.3) so any tips or hints would be greatly appreciated. Feel free to make your own .deb packages and post the links to them here.

---

### Post by bionnaki on 2008-10-17
or just do it the easy way: [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

that repo has version 094.

---

### Post by Neo_The_User on 2008-10-17
> **bionnaki said:**
> or just do it the easy way: [http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/](http://tombuntu.com/index.php/2008/09/16/install-vlc-media-player-092-in-ubuntu/)

that repo has version 094.

0.9.3 is what this is all about. The older version works better.

---

### Post by bionnaki on 2008-10-18
then use apt-get to select the version you want.

sudo apt-get install vlc=0.9.3

or so.

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

---

### Post by slumbergod on 2008-10-18
So far as I can tell, the repo that Tombuntu refers to no longer has 0.9.3
It only has 0.9.4 which is the source of so many problems for us. Since there are no other obvious repos online with 0.9.3 the only other option is to build it. That is the whole point of this thread.

---

### Post by Neo_The_User on 2008-10-20
> **slumbergod said:**
> So far as I can tell, the repo that Tombuntu refers to no longer has 0.9.3
It only has 0.9.4 which is the source of so many problems for us. Since there are no other obvious repos online with 0.9.3 the only other option is to build it. That is the whole point of this thread.

Making a .deb package is difficult for me. Can I have some assistance? Some name of a program? I'm using checkinstall and I'm noticing some problems. Will checkinstall even build a .deb package for me or does it just check stuff?

---

### Post by slumbergod on 2008-10-22
Yeah, that is why I haven't had a crack at building this myself. Most source code is easy to compile. vlc apparently has lots of obscure libraries that you wouldn't normally have so it isn't a job for beginners. 

I am surprised that there are not more people who are after 0.9.3. Maybe the old version in the repositories is enough for people. I get frustrated with 0.8.6 because it allows multiple instances and when you go to load a subtitle it makes you start the whole movie again. 

Hopefully, 0.9.5 will hopefully correct the major bugs plaguing 0.9.4

---

### Post by Neo_The_User on 2008-10-25
> **slumbergod said:**
> Yeah, that is why I haven't had a crack at building this myself. Most source code is easy to compile. vlc apparently has lots of obscure libraries that you wouldn't normally have so it isn't a job for beginners. 

I am surprised that there are not more people who are after 0.9.3. Maybe the old version in the repositories is enough for people. I get frustrated with 0.8.6 because it allows multiple instances and when you go to load a subtitle it makes you start the whole movie again. 

Hopefully, 0.9.5 will hopefully correct the major bugs plaguing 0.9.4

No. 0.9.4 and up will never have the video inside the window again. However, after switching debian, 0.8.6h4 fixed everything that 0.8.6e had. I'll give you a deb package. It might mess up all your repositories and your system by an unknown degree so please back up all your data before using gdebi. The .deb will be avaliable shortly.

(If only vlc would keep building on 0.9.3 instead of going down a whole new road)

Another thing I can do is re-program 0.9.4 and mix 0.9.3 and 0.9.4 togethor and do something like that. I have lots of ideas. I don't know what I'm going to do. Give me some time. I think about this all the time. As far as compiling goes, that isn't the hard part. I just don't know the actual steps on making a deb package. If I have a problem with a file, I'll make it work. Easy as pie. Re-programming and changing some code around no biggie. It's not that its hard for me and I'm not really a beginner either. I just don't know the steps on how to do it. I'm lost. If I had like a general outline of making a deb package, I could do it. I just don't know where to start. Once I get started, I'll finish it. If I only knew more about software besides programming languages and command line.

---

### Post by cariboo on 2008-10-25
I don't know if this will help with your deb building problem, but have your tried checkinstall, in stead of using the make command? CHeckinstall is available in the repositories.

Jim

---

### Post by Neo_The_User on 2008-10-25
> **cariboo907 said:**
> I don't know if this will help with your deb building problem, but have your tried checkinstall, in stead of using the make command? CHeckinstall is available in the repositories.

Jim

So checkinstall WILL make me a deb package. Thanks Jim!

---

### Post by mc4man on 2008-10-26
Version 0.9.5 has been released and again embedded video has been disabled. I'm running built versions of both 0.9.3 and 0.9.5 (embedded enabled) on hardy and don't see much difference issue wise from either. (0.9.5 is reported to fix 'some' things
I think the best way atm for either ver. is to build on ones own machine for any number of reasons, one of which is you can test or run without installing. 
Just run it from the build folder, you can create a launcher, add it to the apps. menu, set it as default auto run player, create file associations, ect.

If you want to build and try 0.9.5 with embedded enabled it's very simple to do, 1 line needs to be changed in vlc-0.9.5/modules/gui/qt4/qt4.cpp at line 216 (may show as 217

Orig.

```
#ifdef WIN32   [COLOR="Red"]<-[/COLOR]
    add_submodule();
        set_capability( "vout window", 50 );
        set_callbacks( WindowOpen, WindowClose );
#endif
vlc_module_end();

```

change to 

```
#if !defined (Q_WS_X11) || defined HAS_QT43
    add_submodule();
        set_capability( "vout window", 50 );
        set_callbacks( WindowOpen, WindowClose );

```

Obviously they've disabled it for a reason but I've had no issues myself.
(I've found some things that don't work right but they are seen in 0.9.2 -> 0.9.5 embedded or not.


Just for the hell of it I took the korn ppa 0.9.5 release and redid it with embedded enabled and built the normal package. While I'm not using it on my main box  quickly testing on another machine it seemed to do ok. 
I'll post a link here if anyone wants to test it out.

Note that you should have the korn ppa for hardy enabled as a third party source so any missing deps will be installed.

Also note that I built it on a machine that isn't the 'normal' hardy install lib wise so no assurance it will be completely right, more to try out. _I still think one is better off building they're own._

With the korn ppa enabled, his version will be considered an upgrade, so beware of updates. 

When I built it I also built all the dep and plugins packages but i'm not going to upload those so this .deb is only good to install while the necessary packages are available from korn in this version # (vlc-nox, libvlc0, vlc-plugin-pulse - 0.9.5+x264snapshot20080928+faad2.6.1-1~ppa1 (or already saved on hdd

to add ppa- change drop down to hardy
[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive) 

for vlc 0.9.5 embedded  (again no promises
<removed link> korn ppa has reverted to 0.9.3 - why i don't know, 0.9.3 with embedded enabled is just as likely to cause problems, has the same flaws as any ver. w/ embedded, and certainly is buggier than 0.9.5 otherwise

---

### Post by Neo_The_User on 2008-10-26
Sorry. I've been really busy lately. Yeah... I currently can't build a .deb package right now for Ubuntu 8.04 since I was trying to get DRI working in Debian and compiling my custom version of mesa on my computer (for my personal use only sorry) so I'm going to push this vlc project of mine off for awhile. If anybody wants to try solving everybodies problems with vlc, go ahead and take a swing.

Best regards,

Neo_The_User Playstation 3 developer.

---

### Post by jar72 on 2008-11-02
I'm new to ubuntu, but if I wanted to remove this version of vlc how would I go about doing it?

Doing the add/remove thing doesn't work because vlc isn't "installed".  Any help would be appreciated.

---

### Post by Neo_The_User on 2008-11-02
jar72, use Synaptic Package Manager from System > Administration. Do a search for vlc in Synaptic. Click on the little green square next to vlc and hit remove or complete removal. (I would do complete removal even though Synaptic does a terrible job of uninstalling apps. I usually do everything by hand.)

OK Just wanted to let you all know, I downloaded vlc 1.0.0 and I got embedded video and everything that you all wanted... working. Bad news, it was on Debian sid. I just installed Ubuntu 8.10 2 nights ago. I am currently using the version of vlc from the repository (0.9.4) and its terrible.

I diagnosed why running vlc right after you compiled it runs terribly. It doesn't build vlc-nox and all that other stuff. It just makes an executable. It's really really buggy. I fixed all the source files in vlc to build a .deb package. It will be ready soon (however long that'll be)

Sorry for the inconvenience.

P.S. My .deb package that I will be making might not have x264 for awhile.

-Neo_The_User

---

### Post by jar72 on 2008-11-02
Thanks for the quick reply and your work.

I went into System > Administration > Synaptic and searched for VLC, but there aren't any green squares next to any of the vlc items. I used the method you described in the first post to install vlc 0.9.3.

---

### Post by Neo_The_User on 2008-11-02
I'm pretty sure you don't have it installed then. If you are building vlc by following my guide, it isn't "installed" so don't worry about it. It's just an executable. Took me awhile to figure out why it still has so many bugs (the custom built one) but I'm working on a deb package. I switched to 8.10 but I'll go back soon. This is just really really boring for me so I'm kind of taking my time.

---

### Post by Neo_The_User on 2008-11-07
OK NEW UPDATE!!!

After about 3 fresh installs of Ubuntu 8.10 and installing vlc 0.9.4 FROM THE OFFICIAL UBUNTU REPOSITORIES, I got a different result on the third try. The window of the visualization, movie playback, whatever I was watching, would be in the window. THE EXACT SAME VERSION! Installed Debian Lenny/sid about 6 times and it always worked the way I wanted it to except on the first time. I also messed with my computer a lot (on the third time of 8.10 only) and got my ATi card lightning quick with many many tweaks related to X11, mesa, xorg etc etc. I'd like to dig into this further but I've been quite busy lately.

---

### Post by Neo_The_User on 2008-11-10
vlc 0.9.3 deb package has been generated. However, it won't work. "vlc: error while loading shared libraries: libvlc.so.2: cannot open shared object file: No such file or directory"

I know you probably have a lot of questions. Give me some more time. I might have this working in a week or so. This is so complicated because the vlc developers can't write good C code without spelling something wrong or doing something stupid. I always have to modify their stupid misspelled code and waste my time fixing their dumb mistakes. I'm fed up again with this vlc project so I'll be taking a nice long break.

At least I can do a fresh install of Ubuntu 8.10 and use vlc 0.9.4 with perfectly good embedded video without a new window popping up.

---

### Post by Sagoober on 2009-07-07
For anybody still looking for a solution to this, I found this link

[http://webupd8.blogspot.com/2009/05/install-vlc-10-rc-in-ubuntu-from-ppa.html](http://webupd8.blogspot.com/2009/05/install-vlc-10-rc-in-ubuntu-from-ppa.html)

so far it is working beautifully for me.  Reminds me of why I loved vlc in the first place so many years ago.

---

