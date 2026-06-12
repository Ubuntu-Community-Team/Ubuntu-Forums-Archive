---
title: "Compiling Xournal Fork from source, says it needs glib, but thought I had it already?"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by SnickerSnack on 2010-03-01
Hi,

I hope this is the right subforum for my question.

I'm trying to install this fork of Xournal from source: [http://github.com/dmgerman/xournal](http://github.com/dmgerman/xournal)

At first I had trouble with the lack of a configure file, but an email to the person who released it showed me that there was a script (follow the link above and click on autogen.sh) that would make the configure file.  So, I ran the script, and received an error:

```
zsharon@Weierstrass:~/installersNdebs/dmgerman-xournal-42d60c6$ ./autogen.sh 

**Error**: You must have `autoconf' installed.
Download the appropriate package for your distribution,
or get the source tarball at ftp://ftp.gnu.org/pub/gnu/

**Error**: You must have `glib' installed.
You can get it from: ftp://ftp.gtk.org/pub/gtk

**Error**: You must have `automake' installed.
You can get it from: ftp://ftp.gnu.org/pub/gnu/
```

So, I installed autoconf and automake.  But, it seems as though I already have glib.  Synaptic has this listed: libglib2.0-0, and google searching turned up nothing useful.  So I tried again:

```
zsharon@Weierstrass:~/installersNdebs/dmgerman-xournal-42d60c6$ ./autogen.sh 

**Error**: You must have `glib' installed.
You can get it from: ftp://ftp.gtk.org/pub/gtk
```

Then, I followed the url given, but it appears to be outdated.  Some of the links are broken, and the thing that looked closest to what I need appears to be non-existent:

> 0  2001-04-21LATEST-GLIB-1.2.10  29 mirrors

where the zero on the left indicates the file size.

So, what am I to do?

(I know that Xournal is available through apt, but this fork has an added feature that I need.)

I should also point out that the "official" Xournal installs and runs fine.  I'm guessing that the autogen.sh script simply can't find my installation of glib, but I don't know how to be sure of that or how to correct it.

---

### Post by oldos2er on 2010-03-01
It's probably looking for libglib2.0-dev

---

### Post by gsmanners on 2010-03-01
Did you do the following:

sudo apt-get build-dep xournal

That should give you all the packages you need to make that from source.

---

### Post by SnickerSnack on 2010-03-01
> **oldos2er said:**
> It's probably looking for libglib2.0-dev

That did it; thanks!

> **gsmanners said:**
> Did you do the following:

sudo apt-get build-dep xournal

That should give you all the packages you need to make that from source.

Thanks, that's good to know.  libglib2.0-dev was among those packages that would be installed that way.  I opted to install just that package, though, since it was enough.

EDIT:

So, the autogen ran, but then reported that several things were missing.  So, I'm running

sudo apt-get build-dep xournal

We'll see how that goes.

---

### Post by SnickerSnack on 2010-03-01
Firstly, the autogen.sh runs and the last line says: now run make to compile.  Also, ./configure ran fine, so I'm going to go ahead and install, though I'm a bit worried about the things outlined below.  

But (and I don't know if this is impostant), everything ran fine except for this (near the beginning of the autogen.sh output):

```
processing .
Creating ./aclocal.m4 ...
Running glib-gettextize...  Ignore non-fatal messages.
Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).
```

Short version: I found some of the missing files, and I could probably find the rest, but what do I do with them?  I don't understand the directions for the .m4 files, and no direction is given for the config files (I would assume I should put them in the directory where the autogen.sh is).

Longer version:

I found a bunch of .m4 files in /usr/share/aclocal, but none are those listed (which I assume is the problem).  I don't know where/how to get these.

I located codeset.m4 and gettext.m4 here: [https://svn.r-project.org/R/trunk/m4/](https://svn.r-project.org/R/trunk/m4/), but I don't know if these are indeed what I need (or just happen to have the same names), and I would guess that they should go where the rest of the .m4 files are.

I found glibc21.m4 here: [http://cvs.gnupg.org/cgi-bin/viewcvs.cgi/trunk/m4/glibc21.m4?rev=2407&root=GnuPG&view=log](http://cvs.gnupg.org/cgi-bin/viewcvs.cgi/trunk/m4/glibc21.m4?rev=2407&root=GnuPG&view=log).

I found iconv.m4 here: [http://opensource.apple.com/source/gcc/gcc-5483/config/iconv.m4](http://opensource.apple.com/source/gcc/gcc-5483/config/iconv.m4)

Anyway, I can probably find each of them somewhere.  Should that work?  I assume that I should just put them where the others are located.

I found this: > Note that iconv.m4 is also part of the GNU gettext package, which installs it in /usr/local/share/aclocal/iconv.m4. here: [http://www.gnu.org/software/libiconv/](http://www.gnu.org/software/libiconv/).  But, I have gettext installed, and I have no aclocal directory in /usr/local/share.  Plus, there doesn't seem to be a related package.  Running

sudo apt-get build-dep gettext

lists these as needed: default-jdk default-jre default-jre-headless fastjar libcroco3-dev libncurses5-dev libxml2-dev libxt-dev openjdk-6-jdk

I could try installing them, but none seem to be related to what I need.


I have config.guess and config.sub, but I don't know where to put them.  While searching, I found this little tidbit:

> If you don't use automake, append m4/iconv.m4 to your aclocal.m4 file.
If you do use automake, add m4/iconv.m4 to your m4 macro repository. (same place as the earlier quote).  Now, I found aclocal.m4 here /home/zsharon/installersNdebs/sage-4.3.3-linux-32bit-ubuntu_9.10-i686-Linux/local/lib/gap-4.4.12/cnf/aclocal.m4.  Searching this forum, I found this thread: [http://ubuntuforums.org/showthread.php?t=469577](http://ubuntuforums.org/showthread.php?t=469577), which suggests that I should put them in /usr/share/autoconf/autoconf.

I really appreciate any help in fixing this.

EDIT: It runs.  Though, I'd still like to know about those files.

---

### Post by gsmanners on 2010-03-02
Those m4 files are made automatically by autogen when you run that. I didn't notice any special rules for this package, so it should be okay like that.

---

### Post by SnickerSnack on 2010-03-02
> **gsmanners said:**
> Those m4 files are made automatically by autogen when you run that. I didn't notice any special rules for this package, so it should be okay like that.

I guess I forgot the updatedb when I looked for them earlier.  They're there now.  The config. files are present in another directory.

Thanks.

PS Should this thread be marked as SOLVED?  If so, how? EDIT: nevermind, found it.

---

