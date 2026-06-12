---
title: "Mono 1.2.6 &amp; Ubuntu 7.10"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by andrewvk on 2008-01-16
How can I install mono 1.2.6 in gutsy release?

---

### Post by emperon on 2008-01-16
> **andrewvk said:**
> How can I install mono 1.2.6 in gutsy release?

unfortunately ubuntu maintainers are ignorant to back port mono packages. So you have two choices.

use the binary installer from mono downloads page (will install Gtk# 2.8 which won't run tomboy)

or compile it from source (fairly easy)

---

### Post by SonicSteve on 2008-01-17
How do you get mono to work with Firefox? Any ideas?

---

### Post by emperon on 2008-01-18
> **SonicSteve said:**
> How do you get mono to work with Firefox? Any ideas?

I actually am not sure if I understood the question correctly. Firefox is a browser. it renders html and javascript. You mean moonlight  ?

---

### Post by SonicSteve on 2008-02-05
Hi there,
Sorry it's been so long. Yes I mean moonlight. I guess I'm confused about how moonlight and mono work together. I installed mono thinking that it would allow firefox to use silverlight video. It would seem I was wrong. 

So really my question is about Moonlight in firefox.

---

### Post by SonicSteve on 2008-02-05
OK I found this how to;
I have not tried it yet, I will when I have some free time at home. It does not seem to be a simple process and some people have had problems with it. Perhaps it might be a place to start though. 
USE AT OWN RISK!!!!

[PHP] Hello All,
          I've spent some time messing with silverlight on feisty, and
have some notes I wrote down while getting it to work. See if these
help. They replace the built in mono stack with one from svn, and
install everything needed from svn.

Let me know if it works for you guys.

--Chris Hamons

Install Ubuntu 7.4 onto your test machine or VMware image. [link
http://www.ubuntu.com/getubuntu/download]
Update using build in updater.
        This prepares a base to build our moonlight stack upon. Any ubuntu
7.4 machine could be used here instead.
sudo apt-get update
sudo apt-get install subversion
mkdir mono
cd mono
svn co svn://anonsvn.mono-project.com/source/trunk/mcs
svn co svn://anonsvn.mono-project.com/source/trunk/mono
svn co svn://anonsvn.mono-project.com/source/trunk/gtk-sharp
svn co svn://anonsvn.mono-project.com/source/trunk/gnome-sharp
svn co svn://anonsvn.mono-project.com/source/trunk/olive
svn co svn://anonsvn.mono-project.com/source/trunk/moon
svn co svn://anonsvn.mono-project.com/source/trunk/monodoc
sudo apt-get install libavcodec0d libavformat0d libgtk2.0-dev libnspr-
dev firefox-dev libavcodec-dev libavformat-dev libasound2-dev librsvg2-
dev
sudo apt-get install autoconf automake libtool build-essential bison
sudo apt-get install prevu
        Little bit of explanation here. One of the required libraries
(libswscale-dev) does not exist under 7.4. 7.10 has a copy, but it's
not part of the traditional backports repository. Prevu is an
application which creates a self-contained build environment (similar
to gentoo's emerge) to build a .deb file of a 7.10 program/library for
7.4.
sudo prevu-init
        Sets up the build environment. This could take awhile. Answer
yes when asked
Edit /etc/apt/sources.list as root and add "deb-src http://us.archive.ubuntu.com/ubuntu
gutsy main universe restricted multiverse"
        Add the repository for gutsy (7.10)
sudo apt-get update
prevu libswscale-dev
cd /var/cache/prevu/feisty-debs
sudo dpkg -i *.deb
        This installs all the packages build by prevu. Ignore the ones about
ffmpeg not being able to be installed
cd ~
sudo apt-get install mono-mcs (we're bootstrapping mono with the
ubuntu version of mcs)
cd mono
Download patch found at www.mono-project.com/Moonlight to mono/mono
cd mono/mono
patch -p0 < mono-delegate-appdomain-patch
./autogen.sh --prefix=/usr --with-moonlight=yes
make
sudo apt-get remove mono-mcs
sudo apt-get autoremove
sudo make install
cd ../olive
./configure --prefix=/usr
make
sudo make install
cd gtk-sharp
./boostrap-2.10 --prefix=/usr
make
sudo make install
cd ../monodoc
./autogen.sh --prefix=/usr
make
make install
cd ../gnome-sharp
./bootstrap-2.16 --prefix=/usr
make
sudo make install
cd ../moon
./autogen.sh --prefix=/usr
sudo make install
cd /usr/local/lib/moon/plugin
sudo cp *.so moonlight.exe /usr/lib/mozilla-firefox/plugins
        Install the firefox plugin
sudo ln -s /usr/local/lib/mono /usr/lib/mono/3.0
        Install a symbolic link to fix an install issue
firefox
        Launch Firefox
In the address bar, about:plugins
        Confirm WPFe plugin is there
Woot! You should be good.
[/PHP]

DANG this needs to be simplified! Moonlight doesn't stand a chance If this is truly how the folks at the mono project expect people to install it.

---

### Post by SonicSteve on 2008-02-07
One thing I've noticed. 

All my mono programs are now broken, Tomboy, Banshee etc. if there are others I bet they don't work either.

---

### Post by MorphiusFaydal on 2008-02-09
> **SonicSteve said:**
> OK I found this how to;
I have not tried it yet, I will when I have some free time at home. It does not seem to be a simple process and some people have had problems with it. Perhaps it might be a place to start though. 
USE AT OWN RISK!!!!

[PHP] Hello All,
          I've spent some time messing with silverlight on feisty, and
have some notes I wrote down while getting it to work. See if these
help. They replace the built in mono stack with one from svn, and
install everything needed from svn.

Let me know if it works for you guys.

--Chris Hamons

Install Ubuntu 7.4 onto your test machine or VMware image. [link
http://www.ubuntu.com/getubuntu/download]
Update using build in updater.
        This prepares a base to build our moonlight stack upon. Any ubuntu
7.4 machine could be used here instead.
sudo apt-get update
sudo apt-get install subversion
mkdir mono
cd mono
svn co svn://anonsvn.mono-project.com/source/trunk/mcs
svn co svn://anonsvn.mono-project.com/source/trunk/mono
svn co svn://anonsvn.mono-project.com/source/trunk/gtk-sharp
svn co svn://anonsvn.mono-project.com/source/trunk/gnome-sharp
svn co svn://anonsvn.mono-project.com/source/trunk/olive
svn co svn://anonsvn.mono-project.com/source/trunk/moon
svn co svn://anonsvn.mono-project.com/source/trunk/monodoc
sudo apt-get install libavcodec0d libavformat0d libgtk2.0-dev libnspr-
dev firefox-dev libavcodec-dev libavformat-dev libasound2-dev librsvg2-
dev
sudo apt-get install autoconf automake libtool build-essential bison
sudo apt-get install prevu
        Little bit of explanation here. One of the required libraries
(libswscale-dev) does not exist under 7.4. 7.10 has a copy, but it's
not part of the traditional backports repository. Prevu is an
application which creates a self-contained build environment (similar
to gentoo's emerge) to build a .deb file of a 7.10 program/library for
7.4.
sudo prevu-init
        Sets up the build environment. This could take awhile. Answer
yes when asked
Edit /etc/apt/sources.list as root and add "deb-src http://us.archive.ubuntu.com/ubuntu
gutsy main universe restricted multiverse"
        Add the repository for gutsy (7.10)
sudo apt-get update
prevu libswscale-dev
cd /var/cache/prevu/feisty-debs
sudo dpkg -i *.deb
        This installs all the packages build by prevu. Ignore the ones about
ffmpeg not being able to be installed
cd ~
sudo apt-get install mono-mcs (we're bootstrapping mono with the
ubuntu version of mcs)
cd mono
Download patch found at www.mono-project.com/Moonlight to mono/mono
cd mono/mono
patch -p0 < mono-delegate-appdomain-patch
./autogen.sh --prefix=/usr --with-moonlight=yes
make
sudo apt-get remove mono-mcs
sudo apt-get autoremove
sudo make install
cd ../olive
./configure --prefix=/usr
make
sudo make install
cd gtk-sharp
./boostrap-2.10 --prefix=/usr
make
sudo make install
cd ../monodoc
./autogen.sh --prefix=/usr
make
make install
cd ../gnome-sharp
./bootstrap-2.16 --prefix=/usr
make
sudo make install
cd ../moon
./autogen.sh --prefix=/usr
sudo make install
cd /usr/local/lib/moon/plugin
sudo cp *.so moonlight.exe /usr/lib/mozilla-firefox/plugins
        Install the firefox plugin
sudo ln -s /usr/local/lib/mono /usr/lib/mono/3.0
        Install a symbolic link to fix an install issue
firefox
        Launch Firefox
In the address bar, about:plugins
        Confirm WPFe plugin is there
Woot! You should be good.
[/PHP]

DANG this needs to be simplified! Moonlight doesn't stand a chance If this is truly how the folks at the mono project expect people to install it.

You *do* realize that Moonlight is still considered "alpha" software, and you're not supposed to install it unless you're going to be developing it or testing it.  Once it reaches a state where it could function as a release, we'll see normal packages for install.

---

### Post by chamons on 2008-02-18
Yeah, I could see that wrecking your local copy of mono, and the programs (Tomboy, Banshee) that use them. I wrote it to _replace_ your local copy of the mono.

> Install Ubuntu 7.4 onto your test machine or VMware image. 

I was using a virtual image, and so didn't care if I broke those apps. 

The newsgroup I posted this on is here:
[http://groups.google.com/group/mono-olive/browse_thread/thread/a8a35fa2485e362b#](http://groups.google.com/group/mono-olive/browse_thread/thread/a8a35fa2485e362b#)

Some people there refined my instructions a bit. Also, on 7.10, I believe you can skip all those instructions about prevu. 

The alpha copies of 8.4 have the newer versions of mono, but I don't believe they have the moonlight patches. So if you want to mess w\ moonlight, you'll need to jump through hoops like these.

Hope that helps!

---

### Post by SonicSteve on 2008-02-23
YUP it did wreck the local install of mono. No mono based apps work now. OH well eventually I'll either fix it or reinstall with Hardy. 

From what I've read mono has been around for a few years now and it's still in the alpha stages?  I wouldn't recommend installing it.

---

### Post by reverseblade on 2008-02-24
> **SonicSteve said:**
> YUP it did wreck the local install of mono. No mono based apps work now. OH well eventually I'll either fix it or reinstall with Hardy. 

From what I've read mono has been around for a few years now and it's still in the alpha stages?  I wouldn't recommend installing it.

It is not mono that is alpha.  It is moonlight that is alpha. Mono it self is quite production ready

---

