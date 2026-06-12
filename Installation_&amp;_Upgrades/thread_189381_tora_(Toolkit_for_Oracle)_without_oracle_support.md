---
title: "tora (Toolkit for Oracle) without oracle support???"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by jonas_larson on 2006-06-05
Hi,

I just installed Ubuntu 6.06 and was a happy camper...

Then I installed the tora package, fired it up and found...

postgreSQL support only... :confused: 

Tora (Toolkit for ORAcle = tora)...

Why is that?

Then I tried to compile it myself with no luck... 

Anybody that is running tora out there that can give me a hand?

//jonas

---

### Post by element on 2006-06-08
I have the same problem.  Ive been using SqlDeveloper from Oracle till I can figure out Tora.
[http://www.oracle.com/technology/products/database/sql_developer/index.html]("http://www.oracle.com/technology/products/database/sql_developer/index.html")

---

### Post by jonas_larson on 2006-06-08
Crap!

I really want ubuntu to shine over my "normal" distro (gentoo) but the little things just tick me off...

But thats just me I guess... 8-) 

I still think ubuntu is going places and we use it at work so I'm gonna find a solution to this and post here...

I'll be back... 

//jonas

---

### Post by kavanutz on 2006-06-16
i had to compile it, but this worked for me

> export ORACLE_HOME=<path to the oracle client installation>
> export LD_LIBRARY_PATH=$ORACLE_HOME/lib
> cd /usr/src
> apt-get source tora
> cd tora-1.3.18
> vi debian/rules 

and change the following line 

./configure --prefix=/usr --without-oracle --without-rpath --disable-new-check --with-kde --enable-libsuffix=

to 

./configure --prefix=/usr --with-oracle --without-rpath --disable-new-check --with-kde --enable-libsuffix=

> debian/rules binary
> dpkg -i ../tora_1.3.18-4ubuntu1_i386.deb

and that should be it.

now tora always shows up in synaptic as needing to be updated, but at least its installed!!

---

### Post by thermans on 2006-07-05
See [here]("http://www.benpinter.net/article.php?story=20051208034638928") for full details on compiling Tora with Oracle support.

To stop Synaptic from trying to upgrade it everytime, higlight Tora in the Synaptic list, then click the "Package" menu and select "Lock Version".

---

### Post by nwgray on 2006-07-07
[QUOTE=kavanutz;1145626]i had to compile it, but this worked for me

> apt-get source tora

Can't get the source. I get this error:

sudo apt-get source tora
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for tora


Anyone know which repo I should add? Where else can I get it?

thx

---

### Post by DSn0wMan on 2006-07-07
You can get the source here.

[http://sourceforge.net/project/showfiles.php?group_id=16636&package_id=25533](http://sourceforge.net/project/showfiles.php?group_id=16636&package_id=25533)

---

### Post by DSn0wMan on 2006-07-08
I can get the debian/rules binary to run until it chokes on qscintilla.

checking for qscintilla... configure: error: Couldn't compile a simple QScintilla application. See config.log or specify its location with --with-qscintilla-includes

First question what the heck is qscintilla?

I thought it might want the qt3 includes, but that didn't work.

slocate finds some libs in qt3 directories, but no includes.

What am I missing? It's probably obvious.

---

### Post by nwgray on 2006-07-11
I had the same issue. Using synaptic, i found the following package:

libqscintilla-dev

I installed that and then did a make. It took forever, but it did finish. I then used Checkinstall to install. However, I still only have Postgres listed when I start Tora. I have SQL Developer running and I can connect to my Oracle db but I'd rather have Tora. I use Toad on windows now. 

I keep getting one step closer. one day, I may be able to totally switch to Ubuntu or another distro and only use Windows to run Qemu and DSL.

Anyone have any thoughts? I have made sure that the rules file includes the ref to instant-client. I have installed the instant-client too but it doesn't connect either. Could be because I'm running Oracle 9i but I would think that it could connect anyway but with reduced functionality.

L8R

---

### Post by DSn0wMan on 2006-07-11
Thanks for the help. Tora is now working for me.
 
I am using Oracle XE 10.0.1 locally. No need for instant-client.

Here are the agruments I used

./configure --prefix=/u01/app/tora --with-oci-version=10G --without-kde

---

### Post by Jivicin on 2006-08-24
I managed to get TOra up and running, but am still having trouble getting it to work with Oracle.  I compiled it using the options for Oracle support, but when I start TOra, the only selection option I have is for MySQL.

I also get this error when I try to fire it up, but it still works:
```
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

I'm not sure if that has anything to do with my problem or not.

Any ideas?

---

### Post by nwgray on 2006-09-22
trying compile this again, i get this error:

:/usr/src/tora-1.3.18$ sudo debian/rules binary 
dh_testdir
make: dh_testdir: Command not found
make: *** [configure-stamp] Error 127


I've never seen this make error before. Any Ideas?

Thx

---

### Post by spiderwort on 2006-09-24
nwgray, you need to install debhelper to get rid of that error.

I have been following the instructions that thermans pointed to in post #5 of this thread. I have the Oracle instant client installed. My current hurdle that I have not been able to leap looks like this (this is in the debian/rules binary step):

checking for oracle... checking oci works... configure: error: Couldn't compile and run a simpile OCI app.
      Try setting ORACLE_HOME or check config.log.
      Otherwise, make sure ORACLE_HOME/lib is in /etc/ld.so.conf or LD_LIBRARY_PATH
make: *** [configure-stamp] Error 1


I have ORACLE_HOME, LD_LIBRARY_PATH, and TNS_ADMIN all pointing to the top of the instant client install.

Anyone have any suggestions?

---

### Post by nwgray on 2006-09-24
spiderwort
   Thx for the info on debhelper. I installed it and then I noticed that if you copy and paste pinter's text from the webpage, it doesn't have the -- that is needed in the rules file. I changed this:

./configure –prefix=/usr –with-instant-client –without-rpath –disable-new-check –without-kde –enable-libsuffix=

with this:

./configure –prefix=/usr --with-instant-client --without-rpath --disable-new-check --without-kde --enable-libsuffix=

and I'm almost there. I get an Oracle-includes error. Here's the term output from my debian/rules binary run:

checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output...
checking for a BSD-compatible install... /usr/bin/install -c -p
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ./configure: line 5783: s/^[ABCDGIRSTW][ABCDGIRSTW]* \(.*\) \(.*\)$/  {"\2", (lt_ptr_t) \&\2} ,/: No such file or directory
ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc static flag  works... yes
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for unistd.h... (cached) yes
checking sys/param.h usability... yes
checking sys/param.h presence... yes
checking for sys/param.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking time.h usability... yes
checking time.h presence... yes
checking for time.h... yes
checking sys/mkdev.h usability... no
checking sys/mkdev.h presence... no
checking for sys/mkdev.h... no
checking sys/sysmacros.h usability... yes
checking sys/sysmacros.h presence... yes
checking for sys/sysmacros.h... yes
checking for string.h... (cached) yes
checking for memory.h... (cached) yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking dirent.h usability... yes
checking dirent.h presence... yes
checking for dirent.h... yes
checking sys/ndir.h usability... no
checking sys/ndir.h presence... no
checking for sys/ndir.h... no
checking ndir.h usability... no
checking ndir.h presence... no
checking for ndir.h... no
checking alloca.h usability... yes
checking alloca.h presence... yes
checking for alloca.h... yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking whether time.h and sys/time.h may both be included... yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking for struct utimbuf... yes
checking whether sys/types.h defines makedev... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for snprintf... yes
checking for vsnprintf... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking whether struct tm is in sys/time.h or time.h... time.h
checking for struct stat.st_blocks... yes
checking for dirent.h that defines DIR... yes
checking for library containing opendir... none required
checking whether closedir returns void... no
checking for size_t... yes
checking enable plugin support... no
checking if monolithic build... no
checking whether to link plugins into binary... need link
not using lib directory suffix
checking for extra includes... no
checking for extra libs... no
checking for X... libraries /usr/X11R6/lib, headers in standard search path
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for pthread_create in -lpthread... yes
checking for libz... -lz
checking have kde... no
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for Qt... checking for X... libraries /usr/X11R6/lib, headers
checking for IceConnectionNumber in -lICE... (cached) yes
checking for libXext... yes
checking for Xinerama... no

      libqt:     -lqt-mt -lpng -lz -lm -ljpeg  -lSM -lICE -lXext -lX11 -lSM -lIC E ,
      libraries: /usr/lib,
      headers:   /usr/include/qt3 using -mt
checking for lrelease... /usr/bin/lrelease
checking for lupdate... /usr/bin/lupdate
checking for moc... /usr/bin/moc
checking for uic... /usr/bin/uic
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if STL implementation is SGI like... yes
checking for oracle... configure: error: /usr/include/oracle/tnsnames.ora/client  doesn't exist. Please install the sdk package or use --oracle-includes.
make: *** [configure-stamp] Error 1


I dont' know where the ref for oracle is coming from. Any ideas?

Thx

---

### Post by spiderwort on 2006-09-24
Even though this is _supposed_ to work gracefully with the instant client, I'm finding that it doesn't seem to. I've come up with some work-arounds. My configure line in debian/rules now looks like this:

./configure --prefix=/usr --with-instant-client --without-rpath --disable-new-check --without-kde --with-oracle-includes=/usr/lib/oracle/sdk/include --with-oracle-libraries=/usr/lib/oracle --enable-libsuffix=

I also added some symbolic links within the instant client directories:
ln -s /usr/lib/oracle /usr/lib/oracle/bin   # needs this to find sqlplus
ln -s libclntsh.so.10.1 libclntsh.so    # needs this to find the libclntsh library
ln -s libocci.so.10.1 libocci.so   # just to make sure it doesn't complain :-)

I've got it to ths point where it is complainig about qscintilla. I saw a post about that somewhere.......hope I can find it again.....

Edit: Duh! Install libqscintilla-dev! It is now compiling.....NO idea how long it will take!

---

### Post by nwgray on 2006-09-25
Spiderwort,
   When I changed my ./configure line to match yours, I get this error:

checking for oracle... checking oci works... configure: error: Couldn't compile and run a simpile OCI app.
      Try setting ORACLE_HOME or check config.log.
      Otherwise, make sure ORACLE_HOME/lib is in /etc/ld.so.conf or LD_LIBRARY_PATH
make: *** [configure-stamp] Error 1

I dont' have an sdk directory under oracle and I set the links that you have listed below:

ln -s /usr/lib/oracle /usr/lib/oracle/bin   # needs this to find sqlplus
ln -s libclntsh.so.10.1 libclntsh.so    # needs this to find the libclntsh library
ln -s libocci.so.10.1 libocci.so   # just to make sure it doesn't complain :-)

Where do I get the sdk stuff? How can I verify what my Oracle_home is set to? I followed pinter's stuff but I want to make sure.

Thx

---

### Post by spiderwort on 2006-09-26
nwgray, to answer your specific issue, the sdk stuff is part of the Oracle Instant Client. There are 3 separate pieces you need to install.

I have actually gotten my TOra talking to my Oracle database....8i, no less! That version is a little long in the tooth, and I would expect to have the most trouble with it rather than a newer version.

Here are the step-by-step instructions I went through. This is for a fairly straightforward Dapper installation. YMMV, etc. I assume a certain amount of basic knowledge....

- Download Oracle Instant Client from OTN
- Unzip basic & sqlplus & sdk into "some directory somewhere"
- Copy tnsnames.ora & sqlnet.ora to "some directory somewhere" (if you copy it over from Windows MAKE SURE the line termination character is correct...I don't know how many times this one has bitten me....do a hex dump on it if you have to!)
- Create symlink /usr/lib/oracle pointing to "some directory somewhere"/instantclient_xx (this is the directory created by unzipping the OTN download)
- ln -s /usr/lib/oracle /usr/lib/oracle/bin # this is so that configure will find sqlplus to get the Oracle version
- ln -s libclntsh.so.10.1 libclntsh.so # this is so that configure will find this library
- ln -s libocci.so.10.1 libocci.so # preventive....just in case
- Edit (or create) /etc/ld.so.conf, add /usr/lib/oracle
- Reload library cache: sudo ldconfig
- Edit ~/.bashrc, add:
	- LD_LIBRARY_PATH=/usr/lib/oracle:$LD_LIBRARY_PATH
	- export TNS_ADMIN=/usr/lib/oracle
	- export ORACLE_HOME=/usr/lib/oracle
- re-login or open new terminal window (this picks up the new environment variables from your .bashrc)
- Install TOra (apt-get install tora) (this installs a whole bunch of dependencies for you)
- Get TOra source (cd /usr/src; apt-get source tora) (better: get source from sourceforge....some fixes have been applied for instant client) [EDIT 10/9/2006: **Since it has been reported that the Dapper source does not work, don't use it with these instructions**]
- Get build tools:
	- g++
	- gcc
	- autoconf
	- automake
	- flex
	- zlib1g-dev
	- docbook-xsl
	- libqt3-mt-dev
	- libq3-compat-headers
	- debhelper
	- libqscintilla-dev
- In TOra source tree, edit debian/rules:
	./configure --prefix=/usr --with-instant-client --without-rpath --disable-new-check --without-kde --with-oracle-includes=/usr/lib/oracle/sdk/include --with-oracle-libraries=/usr/lib/oracle --enable-libsuffix=
- from source directory: debian/rules binary
- ~ 45 minutes to compile
- End up with a .deb package just above source directory
- Remove TOra installed above (use synaptic or sudo apt-get remove ...)
- Install new package: dpkg -i tora_1.3.21-1_i386.deb (or whatever your file ended up being called)
- Test out your instant client setup: sqlplus schema_name/password@database.name.in.tnsmames.ora
- If that works, try starting up TOra from command line from same directory as where tnsnames.ora lives

Good luck!

---

### Post by nwgray on 2006-09-27
I get this when trying to compile:

debian/rules:22: *** commands commence before first target.  Stop.

?

---

### Post by nwgray on 2006-09-27
okay, fixed that problem but I'm still getting this error after about two minutes of compiling:

checking for oracle... checking oci works... configure: error: Couldn't compile and run a simpile OCI app.
      Try setting ORACLE_HOME or check config.log.
      Otherwise, make sure ORACLE_HOME/lib is in /etc/ld.so.conf or LD_LIBRARY_PATH
make: *** [configure-stamp] Error 1

This is from the config.log 

configure:32474: gcc -o conftest -g -O2 -I/usr/lib/oracle/instantclient_10_2/sdk/include   -L/usr/lib/oracle/instantclient_10_2 conftest.c -lclntsh >&5
/usr/bin/ld: cannot find -lclntsh
collect2: ld returned 1 exit status

---

### Post by spiderwort on 2006-09-28
Oops....looks like you didn't read my mind when I typed up those lousy instructions :-). I have adjusted them....your symbolic link in /usr/lib which is called oracle should point to the directory which was created when you unzipped the instant client download. Thus, "some directory somewhere"/instantclient_xx (where xx is whatever version).

Also, make certain you have the symbolic link libclntsh.so pointing to libclntsh.so.10.1. But it is possible it is getting confused because /usr/lib/oracle is one level too high.

Let me know how it goes....sorry you have to be the guinea pig on my instructions.

---

### Post by nwgray on 2006-09-29
spiderwort
   Still getting the same error. I have installed sqldeveloper and it works like a champ. I also installed the xe client from the repos and can connect to my db via sqlplus command line. I just wish Tora would work. I will keep trying following your instructions and may even try a clean install on another machine to have a "nothing installed related to Oracle" environment. Thx for all of your help. Your instructions are very well written. I am still just learning and am probably either overlooking something easy or just plain screwing it up. I will post back if/when I get it working or at least get past that OCI error.

Thx again and have a great weekend!

---

### Post by ryanov on 2006-10-04
The above instructions will NOT work with the version of tOra that comes with Dapper ( 1.3.18 ). ](*,) What appears to be working (time will tell) is downloading the source package from the "edgy" universe repository (this is v1.3.21ubuntu3).

Once you've downloaded the .dsc, the .orig.tar.gz and the .diff.gz files, you run dpkg-src -x filename.dsc and do the same set of steps as the gentleman above lists. I've got the thing building right now, anyway, and I have no reason to believe that it won't work when I'm done.

---

### Post by spiderwort on 2006-10-09
ryanov, I'm sorry you banged your head over the Dapper source. I never used it...I figured that if I had to go to the trouble of compiling from source, I might as well get the latest-and-greatest, especially as the release notes indicated there had been fixes related to the Oracle Instant Client. I have added an additional note to my instructions.

You'll have to let us know of your success....or not...with the Edgy source.

---

### Post by paschalis_sp on 2007-02-13
Try the following:

a) Get tora source package  tora-1.3.21.tar.gz from tora official site
[http://sourceforge.net/project/showfiles.php?group_id=16636&package_id=25533&release_id=396090](http://sourceforge.net/project/showfiles.php?group_id=16636&package_id=25533&release_id=396090)

b) Untar the tora package.

c) Install gcc-2.95, libxinerama1, libxinerama1-dev with synaptic.

d) Configure tora as follows:
./configure --with-oracle=$ORACLE_HOME --with-oci-version=10G CC=gcc-2.95 --without-kde --with-xinerama

e) make 

f) sudo make install

---

### Post by KeighleHawk on 2007-03-15
> **paschalis_sp said:**
> Try the following:

a) Get tora source package  tora-1.3.21.tar.gz from tora official site
[http://sourceforge.net/project/showfiles.php?group_id=16636&package_id=25533&release_id=396090](http://sourceforge.net/project/showfiles.php?group_id=16636&package_id=25533&release_id=396090)

b) Untar the tora package.

c) Install gcc-2.95, libxinerama1, libxinerama1-dev with synaptic.

d) Configure tora as follows:
./configure --with-oracle=$ORACLE_HOME --with-oci-version=10G CC=gcc-2.95 --without-kde --with-xinerama

e) make 

f) sudo make install


With the exception of having to install additional libraries mentioned earlier by spiderwort, this worked for me.

P.S.  Don't know if it made a difference but while installing some of the listed libraries, I saw some specific to MySQL and ODBC and added those.  That support also shows in TOra now (woohoo!)

P.P.S.  FWIW, I noticed (too late) the original install of TOra I did (via Synaptic) installed to /usr/bin and the compile from source installed to /usr/local/tora.  So don't trick yourself into thinking it did not install by running the old version!

---

### Post by marianom on 2007-03-15
I can too confirm that the trick was to use $ORACLE_HOME in the configuration line to make it work.

---

### Post by marianom on 2007-03-16
> **KeighleHawk said:**
> P.S.  Don't know if it made a difference but while installing some of the listed libraries, I saw some specific to MySQL and ODBC and added those.  That support also shows in TOra now (woohoo!)

Care to share where did you find it (I checked the --help but didn't see it) and how to enable the support?

By the way, I'm having post installation issues but I'll post a new thread to keep this one on installation issues.

---

### Post by marianom on 2007-03-16
[Here's]("http://www.ubuntuforums.org/showthread.php?p=2307796") my post with post installation issues. If somebody can help, I appreciate it.

---

### Post by KeighleHawk on 2007-03-16
> **marianom said:**
> Care to share where did you find it (I checked the --help but didn't see it) and how to enable the support?

By the way, I'm having post installation issues but I'll post a new thread to keep this one on installation issues.

When I searched for libqt3-mt I noticed libqt3-mt-mysql, odbc, psql and sqlite, so I selected all of those while I was at it...

---

### Post by marianom on 2007-03-16
I can see them now, thanks for that.

---

### Post by marianom on 2007-03-23
I uploaded my deb package for tora 1.3.21 that I built with checkinstall. I built it in my pc and then installed it in a laptop and it worked ok.

I compiled it with the following instructions:

```
sudo auto-apt run ./configure --with-oracle=$ORACLE_HOME --without-kde --with-oci-version=10G

sudo make

sudo checkinstall

```

Please note the following:
1- I'm using a full oracle 10g r2 client to work. TOra really needs libclntsh.so.10.1. In my case, the working directory is /opt/oracle/product/10.2.0/client_1/lib. If your configuration is different, create a symlink and it should work.
2- I'm pretty sure it won't work with instant clients. You're free to try.
3- I first downloaded and installed all dependencies as they're listed in the official repository tora. This deb won't check for dependencies, so please first install em all.
4- it was built in a ubuntu 6.10 386.

I have a spare machine where I can try other configurations if you need them and I have some time. Please let me know.

---

### Post by codingbabies on 2007-04-11
Hi, here it goes...

While i keep searching for the answer and as a recent member got over this issue i ask for your help.

Can't get passed the "debian/rules:22: *** commands commence before first target. Stop."

Downloaded tora-1.3.21 and now trying to configure/compile it with oracle support.

Thanks in advance.

---

### Post by pickles on 2007-04-13
Hi all,

### If you would like this package send me a message, as it is too big to post.

Am a newbie on this forum, but I had so many issues with installing Tora with Oracle support on my Ubuntu Ultimate Edition install that I thought I would post the .deb package that I created.
I have tested this package on a fresh install of Ubuntu (kernel -> 2.6.17-11-generic) and it works perfectly. The procedure required to install is as follows... please do as root.

Download oracle client from [http://www.oracle.com/technology/software/tech/oci/instantclient/htdocs/linuxsoft.htm](http://www.oracle.com/technology/software/tech/oci/instantclient/htdocs/linuxsoft.htm).
I grabbed the rpms from there and converted them using alien (alien -d xxx.rpm).

Install the packages (dpkg -i xxx.deb):
oracle-instantclient-basic_10.2.0.3-2_i386.deb
oracle-instantclient-devel_10.2.0.3-2_i386.deb
oracle-instantclient-sqlplus_10.2.0.3-2_i386.deb

Three steps above will instal OIC at /usr/lib/oracle.
Copy your tnsname.ora file to /usr/lib/oracle, an example entry is as below.

MYDBCONN =
(DESCRIPTION =
(ADDRESS_LIST =
(ADDRESS = (PROTOCOL = TCP)(HOST = 123.123.123.123)(PORT = 1521))
)
(CONNECT_DATA =
(SERVICE_NAME = MYSERVICE)
) )

###Make sure the version of the OIC is the same as below, i.e. 10.2.0.3
Add the following line below to /etc/ld.so.conf :
/usr/lib/oracle/10.2.0.3/client/lib
Execute the following command to create the appropriate links.
>>> ldconfig
Add lines below to /etc/profile :
LD_LIBRARY_PATH=/usr/lib/oracle/10.2.0.3/client/lib:$LD_LIBRARY_PATH
TNS_ADMIN=/usr/lib/oracle
ORACLE_HOME=/usr/lib/oracle/10.2.0.3/client
export LD_LIBRARY_PATH TNS_ADMIN ORACLE_HOME

###Open a new terminal (to reload /etc/profile). Or use the source command.
Check that the config is ok by doing the following...
echo $LD_LIBRARY_PATH
echo $ORACLE_HOME
>>>sqlplus user/pword@MYDBCONN
This should open a session with MYDBCONN. If this is ok, we are sweet, otherwise you need to work out why this isn't so.

Now install the package and it's dependencies.
apt-get install libqscintilla-dev (the only dependency I had :-) )
dpkg -i tora_1.3.21-3ubuntu1_i386.deb

Open Tora and you should have oracle support and all the connections listed in your tnsname.ora file.

Hope this helps some people... :-)


**_NOTE:_** DO NOT UPGRADE THIS PACKAGE AFTER INSTALL as it will not support oracle anymore.

---

### Post by hashinclude on 2007-06-19
I followed the instructions above, namely
[LIST=1]
[*]Download Oracle 10g XE Client from [www.oracle.com](www.oracle.com)
[*]Download the TORA sources with apt-get source tora (you might need to enable universe and multiverse first)
[*]Edit the debian/rules file and changed --without-oracle to --with-oracle (all else remains the same)
[*] export ORACLE_HOME=/path/to/oracle
[*] export LD_LIBRARY_PATH=$ORACLE_HOME/lib
[*]Installed a number of -devel packages (zlib, qscintilla, kde, debhelper, etc - apt-get install foo-dev if libfoo is missing)
[*]build with debian/rules binary
[/LIST]

However, building with ```
debian/rules binary
```  does **not** work for me, and I get this instead:
```

make[1]: Leaving directory `/usr/src/tora-1.3.21'
xsltproc -''-nonet /usr/share/sgml/docbook/stylesheet/xsl/nwalsh/manpages/docbook.xsl debian/tora.xml
warning: failed to load external entity "/usr/share/sgml/docbook/stylesheet/xsl/nwalsh/manpages/docbook.xsl"
cannot parse /usr/share/sgml/docbook/stylesheet/xsl/nwalsh/manpages/docbook.xsl
make: *** [build-stamp] Error 4

```

However, building with ```
make && checkinstall
``` works (and gives you a nice .deb package too), but you must remember to ```
export ORACLE_HOME=/path/to/oracle
``` and ```
export LD_LIBRARY_PATH=$ORACLE_HOME/lib
``` **before** launching tora.

---

### Post by oky on 2007-09-07
when I try running sqlplus I get
sqlplus: error while loading shared libraries: libaio.so.1: cannot open shared object file: No such file or directory


I am guessing I am missing some apt-get install ..., but which one?

Also, is there a difference between using ld.so.conf or  putting a file inside ld.so.conf.d?

BTW I used alien to convert the rpm packages.

---

### Post by oky on 2007-09-07
sudo apt-get install libaio
   sudo apt-get install libqscintilla-dev

It bothers me that different people get different results. I will think that if we all using the same os, it should be the same.?????

Even after setting the ORACLE_HOME, TNS_NAMES AND LD_LIBRARY_PATH in /etc/bash.bashrc, it never found
this variables.

The only way I could fixed it was declaring the variables inside /debian/rules so I added this
export LD_LIBRARY_PATH=/usr/lib/oracle/11.1.0.1/client/lib
export ORACLE_HOME=/usr/lib/oracle/11.1.0.1/client
export TNS_ADMIN=/usr/lib/oracle

	./configure --prefix=/usr --with-instant-client --without-rpath --disable-new-check --without-kde --with-xinerama --enable-libsuffix=

after that 
  sudo debian/rules binary


It works now

---

### Post by dlandis on 2007-10-21
Is there a new, easier way to get Tora with Oracle support with Gutsy Gibbon?

Also if I still have to compile it as I did with Feisty Fawn, I would like to know how to avoid having Synaptic always list it as a package that requires upgrade. I tried setting the "lock version" thing but that did not help.

---

### Post by fritzs on 2007-11-09
I got an error with oci which I fixed by editing the configure file.

change the line 

ora_lib=-lclntsh

to

ora_lib=-lclntsh -lnnz10

I have no idea why this works (apparently the so files link to eachother), but it builds correctly.

---

### Post by akintemel on 2007-11-22
I install all the oracle packages what you are write and i install tora Version 1.3.22svn and its work fine.But can not connect oracle .In  " Connection provider " field  just PostgreSql vaule, Host value write localhost  , Port 5432  Database field is empty.What am i do wrong.
&#304; install oracle client and copy the TNSnames.ora but i dont see and sqlplus  didnot work ..

What should i do .Please help me.:(..( sory my bad english )

---

### Post by hopfen on 2007-11-30
I'd been having a dickens of a time to get the bloody thing to compile. I kept getting errors on a test compile of an OCI app. (Sound familiar?)

I'm using Gutsy and the most recent Oracle Instant Client (11.1.0.1). For this, the simple and basic instructions in [https://help.ubuntu.com/community/HowToBuildToraWithOracle](https://help.ubuntu.com/community/HowToBuildToraWithOracle) almost worked. A few additions/changes were required. 

1) I needed to do an **apt-get install xsltproc** in addition to the other materials listed under Step 2.

2) The configure string in debian/rules was not quite correct for me. TOra 1.3.21pre22 didn't know anything about --with-oracle-includes. My line was modified to:

[INDENT]./configure --prefix=/usr --with-instantclient **--with-extra-includes**=/usr/include/oracle/11.1.0.1/client --without-kde --without-rpath --disable-new-check --enable-libsuffix= [/INDENT]

3) Compilation was successful. However, the line for installing the resulting deb file wasn't quite right. I used this instead:

[INDENT]dpkg -i tora_1.3.21pre22-2ubuntu1_i386.deb [/INDENT]

And it worked! It really, really worked. Thank goodness...now I can get back to my database work.

---

### Post by WhiteNoiseWN on 2007-12-12
Thanks for the advice that you guys have already posted, however I'm still having a problem getting past the 'debian/rules binary' configuration step.

I have libqt3-mt-dev installed, installed kde-dev, I'm using --without-kde, but I keep getting this error no matter what I do:

checking for Xinerama... no
configure: error: Qt () (library qt-mt) not found.
      Please check your installation! For more details about this problem,
      look at the end of config.log.Make sure that you have compiled Qt with thread support!

Anyone know what I need?

Thanks!

---

### Post by hemna on 2008-01-02
I'm having the same exact problem

> 
checking for Xinerama... no
configure: error: Qt () (library qt-mt) not found.
      Please check your installation! For more details about this problem,
      look at the end of config.log.Make sure that you have compiled Qt with thread support


---

### Post by hemna on 2008-01-02
ok I solved it

apt-get install kdebase-dev
apt-get install g++

---

### Post by Andrewsha on 2008-05-27
Hello!

i have a problem with
```
**sudo apt-get source tora**
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;... &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
E: &#1042;&#1099; &#1076;&#1086;&#1083;&#1078;&#1085;&#1099; &#1079;&#1072;&#1087;&#1086;&#1083;&#1085;&#1080;&#1090;&#1100; sources.list, &#1087;&#1086;&#1084;&#1077;&#1089;&#1090;&#1080;&#1074; &#1090;&#1091;&#1076;&#1072; URI &#1080;&#1089;&#1090;&#1086;&#1095;&#1085;&#1080;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1090;&#1086;&#1074;

```

I suppose In English translation something like that:
```
You should fill **sources.list**, with source package **URI**
```

But I'm completely new with Linux, please give me step by step instruction in this situation.
Thanks for advance!

---

### Post by Andrewsha on 2008-06-19
Hello!
is there any difference to compile TOra myself or download RPM and install it?
Thanx

---

### Post by ts007 on 2008-06-25
I get such messages,what's wrong with it ? I build it under xubuntu 8.04

install --owner root --group root --mode=644 /usr/src/tora-1.3.22/debian/tora.desktop /usr/src/tora-1.3.22/debian/tora/usr/share/applications
dh_testdir
dh_testroot
dh_installdocs
dh_installexamples
dh_installmenu
dh_installman tora.1
dh_installinfo
dh_installchangelogs 
dh_desktop
dh_link
dh_strip
dh_compress
dh_fixperms
xargs: xargs.c:443: main: &#26029;&#35328; `bc_ctl.arg_max <= (131072-2048)' &#22833;&#36133;.
Aborted
dh_fixperms: command returned error code
make: *** [binary-arch] &#38169;&#35823; 1

---

