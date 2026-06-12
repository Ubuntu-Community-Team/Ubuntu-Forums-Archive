---
title: "neither totem nor music player will play ANYTHING"
date: 2006-08-22
forum: Installation &amp; Upgrades
---

### Post by omega_c on 2006-08-22
Hey folks

First post...

I just got linux because windows was starting to be really slow, and spyware started bugging me

I installed ubuntu, the dapper drake release.

The thing is, neither Totem movie player nor Rythmbox music player will play anything.

I've tried avi, mp3 mpeg, ogg... nothing works.

I searched the forums for stuff like this, but i didn't find any posts regarding .avi files not playing. Most of my video files are .avi, and so i'd like to resolve this...

Can someone please give me a link to a codec pack or something of the sort to get rid of this problem?

Thanks!

---

### Post by moore.bryan on 2006-08-22
*first, have you enabled extra repositories?*

---

### Post by omega_c on 2006-08-22
no

How do i do that?

(I started using ubuntu yesterday, so i know pretty much nothing about it)

---

### Post by moore.bryan on 2006-08-22
[I]well, you can either go through synaptic (System>Administration>Synaptic) or get used to the command line (apt-get).  with linux, you want to be comfortable with command lines, so you might as well go that way.  to edit where apt-get gets programs, type the following in the terminal
```
sudo apt-get gedit /etc/apt/sources.list
```
if you don't know how to get a terminal, either try in Applications>Accessories or just hit ALT+F2 and type ```
xterm
```
once in the sources.list, you'll need to do some adding.  a lot of posts suggest just using an all-inclusive list; mine's here:
> # Ubuntu supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

# Ubuntu backports project (packages, GPG key: 437D05B5)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

# Ubuntu backports project (sources, GPG key: 437D05B5)
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
 
# CANONICAL (Hosted on Canonical servers, not Ubuntu servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

# Seveasâ€™ packages (packages, GPG key: 1135D466)
deb [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) dapper-seveas all

# Seveasâ€™ packages (sources, GPG key: 1135D466)
deb-src [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb [ftp://cipherfunk.org/pub/packages/ubuntu/](ftp://cipherfunk.org/pub/packages/ubuntu/) dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src [ftp://cipherfunk.org/pub/packages/ubuntu](ftp://cipherfunk.org/pub/packages/ubuntu) dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main

# kubuntu.org packages for the latest KDE version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) dapper main
deb [http://kubuntu.org/packages/kde-354](http://kubuntu.org/packages/kde-354) dapper main

# kubuntu.org packages for the latest Koffice version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest Koffice version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/koffice-latest](http://kubuntu.org/packages/koffice-latest) dapper main

# kubuntu.org packages for the latest amaroK version (packages, GPG key: DD4D5088)
deb [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# kubuntu.org packages for the latest amaroK version (sources, GPG key: DD4D5088)
deb-src [http://kubuntu.org/packages/amarok-latest](http://kubuntu.org/packages/amarok-latest) dapper main

# Bleeding edge wine packages (packages)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Bleeding edge wine packages (sources)
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main

# Penguin Liberation Front (packages)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# Penguin Liberation Front (sources)
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free

# Amarok 1.4 Packages
deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main

# KDE 3.5.3 Packages
deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main

# KOffice 1.5.1 Packages
deb [http://kubuntu.org/packages/koffice-151](http://kubuntu.org/packages/koffice-151) dapper main

# Dev not-public (Breezy Packages)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/](http://antesis.freecontrib.org/mirrors/ubuntu/devnotpublic/) breezy free non-free

# Achimâ€™s Unofficial â€˜dapperâ€™ Kubuntu packages
deb [http://www.mpe.mpg.de/~ach/kubuntu/dapper](http://www.mpe.mpg.de/~ach/kubuntu/dapper) ./
deb-src [http://www.mpe.mpg.de/~ach/kubuntu/dapper](http://www.mpe.mpg.de/~ach/kubuntu/dapper) ./

# Ubuntu Taiwan ubuntu extra repository
deb [http://apt.ubuntu.org.tw](http://apt.ubuntu.org.tw) ubtw/
deb [http://apt.ubuntu.org.tw](http://apt.ubuntu.org.tw) ubtw-testing/

# Ubuntu dapper University Klagenfurt packages
# $ wget [http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub](http://ubuntu.uni-klu.ac.at/uniklu-debuild.pub)
# $ sudo apt-key add uniklu-debuild.pub
# uniklu: backports and new packages
# uniklu-desktop: packages for uniklu desktop
# uniklu-intern: not freely redistributable (jvm), or modified packages
# uniklu-nfsv4: nfsv4 kernel and packages
# uniklu-vserver: vserver kernel
# uniklu-testing: packages not ready for general use !
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-desktop
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-intern
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-nfsv4
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-vserver
deb [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-testing
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-desktop
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-intern
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-nfsv4
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-vserver
deb-src [http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/](http://ubuntu.uni-klu.ac.at/ubuntu.uniklu/) dapper uniklu-testing

## MaXeR (KDE Apps)
deb [http://repos.knio.it/](http://repos.knio.it/) dapper main contrib non-free
deb-src [http://repos.knio.it/](http://repos.knio.it/) dapper main contrib non-free

# Quinnâ€™s Compiz Packages - [http://xgl.compiz.info/](http://xgl.compiz.info/)
deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

# CompizTool package
deb [http://compiztools.free.fr/debian](http://compiztools.free.fr/debian) unstable main

# Wormux - Worm Clone packages
deb [http://download.gna.org/wormux/debs](http://download.gna.org/wormux/debs) dapper/

# Skype packages
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

# Audacious
deb [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious
deb-src [http://vdlinux.sourceforge.jp/](http://vdlinux.sourceforge.jp/) experimental audacious

#Asher's Repo
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) dapper  main dupdate french
deb [http://asher256-repository.tuxfamily.org](http://asher256-repository.tuxfamily.org) ubuntu main dupdate french

# Gauvain Repository
deb [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib
deb-src [http://gauvain.tuxfamily.org/repos](http://gauvain.tuxfamily.org/repos) dapper contrib

## lprod packages: many audio/video apps: avidemux, cinelerraâ€&#352; (breezy partly working on dapper)
deb [http://lprod.org/deb/breezy/](http://lprod.org/deb/breezy/) ./

# Mjpegtools and Cinelerra packages (choose your arch)
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/) ./
deb [http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/pentium4/) ./

# A little too quiet
deb [http://apt.alittletooquiet.net/staging](http://apt.alittletooquiet.net/staging) dapper main

# Dapper Stuff: Broadcom kernel firmwares, google-earth, beagled€&#352; (GPG key: 969F3F57)
deb [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego all bcm43xx
deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) dapper-cafuego all bcm43xx

# Debuntu Ubuntu dapper packages
# GPG Key-flie: wget [http://repository.debuntu.org/GPG-Key-chantra.txt](http://repository.debuntu.org/GPG-Key-chantra.txt)
deb [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse
deb-src [http://repository.debuntu.org/](http://repository.debuntu.org/) dapper multiverse

deb [http://exodus.xmms.se/debian](http://exodus.xmms.se/debian) dapper main
what that does is add a bunch of new repos into the sources.list.  exit out of gedit, saving of course, and type
```
sudo apt-get update
```
it'll go through its thing and then you can use synaptic to check for audio/video decoders.

[/I]

---

### Post by Scythe!? on 2006-08-22
Type this into terminal:
```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```
then type
```
automatix
```
Type your password.
Press the Ok button a few times and then tick what you want.

The mp3 & other codecs are called "Multimedia Codecs". Once you ticked what you want, press Ok and type your password when it asks for it.

---

### Post by omega_c on 2006-08-22
ok, thanks!

I actually can't get back onto my ubuntu computer for a while, but once i do, i'll test it out!

Thanks again!

---

### Post by moore.bryan on 2006-08-22
> **Scythe!? said:**
> Type this into terminal:
```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
``` then type
```
automatix
``` Type your password.
Press the Ok button a few times and then tick what you want.

The mp3 & other codecs are called "Multimedia Codecs". Once you ticked what you want, press Ok and type your password when it asks for it.
 
[I]thanks scythe, i've had bad experiences with automatix with my config, so i forget all about it.

good luck omega_c...
[/I]

---

### Post by omega_c on 2006-08-22
um...which one should i use?

---

### Post by omega_c on 2006-08-22
Let me clarify

Is one way better than/install more codecs than the other?

Looks like the second method is simpler.

Thoughts?

---

### Post by anasofiapaixao on 2006-08-22
To clarify: Updating your sources.list file isn't really a solution, it is a troubleshooing step. Doing that will allow to download software from the "universe" and "multiverse" repositories; translating to english, you will be able to choose from lots more of applications that are not officially supported, but can be seriously important/useful/fun.

So do that. I would recommend for now to stick with the Ubuntu repos. There is a 'point-and-click' way to do it if you prefer (I know when one is beggining that it is a relief to be able to do some things with a GUI and yet I am a command line fangirl): Go to System--> Administration--> Software Properties, click "Add" and be sure all boxes are checked. Click the Add button and you're done.

Automatix is a script that will basically do the hard work for you, installing configure many things. I have never tried automatix, but I have used [EasyUbuntu]("http://easyubuntu.freecontrib.org/") and it goes fine except for a package or two I had to uncheck and which I don't remember.

Also, [there is a page on the Ubuntu wiki]("https://wiki.ubuntu.com/RestrictedFormats") telling you how to do what the script does about the sound manually; I would suggest you to check it out in order to understand why things don't work out of the box.

Good luck!

---

### Post by omega_c on 2006-08-23
ok, thanks.

I cant get onto my ubuntu computer until tomorrow, so we'll see how that works out...

---

### Post by moore.bryan on 2006-08-23
[I]good advice, anasofiapaixo, but i'm not sure i'd classify an inclusive sources.list as troubleshooting...  ;-)
make sure to let us know if there's anything else omega_c.
[/I]

---

### Post by FastZ on 2006-08-25
Wow!  Thanks a million!  I was trying to watch an orientation video for one of my college classes while I was on my Ubuntu machine and couldnt get it to play in Totem.  I ran the Automatix script (which took a while to finish but it's worth it) and now I can watch the videos I need to watch and plus I have several other programs that I installed with the script as well.  Thanks again!

---

### Post by heather on 2006-08-26
Nice post

i am now able to play everything from
avi-mpeg-mpg.including encryped files
havent tried wmv yet

---

### Post by sagara on 2006-09-17
> **Scythe!? said:**
> Type this into terminal:
```
wget http://www.getautomatix.com/files/automatix-installer
chmod 755 ~/automatix-installer
./automatix-installer
```
then type
```
automatix
```
Type your password.
Press the Ok button a few times and then tick what you want.

The mp3 & other codecs are called "Multimedia Codecs". Once you ticked what you want, press Ok and type your password when it asks for it.

Scythe I also tried this and it worked beautifully.  Thank you for the tip!

I **have a question** though: at the end it asked me if I wanted to keep my original repository list file or use the new one automatrix used.  I selected the latter was this ok?

---

### Post by heather on 2006-09-17
hi
thank you so much for your reply
dont shoot me please lol but i have been using FreeBSD for a few weeks now
although i Love Ubuntu Still
i will use your reccomended commands
on my other PC where i am using Ubuntu 6.01

thank you :)

---

### Post by jocheem67 on 2006-09-18
No-one will kill you for that,lol. It's a beautiful OS...

However, I think that both solutions given to you here are at least a bit overkill...and even dangerous. It can **** up your system to use automatix. One has limited control over what it's doing...The 'source.list' as given here earlier is a massive one, and one with a lot of unofficial repo's. I recommend you, as a beginner, don't touch those. There wil be a lot of betasoftware involved.

If you uncheck the repo's already present in your sources.list as it is now, and read ( and learn ) the restricted formats page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

then you're a lot safer....

---

### Post by heather on 2006-09-18
> **jocheem67 said:**
> No-one will kill you for that,lol. It's a beautiful OS...

However, I think that both solutions given to you here are at least a bit overkill...and even dangerous. It can **** up your system to use automatix. One has limited control over what it's doing...The 'source.list' as given here earlier is a massive one, and one with a lot of unofficial repo's. I recommend you, as a beginner, don't touch those. There wil be a lot of betasoftware involved.

If you uncheck the repo's already present in your sources.list as it is now, and read ( and learn ) the restricted formats page:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

then you're a lot safer....


well thank you
i appreciate all your help :)

---

