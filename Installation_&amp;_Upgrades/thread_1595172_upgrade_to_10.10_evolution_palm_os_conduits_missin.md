---
title: "upgrade to 10.10 evolution palm os conduits missing"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by kend650 on 2010-10-13
I just upgraded from 10.04 to 10.10 and everything went smoothly.  But when I tried to sync my Treo 700P to evolution, the calander, to-do list, contacts, and memo conduits were missing, and I don't see how to add them to the gnome-pilot settings.  Is there a new, undocumented way, to restore those conduits, or another way around this??

Thanks for any help in advance!

Kend650

---

### Post by seydou on 2010-10-13
There is a way, but only for dauntless ;-). I was disappointed the same way as you, it took me a while to dig out the solution:

First, remove evolution:

```

sudo apt-get P evolution evolution-common libevolution evolution-plugins

```

At this point, you have 2 options - either trust me, and download my packages, or go on and compile it yourself. I would suggest the latter, it is much more fun :P. Anyway, the download link for replacement binary packages is:

[http://sarakinas.wu.cz/doku.php?id=evo-pilot]("http://sarakinas.wu.cz/doku.php?id=evo-pilot")

In order to compile evolution, we would need heaps of headers. I lost the track of them while test-running this process, so start with build essentials and watch for error messages later:

```

sudo apt-get install build-essential fakeroot dpkg-dev checkinstall

```

Here are are a few packages evolution needs to get compiled, it is probably far from complete, but if you run this, you get most of them for sure:

```

sudo apt-get install cdbs  python-dev gtk-doc-tools  libgnome-pilot2-dev  \
libnss3-dev evolution-data-server-dev  evolution-data-server-dev \
libegroupwise1.2-dev  libebackend1.2-dev  libgdata1.2-dev  libgdata-google1.2-dev \
libecal1.2-dev  libnm-glib-dev libnotify-dev  libexchange-storage1.2-dev \
libgstreamer0.10-dev libytnef0-dev libical-dev libicu-dev libgweather-dev \
libpst-dev  liblpint-bonobo-dev

```

Purge the distro evolution, as described above, and obtain the source. Create arbitrary directory in your home and descend to it.

```

mkdir evolution-build
cd evolution-build
apt-get source evolution

```

It is around 40MB, so after a little depending on your connection you have the complete source tree. Descend to the directory 'evolution-2.30.3'

```

cd evolution-2.30.3

```

Open up debian/rules, and do the changes you need:

```

vi debian/rules

```

We are interested in DEB_CONFIGURE_EXTRA_FLAGS section (starting form line 28), changing 'disabled' to 'enabled' - yes, it is '&#8211;enable-pilot-conduits' parameter. I also enable pst import, because I want it, but it is not necessary for pilot conduits, of course. The final section can look like this:

```

DEB_CONFIGURE_EXTRA_FLAGS += \
        --with-openldap \
        --enable-nls \
        --disable-scrollkeeper \
        --enable-pilot-conduits \
        --with-krb5=/usr \
        --sysconfdir=/etc \
        --libexecdir=/usr/lib \
        --enable-plugins=experimental \
        --enable-python \
        --enable-pst-import \
        --disable-image-inline \
        --disable-contacts-map

```


Next, edit debian/evolution-common.install and add following line to it
```

debian/tmp/usr/share/gnome-pilot

```
After that, edit debian/evolution.install, and add this line
```

debian/tmp/usr/lib/evolution/2.30/conduits/*.so

```
and you are done with this. 

It is time to build now, so run this command:
```

dpkg-buildpackage -rfakeroot

```

You need a lot of patience, now. Examine the error messages and add necessary development packages. For example, if you see the complaint about missing 'libebook' package, look for what is available:

```

apt-cache search libebook

```

You would see following:

```

libebook1.2-dev - Client library for evolution address books (development files)
libebook-tools-perl - E-Book manipulation tool and Perl libraries
libebook1.2-9 - Client library for evolution address books

```

It is -dev package, we need, so fetch it like this

```

sudo apt-get install libebook1.2-dev

```

And so on, until the dpkg-buildpackage runs on smoothly. Once finished, you should have a bunch of *.deb files in above directory. Do this to install:
```

cd ..
sudo dpkg -i *deb

```

or select only packages you want (evolution, evolution-common, evolution-plugins and libevolution being the important ones).

We are done, as a final touch fire up Synaptics, and lock respective packages in their current versions.

ENJOY!

PS: I use it with ancient PALM M500. It is great e-books reader, and  I have contacts and calendar as a bonus. What is the best, I only need to charge it once a week!

---

### Post by kend650 on 2010-10-13
Thanks for this info.  But as you said, this work-around is for the dauntless, and I left my programming skills back at the office when I retired!!  So I'll wait till Ubuntu/Evolution comes out with the 'fix', assuming that there is enough demand to get it 'fixed'.  I hope the lack of a 'fix' doesn't force me to upgrade to an Android phone or move back to Thunderbird...

Thanks again...

---

### Post by seydou on 2010-10-13
Fair enough :) In the meantime, I have found a hack to the source package, so I just compiled the alternative set of proper debian packages - better than all-in-one above. They are vailable at

[http://sarakinas.wu.cz/doku.php?id=evo-pilot]("http://sarakinas.wu.cz/doku.php?id=evo-pilot")

They are one-to-one replacement of standard UBUNTU packages, only with pilot conduits, and the installation can not be easier :). Just tested on mu Palm M500, everything works all right. Above tutorial was amended, and shows the changes I made to debian/* files.

---

### Post by Tulainas on 2010-10-15
> **kend650 said:**
> Thanks for this info.  But as you said, this work-around is for the dauntless, and I left my programming skills back at the office when I retired!!  So I'll wait till Ubuntu/Evolution comes out with the 'fix', assuming that there is enough demand to get it 'fixed'.  I hope the lack of a 'fix' doesn't force me to upgrade to an Android phone or move back to Thunderbird...

Thanks again...


 Yup, I thank you also, but my programming skills are not that good... (i don't have much patience these days) :-S

 I guess I'll wait too until this is fixed (i've tried your method with no succes yet).

**Where can I make myself hear that I need this feature back???** 

 I'll keep trying to make it work in the meantime...

 
------> D'you know how to sync my  Palm T|X with those new conduits? Any suggestions?
 
Thank you all again!

---

### Post by seydou on 2010-10-16
> **Tulainas said:**
> Yup, I thank you also, but my programming skills are not that good... (i don't have much patience these days) :-S

 I guess I'll wait too until this is fixed (i've tried your method with no succes yet).

**Where can I make myself hear that I need this feature back???** 

...

Have you tried my precompiled binaties? These are ready to install, no compilation needed. The link is above.

---

### Post by kend650 on 2010-10-17
Does the get-apt -P delete all of my existing contacts, memos, and email I have stored in my .evloution directories?  Obviously I don't want to loose all my data.  I will make a backup of this data anyway, but just to be sure of what will be deleted with that command...

Thanks for the info, once again!!

Ken

---

### Post by seydou on 2010-10-18
> **kend650 said:**
> Does the get-apt -P delete all of my existing contacts, memos, and email I have stored in my .evloution directories?  Obviously I don't want to loose all my data.  I will make a backup of this data anyway, but just to be sure of what will be deleted with that command...

Thanks for the info, once again!!

Ken

Not at all! It only purges system-wide files. Your contacts etc. live in your home (~/.evolution and subdirectories), and are not touched by the installer.

If you want to see what comes with the package and what thus gets erased, use this command (for example evolution package itself):

```
dpkg -L evolution
```

---

### Post by faisalti on 2010-10-18
I apologies ahead of time if this is not the proper thread to post this. I am trying to sync my palmOS with gnome-pilot. In Ubuntu 10.04, I was able to sync my memo, todo list and address. After I upgraded to 10.10, I no longer have these conduits in gnome-pilot. Will updating evolution fix this? Thanks in advance.

---

### Post by seydou on 2010-10-19
> **faisalti said:**
> I apologies ahead of time if this is not the proper thread to post this. I am trying to sync my palmOS with gnome-pilot. In Ubuntu 10.04, I was able to sync my memo, todo list and address. After I upgraded to 10.10, I no longer have these conduits in gnome-pilot. Will updating evolution fix this? Thanks in advance.

Ubuntu maintainers decided to compile evolution without pilot conduits, and there is little hope it will be brought back again, hence standard upgrade will not fix it. Read above and install alternative packages manually.

---

### Post by mcdavey on 2010-10-25
There is a much simpler solution!

The gnome-pilot evolution conduits have been moved from the evolution package to the gnome-pilot package.

You need to get hold of gnome-pilot 2.32.0.

There are instructions attached to this ubuntu bug report:
[https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/569601](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot/+bug/569601)

---

### Post by ski_phreak on 2010-10-31
seydou,

Thanks for documenting such a simple how-to, even though it's a complex procedure.  This is what brings me back to Ubuntu forums even though I've always used Debian or it's other variants.

I would love to have used your binaries, but I'm running AMD64...no joy.

Your source-code walk-through worked beautifully for my amd64 machine, however.  I've summarized my experience in case it might help any newbies intimidated by your instructions.

If anyone has space/bandwidth to host 30+ meg of amd64 debs, I'll happily send them to you.  Let me know before I delete the debs.

* n00b note:  Open and keep open a terminal window to type in (or copy/paste) all code below. (Applications->Accessories->Terminal)*  Unlike m$dos within window$, you can copy/paste in and out  of a terminal.  You can paste any line of code in this walk-through directly into your terminal window.

INSTALL COMPILER BASICS: 
```
  sudo apt-get install build-essential fakeroot dpkg-dev checkinstall 
```GET SOURCECODE AND A PLACE TO WORK ON IT:
```

  mkdir evolution-build
  cd evolution-build
  apt-get source evolution
  cd evolution-2.30.3

```EDIT THE 3 FILES BELOW AS NOTED
* (n00b note: use vi or emacs or jed or gedit or pretty much anything EXCEPT OpenOffice.  The most n00b-friendly is probably gedit, which can be typed in the same terminal as in these examples .)*
```
gedit debian/rules
```change '--disable-pilot-conduits' to '--enable-pilot-conduits' (line 32)

```
gedit debian/evolution-common.install
```add 'debian/evolution-common.install' to the end of the file (no quotes ')

```
gedit debian/evolution.install
```add 'debian/tmp/usr/lib/evolution/2.30/conduits/*.so' to the end of the file (no quotes ')


COMPILE & TEST (or install the packages I did below, then test it out):
```

dpkg-buildpackage -rfakeroot

```My own list of errors led me to install the following. 
```

  sudo apt-get install bison cdbs cdbs dh-autoreconf evolution-data-server-dev evolution-data-server-dev evolution-data-server-dev evolution-data-server-dev flex gnome-pkg-tools gtk-doc-tools gtk-doc-tools libcamel1.2-dev libcanberra-gtk-dev libebackend1.2-dev libebackend1.2-dev libebook1.2-dev libecal1.2-dev libecal1.2-dev libedataserverui1.2-dev libegroupwise1.2-dev libegroupwise1.2-dev libexchange-storage1.2-dev libgdata-google1.2-dev libgdata-google1.2-dev libgdata1.2-dev libgdata1.2-dev libgnome-desktop-dev libgnome-pilot2-dev libgnome-pilot2-dev libgstreamer0.10-dev libgstreamer0.10-dev libgtkhtml-editor-dev libgtkhtml3.14-dev libgweather-dev libgweather-dev libical-dev libical-dev libicu-dev libicu-dev libkrb5-dev libldap2-dev liblpint-bonobo-dev liblpint-bonobo-dev libnm-glib-dev libnm-glib-dev libnotify-dev libnotify-dev libnss3-dev libnss3-dev libpst-dev libpst-dev libunique-dev libytnef0-dev libytnef0-dev python-dev python-dev sharutils

```If your system still lacks something, then copy/paste the names of the missing dependencies and 'sudo apt-get install <packagename1> <packagename2> ... <packagenameN>' as above, or use 'apt-cache search' to locate a package name that differs slightly from what the error says.  seydou's walk-through on page 1 is excellent.

INSTALL THE NEWLY MINTED DEBS:
```

cd ..
sudo dpkg -i *.deb

```CLEANUP (delete your work files):
```

cd ..
rm -Rvf evolution-build/ 

```[I]

n00b note: Any of the code above has extensive manuals ('man-pages' accessible by typing 'man <command-name>' and often 'info <command>'.  Most questions (about apt-get or rm or mkdir are answered by 'man apt-get' or 'info rm' etc.

[/I]THAT'S IT.  FINISHED. DONE!

---

### Post by markenaix on 2010-10-31
Hi,

Post from ski_phreak was very useful although I think there is a typo in the editing direction for file:

debian/evolution-common.install

Instead of adding  'debian/evolution-common.install' to the end of the file (no quotes '), 
It works adding 'debian/tmp/usr/share/gnome-pilot' after line 'debian/tmp/usr/share/gnome' (no quotes ').

You should also terminate the pilot_plugin daemon before issuing the last command:

sudo dpkg -i *.deb

Otherwise errors are reported because of a conduit conflict between those already in the daemon and those being installed.

Thanks for the post again. The usual conduits from 10.04 are available now.

---

### Post by markenaix on 2010-11-04
Hi again,

Everything was fine ultill today's security update on Evolution package automatically installed.

Is there a way to keep being updated but in source form so that .deb can be recomplied with the pilot conduits enabled ?

When getting sources (apt-get source evolution) I noticed it is recommended to update with the following command:

bzr get [https://code.launchpad.net/~ubuntu-desktop/evolution/ubuntu]("https://code.launchpad.net/%7Eubuntu-desktop/evolution/ubuntu")

Which I did, but then, after editing the 3 files that need to be modified, i.e. debian/rules, debian/evolution.install and debian/evolution-common.install, the 'dpkg-buildpackage -rfakeroot' command fails with the following message:

dpkg-source: avertissement: le fichier de différences modifie les fichiers amont suivants : 
 .bzr-builddeb/default.conf
 .bzr/README
 .bzr/branch-format
 .bzr/branch/branch.conf
 .bzr/branch/format
 .bzr/branch/last-revision
 .bzr/branch/tags
 .bzr/checkout/conflicts
 .bzr/checkout/format
 .bzr/repository/format
 .bzr/repository/pack-names
dpkg-source: info: choisissez le format « 3.0 (quilt) » pour utiliser des modifications séparées et documentées dans les sources amont, voir dpkg-source(1)
dpkg-source : modifications non représentables des sources
dpkg-buildpackage: erreur: dpkg-source -b ubuntu a produit une erreur de sortie de type 1

Being a newbie, I'm stuck at that point.

Thanks for any help that can be provided.

--Marc

---

### Post by markenaix on 2010-11-06
Hi All,

I've solved my problem following the thread indicated by mcdavey (thanks to him).

Updating gpilot instead of evolution seems to be a better way because of updates.

Indeed, after a few days of successful synchronizations, Evolution updates broke the conduits again and I could not find an easy way to keep updated while keeping the conduits enabling modification.

Thanks,

--Marc

---

### Post by nanoktom on 2010-11-08
Thanks a lot seydou. Your package deal worked for me after a bit of fiddling with some dependency issues.
Evolution and my Treo are talking to each other again now!

---

### Post by KPDXHAM on 2011-02-17
Sorry to ask, but what's the advantage of using Evolution over Thunderbird?:-k  I had thought of using Evolution, but Thunderbird seems to work fine without having to tweak anything. ;)

---

