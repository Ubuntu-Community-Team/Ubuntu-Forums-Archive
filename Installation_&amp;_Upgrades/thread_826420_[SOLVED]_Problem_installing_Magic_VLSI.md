---
title: "[SOLVED] Problem installing Magic VLSI"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by jelson on 2008-06-11
I decided to install this because running this program via SSH on my school's Solaris 5.9 machines has been causing problems, notably the program fails after awhile (probably my doing).  Anyway, to make things simpler, I'm trying to run the program on my own machine, and I'm having some problems. Here's what happens when I run ./configure in the magic-7.5 directory:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking for library containing strerror... none required
checking for a BSD-compatible install... /usr/bin/install -c
checking for ranlib... ranlib
checking for gm4... no
checking for gnum4... no
checking for m4... no
configure: error: M4 is required

Well, I tried installing what I thought would fix the problem, m4-1.4.9, but still no joy.  I was going to try and install Solaris 10, but my computer and Solaris don't get along, and OpenSolaris has issues with some of my hardware, thus why I'm trying to do this in Ubuntu.  Are there any suggestions?  Should I switch to Red Hat, or rather, Fedora?

-edit- Ok I made a mistake, I did not install m4 on my system.  I was able to do the ./configure, and then the make, but when I typed make install, I got this:  
(saving you the trouble, blah blah blah,
blah blah blah
..
..
..
finally, near the end it says:
test -z "/usr/local/bin" || /bin/mkdir -p "/usr/local/bin"
  /usr/bin/install -c 'm4' '/usr/local/bin/m4'
/usr/bin/install: cannot create regular file `/usr/local/bin/m4': Permission denied
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/jeff/m4-1.4.10/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/jeff/m4-1.4.10/src'
make: *** [install-recursive] Error 1

Any ideas?

- edit again
I seem to be fixing my problems just by typing things on a forum, even if I don't get a response.  I found m4 1.4.10 using Synaptic and installed it.  I was able to do the ./configure, the make, but when I get this lovely mess:
--- errors and warnings logged in file make.log
--- making header file database/database.h
jeff@jeff-laptop:~/magic-7.5$ make install
--- installing executable to /usr/local/bin
--- installing runtime files to /usr/local/lib
mkdir: cannot create directory `/usr/local/lib/magic': Permission denied
mkdir: cannot create directory `/usr/local/lib/magic/sys': No such file or directory

...and it basically repeats this over and over again.  Thanks for the help!

---

### Post by Partyboi2 on 2008-06-11
use sudo infront of make install
```
sudo make install
```

---

### Post by jelson on 2008-06-11
No joy. I tried that already, and I'm still getting errors.  There seems to be some sort of problem with Tx....  In both the make.log and the install.log it keeps repeating things like:
/home/jeff/magic-7.5/tcltk/tclmagic.c:611: multiple definition of `TxDialog'
../textio/libtextio.o:/home/jeff/magic-7.5/textio/txInput.c:325: first defined here
../tcltk/libtcltk.o: In function `TxSetPrompt':
/home/jeff/magic-7.5/tcltk/tclmagic.c:672: multiple definition of `TxSetPrompt'
../textio/libtextio.o:/home/jeff/magic-7.5/textio/txInput.c:369: first defined here
../tcltk/libtcltk.o: In function `TxFlushOut':
/home/jeff/magic-7.5/tcltk/tclmagic.c:805: multiple definition of `TxFlushOut'
../textio/libtextio.o:/home/jeff/magic-7.5/textio/txOutput.c:267: first defined here
../tcltk/libtcltk.o: In function `TxStopMore':
/home/jeff/magic-7.5/tcltk/tclmagic.c:660: multiple definition of `TxStopMore'
../textio/libtextio.o:/home/jeff/magic-7.5/textio/txOutput.c:441: first defined here
../tcltk/libtcltk.o: In function `TxFlushErr':

Finally, at the bottom I get "make[2]: *** [tclmagic.so] Error 1"
This is both in the make.log, and in the terminal when I do sudo make install.

It actually acts as if it installed, but when I run magic, I get a tkcon 2.3 and a tkcon.tcl window that pops up, and the tkcon 2.3 main window says:
loading history file ... 0 events added
error in slave eval:
couldn't load file "/usr/local/lib/magic/tcl/tclmagic.so": /usr/local/lib/magic/tcl/tclmagic.so: cannot open shared object file: No such file or directory
Main console display active (Tcl8.4.16 / Tk8.4.16)
(bin) 1 % 

What I should get (at least of the computers at school is something that looks like this:
[ATTACH]73750[/ATTACH]

---

### Post by Partyboi2 on 2008-06-12
Another way to install magic is to add
```

deb [http://ppa.launchpad.net/aanjhan/ubuntu](http://ppa.launchpad.net/aanjhan/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/aanjhan/ubuntu](http://ppa.launchpad.net/aanjhan/ubuntu) hardy main
``` to your sources.list (System>Admin>Software Sources>3rd Party)
then 
```
sudo apt-get install magic
```

---

### Post by jelson on 2008-06-12
Ok, it seemed to work. It said:
Get:1 [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy/main magic 7.5.129-0ubuntu2 [1712kB]
Fetched 1712kB in 2s (610kB/s)  
Selecting previously deselected package magic.
(Reading database ... 118715 files and directories currently installed.)
Unpacking magic (from .../magic_7.5.129-0ubuntu2_i386.deb) ...
Setting up magic (7.5.129-0ubuntu2) ...
me@me-laptop:

I don't know if that means it has installed or not.  When I go cd /usr/local/bin, then type in magic, I get the same results.

---

### Post by Partyboi2 on 2008-06-12
in the terminal type
```
magic
```

---

### Post by jelson on 2008-06-12
That's just a quicker way to get to the same error it looks like.  I get a tkcon 2.3 Main window that says:
loading history file ... 0 events added
error in slave eval:
couldn't load file "/usr/local/lib/magic/tcl/tclmagic.so": /usr/local/lib/magic/tcl/tclmagic.so: cannot open shared object file: No such file or directory
Main console display active (Tcl8.4.16 / Tk8.4.16)
(jeff) 1 % 

and then I have a tkcon.tcl #2 window that has absolutely nothing in it.  Of course the school was using magic 6.9, so what I'm used to seeing and what I should be seeing now may be two different things, but I'm pretty sure this isn't right.

---

### Post by jelson on 2008-06-12
I think I know what the problem is, though I don't know how to fix it.  I have at least two magic executables, one in /usr/local/bin, and the other in /usr/bin.  I think I need to uninstall the one in /usr/local/bin, but I don't know how.  As a matter of fact, I should probably uninstall all magic files and folders and start from scratch, you think?

---

### Post by Partyboi2 on 2008-06-12
worth a shot :)

---

### Post by jelson on 2008-06-12
Ummm, okay, I'm an uber newb, so I need a little help with that, also.  I noticed I can't just delete the magic files from my directory, it doesn't let me.  So, how do I uninstall magic?

---

### Post by Partyboi2 on 2008-06-12
to remove the deb package that you installed
```
sudo apt-get remove magic
```to remove the one you compiled
cd into the directory and
```
sudo make uninstall
```

Edit: If you want to remove the config files for the deb package as well use --purge
```
 sudo apt-get remove --purge magic
```

---

### Post by jelson on 2008-06-12
Hmmm... when I do sudo make uninstall, it says "make: *** No rule to make target 'uninstall'. Stop.

---

### Post by jelson on 2008-06-12
Yay!  It works, now!  I had to delete my entire partition and reinstall ubuntu to get it to work, though.  That's okay, because this program is pretty much the whole reason I installed ubuntu in the first place!  The only problem is that my school was using magic 6.5, and this is 7.5, and I sort of don't really know how to get this version to work.  Hopefully the files are cross-compatible.  Anyway, in 6.5, all of the commands are done from the terminal, but in 7.5, it appears they all come from a tkcon terminal.  The normal command :rsim doesn't appear to do anything, unfortunately, so I'll have to relearn how to use this program.

---

### Post by jelson on 2008-06-12
Well, it looks like magic doesn't automatically come with irsim, so I have to install that as well.  I found on the web an irsim version 9.7.66, and when I went to perform ./configure from within the directory, I got this:

checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

I'm attaching the config.log file

---

### Post by jelson on 2008-06-14
Well my problem is completely solved, and I'm going to post info for everyone who might encounter the same problem again.  The deb packages that Partyboi2 referred me to worked great for installing magic, as well as the deb packages he sent to me through a private message.  I'm going to go ahead and post them, and I hope this is all right with Partyboi2, so that others can benefit from his good work.  The deb package install instructions were posted earlier, and [here]("http://www.mediafire.com/?jremix2fnlz") is the link to the deb package he made to install IRSIM.  Thanks again for all your help, partyboi2!

---

