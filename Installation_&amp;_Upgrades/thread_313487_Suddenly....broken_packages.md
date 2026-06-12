---
title: "Suddenly....broken packages"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by robbie75 on 2006-12-06
Hi all,
I'm a new ubuntu user since I moved
to dapper before the last summer vacations :-)
after a loooong period with my trusty Debian :-P

So, here it is my problem:
I've always managed to install/remove packages by
aptitude or synaptic and (as usual) everything has
gone without problems...

But the last night I noticed a very strange thing
with my packages....this is what aptitude returns
to me:
```
roberto@dell500m:~$ sudo aptitude install
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  g++ g++-4.0 gtkorphan libxml-parser-perl mozilla-mplayer
The following packages are unused and will be REMOVED:
  portmap
The following NEW packages will be installed:
  mozplugger
The following packages will be REMOVED:
  acroread-plugins afio amule amule-common bluefish boa-constructor buffer bum checkgmail faac faad
  firefox-themes-ubuntu firestarter flac gawk gcc gcc-4.0 gdk-imlib11 ghex gkdial gnome-bin
  gnome-bluetooth gnome-libs-data gnome-splashscreen-manager gnome-think gnotepad+ gobby gpaint gparted
  gstreamer0.8-alsa gstreamer0.8-faac gstreamer0.8-ffmpeg gstreamer0.8-flac gstreamer0.8-gnomevfs
  gstreamer0.8-lame gstreamer0.8-mad gstreamer0.8-misc gstreamer0.8-vorbis gtkhtml3.6 hexcurse hexer
  html2ps htmldoc htmldoc-common hyphen-show i8kutils imlib-base jargon-text lame latex-beamer
  latex-xcolor latex2rtf-doc libaltlinuxhyph-dev libart2 libartsc0 libatk1-ruby libavahi-compat-howl0
  libcairo-ruby libcompress-zlib-perl libcrypt-blowfish-perl libcrypt-simple-perl libcrypt-ssleay-perl
  libcrypto++5.2c2a libdb3 libemail-mime-encodings-perl libevent1 libfltk1.1 libfreezethaw-perl libfuse2
  libgconf2-ruby libgdk-pixbuf2-ruby libggi2 libgii0 libgii0-target-x libglade-gnome0 libglade0
  libglade2-ruby libglib2-ruby libglibmm-2.4-1c2a libgmime2.1 libgmpxx3 libgnome32 libgnomesupport0
  libgnomeui32 libgnorba27 libgnorbagtk0 libgnutls11 libgstreamer-gconf0.8-0 libgtk2-gladexml-perl
  libgtk2-ruby libgtk2-trayicon-perl libgtkhex0 libgtkhtml3.6-18 libgtkmm-2.4-1c2a libgtkxmhtml1 libhnj0
  libhtml-lint-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libmd5-perl libnet6-1.2-0
  libnfsidmap1 libntfs8 libobby-0.3-0 liboggflac3 liborbit0 libpango1-ruby libpaper-utils libqcad0
  libqt4-core libqt4-gui librexml-ruby libruby1.8 libsdl-mixer1.2 libsmpeg0 libsp1c2 libssl0.9.7 libt1-5
  libungif4g liburi-perl libwww-perl libxml++2.6c2a libxml-libxml-common-perl libxml-libxml-perl
  libxml-namespacesupport-perl libxml-sax-perl libxml-simple-perl libxml1 linuxdoc-tools
  linuxdoc-tools-latex lzop mail-notification mindi mindi-busybox mondo mondo-doc mozilla-acroread
  mplayer mplayer-686 mplayer-skins ms-sys nasm nautilus-actions nautilus-script-audio-convert
  nautilus-script-manager nfs-common nfs-kernel-server nmap nrg2iso ntfsprogs ntp ntp-server ntp-simple
  peacock perlmagick pgf planetpenguin-racer planetpenguin-racer-data pychecker python-gst
  python-wxgtk2.6 python-wxversion python2.2 python2.2-tk python2.3 python2.3-dev python2.3-tk
  python2.3-xml python2.4-libbtctl python2.4-psycopg qcad qcad-doc qt3-assistant qt3-doc ruby ruby1.8
  soundconverter sp syslinux tetex-base tetex-bin tetex-doc tetex-extra tex-common texify texmaker
  vorbis-tools weblint-perl xfonts-terminus-dos xhtml2ps zope-common
0 packages upgraded, 1 newly installed, 193 to remove and 0 not upgraded.
Need to get 45.4kB of archives. After unpacking 511MB will be freed.
The following packages have unmet dependencies:
  g++-4.0: Depends: gcc-4.0 (= 4.0.3-1ubuntu5) but it is not installable
  g++: Depends: gcc (>= 4:4.0.3-1) but it is not installable
       Depends: gcc-4.0 (>= 4.0.3) but it is not installable
  libxml-parser-perl: Depends: liburi-perl but it is not installable
                      Depends: libwww-perl but it is not installable
  mozilla-mplayer: Depends: mplayer (>= 1.0-pre5) but it is not installable or
                            mplayer-custom (>= 1.0-pre5) but it is not installable or
                            mplayer-386 (>= 1.0-pre5) but it is not installable or
                            mplayer-586 (>= 1.0-pre5) but it is not installable or
                            mplayer-686 (>= 1.0-pre5) but it is not installable or
                            mplayer-k6 (>= 1.0-pre5) but it is not installable or
                            mplayer-k7 (>= 1.0-pre5) but it is not installable or
                            mplayer-powerpc (>= 1.0-pre5) but it is not installable or
                            mplayer-g4 (>= 1.0-pre5) but it is not installable or
                            mplayer-amd64 (>= 1.0-pre5) but it is not installable or
                            mplayer-nogui (>= 1.0-pre5) but it is not installable
  gtkorphan: Depends: libgtk2-gladexml-perl but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
gnormalize
mozilla-mplayer

Keep the following packages at their current version:
gcc [4:4.0.3-1 (dapper, now)]
gcc-4.0 [4.0.3-1ubuntu5 (dapper, now)]
gnome-bluetooth [0.7.0-0ubuntu4 (dapper, now)]
libcompress-zlib-perl [1.41-1 (dapper, now)]
libgtk2-gladexml-perl [1.005-1 (dapper, now)]
libhtml-parser-perl [3.48-1 (dapper, now)]
libhtml-tagset-perl [3.10-1 (dapper, now)]
libhtml-tree-perl [3.19.01-1 (dapper, now)]
liboggflac3 [1.1.2-3ubuntu1 (dapper, now)]
libpaper-utils [1.1.14ubuntu8 (dapper, now)]
liburi-perl [1.35-1 (dapper, now)]
libwww-perl [5.803-4 (dapper, now)]
lzop [1.01-3 (dapper, now)]
python2.4-libbtctl [0.6.0-0ubuntu3 (dapper, now)]
vorbis-tools [1.1.1-3 (dapper, now)]

Leave the following dependencies unresolved:
python-epydoc recommends tetex-extra
Score is -1587

Accept this solution? [Y/n/q/?]


```

But, even the ubuntu-desktop package complains that
there are unsolved dependencies...

What's goin'on with my dapper?
Is that because of a general package upgrade in
ubuntus'repository? :-?

---

### Post by renzokuken on 2006-12-06
try passing 

```
sudo apt-get update
```

first, then try again

also, do you have the universe and multiverse repos enabled?

---

### Post by robbie75 on 2006-12-06
Hi renzokuken!

> **renzokuken said:**
> try passing 

```
sudo apt-get update
```

first, then try again

also, do you have the universe and multiverse repos enabled?

just tried....same response from aptitude :-(

And yes, I do have multiverse and universe, but till some weeks ago
(maybe even less I think....) I do not have any dependencies problem...

Anyway what follows is my sources.list
```

deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

```

Thank you for your time!
Rob

---

### Post by yota on 2006-12-06
If you issue 'aptitude install' without a package list, you tell aptitude to process "pending actions".
From man aptitude:
> 
As a special case, 'install' with no arguments will act on any stored/pending actions.


So I suppose that you have actually no package  broken (eventually you can use debsums to check), but simply aptitude has a lot of controverse pending operations (maybe you cancelled some operations while they were runnning).

If you're happy with your system, you can safely flush pending operation list with:
```

sudo aptitude keep-all

```
The only side-effect is that packages installed  just to satisfy dependencies will be kept if you'll remove the packages that need them (the 'id' state will become 'i' state)

Hope this helps.

---

### Post by robbie75 on 2006-12-06
> **yota said:**
> If you issue 'aptitude install' without a package list, you tell aptitude to process "pending actions".
From man aptitude:


So I suppose that you have actually no package  broken (eventually you can use debsums to check), but simply aptitude has a lot of controverse pending operations (maybe you cancelled some operations while they were runnning).

If you're happy with your system, you can safely flush pending operation list with:
```

sudo aptitude keep-all

```
The only side-effect is that packages installed  just to satisfy dependencies will be kept if you'll remove the packages that need them (the 'id' state will become 'i' state)

Hope this helps.

Hi yota thank you too!
You're right about the meaning of the syntax I'm using ;)
but, if a take a closer look to what aptitude is complaining,
I can see that all the packages marked as "broken" are actually
installed and not "pending" so, I guess it's not my case (I think)...

If I correctly recall, I already got into a similar situation when
I tried the new Debian testing distro (etch)... in fact, there were
some packages that couldn't be upgraded because of some dependent
packages not yet ready for the upgrade.
What do you think?
thank you again!

---

### Post by yota on 2006-12-06
Hi robbie,

I had experienced the same situation some time ago, after upgrading from breezy to dapper; the solution I told you before worked for me.

If you fear that some package is broken you can reinstall it, thus enforcing dependencies too.
I would reinstall them one by one with apt-get (install --reinstall), avoiding eventual malfunctions of aptitude.

Then you can check them like this:
> 
yota@linbook:~$ debsums g++-4.0
/usr/share/doc/gcc-4.0-base/C++/README.C++   OK
/usr/share/doc/gcc-4.0-base/C++/changelog.gz   OK
/usr/bin/g++-4.0   OK
/usr/lib/gcc/i486-linux-gnu/4.0.3/cc1plus   OK

(please install debsums if you haven't done yet)

When everything is alright issue the 'aptitude keep-all' and 'aptitude install' will stop complaining.
As personal feeling I don't think it can be a real issue, because removing hundreds of packages because g++ has an unmet dependecy is quite unbelievable... I suppose it's just a problem with aptitude.

Let me know!

---

### Post by renzokuken on 2006-12-06
im not quite sure about your sources but there are a couple of odd things, first, backup your old sources list

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
```

and then replace it all with the following ( i simply edited the one you posted above a bit)

```

deb-src http://au.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://au.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://asher256-repository.tuxfamily.org dapper main dupdate french
deb http://asher256-repository.tuxfamily.org ubuntu main dupdate french

```

then try again and see what happens, if its still playing up, restore your old sources.list

```
sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list
```

and we can start again

---

### Post by robbie75 on 2006-12-06
Ok guys, first of all I have to thank you both for
your time!

Now back to our problem with dependencies:
I've followed both your hints and something
changed:
apt-get -f install now is not returning broken dependencies
aptitude install keeps on complaining with dependencies.

I have to say that I've never ever get into something like that
before...

What do you think guys?

Is it because of messed synaptic stuff or what else?

---

### Post by yota on 2006-12-06
Weird...
What if you:
[LIST=1]
[*]remove the packages reported as broken
[*]check if 'aptitude install' is ok (finally)
[*]reinstall those packages
[*]check 'aptitude install' again
[/LIST]

I hope we can narrow down to the package(s) causing headache to aptitude in this way.

---

### Post by renzokuken on 2006-12-07
it could be that the Austrian repos (i guess thats what au stands for, or Australia) are experiencing problems. it could be worth trying the main repos (america, or another set nearby, like UK)

it may also be worth just commenting out the asher-256 repos for now and trying again without them, may be they are conflicting somehow.

---

### Post by renzokuken on 2006-12-07
here is a fairly standard and complete sources.list for edgy

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Repositories)

---

### Post by robbie75 on 2006-12-07
Ok guys, as soon as possibile (it's a busy day today)
i'll try to remove/install all the
packages marked as broken so I can
tell you what aptitude will return to me. ;)

Moreover I managed to change the repository to point to
my local, but with the same result.

BTW I noticed that, either apt-get and synaptic are
working as expected (just run a check for problems
and everything went ok) only aptitude complains about
broken dependencies, so I guess that the problem is
just aptitude.
I do have to remove and then install again all faulty 
packages just within aptitude and see what happens :)

I'll let you know asap ;)

---

### Post by robbie75 on 2006-12-07
Ok, just got it ;)

I removed by aptitude all the broken packeges,
unmarked all packages scheduled to be removed,
updated,upgraded and then reinstalled what
I've previously removed and, finally, everything
went ok :)

Thank you guys for your time!

Anyway I have to admit that in so many years with linux
(red hat first, then debian and now still debian for my servers
but ubuntu for my notebooks/desktop/workstations) I've
never ever had such weird situations... :-|

---

### Post by fakie_flip on 2006-12-08
I saw this thread when I was searching around yesterday, and then you replied to my thread to say look at this one. The same thing happened to me. aptitude did so much complaining, but Synaptic and apt-get did not, and because of that, using Synaptic to try to fix broken dependencies did nothing because it did not know about any. I will try your solution when I get home or next chance I get.

---

