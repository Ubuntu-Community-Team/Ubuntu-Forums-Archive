---
title: "XBMC for Lucid (It says for Karmic or higher?)"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by schwabdale on 2010-04-16
I have done what they said on their site, but it does not show up in my package manager. 
Is XBMC available for Lucid yet?

---

### Post by schwabdale on 2010-04-16
Can someone do a test install on Lucid and let me know if it works?

---

### Post by Chromagnum on 2010-04-16
I don't know about fresh Lucid installation nor about fresh XBMC installation on Lucid, but I've been using XBMC since Karmic. And since I've upgraded Karmic to Lucid (now beta 2), XBMC running perfectly fine; no error, no crash, no sound trouble nor video stutering or anything really.

---

### Post by Atermoon on 2010-04-16
I used the karmic deb from the ppa two weeks ago and it worked fine. Not sure if it still does since I reinstalled several times since then but I guess it should.

---

### Post by dannyboy79 on 2010-04-17
i am trying to compile from SVN and it won't build. I keep getting:
configure: error: Could not find a required library. Please see the README for your platform.

i went through the README.linux and checked for all the dependencies and it still won't configure. Any help please.

---

### Post by Rob2687 on 2010-04-17
Use this PPA
[https://launchpad.net/~team-xbmc-svn/+archive/ppa](https://launchpad.net/~team-xbmc-svn/+archive/ppa)

---

### Post by JohnnyC35 on 2010-04-18
> **Rob2687 said:**
> Use this PPA
[https://launchpad.net/~team-xbmc-svn/+archive/ppa]("https://launchpad.net/%7Eteam-xbmc-svn/+archive/ppa")

hmmm. I added that but I still don't have xbmc in my Synaptic list and cannot install it from the terminal.

oh
there is no xbmc package for lucid yet:
[http://ubuntuforums.org/showthread.php?t=1450723&highlight=xbmc+lucid](http://ubuntuforums.org/showthread.php?t=1450723&highlight=xbmc+lucid)

---

### Post by dannyboy79 on 2010-04-18
> **JohnnyC35 said:**
> hmmm. I added that but I still don't have xbmc in my Synaptic list and cannot install it from the terminal.

oh
there is no xbmc package for lucid yet:
[http://ubuntuforums.org/showthread.php?t=1450723&highlight=xbmc+lucid](http://ubuntuforums.org/showthread.php?t=1450723&highlight=xbmc+lucid)

which is why I was trying to compile it from source.

---

### Post by petejk on 2010-04-18
I used the karmic ppa
also had to add the ubuntu karmic repo (main and universe) to my sources so a couple of libraries could be installed (libcdio7 libfaad0)

Seems to be working fine

---

### Post by l.capriotti on 2010-04-19
> **JohnnyC35 said:**
> 
there is no xbmc package for lucid yet:
[http://ubuntuforums.org/showthread.php?t=1450723&highlight=xbmc+lucid](http://ubuntuforums.org/showthread.php?t=1450723&highlight=xbmc+lucid)

pls check again:

[XBMC Lucid Packages]("https://edge.launchpad.net/~team-xbmc-svn/+archive/ppa?field.series_filter=lucid")

---

### Post by dannyboy79 on 2010-04-19
> **l.capriotti said:**
> pls check again:

[XBMC Lucid Packages]("https://edge.launchpad.net/~team-xbmc-svn/+archive/ppa?field.series_filter=lucid")

Are you saying this because you actually used it or just because you found it??????
that's been there since 3-1-10 and if you notice it does NOT build properly. See the RED "X" for the lucid xbmc package?

[https://edge.launchpad.net/~team-xbmc-svn/+archive/ppa/+packages](https://edge.launchpad.net/~team-xbmc-svn/+archive/ppa/+packages)

---

### Post by Aenima99x on 2010-04-19
> **dannyboy79 said:**
> Are you saying this because you actually used it or just because you found it??????
that's been there since 3-1-10 and if you notice it does NOT build properly. See the RED "X" for the lucid xbmc package?

[https://edge.launchpad.net/~team-xbmc-svn/+archive/ppa/+packages](https://edge.launchpad.net/~team-xbmc-svn/+archive/ppa/+packages)

Ummm yeah :roll: ....maybe he's saying it because he is one of the XBMC Devs. If it errored out during the SVN compile looking for a dependency, then the last line should say which it needs and is not installed.

---

### Post by dannyboy79 on 2010-04-19
well it doesn't say what package is required. it only says that one of the required libraries is missing and that I should read the README for my platform. WHich I did, i went through and installed most (maybe not all) of the files per the README.linux. I was just hoping there was a PPA that had downloadable deb. or at least a PPA that I could run the build-dep against for xbmc or xbmc-common. I guess I haev to wait a little longer.

---

### Post by Novae on 2010-04-20
Dannyboy, what is the line right above the missing dependency one? Something to do with libSDL-mixer?

I was able to compile the svn fine the other day but have been unable to due to this error for some time now, i've installed both libsdl-mixer and the dev libraries and neither has any effect.

---

### Post by Novae on 2010-04-20
Actually, scrap that, it seems by doing a reinstall of all the base SDL audio packages i was able to get passed that configure stop.

---

### Post by dannyboy79 on 2010-04-20
the last line is this:
checking for main in -lGL... no

and doing a search within aptitude or synaptic, I find nothing with this in the name

---

### Post by Novae on 2010-04-20
Thats sounds like libGL to me, at least based on the naming pattern normally used in configure scripts. Although i'd assume you'd already have it installed.

It could be libgl1-mesa but that seems to be tightly linked to the desktop. Possibly try 'aptitude reinstall libgl1-mesa-dev'

---

### Post by dannyboy79 on 2010-04-20
ok, i added the karmic launchpad ppa for xbmc shown here:
[https://launchpad.net/~team-xbmc/+archive/ppa?field.series_filter=karmic](https://launchpad.net/~team-xbmc/+archive/ppa?field.series_filter=karmic)
i then added the key.
i then ran ```
sudo apt-get build-dep xbmc
```
and it appeared to install all libraries and dependencies.
but I still got this error when running ./configure:
checking for main in -lmicrohttpd... no
so I then did ```
sudo aptitude install libmicrohttpd-dev libmicrohttpd5 micro-httpd
```
then i ran it again and got this:
checking for main in -lmodplug... no
so I did this ```
sudo aptitude install libmodplug-dev
```
and ran ./configure again.
I get this when it's all done compiling:
Debugging:	Yes
  Profiling:	No
  Crosscomp.:	No
  target ARCH:	no
  target CPU:	no
  Optimization:	Yes
  OpenGL:	Yes
  VDPAU:	Yes
  VAAPI:	No
  CrystalHD:	No
  Joystick:	Yes
  XRandR:	Yes
  GOOM:		No
  PCRE Support:	Yes
  MID Support:	No
  ccache:	No
  PulseAudio:	Yes
  FAAC:		Yes
  DVDCSS:	Yes
  Avahi:	Yes
  Non-free:	Yes
  ASAP Codec:	No
  Webserver:	Yes
  Deprecated libdts:	No
  Deprecated liba52:	No
  External Libraries:	No
  External FFmpeg:	No
  External liba52:	No
  External libdts:	No
  External libass:	No
  External Python:	No
  prefix:	/usr/local

i then ran ```
make -j2
```
it did it's thing.

i'll be back

ok, im back. IT WORKED!!!!!!!!
I have some things to figure out but at least xbmc started up. for some reason there are no default scrapers setup. i am wondering if I was suppose to ./configure it with some options?

NEVERMIND, can't figure it out. I have no option for setting content withinthe video sources I added nor are there any default scrapers. I wonder if it's because I downloaded a tar.gz from here: [http://sourceforge.net/projects/xbmc/files/XBMC%20Source%20Code/Camelot%20-%209.11/xbmc-9.11.tar.gz/download](http://sourceforge.net/projects/xbmc/files/XBMC%20Source%20Code/Camelot%20-%209.11/xbmc-9.11.tar.gz/download)
instead of building from svn.

---

