---
title: "How do I install the latest gtkpod? (iPod program question)"
date: 2011-09-26
forum: Installation &amp; Upgrades
---

### Post by anicetus001 on 2011-09-26
Ok, so I'm fairly new with Ubuntu. Still a beginner though, so sorry if I'm asking a stupid question.

I'm trying to install this version of gtkpod from their website, since the version in "Software Center" is only 1.0.0 and I have a couple problems with it, also I just like having most of my programs updated. 

So, here's my question...

How do I install the latest gtkpod? I downloaded the tar.gz file from their website. (gtkpod-2.1.0.tar.gz)
Then I unzipped it and the folder is called "gtkpod-2.1.0".

Now, I open the folder "INSTALL" and it tells me this, on how to install it in Ubuntu, but it makes little to zero sense to me, and I tried what they say in the command line, the first 2-3 steps work, but then the rest don't.

"Quick guide for Ubuntu/Debian

The following steps were necessary to install libgpod and gtkpod on a fairly virgin Ubuntu Hardy (LTS 8.04) installation.

# required packages
sudo apt-get install autoconf flex gettext libglib2.0-dev libgtk2.0-dev libglade2-dev libid3tag0-dev libxml-parser-perl pkg-config automake gcc git-core gtk-doc-tools

# recommended packages
sudo apt-get install libcurl4-dev libflac-dev libgnomevfs2-dev libhal-dev libvorbis-dev libmp4v2-dev libwebkit-dev

# checkout libgpod and gtkpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/libgpod
git clone git://gtkpod.git.sourceforge.net/gitroot/gtkpod/gtkpod

# compile libgpod
cd libgpod/
./autogen.sh
make
sudo make install

# compile gtkpod
cd ../gtkpod/
cd libgpod/
./autogen.sh
make
sudo make install
sudo ldconfig

#start gtkpod
gtkpod &"


Please help. :D

Thanks guys.

---

### Post by anicetus001 on 2011-09-27
bump?

Not sure how many pages this will go, to where it will never get looked at.

---

### Post by anicetus001 on 2011-10-08
Bumpity bump bump.

Come on you smart fools, where ya'll at?! :D

:popcorn:

---

### Post by TehSofaWolf on 2011-10-08
You could try adding this repo to your software center. [B]ppa:phantomjinx/gtkpod-2.0.1-beta

It's a beta version though, so your mileage may vary. As for 2.1.0, I think it's only for Oneiric so far? ([https://launchpad.net/ubuntu/+source/gtkpod](https://launchpad.net/ubuntu/+source/gtkpod))

"[/B][The Oneiric Ocelot]("https://launchpad.net/ubuntu/oneiric/+source/gtkpod")           (pre-release freeze)                                                                   [gtkpod master series]("https://launchpad.net/gtkpod/master")                                                      
                                                                                                         [                         ]("https://launchpad.net/ubuntu/+archive/primary/+sourcepub/1903935/+listing-archive-extra")           [             [IMG]https://launchpad.net/@@/package-source[/IMG]             2.1.0-1ubuntu1           ]("https://launchpad.net/ubuntu/+source/gtkpod/2.1.0-1ubuntu1")                             release           (universe)                                          7 weeks             ago                               "

I could be wrong, but the 2.1.0 will probably be released within a couple weeks.

---

