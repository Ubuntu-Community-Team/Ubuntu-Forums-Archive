---
title: "Vlc 0.9.2"
date: 2008-09-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ace214 on 2008-09-15
New version of VLC out... The site is being sporatic but [this mirror]("http://vlc.mirrors.adc.am/vlc/0.9.2/") has the source and a new features video.

Any chance of this getting into Intrepid?

---

### Post by Nullack on 2008-09-15
Ask MOTU

---

### Post by talkingwires on 2008-09-15
From the [changelog]("http://www.videolan.org/developers/vlc/NEWS"):> Brand new interface for Linux and Windows, based on the Qt toolkitThat might put a damper on things. IMHO, Amarok and VLC are two of the best media player options for Linux, and now both are QT based. 

When Intrepid drops, I may give Kubuntu a whirl to see if they've tweaked KDE4 into a usable environment. I last tried 4.0 with Open SuSE, and that was a nightmare. Personally, I think they should've used the release of Amarok 2.0 as the benchmark for releasing KDE 4.0.

---

### Post by ace214 on 2008-09-15
> **talkingwires said:**
> From the [changelog]("http://www.videolan.org/developers/vlc/NEWS"):That might put a damper on things. IMHO, Amarok and VLC are two of the best media player options for Linux, and now both are QT based.
If you watch the video they show off a GTK interface and a QT interface, so I think that the QT interface is just new *in addition* to the GTK interface.

---

### Post by TheMono on 2008-09-15
Request for freeze exception filed here:
[https://bugs.edge.launchpad.net/ubuntu/+source/vlc/+bug/270404](https://bugs.edge.launchpad.net/ubuntu/+source/vlc/+bug/270404)

---

### Post by Nullack on 2008-09-15
You dont say why, only that you believe so. Perhaps:

* Not part of the default install
* Brings many bug fixes
* Brings new functionality such as new demuxers and decoders

---

### Post by Starks on 2008-09-15
Just a reminder: VLC 0.9.2 is useless unless libass is compiled in.

---

### Post by Nullack on 2008-09-15
And ffmpeg is updated, which I was advised by Reinhard wont happen for Intrepid.

One of the things I dont like about VLC is how it does have libavcodec statically linked to SVN like mplayer does - an mplayer compile from SVN is also an ffmpeg svn compile by default.

Anyway - gstreamer is good tech. Some plugins were updated in Intrepid for gstreamer.

---

### Post by chacham23 on 2008-09-15
Looks great! is it in the rep' allready?
I tried and in package manger it still 0.8.6..

---

### Post by dakira on 2008-09-15
Oh man. VLC ist just the best player. Can't wait to get my hands on some debs. This beast is not easily packaged ;)

---

### Post by MadMan2k on 2008-09-15
> **ace214 said:**
> If you watch the video they show off a GTK interface and a QT interface, so I think that the QT interface is just new *in addition* to the GTK interface.
no, its both Qt; they just use the new Qt GTK Style, which integrates nicely.

---

### Post by forteller on 2008-09-15
This has been in development for more than two years. That means a ton of bugfixes and whatnot. It would be a shame if it doesn't get in Ubuntu repositories for another six months!

---

### Post by meborc on 2008-09-15
> **forteller said:**
> This has been in development for more than two years. That means a ton of bugfixes and whatnot. It would be a shame if it doesn't get in Ubuntu repositories for another six months!

i have one word for you - backports ;)

oh, and probably getdeb also, whenever the dependencies are resolved

---

### Post by munky99999 on 2008-09-15
There has been a security issue/advisory with VLC. So really they should be updating the repositories.

Hopefully the fullscreen thing was fixed with vlc.

---

### Post by Starks on 2008-09-15
> **dakira said:**
> Oh man. VLC ist just the best player. Can't wait to get my hands on some debs. This beast is not easily packaged ;)

I will vehemently attest to this as VLC tester for this releaser.

---

### Post by meborc on 2008-09-15
> **Starks said:**
> I will vehemently attest to this as VLC tester for this releaser.

so you are saying it is hard to do, but can still be done? any howto's?

(had to search for those fancy words in dictionary) :D

---

### Post by forteller on 2008-09-15
> **meborc said:**
> i have one word for you - backports ;)

oh, and probably getdeb also, whenever the dependencies are resolved

Yeah, that works all well and good for me. But how about all the total Linux newbies that we plan to give a taste of freedom and the awesomeness of the next version of Ubuntu? Telling them to enable backports or go install three packages (in the right order) from getdeb is just not good enough!

---

### Post by Starks on 2008-09-15
> **meborc said:**
> so you are saying it is hard to do, but can still be done? any howto's?

(had to search for those fancy words in dictionary) :D
esoteric dependencies make for a difficult deb building. normal compiling is rather simple though.

---

### Post by meborc on 2008-09-15
> **forteller said:**
> Yeah, that works all well and good for me. But how about all the total Linux newbies that we plan to give a taste of freedom and the awesomeness of the next version of Ubuntu? Telling them to enable backports or go install three packages (in the right order) from getdeb is just not good enough!

linux newbies will probably use totem anyway, as that is the default player... or if they are lucky, they will install mplayer... but for sure they will not miss any of the new features even if they install vlc... as vlc works just fine now...

ubuntu includes a lot of up-to-date programs... just look at what debian stable is shipping ;)

---

### Post by AaronMT on 2008-09-15
Has anyone compiled VLC 0.9.2?

Just curious what libraries are required for the compile? I tried looking on the videolan website but it did not list.

Thanks in advance,

AaronMT

---

### Post by llelectronics on 2008-09-15
You have to install this is you want to build a vlc deb easily:

```
sudo apt-get install autoconf automake build-essential libtool checkinstall libdbus-1-dev libmad0-dev libavcodec-dev libavformat-dev libpostproc-dev liba52-dev libfribidi-dev libqt4-dev
```

---

### Post by andrewsomething on 2008-09-15
> **munky99999 said:**
> There has been a security issue/advisory with VLC. So really they should be updating the repositories.

While, I too want to see the new vlc in Intrepid, this isn't a completely true claim. While we have an older version of vlc in the repo, security patches have been continuously applied. Just look at the [_changelog_]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/v/vlc/vlc_0.8.6.release.h-1ubuntu1/changelog") for the Ubuntu package.

If you know of a security issue/advisory that has not been addressed, please file a bug report as soon as possible. Even if the new version doesn't get in, security patches can be backported to the version in the archive.

---

### Post by munky99999 on 2008-09-15
> **andrewsomething said:**
> While, I too want to see the new vlc in Intrepid, this isn't a completely true claim. While we have an older version of vlc in the repo, security patches have been continuously applied. Just look at the [_changelog_]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/v/vlc/vlc_0.8.6.release.h-1ubuntu1/changelog") for the Ubuntu package.

If you know of a security issue/advisory that has not been addressed, please file a bug report as soon as possible. Even if the new version doesn't get in, security patches can be backported to the version in the archive.

well repositories are 8.6e

The security advisory says 

Affected versions : VLC media player 0.8.6i and earlier

ABCDFGHIE isnt the alphabet I know.

Though; VLC media player 0.9.1 addresses these issues. Patches for VLC media player 0.8.6 are available from the official VLC source code repository. 

So you may be entirely correct. I have no idea. :( Imma keep my eye on getdeb and this thread for a deb. Toooo lazy to compile anything.

---

### Post by SigmundFreud on 2008-09-15
This blog entry: [http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html](http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html) gives instructions and a link to a repository. I guess someone could try it.

---

### Post by dualpretop on 2008-09-15
VLC 0.9.2 - Hardy(KDE 4.1)

[[IMG]http://img176.imageshack.us/img176/5025/444aa444xj4.th.jpg[/IMG]](http://img176.imageshack.us/my.php?image=444aa444xj4.jpg)

Upgrade 0.9.0 on 0.9.2

sudo apt-get install autoconf automake build-essential libtool checkinstall libdbus-1-dev libmad0-dev libavcodec-dev libavformat-dev libpostproc-dev liba52-dev libfribidi-dev libqt4-dev

[http://vlc.mirrors.adc.am/vlc/0.9.2/vlc-0.9.2.tar.bz2](http://vlc.mirrors.adc.am/vlc/0.9.2/vlc-0.9.2.tar.bz2)

cd ...
./configure --prefix=/usr
make
sudo make install

---

### Post by krul on 2008-09-15
> **SigmundFreud said:**
> This blog entry: [http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html](http://blog.jetienne.com/2008/09/vlc-092-on-ubuntu-804.html) gives instructions and a link to a repository. I guess someone could try it.

Works for me ;)

Very nice!

---

### Post by mgsfan on 2008-09-15
same as above works for me

---

### Post by KuriKai on 2008-09-15
Could some one compile it for 64bit hardy?

---

### Post by Starks on 2008-09-15
I prefer the following config line.

./configure --prefix=/usr --enable-faad --enable-libass

Be sure to install the dev packages faad and libass beforehand.

---

### Post by SigmundFreud on 2008-09-15
> **mgsfan said:**
> same as above works for me

I tried it but it just reinstalled the 'old' version. Any ideas?

---

### Post by aidave on 2008-09-15
> **SigmundFreud said:**
> I tried it but it just reinstalled the 'old' version. Any ideas?

Ditto.  Running 64 bit tho, that might be why ... probably no 64bit version yet.

---

### Post by devcon101 on 2008-09-15
I also installed from the blog posting, and have not had any noticeable problems.

That being said, my initial impression with this release is 'impressed'.  I think it has just replaced both totem and audacious in one swoop.  It seems quick, accurate, and of course, full of options.  The music options still leave a bit to be desired, but they said it will be improved in future releases.  It kind of froze up with no progress bar when adding about 25 gigs of music to the library, but after loading, no problems.

I think it has even surpassed my previous favorite, KMPlayer on Windows.

Edit:  Another comment, it seems to freeze occasionally when changin options while something is playing.  No big deal though.

---

### Post by Starks on 2008-09-15
btw, the ppa has now has libass (styled subtitles) enabled for the hardy dist.

[https://edge.launchpad.net/~c-korn/+archive](https://edge.launchpad.net/~c-korn/+archive)

---

### Post by darweth on 2008-09-15
> **aidave said:**
> Ditto.  Running 64 bit tho, that might be why ... probably no 64bit version yet.

Not running 64bit here.  Just reinstalled the old version too. :/  Hmmm.

Well, I went through the process again and this time it was a success. HMMMM.

---

### Post by MRiGnS on 2008-09-15
> **ace214 said:**
> If you watch the video they show off a GTK interface and a QT interface, so I think that the QT interface is just new *in addition* to the GTK interface.

It's QT4 now, it's not an addition. VLC actually never had a GTK interface. It used wxwidgets and some sort of wrapper.

Now it's the first time that it uses one of the two big toolkits natively, which is a good thing in every aspect. QT4 is also the best way to offer good looks in both QT and GTK environments, as QT wrappers for GTK pretty much don't work as good as the other way around.

---

### Post by bash on 2008-09-15
Hmm the PPA sadly only has .debs for Hardy (although those also as 64bit). Anyone have any .debs for intrepid?

---

### Post by inportb on 2008-09-15
A KDE user like me would be pleased at the resource savings =p

Anyway, I'm disappointed that there are no AMD64 packages for me.

> **MRiGnS said:**
> VLC actually never had a GTK interface. It used wxwidgets and some sort of wrapper.

I believe the Linux port of wxWidgets is also known as wxGTK. I wonder why it's named that way if it isn't GTK, hmmm?

---

### Post by Starks on 2008-09-15
> **bash said:**
> Hmm the PPA sadly only has .debs for Hardy (although those also as 64bit). Anyone have any .debs for intrepid?

The Hardy debs work if you have libpostproc1d installed.

[http://packages.ubuntu.com/hardy-updates/libpostproc1d](http://packages.ubuntu.com/hardy-updates/libpostproc1d)

---

### Post by Nullack on 2008-09-16
Theres a big difference between "works" and "works properly" for testers who have more than a casual look at VLC compiles.

The key is having an ffmpeg SVN compile fed into it.

---

### Post by thomasboleyn on 2008-09-16
Has anyone managed to get this to work on feisty?

---

### Post by plun on 2008-09-16
> **TheMono said:**
> Request for freeze exception filed here:
[https://bugs.edge.launchpad.net/ubuntu/+source/vlc/+bug/270404](https://bugs.edge.launchpad.net/ubuntu/+source/vlc/+bug/270404)

Added security issues to the bug

[http://secunia.com/advisories/product/7788/?task=advisories_2008](http://secunia.com/advisories/product/7788/?task=advisories_2008)

CVE-2008-3732
CVE-2008-3794
CVE-2008-2430

the 0.8.6h version is totally borked...

[https://wiki.ubuntu.com/SecurityUpdateProcedures](https://wiki.ubuntu.com/SecurityUpdateProcedures)

---

### Post by zi99y on 2008-09-16
These packages work fine for me on Hardy:

[http://yabblog.com/2008/09/16/updating-vlc-to-092-for-ubuntu-users/](http://yabblog.com/2008/09/16/updating-vlc-to-092-for-ubuntu-users/)

---

### Post by olavjunior on 2008-09-16
> **zi99y said:**
> These packages work fine for me on Hardy:

[http://yabblog.com/2008/09/16/updating-vlc-to-092-for-ubuntu-users/](http://yabblog.com/2008/09/16/updating-vlc-to-092-for-ubuntu-users/)

Well, I couldn't get any sound, so I removed it right away. I don't quite trust repos like that..

But why can't I never get checkinstall to work??? I always get an error about a file missing in the end, after successful ./configure and make.... I don't like using sudo make install cause I don't know how to remove things if they don't work out right. 

And by the way, what's the thing with the qt-dev lib? Does the old vlc also use that much qt??

---

### Post by nandemonai on 2008-09-16
> **olavjunior said:**
> Well, I couldn't get any sound, so I removed it right away. I don't quite trust repos like that..

But why can't I never get checkinstall to work??? I always get an error about a file missing in the end, after successful ./configure and make.... I don't like using sudo make install cause I don't know how to remove things if they don't work out right. 

And by the way, what's the thing with the qt-dev lib? Does the old vlc also use that much qt??

Worked fine for me. Very nice additions. Especially the subtitle rendering. I'm in anime heaven now. :D

---

### Post by conanrealm on 2008-09-16
for all those who doesn't want to compile anything, you can use the nightly repos from videolan.
[http://nightlies.videolan.org/#debian]("http://nightlies.videolan.org/#debian")

VLC rocks :guitar:

---

### Post by inportb on 2008-09-16
Dude, thanks for that link. Intrepid 1386 and amd64 are on the list as well =D

---

### Post by kempfjb on 2008-09-16
> **ace214 said:**
> If you watch the video they show off a GTK interface and a QT interface, so I think that the QT interface is just new *in addition* to the GTK interface.



Well, NO. The Gtk Interface is the Qt Interface with the new QGtkStyle package that is available since Qt 4.4.

So you can have a native look and feel.

Btw, I am a developer of VLC.

---

### Post by kempfjb on 2008-09-16
> **Starks said:**
> Just a reminder: VLC 0.9.2 is useless unless libass is compiled in.

Libass has entered Intrepid IIRC.

---

### Post by kempfjb on 2008-09-16
> **Nullack said:**
> And ffmpeg is updated, which I was advised by Reinhard wont happen for Intrepid.

One of the things I dont like about VLC is how it does have libavcodec statically linked to SVN like mplayer does - an mplayer compile from SVN is also an ffmpeg svn compile by default.

Anyway - gstreamer is good tech. Some plugins were updated in Intrepid for gstreamer.

This is WRONG, WRONG, FUD.

VLC doesn't link statically to FFmpeg. VLC links dynamically to libavcodec.so.
The version of FFmpeg in Intrepid, if correctly compiled (--enable-swscaler, option recommanded by FFmpeg since more than 1year and a half) will make VLC work perfectly.

You don't need a special version of FFmpeg for VLC.

What I just said in that bug is that some crash from launchpad will be fixed with a newer FFmpeg than the old one in 7.10.

---

### Post by kempfjb on 2008-09-16
> **devcon101 said:**
> I also installed from the blog posting, and have not had any noticeable problems.

That being said, my initial impression with this release is 'impressed'.  I think it has just replaced both totem and audacious in one swoop.  It seems quick, accurate, and of course, full of options.  The music options still leave a bit to be desired, but they said it will be improved in future releases.  It kind of froze up with no progress bar when adding about 25 gigs of music to the library, but after loading, no problems.

I think it has even surpassed my previous favorite, KMPlayer on Windows.

Edit:  Another comment, it seems to freeze occasionally when changin options while something is playing.  No big deal though.

Can you tell me how to reproduce.
A known bug is if you change audio device while playing that could freeze.

---

### Post by SigmundFreud on 2008-09-16
I'm using KDE 3.5.9 and haven't been able to use fullscreen mode. Part of the screen goes grey and I have to do a 'kwin --replace' to get things back to normal. VLC uses the Xvideo extension and changing the output to something else (e.g., X11) mostly means a crash/hang. I'm not using any window effects. It was the same with the previous versions of VLC. Annoying -- any ideas?

---

### Post by Starks on 2008-09-16
Does VLC 0.9.2 require the use of ffmpeg SVN to work properly?

---

### Post by kempfjb on 2008-09-16
> **Starks said:**
> Does VLC 0.9.2 require the use of ffmpeg SVN to work properly?

FFmpeg is always SVN. :D

Any FFmpeg from less than one year will be enough, if correctly compiled (--enable-gpl --enable-pp --enable-swscaler AS FFmpeg advise it)

---

### Post by t_k on 2008-09-16
> **dualpretop said:**
> VLC 0.9.2 - Hardy(KDE 4.1)

[[IMG]http://img176.imageshack.us/img176/5025/444aa444xj4.th.jpg[/IMG]]("http://img176.imageshack.us/my.php?image=444aa444xj4.jpg")

Upgrade 0.9.0 on 0.9.2

sudo apt-get install autoconf automake build-essential libtool checkinstall libdbus-1-dev libmad0-dev libavcodec-dev libavformat-dev libpostproc-dev liba52-dev libfribidi-dev libqt4-dev

[http://vlc.mirrors.adc.am/vlc/0.9.2/vlc-0.9.2.tar.bz2](http://vlc.mirrors.adc.am/vlc/0.9.2/vlc-0.9.2.tar.bz2)

cd ...
./configure --prefix=/usr
make
sudo make install

Thanks man. Worked great on Kubuntu KDE 4.1.1

WOW!!! The flickering problems with video and the ATI drivers are totally gone with the new VLC! WTF! \\:D/ No need to turn off the desktop effects for watching video anymore.

---

### Post by devcon101 on 2008-09-16
> **kempfjb said:**
> Can you tell me how to reproduce.
A known bug is if you change audio device while playing that could freeze.

I could not reproduce it consistently. I did notice that changing audio options does in fact cause a freeze when music is playing.  Inconsistently, it also freezes when changing some of the interface options.  Only occasionally it will freeze when I change, for example, the 'one instance' option.  Obviously there is another factor as it is not everytime.

I also installed from the repository posted on the blog.  It could be the compile.

Additionally, I found this post on google when searching for a vlc .deb, and did not realize it was the Intrepid testing forum.

Hardy 32bit on a P4M, 756MB RAM, GeForce 4

Edit:  I don't know if it is a bug, but the Media Library window will not save the position of the headings.  ie. If I add the artist column, it will dissappear when reloading vlc.

---

### Post by ghindo on 2008-09-16
> **kempfjb said:**
> Libass has entered Intrepid IIRC.Sure has.

[http://packages.ubuntu.com/intrepid/libass1](http://packages.ubuntu.com/intrepid/libass1)

---

### Post by MaX on 2008-09-16
I'm running 0.9.2 in Vista right now and I'd tell you to wait until 0.9.2.1 is released.

They still have some issues with the playslist and menu's getting stuck in fullscreen.

---

### Post by bash on 2008-09-16
> **kempfjb said:**
> FFmpeg is always SVN. :D

Any FFmpeg from less than one year will be enough, if correctly compiled (--enable-gpl --enable-pp --enable-swscaler AS FFmpeg advise it)

Nice that a VLC dev drops by here and helps out. Btw is the vlc firefox plugin getting to anything useable again. Last time I tried in both Windows and Linux it was completly borked.

---

### Post by gibarian on 2008-09-16
> **t_k said:**
> Thanks man. Worked great on Kubuntu KDE 4.1.1

WOW!!! The flickering problems with video and the ATI drivers are totally gone with the new VLC! WTF! \\:D/ No need to turn off the desktop effects for watching video anymore.

And that's exactly why I switched to Gnome when 8.04 came out. Can't believe I endured the whole flickering problem for so long.

---

### Post by kempfjb on 2008-09-16
> **MaX said:**
> I'm running 0.9.2 in Vista right now and I'd tell you to wait until 0.9.2.1 is released.

They still have some issues with the playslist and menu's getting stuck in fullscreen.


Well, no, this is just a Windows issue... Fullscreen controllers are very well working on Linux.

---

### Post by kempfjb on 2008-09-16
> **bash said:**
> Nice that a VLC dev drops by here and helps out. Btw is the vlc firefox plugin getting to anything useable again. Last time I tried in both Windows and Linux it was completly borked.

When you fix it.

Well, it should be more stable. But no guarantee.

---

### Post by munky99999 on 2008-09-16
So I tried the nightly build amd64 and the damn thing wont install because the versions on the dependancies are bad.

vlc:
 Depends: vlc-nox but it is not going to be installed
  Depends: libcaca0 (>=0.99.beta14-1) but 0.99.beta13b-4 is to be installed
  Depends: libcucul0 (>=0.99.beta14-1) but 0.99.beta13b-4 is to be installed
 Depends: libqtcore4 (>=4.4.0) but it is not installable
 Depends: libqtgui4 (>=4.4.0) but it is not installable

Which I have but I dont have the beta14-1 for those 2 top.

Not a rush or anything. I'm happy with what I have now I guess.

---

### Post by nelsonm on 2008-09-16
Hi all,

I installed VLC 0.9.2.

Looks great except that clicking on the "Open File" or "Open Directory" does not recognize network paths or places so i can't access video files on my windows server. It only accesses local files.

Does anyone know how to fix that?

---

### Post by Nullack on 2008-09-16
> **kempfjb said:**
> FFmpeg is always SVN. :D

Any FFmpeg from less than one year will be enough, if correctly compiled (--enable-gpl --enable-pp --enable-swscaler AS FFmpeg advise it)

I dont agree. In particular there has been massive improvements to H.264 / AVC decoding in recent ffmpeg history thats resolves numerous problems.

---

### Post by SilverDrake11 on 2008-09-16
i had a very hard time installing this without compiling it myself. im running hardy 64bit.

following the instructions [here]("http://yabblog.com/2008/09/16/updating-vlc-to-092-for-ubuntu-users/") did not work for me; all it did was reinstalling it and gave me a bunch of errors. however, this worked for me perfectly and if any of you are having trouble installing it follow these steps:

1. completely remove the old version of vlc

```
sudo apt-get remove vlc vlc-nox
sudo apt-get autoremove
```2. add the 2 lines (depending on whether you have hardy or intrepid) to your sources list (the first 2 are hardy and the next 2 are intrepid)

```
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main
```
```
deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) intrepid main
```(I found those entries [here]("https://launchpad.net/%7Ec-korn/+archive"))

3. install vlc 0.9.2
```
sudo apt-get reload
sudo apt-get install vlc vlc-nox
```let me know if this worked for you....

---

### Post by Starks on 2008-09-16
Is the repo ffmpeg new enough?

---

### Post by Nullack on 2008-09-16
> **Starks said:**
> Is the repo ffmpeg new enough?

I dont consider it so, no. If you look up the package you will see how old it is. Compare that to the CVS mailing list for ffmpeg since which lists every change being made to ffmpeg SVN.

---

### Post by devveloper on 2008-09-17
works like :popcorn:

---

### Post by paulle on 2008-09-17
VLC 0.92 works great here. (amd64 hardy).

---

### Post by morfeasrev on 2008-09-17
anyway to find a repo that does not include other packages like wine?
I already get wine from the official repo and do not want this one...

---

### Post by ubu-for on 2008-09-17
> **thomasboleyn said:**
> Has anyone managed to get this to work on feisty?

I'm a rookie in compiling and would need a guidance, an additional mirror for my source.list or a .deb file for Feisty, too.

[quote=VLC Website]Ubuntu Gutsy Gibbon 7.10,
Ubuntu Feisty Fawn 7.04

Graphical way

Open Synaptic (System -> Administration -> Synaptic Package Manager). In Settings -> Repositories, make sure you have a "universe" repository activated.

Search for vlc and install it. You should also install vlc-plugin-esd, mozilla-plugin-vlc (and libdvdcss2).

Command line way

You need to check that a "universe" mirror is listed in your /etc/apt/sources.list.

    % sudo apt-get update
    % sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc[/quote]

Doesn't work!

Thanks for your help!

---

### Post by forteller on 2008-09-17
I successfully installed 0.9.2 with the guide in the blogpost that was linked to earlier ([http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main).

But yesterday Update Manager pushed out an update to vlc, libass, and some other VLC related packages I can't remember, and now VLC crashes the moment it starts.

Running VLC from terminal gives me the error message "Segmentation fault". Help?

---

### Post by devcon101 on 2008-09-17
> **forteller said:**
> I successfully installed 0.9.2 with the guide in the blogpost that was linked to earlier ([http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main).

But yesterday Update Manager pushed out an update to vlc, libass, and some other VLC related packages I can't remember, and now VLC crashes the moment it starts.

Running VLC from terminal gives me the error message "Segmentation fault". Help?

The same thing happened to me when I upgraded from that repository.  But, it was only the first time I tried to open vlc.  Now it works fine in general, but it spits out a number of error messages such as "cannot read from file" when playing songs however it is in fact playing the song.

I'm not sure if it is my music or another factor, but the sound is inconsistent when playing flac files.  I need to do some more testing to determine if it is the encoding, but MP3's do play fine apart from the error message stated above.

---

### Post by SilverDrake11 on 2008-09-17
forteller and devcon, did you add both lines to your sources list from "http://ppa.launchpad.net/c-korn/ubuntu hardy main" or just the one? if you didnt add both, try removing vlc and reinstalling it with both lines added to your sources list (i listed them on pg 7 of this post).

---

### Post by forteller on 2008-09-17
SilverDrake: Thanks for the tip, but I tried it and it's still the same problem!

---

### Post by ferossan on 2008-09-17
> **SilverDrake11 said:**
> forteller and devcon, did you add both lines to your sources list from "http://ppa.launchpad.net/c-korn/ubuntu hardy main" or just the one? if you didnt add both, try removing vlc and reinstalling it with both lines added to your sources list (i listed them on pg 7 of this post).

I successfully installed 0.9.2 (using both lines) under Hardy
Just a couple of issues:
1) Searching updates (via Help menu) crashes VLC
2) Subtitles do not works well; not possible to change font, color or perfil.

Is it just me?

---

### Post by SilverDrake11 on 2008-09-17
yea i have the same problem with searching updates. subtitles work well, but i havent tried changing font or colors or anything. i guess we'll just have to wait for the official release......

---

### Post by mgsfan on 2008-09-17
the updated version does'nt crash on my system after installed

---

### Post by itkeepsrepeating on 2008-09-18
I got 0.9.2 installed, and it's working awesome. Having one issue. I see they moved the 'services discovery' to the regular preferences menu, found after checking 'all' under 'show settings' box. Unfortunately, shoutcast tv is not showing under services discovery on mine. Anyone else having this problem? Is there a manual way to enable it via the line under the checkboxes?

---

### Post by colo505 on 2008-09-18
[http://igloo.dreamnid.com/wp/dreamnid/?p=298](http://igloo.dreamnid.com/wp/dreamnid/?p=298)

---

### Post by PRGUY85 on 2008-09-18
It works for me yet I can't get any sound  out of DVDs or movies with AC3 encoding.  I could do this before.  Any thoughts?

---

### Post by TheMono on 2008-09-18
Is this as in decoded on the PC, or passed through SPDIF? If the latter, I have the same issue - but I did with the old VLC as well.

---

### Post by PRGUY85 on 2008-09-18
> **TheMono said:**
> Is this as in decoded on the PC, or passed through SPDIF? If the latter, I have the same issue - but I did with the old VLC as well.

Decoded on PC.

---

### Post by kyleabaker on 2008-09-19
Will VLC be getting an upgrade in Intrepid? It was released only a few days ago, but I thought it would have upgraded by now. Still using v0.8.6h and the new features and layout in v0.9.2 look great.

I'm just hoping it will make it into Intrepid. :D

---

### Post by olskar on 2008-09-19
Check out [http://ubuntuforums.org/showthread.php?t=920204](http://ubuntuforums.org/showthread.php?t=920204)

---

### Post by rbmorse on 2008-09-19
You can build it from source, or getdeb.net has the binaries. Works OK for me in Hardy. For Intrepid you'll have to do some dependency chasing to install all of the getdeb.net packages

---

### Post by Sef on 2008-09-19
Merged threads.

---

### Post by xlinuks on 2008-09-20
Hi,
recently there's been a significant update to VLC (from version 0.8 to 0.9), until it's not too late I wonder whether this version would be included into Intrepid.
I found out more info about the new set of features at:
[http://www.heise.de/english/newsticker/news/116009](http://www.heise.de/english/newsticker/news/116009)

---

### Post by mike1234 on 2008-09-20
> **xlinuks said:**
> Hi,
recently there's been a significant update to VLC (from version 0.8 to 0.9), until it's not too late I wonder whether this version would be included into Intrepid.
I found out more info about the new set of features at:
[http://www.heise.de/english/newsticker/news/116009](http://www.heise.de/english/newsticker/news/116009)

 Apparently not since Intrepid has been "frozen" pending release next month. Here is a link about installing source though.

[http://ubuntuforums.org/showthread.php?t=920204&page=3&highlight=vlc](http://ubuntuforums.org/showthread.php?t=920204&page=3&highlight=vlc)

M.

---

### Post by forteller on 2008-09-20
I got VLC 0.9.2 working again by using Synaptic to remove it completely and installing it again.

---

### Post by psyke83 on 2008-09-20
> **xlinuks said:**
> Hi,
recently there's been a significant update to VLC (from version 0.8 to 0.9), until it's not too late I wonder whether this version would be included into Intrepid.
I found out more info about the new set of features at:
[http://www.heise.de/english/newsticker/news/116009](http://www.heise.de/english/newsticker/news/116009)

Please, check the forum before making new posts. There's a VLC thread being discussed extensively, linking to SRUs requests and testing packages.

---

### Post by mike1234 on 2008-09-20
> **psyke83 said:**
> Please, check the forum before making new posts. There's a VLC thread being discussed extensively, linking to SRUs requests and testing packages.

 Take your pick.

[http://ubuntuforums.org/search.php?searchid=48307463](http://ubuntuforums.org/search.php?searchid=48307463)

M.

---

### Post by Rocket2DMn on 2008-09-20
Threads merged.

---

### Post by PRGUY85 on 2008-09-20
Does anyone know how to get the AC3 decoder to work?  I can't get AC3 sound with VLC 0.92 and on the repositories version I get same sound through all speakers, not true 5.1.  I have an onboard card with snd-hda-intel drivers.  I have an X-FI too but that only does 2.1 under Linux.

---

### Post by jlh on 2008-09-20
I installed v.0.9.2 on Hardy using the instructions in Thread #65 above.  The update works nicely for audio CDs and video files.  However. I can't play DVDs.  I get isolated frames from the DVD.  Although the progress bar seems to move, the video does not play - that is, the frame shown does not change.

Ideas?

By the way, despite several tries with the installation approach described in #65, vlc on my drop-down Applications>Sound and Video menu continued to be the prior version, and if I type vlc at the command line, that's what launches.  However. v.0.9.2 lives as usr>bin.  Therefore, setting that to launch from the App dropdown gets me to the new version.  The old one is still there; plays DVDs fine.

---

### Post by plun on 2008-09-20
> **PRGUY85 said:**
> Does anyone know how to get the AC3 decoder to work?  I can't get AC3 sound with VLC 0.92 and on the repositories version I get same sound through all speakers, not true 5.1.  I have an onboard card with snd-hda-intel drivers.  I have an X-FI too but that only does 2.1 under Linux.

I found this and I am unsure about real AC3 decoding

[http://ubuntuforums.org/showthread.php?t=795525](http://ubuntuforums.org/showthread.php?t=795525)

---

### Post by BwackNinja on 2008-09-20
I could never get anything beyond stereo with vlc and PulseAudio. If you supply the command line option --alsa-device=surround51 then you should have 5.1 sound, same for surround40 4.0 sound, etc. But that doesn't work for trying to route through PulseAudio, only ALSA. Mplayer will play 5.1 well though (-channels=6 for 5.1, -channels=4 for 4.0, etc), and even through PulseAudio. You can confirm there with pavumeter.

What's annoying is that VLC has soooo much better handling of DVD menus... (especially considering that support exists without having to recompile)

---

### Post by PRGUY85 on 2008-09-21
So how should I open Mplayer to get true 5.1?  You talk about inputing command line options.  How so?

---

### Post by ronacc on 2008-09-21
built and runs good on intrepid 64bit , I did have to install libgcrypt-dev in addition to the other stuff noted on page 3 of this thread to get ./configure to complete but once that was added it built smoothly .

---

### Post by BwackNinja on 2008-09-21
> **PRGUY85 said:**
> So how should I open Mplayer to get true 5.1?  You talk about inputing command line options.  How so?

open a terminal (or the run dialog will work too) and type:
```
gmplayer your_file -channels 6
```
where your_file is the file you want to play

```
gmplayer dvd:// -channels 6
```
is probably what you'd want because it mostly only matters for dvds anyway.

You can add "channels 6" to your mplayer config too (I haven't messed with that in a while) so you don't have to run mplayer from the command line.

---

### Post by meborc on 2008-09-21
> **ronacc said:**
> built and runs good on intrepid 64bit , I did have to install libgcrypt-dev in addition to the other stuff noted on page 3 of this thread to get ./configure to complete but once that was added it built smoothly .

i did the same with intrepid 32bit... 

only problem is in full screen mode... the screen is black and the video plays in upper left corner with original size :( **EDIT: some files play nice... some don't... i have to look more into why ;)**

too bad... i guess i'm back to 8.6

---

### Post by kyleabaker on 2008-09-21
> **meborc said:**
> too bad... i guess i'm back to 8.6
Same here..for now. (0.8.6) :(

---

### Post by ronacc on 2008-09-21
hmm I see what you mean , I just happened to pick a couple that did play fullscreen to try it with .

---

### Post by meborc on 2008-09-21
> **ronacc said:**
> hmm I see what you mean , I just happened to pick a couple that did play fullscreen to try it with .

have you noticed any method in this mayhem? :D why some files play fullscreen and some don't?

---

### Post by ubu-for on 2008-09-22
> **colo505 said:**
> [http://igloo.dreamnid.com/wp/dreamnid/?p=298](http://igloo.dreamnid.com/wp/dreamnid/?p=298)

Thanks colo505!

---

### Post by plun on 2008-09-24
> **meborc said:**
>  why some files play fullscreen and some don't?

Well, I only have a few movies and they all plays in full screen.

x11 and x264 seems to be updated today.

I used this test ppa for VLC 0.9.2 install

[https://edge.launchpad.net/~motumedia/+archive](https://edge.launchpad.net/~motumedia/+archive)


The mozilla plugin is just great for watching different "dirty" stuff. :)

```
sudo apt-get remove totem-mozilla && sudo apt-get install mozilla-plugin-vlc
```

Restart browser.... Have Fun !

---

### Post by plun on 2008-09-25
VLC did it...:)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007590.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007590.html)

 * New Upstream Release, exception granted

The mozilla plugin is just great after further testing...

---

### Post by BobCFC on 2008-09-25
> **plun said:**
> Well, I only have a few movies and they all plays in full screen.

x11 and x264 seems to be updated today.

I used this test ppa for VLC 0.9.2 install

[https://edge.launchpad.net/~motumedia/+archive](https://edge.launchpad.net/~motumedia/+archive)


The mozilla plugin is just great for watching different "dirty" stuff. :)

```
sudo apt-get remove totem-mozilla && sudo apt-get install mozilla-plugin-vlc
```

Restart browser.... Have Fun !



Thanks this worked for me in Intrepid Ibex 64bit

Tried a few films quickly and no fullscreen issues, even on 720p

---

### Post by Starks on 2008-09-25
0.9.3 might be granted an exception as well...

---

### Post by ghindo on 2008-09-26
I just got VLC 0.9.2 through the Intrepid repos - was it in backports?

---

### Post by talkingwires on 2008-09-26
> **ghindo said:**
> I just got VLC 0.9.2 through the Intrepid repos - was it in backports?I think it's a bit early for the Intrepid backport repo to be open. :)

It just landed in my mirror's repo, too. I'm letting it install with my nightly dist-upgrade to try it out. But I still find it funny that this thread started with people hoping and pleading for 0.9.2 to be included in Intrepid, and now there's all these posts from people complaining of problems and downgrading. Be careful what you ask for! Especially when you want to break feature freeze.

---

### Post by mc4man on 2008-09-27
Just did a fresh updated install of alpha 6. As far as vlc and dvds, while intrepid takes care of adding vlc to mimeapps for you, (autorun, r. click open with on dvd icon), the default launch command can still be a problem.
If you're having *any difficulties* with commercial dvds from the auto run or r. click - open with, change the launch command of vlc from vlc %U to vlc %m.
Change in  edit menus -> sound & video -> properties of vlc


Edit: I'd change it as a matter of course. %m is the superior launch command in 0.9.2 as it was in .8.6 (7.10, 8.04 and 8.10


Edit : while I use amarok as default audio cd player I noticed vlc is added to the list. *At least here* when using  the default %U the cd doesn't playback at all. Using %m allows playback but on any cd with 10 or more tracks vlc will start on track 10.
A temp. workaround is to create an alternate choice for audio cd player (vlc cd player) with an Exec=  of Exec=vlc cdda:///dev/scd[COLOR="Red"]0[/COLOR] (obviously only works with one device, Tried ....../dev/scd* which works with 2 drives but reverts to the track 10 thing

---

### Post by UbuWu on 2008-09-27
0.9.3 with lots of bugfixes might make it into intrepid. If anyone wants to help testing, see here and report any problems you find or bugs it fixes:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/274721](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/274721)

---

### Post by kyleabaker on 2008-09-28
> **UbuWu said:**
> 0.9.3 with lots of bugfixes might make it into intrepid. If anyone wants to help testing, see here and report any problems you find or bugs it fixes:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/274721](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/274721)

I just got the update for VLC 0.9.3! The changelog is pretty good and it's currently running with no problems. :D

---

### Post by MALEADt on 2008-09-30
One bug left though: the "m3u-extvlcopts" option has magically disappeared... I really hope this gets fixed before release, will make a launchpad entry about it later on.

---

