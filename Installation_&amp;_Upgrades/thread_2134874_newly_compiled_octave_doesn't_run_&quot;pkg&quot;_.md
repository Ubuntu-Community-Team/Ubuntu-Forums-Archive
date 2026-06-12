---
title: "newly compiled octave doesn't run &quot;pkg&quot; command"
date: 2013-04-12
forum: Installation &amp; Upgrades
---

### Post by paatryk on 2013-04-12
Hi,  I have successfully compiled Octave 3.6.3 in Ubuntu 10.04.  Octave now resides in **[FONT=courier new]$HOME/octave-installs/octave-3.6.3 [/FONT]**and can be run using **[FONT=courier new]run-octave[/FONT]** executable script there.  However, when I download a package from [http://octave.sourceforge.net/general/index.html](http://octave.sourceforge.net/general/index.html) and place it in the above mentioned directory thre is a problem installing this package.

The commands:
**pkg install -auto general-1.3.2.tar.gz**
and
**   pkg install -forge general**
both give:

> 
__exit__.cc:16:24: error: octave/oct.h: No such file or directory
__exit__.cc:21: error: expected constructor, destructor, or type conversion before &#8216;(&#8217; token
make: *** [__exit__.oct] Error 1
'make' returned the following error: make: Entering directory `/tmp/oct-derZda/general/src'
/usr/local/bin/mkoctfile-3.6.3 __exit__.cc
make: Leaving directory `/tmp/oct-derZda/general/src'
error: called from `pkg>configure_make' in file /home/patryk/octave-installs/octave-3.6.3/scripts/pkg/pkg.m near line 1385, column 9
error: called from:
error:   /home/patryk/octave-installs/octave-3.6.3/scripts/pkg/pkg.m at line 827, column 5
error:   /home/patryk/octave-installs/octave-3.6.3/scripts/pkg/pkg.m at line 383, column 9


[FONT=arial]A file "octave/oct.h" and "[/FONT][FONT=arial]oct.h[/FONT][FONT=arial]" itself are here:
[/FONT][B][FONT=courier new]   $HOME/octave-installs/octave-3.6.3/octave/oct.h
[/FONT][/B][FONT=arial]and here:[/FONT][B][FONT=courier new]
[/FONT][/B]**[FONT=courier new]   $HOME/octave-installs/octave-3.6.3/src/oct.h[/FONT]**
[FONT=courier new][FONT=arial]and they are identical 1.1 kB scripts.

My problem may be the directory-tree organization.  HELP!  I need newest Octave due to some of package dependencies.

Any ideas? Suggestions?[/FONT][/FONT]

---

### Post by paatryk on 2013-04-15
Any ideas or suggestions, please?

---

### Post by steeldriver on 2013-04-15
Hmm well I hoped to be able to troubleshoot this for you but it appears to work just fine in the same scenario on a version of 3.6.3 that I built from source some time ago in a Mint VM (Linux mint-vm 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux)

```
steeldriver@mint-vm ~/src/octave-3.6.3 $ ls
aclocal.m4  BUGS       config.h     config.status  COPYING  examples              INSTALL.OCTAVE  liboctave  Makefile     NEWS        run-octave.in  stamp-h1
AUTHORS     build-aux  config.h.in  configure      doc      **general-1.3.2.tar.gz**  libcruft        libtool    Makefile.am  README      scripts        test
autogen.sh  ChangeLog  config.log   configure.ac   etc      INSTALL               libgnu          m4         Makefile.in  run-octave  src
steeldriver@mint-vm ~/src/octave-3.6.3 $ 
steeldriver@mint-vm ~/src/octave-3.6.3 $ **./run-octave**
GNU Octave, version 3.6.3
Copyright (C) 2012 John W. Eaton and others.

<SNIP>

[B]octave:1> pkg list
no packages installed.
octave:2> pkg install -auto general-1.3.2.tar.gz
warning: creating installation directory /home/steeldriver/octave
For information about changes from previous versions of the general package, run 'news ("general")'.
octave:3> pkg list
Package Name  | Version | Installation directory
--------------+---------+-----------------------
     general *|   1.3.2 | /home/steeldriver/octave/general-1.3.2
[/B]octave:4> exit
steeldriver@mint-vm ~/src/octave-3.6.3 $
steeldriver@mint-vm ~/src/octave-3.6.3 $ **ls ~/octave/general-1.3.2/**
adresamp2.m  doc-cache                   @inputParser  packinfo       parcellfun.m  safeprod.m  unresamp2.m  ztvals.m
@dict        i686-pc-linux-gnu-api-v48+  majle.m       pararrayfun.m  private       tablify.m   unvech.m

```

The only thing I can think that might be different (apart from that I am based on a 3.x kernel) is that I did a complete configure - make - make install i.e. as well as the local ./run-octave (which gets created at the 'make' stage) I have an actual install in /usr/local:

```
steeldriver@mint-vm ~/src/octave-3.6.3 $ find . -name 'oct.h'
./src/oct.h
steeldriver@mint-vm ~/src/octave-3.6.3 $ find /usr/local -name 'oct.h'
/usr/local/include/octave-3.6.3/octave/oct.h

```  

i.e. maybe 'pkg install' is expecting to find headers in the *--prefix=whatever* dir that you specified to ./configure (in my case, the default /usr/local)?


[COLOR=#0000ff]EDIT: yes that seems to be it - at least, if I move the installed /usr/local/ files somewhere else I get the same error as you:

```
steeldriver@mint-vm ~/src/octave-3.6.3 $ sudo mkdir /opt/include
steeldriver@mint-vm ~/src/octave-3.6.3 $ sudo mv /usr/local/include/octave-3.6.3/ /opt/include
steeldriver@mint-vm ~/src/octave-3.6.3 $ sudo mkdir /opt/lib
steeldriver@mint-vm ~/src/octave-3.6.3 $ sudo mv /usr/local/lib/octave/ /opt/lib/
```

```
octave:1> pkg uninstall general
octave:2> pkg list
no packages installed.
octave:3> pkg install -auto general-1.3.2.tar.gz
__exit__.cc:16:24: fatal error: octave/oct.h: No such file or directory
compilation terminated.
make: *** [__exit__.oct] Error 1
'make' returned the following error: make: Entering directory `/tmp/oct-59tHhR/general/src'
/usr/local/bin/mkoctfile-3.6.3 __exit__.cc
make: Leaving directory `/tmp/oct-59tHhR/general/src'
error: called from `pkg>configure_make' in file /home/steeldriver/src/octave-3.6.3/scripts/pkg/pkg.m near line 1385, column 9
error: called from:
error:   /home/steeldriver/src/octave-3.6.3/scripts/pkg/pkg.m at line 827, column 5
error:   /home/steeldriver/src/octave-3.6.3/scripts/pkg/pkg.m at line 383, column 9
```[/COLOR]

---

### Post by paatryk on 2013-04-19
Hey [**[COLOR=#000000]Steeldriver[/COLOR]**]("http://ubuntuforums.org/member.php?u=1627500")!
You are a genius!  You have helped me with getting out of a silly but long lasting deadlock.  I feel enlightened ;-)  Now I can do this outstanding, but important one part of the simulations for my thesis - thanks to you.

My PROBLEM WAS: I left out "**sudo make install**" before running octave.  And after I executed "sudo make install" everything started working perfectly.  I'm ashamed to make this RTFM-type mistake.

Man, your keen interest and your intention to help me by devoting your time was SOOO generous and helpful.  You have made me greatly indebted to the community, so if I come across someone else's problem, I will do my best to make the wheel of help-and-support spin and will devote my time too.  All the best!

---

