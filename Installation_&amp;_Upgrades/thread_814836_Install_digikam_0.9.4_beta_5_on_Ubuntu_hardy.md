---
title: "Install digikam 0.9.4 beta 5 on Ubuntu hardy"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by quickk on 2008-05-31
In case anyone wants to install the digikam 0.9.4 beta 5 on Ubuntu hardy, it is possible:

First, install digikam 0.9.3 from synaptic.  

Next you have to download and compile the 0.9.4 beta version yourself (get it from: [http://sourceforge.net/project/showfiles.php?group_id=42641]("http://sourceforge.net/project/showfiles.php?group_id=42641"))

To compile, follow these instructions: (which I got from the help file).  My added instructions are in bold.

The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.  If you're
     using `csh' on an old version of System V, you might need to type
     `sh ./configure' instead to prevent `csh' from trying to execute
     `configure' itself.

     Running `configure' takes awhile.  While running, it prints some
     messages telling which features it is checking for.
 
     **When I did this, the script found a bunch of missing programs.  It provided links to get the missing dependencies.  Instead, just open up the synaptic package manager, and search for the missing things.  You'll probably find that they are already installed.  Just install the "dev" versions also and everything should be ok.**


  2. Type `make' to compile the package.

    **When I did this, the make failed because it could not find a certain file.  Once again, open synaptic package manager and search for the file.  Make sure that the "dev" version is installed.  Once I did this, everything worked.  It took about 20 minutes to compile.**

  3. Optionally, type `make check' to run any self-tests that come with
     the package.

  4. Type `make install' to install the programs and any data files and
     documentation.
[B]
You might have to type "sudo make install" for this to work.  Once this was done, I could start digikam 0.9.4 beta 5 by simply selecting it from the applications menu entry that was originally created for digikam 0.9.3.
[/B]


  5. You can remove the program binaries and object files from the
     source code directory by typing `make clean'.  To also remove the
     files that `configure' created (so you can compile the package for
     a different kind of computer), type `make distclean'.  There is
     also a `make maintainer-clean' target, but that is intended mainly
     for the package's developers.  If you use it, you may have to get
     all sorts of other programs in order to regenerate files that came
     with the distribution.

---

### Post by bapoumba on 2008-06-01
Moved to its own thread from [http://ubuntuforums.org/showthread.php?t=814563]("http://ubuntuforums.org/showthread.php?t=814563").

---

