---
title: "Trying to configure Metisse"
date: 2005-08-20
forum: Installation &amp; Upgrades
---

### Post by Stallone on 2005-08-20
I'm trying to configure Metisse but I'm having some problems along the way....

[http://insitu.lri.fr/~chapuis/metisse/download_install.html](http://insitu.lri.fr/~chapuis/metisse/download_install.html)

Everytime I cd to the directory to install nucleo (a dependency for metisse) and type ./configure , it always results with this:

```
 rambo@ubuntu:~/Desktop/nucleo-0.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for a sed that does not truncate output... /bin/sed
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
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
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
checking command to parse /usr/bin/nm -B output from gcc object... ok
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
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking dynamic linker characteristics... GNU/Linux ld.so
appending configuration tag "F77" to libtool
checking whether we are using the GNU C++ compiler... (cached) yes
checking whether g++ accepts -g... (cached) yes
checking dependency style of g++... (cached) gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether byte ordering is bigendian... no
checking for dlopen in -ldl... yes
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking GL/gl.h usability... yes
checking GL/gl.h presence... yes
checking for GL/gl.h... yes
checking for glFlush in -lGL... no
configure: error: GL header found, but fail to found libGL (use LDFLAGS?) 
```

Can anyone help?

---

### Post by Stallone on 2005-08-21
Anyone?

---

### Post by jpkotta on 2006-01-08
Worked for me (not Metisse, haven't tried that yet, just nucleo build).  What are you using for libGL?  I have an nVidia GeForce FX with the proprietary driver.

Edit:

Hmm...looking more closely at it, it looks like you don't have libGL.  If you have a graphics card that has 3D accelleration in Linux, install the driver.  Otherwise, you'll probably need Mesa, which is software OpenGL.  It will probably work with Mesa, but will be slow.

---

### Post by loell on 2006-12-12
it  seems difficult to install metisse on ubuntu.

---

### Post by joehill on 2006-12-12
Yes, I agree.  I can't get past the nucleo installation--it gives me errors about all kings of GL things not being found (even though I'm running Berl just fine).  Anyone have any ideas?

---

### Post by dlanor78 on 2006-12-17
Anyone get this thing compiled yet?  I'm getting errors at building nucleo as well.  Here's the one I can't get past so far:

```

glShader.cxx: In function 'void nucleo::findGLSLprocs()':
glShader.cxx:62: error: 'glXGetProcAddressARB' was not declared in this scope

```

---

### Post by loell on 2006-12-17
try installing libgl1-mesa-dev , libglut3-dev . i've succesfully compiled nucleo in dapper , but metisse won't compile :(

you can use babelfish to translate this metisse discussion

[http://www.esdebian.org/article.php?story=20050619102614248]("http://www.esdebian.org/article.php?story=20050619102614248")

even so with those instructions, it just won't install.

---

### Post by loell on 2006-12-17
try looking in this tutorial too

[http://translate.google.com/translate?u=http%3A%2F%2Fwww.ubuntu-es.org%2Findex.php%3Fq%3Dnode%2F7109&langpair=es%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools]("http://translate.google.com/translate?u=http%3A%2F%2Fwww.ubuntu-es.org%2Findex.php%3Fq%3Dnode%2F7109&langpair=es%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools")

---

### Post by loell on 2006-12-17
ok, i've succesfully compiled metisse 0.4.0rc1 in dapper

download the source from here

[http://www.lri.fr/~chapuis/software/metisse/]("http://www.lri.fr/~chapuis/software/metisse/")

---

### Post by dlanor78 on 2006-12-30
Thanks for the tips loell.  I haven't had a chance to try again yet because of the holiday happenings, but hopefully this weekend I can give it another go.  I'll try to remember to post reults if I get a chance to play with it.

---

### Post by loell on 2006-12-30
no problem, you should also compile and install nucleo 0.5 before installing metisse , i joined their mailing list a week or two ago, and like a clueless newbie, requested a new and more updated release, well typically, they ignore me ;) , no response what so ever.

---

### Post by dlanor78 on 2006-12-30
I tried compiling nucleo from the link listed above and still can't get it to compile.  Now I'm getting:

```

StringUtils.cxx:21: error: explicit instantiation of 'class std::basic_string<char, nucleo::ci_char_traits, std::allocator<char> >' in namespace 'nucleo' (which does not enclose namespace 'std')
StringUtils.cxx:21: error: explicit instantiation of 'struct std::basic_string<char, nucleo::ci_char_traits, std::allocator<char> >::_Alloc_hider' in namespace 'nucleo' (which does not enclose namespace 'std')
StringUtils.cxx:21: error: explicit instantiation of 'struct std::basic_string<char, nucleo::ci_char_traits, std::allocator<char> >::_Rep' in namespace 'nucleo' (which does not enclose namespace 'std')
StringUtils.cxx:21: error: explicit instantiation of 'struct std::basic_string<char, nucleo::ci_char_traits, std::allocator<char> >::_Rep_base' in namespace 'nucleo' (which does not enclose namespace 'std')
make[3]: *** [StringUtils.lo] Error 1
make[2]: *** [all-recursive] Error 1
make[1]: *** [all] Error 2
make: *** [all-recursive] Error 1

```

I did a little searching to find a way around this, but didn't find anything useful.  I'm thinking so far that part of the problem might be that I'm running edgy.  Any ideas?

---

### Post by mirak63 on 2007-01-18
> VideoServer.o: In function `~VideoServer':
/usr/src/metisse/build-nucleo/apps/videoServer/VideoServer.cxx:39: undefined reference to `nucleo::DNSServiceAnnouncer::~DNSServiceAnnouncer()'
/usr/src/metisse/build-nucleo/apps/videoServer/VideoServer.cxx:39: undefined reference to `nucleo::DNSServiceAnnouncer::~DNSServiceAnnouncer()'
collect2: ld returned 1 exit status
make[2]: *** [videoServer] Erreur 1


I have this error](*,)

---

### Post by crazy___cow on 2007-01-25
I have made two debs to install metisse on ubuntu edgy.

[http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html](http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html)
[http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html](http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html)

To launch it, open a terminal in X and type:

Xmetisse -ac -depth 24 -geometry 1680×1050 :1 &
metisse-start-fvwm &

Change geometry and depth!

Crazy Cow

PS: if you have problems with dependencies, try to use treviño sources.list:
[http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)

---

### Post by NoWhereMan on 2007-01-25
Thank You!

---

### Post by rich.bradshaw on 2007-01-26
So... what happens now? I end up in a screen with cloud background, clicking and choosing an application doesn't work - I can change the theme though... am I missing something?

---

### Post by crazy___cow on 2007-01-26
I have no problems. The window manager works perfectly. May be my packages don't work with your edgy. 

Sorry :(

---

### Post by aidanr on 2007-01-26
works for me aswell, thanks

---

### Post by dlanor78 on 2007-01-27
If anyone is still having problems getting metisse working in ubuntu, Mandriva has released a live cd that has metisse fully working.  Might be good to try this out to find out if it's even worth getting to work in ubuntu.

I tried it out and it is interesting, but it's not intuitive yet.  You mostly need to learn a bunch of key/mouse combos to use the fancy features.

You can download the live cd at [http://www.mandriva.com/en/projects/metisse/download](http://www.mandriva.com/en/projects/metisse/download)

---

### Post by aretehou on 2007-01-28
> **crazy___cow said:**
> I have made two debs to install metisse on ubuntu edgy.

[http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html](http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html)
[http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html](http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html)

To launch it, open a terminal in X and type:

Xmetisse -ac -depth 24 -geometry 1680×1050 :1 &
metisse-start-fvwm &

Change geometry and depth!

Crazy Cow

PS: if you have problems with dependencies, try to use treviño sources.list:
[http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)

crazy___cow, great job! Thanks! 
And would u please tell me what package you get to compile nucleo?
When configure nucleo, I got such message:

  Architecture: i686-pc-linux-gnu
  ---
  glWindow backend?    no
  JPEG image support?  yes
  PNG image support?   yes
  EXIF support?        yes
  Freetype2 support?   yes
  DNS-SD support?      yes

---

### Post by Guardian_Bob on 2007-01-28
Hi I installed the deps and I get the following error. I really want to check this out.

```
[FVWM][main]: <<ERROR>> can't open display 127.0.0.1:1

```

---

### Post by Sef on 2007-01-28
> I have made two debs to install metisse on ubuntu edgy.

[http://upload2.net/page/download/zub..._i386.deb.html](http://upload2.net/page/download/zub..._i386.deb.html)
[http://upload2.net/page/download/KOm..._i386.deb.html](http://upload2.net/page/download/KOm..._i386.deb.html)

To launch it, open a terminal in X and type:

Xmetisse -ac -depth 24 -geometry 1680×1050 :1 &
metisse-start-fvwm &

Change geometry and depth!

How do you know what to change the depth and geometry to?

---

### Post by dlanor78 on 2007-01-28
The geometry is simply your screen resolution.  Whatever you're currently running should theoretically be fine.  To find out your current res in ubuntu, go to System>Preferences>Screen Resolution.

The depth is the amount of colors (i.e. 24 million colors, 16 million colors...etc).  You're probably running 24 now and that should be fine.  Not sure how to change this one.

Someone please correct me if I got something wrong here :D



Now, can anyone tell me how to get Metisse running as the only desktop from gdm?  The Metisse site has instructions for those using startx, but I'd rather use gdm sessions if possible.

---

### Post by AgenT on 2007-01-28
> **dlanor78 said:**
> 
Now, can anyone tell me how to get Metisse running as the only desktop from gdm?  The Metisse site has instructions for those using startx, but I'd rather use gdm sessions if possible.You need to make an Xsessions .desktop file. Look for existing ones on your system, copy/paste, and edit with the needed information. For examples, see:
/usr/share/xsessions/

---

### Post by AgenT on 2007-01-28
> **crazy___cow said:**
> I have made two debs to install metisse on ubuntu edgy.

[http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html](http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html)
[http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html](http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html)

To launch it, open a terminal in X and type:

Xmetisse -ac -depth 24 -geometry 1680×1050 :1 &
metisse-start-fvwm &

Change geometry and depth!

Crazy Cow

PS: if you have problems with dependencies, try to use treviño sources.list:
[http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)
Can you please give a list of the packages you had to install for nucleo and metisse to compile?

---

### Post by aidanr on 2007-01-28
see attachments

sorry not bothered writing them out, i just took quick screenshots when installing for reference for removing later because synaptic doesn't show those in it's history if it's installed with gdebi

edit:// oh to compile, nm so, you'll also need dev packages

---

### Post by crazy___cow on 2007-01-28
These are the packages I have installed to compile metisse. I don't think that are all necessary....


fvwm-gnome (1:2.5.16-2)
gnome-bin (1.4.2-32)
gnome-libs-data (1.4.2-32)
libart2 (1.4.2-32)
libdb3 (3.2.9-25)
libgnome32 (1.4.2-32)
libgnomesupport0 (1.4.2-32)
libgnomeui32 (1.4.2-32)
libgnorba27 (1.4.2-32)
libgnorbagtk0 (1.4.2-32)
liborbit0 (0.5.17-11.1ubuntu2)
libstroke0 (0.5.1-5)
rxvt (1:2.6.4-10)
xwnc (0.3.3-8)
libgl1-mesa-dev (6.5.1~20060817-0ubuntu3)
libglu1-mesa-dev (6.5.1~20060817-0ubuntu3)
mesa-common-dev (6.5.1~20060817-0ubuntu3)
avahi-discover (0.6.13-2ubuntu2.4)
avahi-dnsconfd (0.6.13-2ubuntu2.4)
avahi-utils (0.6.13-2ubuntu2.4)
libavahi-compat-libdnssd-dev (0.6.13-2ubuntu2.4)
libavahi-compat-libdnssd1 (0.6.13-2ubuntu2.4)
libavahi-core-dev (0.6.13-2ubuntu2.4)
libnss-mdns (0.7-1ubuntu1)
python-avahi (0.6.13-2ubuntu2.4)
libncurses5-dev (5.5-2ubuntu1)
libreadline5-dev (5.1-7build1)
librplay3-dev (3.3.2-11)
libstroke0-dev (0.5.1-5)
gdk-imlib11-dev (1.9.14-30ubuntu1)
libglib1.2-dev (1.2.10-10.1build1)
libgtk1.2-dev (1.2.10-18)
x-dev (7.0.7-1)
indent (2.2.9-7)
libart-dev (1.4.2-32)
libdb3-dev (3.2.9-25)
libgnome-dev (1.4.2-32)
libgnorba-dev (1.4.2-32)
liborbit-dev (0.5.17-11.1ubuntu2)
libwrap0-dev (7.6.dbs-9)

---

### Post by AgenT on 2007-01-28
> **Guardian_Bob said:**
> Hi I installed the deps and I get the following error. I really want to check this out.

```
[FVWM][main]: <<ERROR>> can't open display 127.0.0.1:1

```That means you already have an X session running at :1. Are you sure you closed/stopped previous Xorg sessions? For example, if you are running GNOME then you are probably running Xorg at :1 (GNOME uses Metacity by default which requires Xorg).

---

### Post by dlanor78 on 2007-01-28
> **AgenT said:**
> You need to make an Xsessions .desktop file. Look for existing ones on your system, copy/paste, and edit with the needed information. For examples, see:
/usr/share/xsessions/

I did try that already and couldn't get it to work.  I'll play around with it some more if I get a chance and if I figure it out I'll post results.  Don't hold your breath for it this weekend though ;-p

---

### Post by yigal.weinstein on 2007-01-28
Is there a way to use Metisse as a window decorator for GNOME?

---

### Post by AgenT on 2007-01-28
> **yigal.weinstein said:**
> Is there a way to use Metisse as a window decorator for GNOME?Metisse is not a window decorator, but a window system. Metisse requires a window manager and currently the only window manager that works with Matisse is FVWM. GNOME uses Metacity for its window manager and you can use FVWM with GNOME instead. The best way to do this would be to first setup Matisse and FVWM and make sure they work. Then modify the scripts to have FVWM replace Metacity by invoking fvwm --replace. Or just add all the needed lines for Metisse and FVWM in the GNOME session manager and remember to add the --replace option.

---

### Post by yigal.weinstein on 2007-01-29
Thank you AgenT and thank you crazy___cow I installed the debs and they are very nice.  I think it is a lot of work to really use metisse but maybe it is worth it.

---

### Post by Drakx on 2007-01-29
> **Guardian_Bob said:**
> Hi I installed the deps and I get the following error. I really want to check this out.

```
[FVWM][main]: <<ERROR>> can't open display 127.0.0.1:1

```

I get the same error along with:

```

Xmetisse -ac -depth 24 -geometry 1024×768 :1 &
[1] 5473
drakx@sphinx:~$ Invalid geometry 1024×768 :1
```

any ideas?

---

### Post by Drakx on 2007-01-29
I got it working just using:

```
Xmetisse -depth 24 -geometry 1024x768 -ac :1
metisse-start-fvwm -wd :1

```

So any one got an idea how to get this up and running for gnome like they have in mandrakes live cd

---

### Post by AgenT on 2007-01-29
> **Drakx said:**
> I got it working just using:

```
Xmetisse -depth 24 -geometry 1024x768 -ac :1
metisse-start-fvwm -wd :1

```So any one got an idea how to get this up and running for gnome like they have in mandrakes live cd
How about actually reading posts before asking? Read two posts above yours for the answer!

---

### Post by navneeth on 2007-01-29
> **AgenT said:**
> That means you already have an X session running at :1. Are you sure you closed/stopped previous Xorg sessions? For example, if you are running GNOME then you are probably running Xorg at :1 (GNOME uses Metacity by default which requires Xorg).

AgenT, could you please explain that in simpler terms? :) How do I make it work?

Thanks.

---

### Post by navneeth on 2007-01-29
Anyone?

---

### Post by patrice.vallade on 2007-01-29
Hello
I've got this problem in a terminal :
Start fvwmi with args -d :0.0 -w metisse://127.0.0.1:1  for FvwmCompositor
[FVWM][main]: <<ERROR>> can't open display 127.0.0.1:1

So, can you give me an answer ?

Excuse my english but i've stell learn english at school..
I think the problem becom from X11 but where ?
Thanks a loot for your works...

---

### Post by navneeth on 2007-01-30
So no one knows how to deal with the error messages? :(

---

### Post by AgenT on 2007-01-30
> **navneeth said:**
> So no one knows how to deal with the error messages? :(
This has been answered. If you do not understand the answer than you should not be installing/compiling/configuring Metisse. It is experimental and not for unexperienced users.

Let me put it in simple terms and step-by-step:[LIST=1]
[*]goto Metisse website
[*]Successfully compile Nucleo first, then Metisse
[*]Install Nucleo first, then Metisse
[*]Quit all of your Xorg sessions (note: it is possible to leave them running, but not recommended)
[*]Start plain Xorg with xterm without a window manager (unless you want to run Metisse inside of your current setup - slow and can cause problems, but I have done it)
[*]Successfully start Xmetisse
[*]Sucessfully start metisse-start-fvwm[/LIST]Giving you further help will not really work because it's all there above and on the Metisse page. Everything you need is already available. If the specific settings do not work on your system that is because no one knows your actual setup and different users will need different settings. If you do not know how to do it yourself, then you should wait either until someone creates deb files (in which case, you will still have to do steps 3-7) or until someone integrates Metisse with Ubuntu by creating startup scripts and xsession .desktop files.

---

### Post by navneeth on 2007-01-30
> **AgenT said:**
> This has been answered. If you do not understand the answer than you should not be installing/compiling/configuring Metisse. It is experimental and not for unexperienced users.

Let me put it in simple terms and step-by-step:[LIST=1]
[*]goto Metisse website
[*]Successfully compile Nucleo first, then Metisse
[*]Install Nucleo first, then Metisse
[*]Quit all of your Xorg sessions (note: it is possible to leave them running, but not recommended)
[*]Start plain Xorg with xterm without a window manager (unless you want to run Metisse inside of your current setup - slow and can cause problems, but I have done it)
[*]Successfully start Xmetisse
[*]Sucessfully start metisse-start-fvwm[/LIST]Giving you further help will not really work because it's all there above and on the Metisse page. Everything you need is already available. If the specific settings do not work on your system that is because no one knows your actual setup and different users will need different settings. If you do not know how to do it yourself, then you should wait either until someone creates deb files (in which case, you will still have to do steps 3-7) or until someone integrates Metisse with Ubuntu by creating startup scripts and xsession .desktop files.

Thanks for the reply. I installed Nucleo and Metisse with the .deb packages that has been linked to in an earlier post in this thread. It's just that I don't understand what quitting Xorg or starting xorg with xterm means. I don't think it's either rebooting the computer or log-out/log-in. I'd appreciate it if you could tell how to do it or provide a link with instructions.

---

### Post by jackliddlephysics on 2007-01-31
> **AgenT said:**
> Metisse is not a window decorator, but a window system. Metisse requires a window manager and currently the only window manager that works with Matisse is FVWM. GNOME uses Metacity for its window manager and you can use FVWM with GNOME instead. The best way to do this would be to first setup Matisse and FVWM and make sure they work. Then modify the scripts to have FVWM replace Metacity by invoking fvwm --replace. Or just add all the needed lines for Metisse and FVWM in the GNOME session manager and remember to add the --replace option.

I've got it all up and running but I'm not really sure what this means I have to do inorder to get it working with GNOME?

Can anyone give an example?

Thanks

I'm not really sure what this means.

---

### Post by Da-Net on 2007-01-31
Thanks a lot for debs! Installed without problems. But I have still complications to lunch the Metisse. Yo write: "open a terminal in X". What das it mean: "in X"? 
I changed the resolution as you have said to my one (1280x1024). The depth I took in the xorg.cong ("default depth 24"). so it stayed the same. But if I insert this (simply in terminal):

Xmetisse -ac -depth 24 -geometry 1280×1024 :1 &
metisse-start-fvwm &

I get these results:

ubuntufreund@ubuntufreund-pc:~$ Xmetisse -ac -depth 24 -geometry 1280×1024 :1 & 
[1] 6178 
ubuntufreund@ubuntufreund-pc:~$ metisse-start-fvwm &Invalid geometry 1280×1024 
use: X [:<display>] [option] 
-a # mouse acceleration (pixels) 
-ac disable access control restrictions 
-audit int set audit trail level 
-auth file select authorization file 
bc enable bug compatibility 
-br create root window with black background 
+bs enable any backing store support 
-bs disable any backing store support 
-c turns off key-click 
c # key-click volume (0-100) 
-cc int default color visual class 
-co file color database file 
-core generate core dump on fatal error 
-dpi int screen resolution in dots per inch 
-deferglyphs [none|all|16] defer loading of [no|all|16-bit] glyphs 
-f # bell base (0-100) 
-fc string cursor font 
-fn string default font name 
-fp string default font path 
-help prints message with these options 
-I ignore all remaining arguments 
-ld int limit data space to N Kb 
-lf int limit number of open files to N 
-ls int limit stack space to N Kb 
-nolock disable the locking mechanism 
-logo enable logo in screen saver 
nologo disable logo in screen saver 
-nolisten string don't listen on protocol 
-p # screen-saver pattern duration (minutes) 
-pn accept failure to listen on all ports 
-nopn reject failure to listen on all ports 
-r turns off auto-repeat 
r turns on auto-repeat 
-render [default|mono|gray|color] set render color alloc policy 
-s # screen-saver timeout (minutes) 
-su disable any save under support 
-t # mouse threshold (pixels) 
-terminate terminate at server reset 
-to # connection time out 
-tst disable testing extensions 
ttyxx server started from init on /dev/ttyxx 
v video blanking for screen-saver 
-v screen-saver without video blanking 
-wm WhenMapped default backing-store 
-x string loads named extension at init time 
-geometry WxH set framebuffer width & height 
-depth D set framebuffer depth 
-pixelformat format set pixel format (BGRnnn or RGBnnn) 
-udpinputport port UDP port for keyboard/pointer data 
-rfbport port TCP port for RFB protocol 
-rfbwait time max time in ms to wait for RFB client 
-nocursor don't put up a cursor 
-rfbauth passwd-file use authentication on RFB protocol 
-httpd dir serve files via HTTP from here 
-httpport port port for HTTP 
-deferupdate time time in ms to defer updates (default 40) 
-economictranslate less memory-hungry translation 
-desktop name METISSE desktop name (default x11) 
-alwaysshared always treat new clients as shared 
-nevershared never treat new clients as shared 
-dontdisconnect don't disconnect existing clients when a new non-shared 
connection comes in (refuse new connection instead) 
-viewonly let clients only to view the desktop 
-localhost only allow connections from localhost 
-interface ipaddr only bind to specified interface address 
-inetd Xmetisse is launched by inetd 
-version report Xmetisse version on stderr

And it stays...
Thenn I press Enter and get:

u[2] 6277 
[1] Exit 1 Xmetisse -ac -depth 24 -geometry 1280×1024 :1 
ubuntufreund@ubuntufreund-pc:~$ Start fvwmi with args -d :0.0 -w metisse://127.0.0.1:1 for FvwmCompositor 
[FVWM][main]: <<ERROR>> can't open display 127.0.0.1:1

I press Enter one more time and get:

[2]+ Exit 1 metisse-start-fvwm 
ubuntufreund@ubuntufreund-pc:~$


What I make false?

---

### Post by Da-Net on 2007-01-31
> **jackliddlephysics said:**
> I've got it all up and running but I'm not really sure what this means I have to do inorder to get it working with GNOME?

Can anyone give an example?

Thanks

I'm not really sure what this means.

Try to go in left upper corner of the window wit the right click. In Mandriva with Metisse you cann so controll rotation of the windows for example.

---

### Post by jackliddlephysics on 2007-01-31
> **Da-Net said:**
> Try to go in left upper corner of the window wit the right click. In Mandriva with Metisse you cann so controll rotation of the windows for example.

I don't know how to launch metisse with gnome though.

Running using the --replace switch was mentioned but I don't know how to start it with GNOME.

If anyone has could they post the command they used to start it please.

Thanks

---

### Post by groggyboy on 2007-01-31
> **navneeth said:**
> Thanks for the reply. I installed Nucleo and Metisse with the .deb packages that has been linked to in an earlier post in this thread. It's just that I don't understand what quitting Xorg or starting xorg with xterm means. I don't think it's either rebooting the computer or log-out/log-in. I'd appreciate it if you could tell how to do it or provide a link with instructions.
naveeth (and Da-Net), what AgenT is trying to say is that you have to exit everything and start Metisse from "scratch".  Log out, or hit ctrl-alt-backspace.  Doing so will log you out of your Xorg session.  Once you are at the GDM login screen, hit ctrl-alt-F1, which presents you with an xterm.  Login with your name and password.  From there, run the commands to get Metisse running:```
Xmetisse -ac :1 -geometry 1280x800 #(or whatever your screen resolution is - I just happen to have widescreen)
metisse-start-fvwm
```



All that aside, I'm having problems of my own.  I can't even get as far as the second command.  Running Xmetisse spits the following error at me and then hangs:```
Could not init font path element /usr/share/fonts/truetype, removing from list!
```
Any suggestions?  I used crazy__cow's .debs to install nucleo and metisse.  Could I be missing a package?  Should I compile it from source?

---

### Post by Da-Net on 2007-01-31
> **groggyboy said:**
> naveeth (and Da-Net), what AgenT is trying to say is that you have to exit everything and start Metisse from "scratch".  Log out, or hit ctrl-alt-backspace.  Doing so will log you out of your Xorg session.  Once you are at the GDM login screen, hit ctrl-alt-F1, which presents you with an xterm.  Login with your name and password.  From there, run the commands to get Metisse running:```
Xmetisse -ac :1 -geometry 1280x800 #(or whatever your screen resolution is - I just happen to have widescreen)
metisse-start-fvwm
```


At last an realy user-frendly explanation! Thanks a lot! (Why Bill Gates has got so rich? Because he liberated the people from using command lines and terminal. ;) Some others should think about it ;). ) 
Only exuse me please for this question: if you could not go far as second command, why you are sure to have to change the command that originaly was given bei crazy_cow, wich has compiled the debs? I just ask me if I should make it as well. But why? You do not say, what the reason.  Thanks again for realy explanation.
 
And about your problem. I cann not realy give advice in the matter, but what I noticed tried in terminal was, that inserting resolution one probably should not use liter x, becouse it gave another result as coping and pasting crazy_cow's original sighn for it. I don not know how he got, wich key used.. :)), but it was different as the liter x.

---

### Post by groggyboy on 2007-01-31
> All that aside, I'm having problems of my own.  I can't even get as far as the second command.  Running Xmetisse spits the following error at me and then hangs:```
Could not init font path element /usr/share/fonts/truetype, removing from list!
```
An update: on the [metisse website]("http://insitu.lri.fr/metisse/docs/building.html"), it states that "The Metisse server will not run without fonts. If your X11 fonts are not installed in /usr/share/fonts/X11, /usr/share/fonts or /usr/lib/X11/fonts, use the --with-fontdir option to indicate their location."  Apparently crazy__cow's debs are pointing to a different font directory than mine.  So I've been spending all afternoon compiling and trying to run nucleo and metisse.  i have nucleo compiled and installed fine, but i'm still having problems compiling (and hence running) metisse.  i compile it using "./configure --enable-mmx --enable-glx-x86" but it still won't work.  running configure returns this: ```
MMX in fb:       yes
Xcursor Library:         yes 
GLX extension:           yes (x86 optimisation)
**Widget tracking support: no csip not found**
Python 2.x:              yes 
```
What is csip, and how do I enable widget tracking support?  Do I need it to run metisse?  Also, it appears to be using GLX, whereas I have AIGLX.  could this be a problem?

---

### Post by groggyboy on 2007-01-31
> **Da-Net said:**
> At last an realy user-frendly explanation! Thanks a lot!
;) You're welcome!
> Why Bill Gates has got so rich? Because he liberated the people from using command lines and terminal. ;) Some others should think about it ;).
I also prefer to use the GUI whenever possible, but that doesn't change the fact that the terminal is *very* powerful.  So powerful, in fact, that Microsoft has a developed newly revamped command line called [PowerShell]("http://en.wikipedia.org/wiki/Windows_PowerShell") to address some shortcomings of the command line in Windows.  Mac OS X has a terminal too!  And I don't want to sound cruel, but if you don't like the command line, trying to install Metisse will be a big challenge.  After all, it is still very experimental.  And Bill Gates became rich by flexing his muscle and forcing computer manufacturers to bundle Windows and Windows *only*, thus making Windows the ugly and braindead 800pound gorilla of the Operating System world.  But I digress.  The last thing I want is a flamewar.
> Only exuse me please for this question: if you could not go far as second command, why you are sure to have to change the command that originaly was given bei crazy_cow, wich has compiled the debs? I just ask me if I should make it as well. But why? You do not say, what the reason.
I use a widescreen laptop that doesn't support (or at least looks really ugly) running at 1024x786 resolution.  The "-geometry" option is only to tell metisse what your screen resolution is.  On older monitors, it might be 800x600, on new monitors, it might be 1280x1024 or larger.  I think someone mentioned it earlier in the thread, but to check what your monitor resolution is, in Gnome go to System > Preferences > Screen Resolution.  The first option, where it says "Resolution:", will be your screen's resolution.  That's what you should use after "-geometry" when running the command to start Xmetisse.  At least, that's how I understand it. ;)

---

### Post by Da-Net on 2007-01-31
> **groggyboy said:**
> ;) You're welcome!

I also prefer to use the GUI whenever possible, but that doesn't change the fact that the terminal is *very* powerful.  So powerful, in fact, that Microsoft has a developed newly revamped command line called [PowerShell]("http://en.wikipedia.org/wiki/Windows_PowerShell") ... 

I use a widescreen laptop that doesn't support (or at least looks really ugly) running at 1024x786 resolution.  The "-geometry" option is only to tell metisse what your screen resolution is. )

I think Bill Gates could not "force" manufuctures to install Windows only if Windows didn't have this liberty of command lines. I do not say the terminal is useles. It may be powerfull, but the money of Bill was paid not from peoples wanting the power of terminal ;), but for those who was wanting one well usable simple to controll pc. These peoples do not want "full power of terminal" ;). Mac have it, Ubuntu have it.. - that is good, but bad were if they would not have at the same time another way to well usable pc. Now I say what I mean. I have heard allready here that Metisse were "an experimental toll". But exuse me...! Install Mandriva and this "experimental" tool will transformate it to one solid working problemless one. It is not Beryl. Beryl is a good thing, but tell me what give Beryl so much to make working with apps more eficently as Gnome with those multiple-desktops? May be very little, if something in generaly.. Beryl is some psichological tool. Good but not enough. Metisse I need realy. And now I read some others supporter wich says as: "...if you do not understood what I hade said, you do not need Metisse...", I don not know what I need more: lough or shutt the window and install Mandriva. I have tried to start Metisse following your explanation. The result stay the same as in terminal fome Gnome: "cann't start display ... 127...."  My color depth according tu Nvidia manager is 32. I tried 32 and 24 - all the same. I typed the resolution this way: 1280*1024. I cann't use the sighn like liter "x". It seems not to be avilable on my keyboard. I stroced everething but it didn't appear.  "*" is multiplication sighn. It seems to work (or it were yet the reason?). I do not know.  It is sad. If these debs are different on every Ubuntu installation, so it woulbe good to make debs on fresh installed Ubuntu. So could everybody who want Metisse reinstall Ubuntu and use these debs. Why I stayed with Ubuntu? Ubuntu is not the fastest for example (Zenwalk is much more fast), but it have good spirit, good idea, good community, repository and security-concept for desktops. But Mandriva have firewall and suppose good protected for puporses of normal users. It is frendly in use as well. May be I'll use it untill Metisse will come to Ubuntu. Thanks for your help, you btw are the real Ubuntu supporter.

---

### Post by groggyboy on 2007-01-31
> **Da-Net said:**
> Ubuntu is not the fastest for example (Zenwalk is much more fast), but it have good spirit, good idea, good community, repository and security-concept for desktops. But Mandriva have firewall and suppose good protected for puporses of normal users. It is frendly in use as well. May be I'll use it untill Metisse will come to Ubuntu. Thanks for your help, you btw are the real Ubuntu supporter.

I saw the videos of Metisse on Mandriva, and it looks really slick.  I haven't actually tried out the liveCD, because I wanted to save myself the hassle of downloading it and burning it.  I love tinkering with desktop environments (i currently have KDE, GNOME, Xfce, beryl, fvwm-crystal, blackbox, enlightenment and Project Looking Glass installed) and I wanted to try out Metisse.  That said, I'm finding it really difficult to get Metisse running on Ubuntu.  I may just end up downloading the LiveCD.  Mandriva looks like a really good, polished distro, from what I've seen, and I'm curious to see it in action.  I doubt I'd install it, but best of luck to you if you do, Da-Net.  :D

---

### Post by Da-Net on 2007-01-31
> **groggyboy said:**
>  I love tinkering with desktop environments (i currently have KDE, GNOME, Xfce, beryl, fvwm-crystal, blackbox, enlightenment and Project Looking Glass installed) ..
About my expiriences ;) you may be will cann look here on my [_[COLOR="LightBlue"][COLOR="RoyalBlue"]blog[/COLOR][/COLOR]_]("http://my.opera.com/loboderusia").

---

### Post by NosLycn on 2007-02-12
> So any one got an idea how to get this up and running for gnome like they have in mandrakes live cd

Drakx, if I didn't get it working like the live cd, then I have a very close approximation.

First, run a Gnome session, and perform the following commands in a terminal:

> $  gnome-session-remove metacity
$  gnome-session-save

The $ is used to represent the terminal prompt, as this quote had more than one command.  Less than one command gets no prompt.

Exit Gnome, exit gdm using the console and specifying, as root, killall gdm.  As a user, change the .xinitrc file to have:

> rxvt
killall Xmetisse

Run startx.

You'll get X11 open with an rxvt terminal and nothing else.  In that terminal, type:

> Xmetisse -ac -depth 24 -geometry 1280x800 :1 & metisse-start-fvwm

That's how I get Metisse running on its own.  Of course, you'll have to specify your own geometry and colour depth.

Next, open a terminal of your choice and run:

> gnome-session :2

I admit that I'm not sure that the :2 is necessary, but that's how I've been doing it and that's how I'll keep doing it, as it worked for me.

You should see Gnome open up, covering up fvwm.  You'll have your metisse options, because that will be your window manager on display 1 and display 2 won't have a window manager because we already got rid of metacity for default Gnome sessions.  So, you wind up with all the options of metisse in fvwm and the handy look of Gnome (Gnome background and what-not).

I hope this helps.

---

### Post by floke on 2007-02-24
Hey all, nice thread

Have managed to install metisse + neoclule (whatever it is thing), but running the metisse-start-fvwm line gives me the message that no such command exists.

Ok, so surely some mistake :) 

When compiling metisse I did get the message that it couldn't do something with fvwm since the noocluealloola thing wasn't compiled (although it was, or at least seemed to be). I guessed that it wouldn't install if everything wasn't ok so would just try to install and see what happened. 

Obviously a wrong assumption!

Any ideas on what I can do?

---

### Post by NosLycn on 2007-02-24
I think there are a few prerequisites, such as fvwm for this to work.  Are you trying to compile from source?  Crazy Cow made a couple of debs that work top-notch.  


> I have made two debs to install metisse on ubuntu edgy.

[http://upload2.net/page/download/zub..._i386.deb.html](http://upload2.net/page/download/zub..._i386.deb.html)
[http://upload2.net/page/download/KOm..._i386.deb.html](http://upload2.net/page/download/KOm..._i386.deb.html)

To launch it, open a terminal in X and type:

Xmetisse -ac -depth 24 -geometry 1680×1050 :1 &
metisse-start-fvwm &

Change geometry and depth!

Crazy Cow

PS: if you have problems with dependencies, try to use treviño sources.list:
[http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)

The links to the debs don't come through properly in the quote.  They are as follows:

[http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html]("http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html")
[http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html]("http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html")

If it still doesn't work, please post the exact errors you receive.  Remember, Metisse (as far as I know) is still in its experimental stages.  Best of luck to you.

---

### Post by floke on 2007-02-24
Thanks for this - definitely easier than compiling!

however - using this:

Xmetisse -ac -depth 24 -geometry 1280x800 

Gives me this...

could not init font path element  /usr/share/fonts/truetype, removing from list!

Whereupon it all hangs

Any ideas? (thanx in adv.)

---

### Post by NosLycn on 2007-02-24
Steve K

Here's what I did.  I made a new .xinitrc file in my ~ directory that contains:

> 
rxvt
killall Xmetisse

This will open up an x11 session with only an rxvt terminal, when you start x11 with startx.  For that, you will need to make sure GDM isn't running.  If you use KDM, replace gdm with kdm, et cetera.

> sudo killall gdm

  From that terminal, I run:

> Xmetisse -ac -depth 24 -geometry 1280x800 :1 & metisse-start-fvwm

If you just run the Xmetisse -ac... line you'll have it hang.  You need to have the :1 and all that after it, or else it doesn't work, in my experience.

If you're still having problems with the font, run updatedb (sudo or as root) and then:

> locate truetype | grep fonts

I would then copy the fonts to /usr/share/fonts.

Bon appetit!

---

### Post by floke on 2007-02-25
Thanks for the help, but still no luck.

Don't know how to set up a new xinit file, so this is what I have done...

At login screen, press ctrl-alt-F1; then sudo killall gdm
then 'Xmetisse -ac -depth 24 -geometry 1280x800 :1 & metisse-start-fvwm'

But it still hangs at the cant init fonts ... message.

I ran the updatedb thing and the fonts are already in usr, so no need to copy them there.

Any ideas?

** EDIT ** When configuring the neoclue doo-dah I didn't get all the 'Yes'es at the end - i.e. Qtcore and a couple of the other end ones were registering a 'no' (although GLX was fine (but do I need to --enable this? and if so, can anyone tell me how?) - I read on the metisse site that the VCN (is that it?) bits didn't need to be working, since their inclusion was a mistake and they won't be in the next tarball.

---

### Post by NosLycn on 2007-02-25
Steve K

After you sudo killall gdm, do this command as a user in the /home/username folder:

> echo 'rxvt' > .xinitrc && echo 'killall Xmetisse' >> .xinitrc

Now (just incase you don't have rxvt):

> sudo apt-get install rxvt

Then:

> startx

You should get an ugly looking X11 session with only an rxvt terminal open.

In that terminal, run:

> Xmetisse -ac -geometry 1280x800 -depth 24 :1 & metisse-start-fvwm

Of course, your desktop resolution would have to be 1280x800 for that to work properly.  I use that resolution because I'm using a "widescreen" laptop.

This last command should get you an fvwm session with Metisse running.  To see if it works, press super-d.  That command zooms out to see all the desktops.  Same keystrokes to go back.


I personally haven't compiled it, so I don't know about your issues there.  However, I have attempted to start Xmetisse when not in an X11 session with only rxvt running.  I had similar errors.  Hence, I am ignoring them.

Best wishes.

---

### Post by floke on 2007-02-25
NosLync - FANTASTIC! 
This works absolutely! 

I have no idea why I want to have this, since its complete nonsense (revolving bloody windows!) - but its all good fun. Will have a play with this for the rest of the evening.

Many many many thanks for your help.

---

### Post by NosLycn on 2007-02-25
Steve K

The most useful feature I've found is the ability to zoom out the desktop.

I'm glad you got it working!  Happy Hacking!

---

### Post by darkmaster on 2007-02-27
Well then, trying out Metisse, I installed the deb packages cause I have some strange compiling problem with the metisse package (nucleo looks OK).
I try to start Xmetisse and everything else from a terminal inside a Gnome Session with Beryl running. Xmetisse in a terminal window, leaving this opened, metisse-... in another terminal window. It should work, look here:

[http://forum.beryl-project.org/viewtopic.php?f=51&t=3323&p=24526&hilit=metisse#p24526](http://forum.beryl-project.org/viewtopic.php?f=51&t=3323&p=24526&hilit=metisse#p24526)

It does not. I get the error explained by me in that link.
Many people had this error. So I followed other instrucions. I restarted Ubuntu and on the gdm screen, I pressed ctrl+alt+f1, logged in and called:

sudo killall gdm
sudo killall Xmetisse (It was not running, of course)

Than I tryed the two command with & beetween one and the other, bacause giving the first command alone from a normal terminal session would have just hanged everything in there. Absolutly no success. I allways get the same error.

```
Start fvwmi with args -d :0.0 -w metisse://127.0.0.1:1?password=no  for FvwmCompositor
[FVWM][main]: <<ERROR>> can't open display 127.0.0.1:1
```

What am I doing wrong? Why Metisse won't start even if gdm and X are not running?? This is driving me crazy, it's a week I'm trying to make it work. Please, someone help me.

---

### Post by NosLycn on 2007-02-27
If you want to try out Metisse from withing Gnome/Beryl, expect some weird side-effects (like Metisse disappearing randomly and Beryl messing with its graphics).  But, here's what you should try for getting it to work within an existing Gnome session while Beryl is running:

Open a terminal.  Run the following (replacing depth and geometry with your specifics):

> Xmetisse -ac -depth 24 -geometry 1280x800 :1 & metisse-start-fvwm

That should do it for you.

If you want to get metisse running on its own (without Gnome/Beryl getting in the way):

Exit Gnome.  At GDM, ALT-CTRL-F1.  killall gdm.  killall Xmetisse.

> nano .xinitrc

Quote out anything in that file with a #.  Add the following lines to that file:

> rxvt
killall Xmetisse

Save the file (ctrl-o).  Exit the editor (ctrl-x).  Run the following command from the terminal:

> startx

This will open a generic X11 session with only rxvt running (it probably works if you use xterm or another terminal emulator).  Inside that rxvt terminal, run (with your particulars instead of my depth and geometry):

> Xmetisse -ac -depth 24 -geometry 1280x800 :1 & metisse-start-fvwm

This will open an fvwm session with metisse running.  Now you can fold and rotate windows to your heart's content.

---

### Post by dan03 on 2007-03-02
This is the closest that I have come in getting metisse to run from gdm.
first create a .desktop file in /usr/share/xsession/metisse.desktop with this entry

[Desktop Entry]
Encoding=UTF-8
Name=Metisse
Comment=This session logs you into the Metisse 3D desktop
Exec=/home/foo/bin/metisse
Icon=
Type=Application

Next create .xinitrc file in your home directory with this entry.

#! /usr/bin/env bash
Xmetisse -geometry 1280x800 -ac :1 & metisse-start-fvwm 
rxvt # this will allow you to terminate this session by typing "exit" and to
     # restart the compositor using metisse-start-fvwm if it ever crashes
killall Xmetisse

Next link ln -snv .xinitrc .xession
Next linx ln -snv .xinitrc /home/foo/bin/metisse
remember to replace foo with your username. 

This works for me, but I get an Xsession: error before metisse runs, maybe someone can help fix this.

---

### Post by NosLycn on 2007-03-13
dan03,

I did what you did to get Metisse as a gdm session.  What I did to get rid of the error was rather odd.  I performed the following command from the console:

chmod 755 ~/.xinitrc

I hope it works for you.  If it does, let me know.

---

### Post by mcglnx on 2007-04-25
> **crazy___cow said:**
> I have made two debs to install metisse on ubuntu edgy.

[http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html](http://upload2.net/page/download/zubKbCXIWuz6z91/nucleo_0.6_i386.deb.html)
[http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html](http://upload2.net/page/download/KOmfp718OTeQ6aw/metisse_0.4.0-rc4_i386.deb.html)

To launch it, open a terminal in X and type:

Xmetisse -ac -depth 24 -geometry 1680×1050 :1 &
metisse-start-fvwm &

Change geometry and depth!

Crazy Cow

PS: if you have problems with dependencies, try to use treviño sources.list:
[http://3v1n0.tuxfamily.org/blog/?page_id=13](http://3v1n0.tuxfamily.org/blog/?page_id=13)


Thanks crazy__cow. I've tried to generate the deb using 
dh_make and dpkg-buildpackage -rfakeroot

But got an error. Finally I'm using plain (old) configure / make / make install.

Do you have a procedure on how you  generated your debs'?

Thanks,
M!

---

### Post by crazy___cow on 2007-04-27
I have used these commands:

dh_make -s -e [email]nick@provider.com[/email] -n -c gpl
./configure
debuild binary

---

### Post by Alendit on 2007-04-29
Hi

I can't compile cvs version of nucleo, i get
```
UdpPlusReceiver.cxx: In member function 'void nucleo::UdpPlusReceiver::_open(int, const char*)':
UdpPlusReceiver.cxx:55: error: 'SOL_SOCKET' was not declared in this scope
UdpPlusReceiver.cxx:55: error: 'SO_RCVBUF' was not declared in this scope
UdpPlusReceiver.cxx:68: error: 'SOL_SOCKET' was not declared in this scope
UdpPlusReceiver.cxx:68: error: 'SO_REUSEADDR' was not declared in this scope
```

./configure gives 
```
  glWindow backend?     GLX + Xinput glXGetProcAddress
  JPEG image support?   yes (using libjpeg)
  PNG image support?    yes (using libpng)
  EXIF support?         yes (using libexif)
  Freetype2 support?    yes
  DNS-SD support?       yes
  <eXpat/> support?     yes
  GnuTLS support?       yes
  ---
  FFmpeg plugin?        yes
  VNC plugin?           no (--with-vnc option not or badly used)
  Qt plugin?            yes
  GD plugin?            yes 
  ------
  Build OpenCV demos?  yes
```

I would like to download the packages, but upload2.net seems to be down. It would be nice if anyone uploaded the packages somewhere else. Thx

Alendit.

---

### Post by phenest on 2007-05-01
I'm unable to download them too. I'm also unable to compile nucleo and metisse. What packages do I need to use: configure, make, make install ? I've never done compiling before in Linux.

---

### Post by phenest on 2007-05-01
When I try to compile, this is the output:

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... configure: error: cannot run C++ compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

As I say, I've never compiled anything in Linux. So what do I do now?

---

### Post by Alendit on 2007-05-02
Hi

do you have build-essential package installed?

Do ```
sudo apt-get install build-essential
``` for it. You need also a video card driver with 3d acceleration (like fglrx for newer atis)

Alendit

---

### Post by phenest on 2007-05-02
Yep. Did that first.

---

### Post by mcglnx on 2007-05-06
I finally was able to start Metisse.
It works fine on an overlapping X session but VERY slooooooow using plain X session.

Plus it lost my MEtacity session :(

BTW: How can I run metacity with metisse? What is the command line?

Cheers,
M.

---

### Post by stevebarnes on 2007-05-26
Hey guys,

OK, I'm a Ubuntu learner. I've installed the packages OK, BUT I'm a bit stuck with starting the window manager. I understand the OS can run without a windowing session to start with, but I have it configured to "startx" (somewhere by default!). What do I have to do to start Metise? Do I need to quit my window environment and go back to command line somehow and then issue the command? How does this work? What about permissions and SUDO stuff?

Thanks for the help,
Steve B
Brisbane, Australia
Joomla Fan, vTiger User and Ubuntu devotee/learner!

---

### Post by rfurman24 on 2007-06-11
I do not know if anyone is still watching this thread but I got Metisse running using the debs from one of the first pages. I'm running Ubuntu 7.04 with Beryl and have Metisse running in beryl. I just created a script and run it from the application menu. I can run metisse on one side of the cube, looking glass on another and still have gnome/metacity on the other sides.

---

### Post by NosLycn on 2007-06-11
> **rfurman24 said:**
> I do not know if anyone is still watching this thread but I got Metisse running using the debs from one of the first pages. I'm running Ubuntu 7.04 with Beryl and have Metisse running in beryl. I just created a script and run it from the application menu. I can run metisse on one side of the cube, looking glass on another and still have gnome/metacity on the other sides.

Oh, cool!  How do you get different window managers on different sides of the cube?  This is of great interest to me, as I use my laptop to show off Linux at college.

---

### Post by NoWhereMan on 2007-06-11
> **rfurman24 said:**
> I do not know if anyone is still watching this thread but I got Metisse running using the debs from one of the first pages. I'm running Ubuntu 7.04 with Beryl and have Metisse running in beryl. I just created a script and run it from the application menu. I can run metisse on one side of the cube, looking glass on another and still have gnome/metacity on the other sides.

do you still run it windowed? I would like to have metisse as a default :/ (it's the only effects I can get to work on my box :/)

---

### Post by rfurman24 on 2007-06-11
I installed metisse using the packages debs in this thread. I installed looking glass in deb package off the internet I forgot to bookmark the sight if I find it I will post. I run this on one side of the cube for looking glass  /usr/share/lg3d/bin/lg3d-app-full
and I created a script to run on another side of the cube metisse
#!/bin/bash

Xmetisse -ac -depth 24 -geometry 1024x768 :2 & metisse-start-fvwm -wd :2 &

I is a little buggy as you could imagine and man does it tap my cpu and ram but it is kind of neat.
I still think at this point looking glass(cpu hog) and metisse are not ready for the desktop but I had to get it going for fun and to show off.

---

### Post by rfurman24 on 2007-06-11
I have yet to run metisse in its own session. I might play with that later. I have 1.5gb ram pc2700 and a p4 533mhz fsb computer and when all is running I am using about 1.2 gb ram and in the 90-95% cpu range.

---

### Post by rfurman24 on 2007-06-11
This is what I did to get looking glass

How to Install Project Looking Glass on Ubuntu

“There are 3 LG3D repositories. The stable repository has the latest stable releases (0.8.1, 1.0 etc.). The testing repository has the pre-release builds (alpha, beta etc.) for the latest version and the unstable repsoitory has the nightly builds.

Edit the /etc/apt/sources.list file

    sudo vi /etc/apt/sources.list

and add the following line which is suitable for you save the file and exit.

    # LG3D repsoitories

For stable

    deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib

For testing

    # deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) testing contrib

For Unstable

    # deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) unstable contrib

Suggested one is stable one

Now you need to update the repositories using the following command

    sudo apt-get update

Install looking glass using the following command

    sudo apt-get install lg3d-core

This will install all the required packages for looking glass desktop environment.

If you want to access the Looking glass Desktop environment logout from the existing KDE, Gnome, Xfce, or Fluxbox session and now you are on ubuntu’s GDM screen. In this you need to select options; selectsession.

From there, select Looking Glass, and Log in. Select “Just for this session” until you’re in love with it.


If I remember correctly I had problems with sudo apt-get install lg3d-core so I ended up just installing from synaptic after I had added the repositories. Hope this Helps someone.

---

### Post by cniesel on 2007-12-16
i found the debian packages again.

here are the links:
[http://yaro.gdi.pl/deb/edgy/nucleo_0.6-1_i386.deb]("http://yaro.gdi.pl/deb/edgy/nucleo_0.6-1_i386.deb")
[http://yaro.gdi.pl/deb/edgy/metisse_0.4.0-rc4-1_i386.deb]("http://yaro.gdi.pl/deb/edgy/metisse_0.4.0-rc4-1_i386.deb")

Enjoy
Cniesel

---

### Post by phenest on 2007-12-26
I have considerably more experience at compiling since my last post here, but I cannot Make Metisse. Neucleo is compiled and installed ok, but Metisse won't Make:
```
fvwmlib.h:11:78: error: X11/Intrinsic.h: No such file or directory
In file included from Flocale.c:48:
fvwmlib.h:121: warning: parameter names (without types) in function declaration
fvwmlib.h:122: warning: parameter names (without types) in function declaration
fvwmlib.h:123: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GetShadow’
fvwmlib.h:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GetHilite’
fvwmlib.h:125: error: expected ‘)’ before ‘foreground’
fvwmlib.h:126: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GetForeShadow’
fvwmlib.h:127: error: expected ‘)’ before ‘in’
fvwmlib.h:128: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GetTintedPixel’
fvwmlib.h:139: error: expected declaration specifiers or ‘...’ before ‘Pixel’
fvwmlib.h:141: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GetSimpleColor’
fvwmlib.h:143: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘GetColor’
fvwmlib.h:146: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fvwmlib_clone_color’
fvwmlib.h:147: error: expected declaration specifiers or ‘...’ before ‘Pixel’
fvwmlib.h:149: error: expected declaration specifiers or ‘...’ before ‘Pixel’
fvwmlib.h:149: error: expected declaration specifiers or ‘...’ before ‘Pixel’
fvwmlib.h:266: error: expected declaration specifiers or ‘...’ before ‘Pixel’
fvwmlib.h:272: error: expected declaration specifiers or ‘...’ before ‘Pixel’
In file included from Flocale.c:52:
PictureBase.h:62: error: expected specifier-qualifier-list before ‘Pixel’
In file included from PictureBase.h:107,
                 from Flocale.c:52:
Colorset.h:13: error: expected specifier-qualifier-list before ‘Pixel’
In file included from Flocale.c:52:
PictureBase.h:113: error: expected specifier-qualifier-list before ‘Pixel’
PictureBase.h:148: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PictureWhitePixel’
PictureBase.h:149: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘PictureBlackPixel’
In file included from Flocale.c:56:
FftInterface.h:13: error: expected declaration specifiers or ‘...’ before ‘Pixel’
FftInterface.h:13: error: expected declaration specifiers or ‘...’ before ‘Pixel’
In file included from Flocale.c:60:
PictureGraphics.h:122: error: expected declaration specifiers or ‘...’ before ‘Pixel’
PictureGraphics.h:133: error: expected declaration specifiers or ‘...’ before ‘Pixel’
Flocale.c:586: error: expected declaration specifiers or ‘...’ before ‘Pixel’
Flocale.c:586: error: expected declaration specifiers or ‘...’ before ‘Pixel’
Flocale.c: In function ‘FlocaleFontStructDrawString’:
Flocale.c:612: error: ‘fgsh’ undeclared (first use in this function)
Flocale.c:612: error: (Each undeclared identifier is reported only once
Flocale.c:612: error: for each function it appears in.)
Flocale.c:623: error: ‘fg’ undeclared (first use in this function)
Flocale.c: At top level:
Flocale.c:640: error: expected declaration specifiers or ‘...’ before ‘Pixel’
Flocale.c:641: error: expected declaration specifiers or ‘...’ before ‘Pixel’
Flocale.c: In function ‘FlocaleRotateDrawString’:
Flocale.c:706: error: ‘fg’ undeclared (first use in this function)
Flocale.c:706: error: ‘fgsh’ undeclared (first use in this function)
Flocale.c:707: warning: passing argument 10 of ‘FlocaleFontStructDrawString’ makes integer from pointer without a cast
Flocale.c:707: error: too many arguments to function ‘FlocaleFontStructDrawString’
Flocale.c:778: warning: passing argument 10 of ‘FlocaleFontStructDrawString’ makes integer from pointer without a cast
Flocale.c:778: error: too many arguments to function ‘FlocaleFontStructDrawString’
Flocale.c: In function ‘FlocaleDrawString’:
Flocale.c:1808: error: ‘Pixel’ undeclared (first use in this function)
Flocale.c:1808: error: expected ‘;’ before ‘fg’
Flocale.c:1886: error: ‘fg’ undeclared (first use in this function)
Flocale.c:1886: error: ‘colorset_t’ has no member named ‘fg’
Flocale.c:1887: error: ‘fgsh’ undeclared (first use in this function)
Flocale.c:1887: error: ‘colorset_t’ has no member named ‘fgsh’
Flocale.c:1900: warning: implicit declaration of function ‘PictureBlackPixel’
Flocale.c:1902: warning: implicit declaration of function ‘GetShadow’
Flocale.c:1919: warning: passing argument 6 of ‘FlocaleRotateDrawString’ makes pointer from integer without a cast
Flocale.c:1919: warning: passing argument 7 of ‘FlocaleRotateDrawString’ makes pointer from integer without a cast
Flocale.c:1919: error: too many arguments to function ‘FlocaleRotateDrawString’
Flocale.c:1924: error: too many arguments to function ‘FftDrawString’
Flocale.c:1957: warning: passing argument 10 of ‘FlocaleFontStructDrawString’ makes integer from pointer without a cast
Flocale.c:1957: error: too many arguments to function ‘FlocaleFontStructDrawString’
Flocale.c:1992: error: too many arguments to function ‘FftDrawString’
Flocale.c:2054: warning: passing argument 10 of ‘FlocaleFontStructDrawString’ makes integer from pointer without a cast
Flocale.c:2054: error: too many arguments to function ‘FlocaleFontStructDrawString’
Flocale.c: In function ‘FlocaleDrawUnderline’:
Flocale.c:2137: error: ‘Pixel’ undeclared (first use in this function)
Flocale.c:2137: error: expected ‘;’ before ‘fg’
Flocale.c:2141: error: ‘fg’ undeclared (first use in this function)
Flocale.c:2141: error: ‘colorset_t’ has no member named ‘fg’
Flocale.c:2142: error: ‘fgsh’ undeclared (first use in this function)
Flocale.c:2142: error: ‘colorset_t’ has no member named ‘fgsh’
Flocale.c:2147: warning: passing argument 6 of ‘PGraphicsDrawLine’ makes pointer from integer without a cast
Flocale.c:2147: warning: passing argument 7 of ‘PGraphicsDrawLine’ makes integer from pointer without a cast
Flocale.c:2147: error: too many arguments to function ‘PGraphicsDrawLine’
make[4]: *** [Flocale.o] Error 1
make[4]: Leaving directory `/home/steve/downloads/metisse/fvwm-insitu/libs'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/steve/downloads/metisse/fvwm-insitu'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/steve/downloads/metisse/fvwm-insitu'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/downloads/metisse'
make: *** [all] Error 2

```
I can't use the debs supplied here as I'm using 64 bit Ubuntu.

---

### Post by bartoz on 2008-02-28
I get exactly the same errors as phenest.
Is there anyone else trying to compile metisse?

---

### Post by ChameleonDave on 2008-06-20
I installed a large number of dependencies, and yet *núcleo* failed to compile, so I installed the .deb.

Metisse then failed to compile, so I installed the .deb for that too.  I had to remove the *fvwm* package to do so, because the .deb seemed to already include elements of FVWM.  I was later able to install the package *fvwm1*.

If I try to run it, I get this:

```
Start fvwmi with args -d :0 -w metisse://127.0.0.1:1  for FvwmCompositor
[FVWM][Echo]: "Starting Compositor -d :0 -w metisse://127.0.0.1:1 "
/usr//libexec/fvwm-insitu/2.5.20/FvwmCompositor: error while loading shared libraries: libNucleo.so.0: cannot open shared object file: No such file or directory
test: 1: ==: unexpected operator
test: 1: ==: unexpected operator
test: 1: ==: unexpected operator
[FVWM][Echo]: Default Config Loaded
[FVWM][Read]: <<ERROR>> file 'extra' not found in /home/david/.fvwm-metisse or /usr//share/fvwm-insitu

```

---

