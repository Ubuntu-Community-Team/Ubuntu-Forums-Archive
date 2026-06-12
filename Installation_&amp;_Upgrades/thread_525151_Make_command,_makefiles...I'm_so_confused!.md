---
title: "Make command, makefiles...I'm so confused!"
date: 2007-08-14
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-14
I've just attempted for a while to install two different Ubuntu programs: one is called Powerd, and the other is a Quicktime package type thing for Ubuntu. Both require use of the make command. I can't for the life of me figure out how to make this work though. I "cd" to the right directory, but I don't know how to use the make command to get things going. All of the info online seems to be about programming with make, not just using it. Any help please?

-Dan

---

### Post by PaulFr on 2007-08-14
As a one-time step, install the basic tools using```
sudo apt-get install build-essential
```This gives you a C/C++ compiler and make.Then for all source packages, this is the usual drill I follow -- after unpacking the package (if it is a proper Linux package), then```
**cd <directory_where_you_unpacked_the_source_files>**
**ls README* INSTALL***

<-- Read the README* and INSTALL* files to
     see if you need to install any packages
     before compiling this package; also they may
     give you instructions on the following commands
<Install those packages, usually the -dev versions to get appropriate header files>

**cd <directory_where_you_unpacked_the_source_files>**
**./configure --help**   <--this is to see what options are supported
**./configure [any options you have selected above]**
**make**          <-- this is to compile the source files
**sudo make install**    <-- this is to install the package deliverables
```Hope this helps.

---

### Post by DirtDawg on 2007-08-14
Before you make anything, you need to install a package called build-essential
```
 sudo apt-get install build-essential 
```

Then you usually cd to the proper folder, enter
```
 ./configure 
```
Then
```
 make 
```
Then
```
 sudo make install 
```
I would also recommend installing checkinstall 
```
 sudo apt-get install checkinstall 
```
This creates a .deb package for easy uninstall. Then you use that in place of make intstall
```
 sudo checkinstall 
```

Feel free to post any error messages you need help with. Installing from source is not as difficult as it looks, but can sometimes get hairy.

---

### Post by DirtDawg on 2007-08-14
By the way, this website has great summaries about various install methods:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)

---

### Post by dbsoundman on 2007-08-14
Well, I tried the method that you all suggested, but I can't get the ./configure demand to work. this is what I get:
```
dan@blackdiamond:~/Quicktime/quicktime4linux-2.2$ ./configure
[: 22: ==: unexpected operator
[: 27: ==: unexpected operator
./configure: 39: Syntax error: Bad fd number

```

If you're curious, quicktime4linux is the program I'm trying to install here, and I also need to install powerd when I can get this to work. The directory I was in at the time has all the makefiles in it; I'm not entirely sure what is in the other directories within this directory. Any suggestions?

BTW, this is the file listing when I use the ls command:
```
dan@blackdiamond:~/Quicktime/quicktime4linux-2.2$ ls
atom.c                edts.c             make_package       smhd.c
avcc.c                elst.c             make_streamable.c  stbl.c
avi_hdrl.c            encore2            matrix.c           stco.c
avi_idx1.c            encore50           mdat.c             stsc.c
avi_indx.c            esds.c             mdhd.c             stsd.c
avi_ix.c              faac-1.24          mdia.c             stsdtable.c
avi_movi.c            faad2-2.0          minf.c             stss.c
avi_odml.c            fastjpg.c          mmx.h              stsz.c
avi_riff.c            fastjpg.h          moov.c             stts.c
avi_strl.c            fastjpgmacro.h     mp4a.c             tkhd.c
CHANGELOG             ffmpeg.052906      mp4a.h             trak.c
cmodel_default.c      funcprotos.h       mpeg4.c            twos.c
cmodel_float.c        global_config      mpeg4.c.orig       twos.h
cmodel_permutation.h  graphics.c         mpeg4.h            udta.c
cmodel_yuv420p.c      graphics.h         mvhd.c             ulaw.c
cmodel_yuv422.c       hdlr.c             plugin.c           ulaw.h
codecs.c              ima4.c             plugin.c.orig      util.c
codecs.h              ima4.h             qtcache.c          v308.c
colormodels.c         index.bt           qtdv.c             v308.h
colormodels.h         jdatadst.c         qtdv.h             v408.c
configure             jdatasrc.c         qtffmpeg.c         v408.h
conftest.c            jpeg               qtffmpeg.h         v410.c
COPYING               jpeg.c             qth264.c           v410.h
ctab.c                jpeg.h             qth264.h           vbraudio.c
dechunk.c             jpeg-mmx.0.1.6     qtinfo.c           vmhd.c
depend.dv             jpeg_old.c         qtmp3.c            vorbis.c
depend.encore50       jpeg_old.h         qtmp3.h            wma.c
depend.faac           lame-3.93.1        qtpng.c            wma.h
depend.faad           libdv-0.104        qtpng.h            wmx1.c
depend.ffmpeg         libdv.c            qtprivate.h        wmx1.h
depend.jpeg           libdv.h            qtvorbis.h         wmx2.c
depend.lame           libmjpeg.c         quicktime.c        wmx2.h
depend.mad            libmjpeg.c.orig    quicktime.h        workarounds.c
depend.vorbis         libmjpeg.h         quicktime.h.orig   workarounds.h
dinf.c                libogg-1.1.2       rawaudio.c         x264.052906
div3.c                libvorbis-1.1.1    rawaudio.h         xanimjpeg.c
div3.h                Makefile           raw.c              xanimjpeg.h
divx.c                Makefile.2         raw.h              yuv2.c
divx.c.2              Makefile.50        README             yuv2.h
divx.c.50             Makefile.dv        rechunk.c          yuv2mov.c
divx.c.encore2        Makefile.encore2   recover.c          yuv4.c
divx.c.encore50       Makefile.encore50  revdct.c           yuv4.h
divx.h                Makefile.faac      rle.c              yuv4toyuv.c
divx.h.2              Makefile.faad      rle.h              yuv9.h
divx.h.50             Makefile.ffmpeg    rtjpeg.c           yv12.c
docs                  Makefile.jpeg      rtjpeg_core.c      yv12.h
dref.c                Makefile.lame      rtjpeg_core.c.X
dump.c                Makefile.mad       rtjpeg_core.h
dv.c.orig             Makefile.vorbis    rtjpeg.h

```


-Dan

---

### Post by timseal on 2007-08-14
Try looking in README.  Also try just 'make' on it's own.  What happens?

---

### Post by dbsoundman on 2007-08-14
It appears that there is no readme or install file, as the ls command doesn't turn them up.

When I try make on it's own, this is what I get:
```
dan@blackdiamond:~/Quicktime/quicktime4linux-2.2$ make
/bin/sh: Syntax error: end of file unexpected (expecting "then")
/bin/sh: cannot create i686/c_flags: Directory nonexistent
/bin/sh: cannot create i686/lame_flags: Directory nonexistent
/bin/sh: cannot create i686/objs: Directory nonexistent
make: *** No rule to make target `i686', needed by `all'.  Stop.

```

As a side note, I've also been trying to install a program called powerd, which is an .rpm file. I followed the instructions on the "how to install ANYTHING" website, and what happens is there's a brief pause in the command line, then it just shows the next line ready for entry; no status indications or anything. I don't know much about how this program works, but I can't find any evidence of it being installed, but the readme files are also very vague as of yet. Anyone have experiences with this one?

-Dan

---

### Post by DirtDawg on 2007-08-14
Do you need those packages specifically? There's a package in the repository that says it is based on quicktime4linux called [libquicktime0]("http://packages.ubuntu.com/feisty/libs/libquicktime0"). If you're trying to get multimedia to work, read the documentation concerning proprietary formats here:
[https://help.ubuntu.com/7.04/musicvideophotos/C/index.html](https://help.ubuntu.com/7.04/musicvideophotos/C/index.html)

There's very little about Powerd out there, but it seems to be software that detects power outages and safely shuts down all computers on a network, is that right? I am not familiar with this, but there may be an alternative application that is in the repositories. 

Usually, building from source is a last resort if you cannot find what you want in the repositories, you can't find a '.deb' file, or you need the absolute latest release of certain software. 

The reason I'm suggesting this is the errors you are getting are not standard make errors. Usually errors return packages that need installing as dependencies which is fairly simple to solve, but it looks like you found troublemakers.

EDIT: btw, if you do need Powerd specifically, try building that from source. Using 'alien' to convert an .rpm into a .deb (I assume that is what you tried) does not always work.

---

### Post by dbsoundman on 2007-08-15
What I'm trying to do with the Quicktime stuff is make Quicktime videos that I view on the web in Swiftfox work; maybe I'm using the wrong approach here? That other package you mentioned is already installed, so that's not the issue it seems.

I'll do some experimentation, but how exactly do I build something from source?

-Dan

---

### Post by DirtDawg on 2007-08-15
EDIT: You should check this link out first. I thought of it after I wrote the rest of the jibber-jabber
It's the unofficial guide. This particular "chapter" will help you install the Win32 Codecs package, among many others:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Multimedia_Codecs_.26_Browser_Plug-ins)

- - - - - 
There is a wiki page about restricted formats here:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you read this page and follow the instructions, you should be able to play just about any restricted format there is. That's not to say everything works perfectly all the time, but quicktime videos should work. I've never used Swiftfox, but I don't think that should make any difference.

If you've already followed the instructions from the wiki page and things still are not working, then there's an issue somewhere else.

As far as compiling, the instructions above really are it. Configure, make, make install. It's usually fairly straightforward (more or less), just not this time.

EDIT: Also, if you haven't already, try installing MPlayer and it's Firefox plugin. Details here:
[https://help.ubuntu.com/community/MPlayer](https://help.ubuntu.com/community/MPlayer)

---

### Post by PaulFr on 2007-08-15
I heartily second the advice given above: please use the restricted codecs and browser plugins docs to get QuickTime working.

I would just like to point out (after downloading quicktime4linux-2.2 myself) there is a README file in the directory with the following contents:> $ **more README**
Quicktime for Linux

by

Heroine Virtual Ltd. (Motion picture solutions for Linux)    
Send harrassment to: [email]broadcast@earthling.net[/email]
Homepage: heroinewarrior.com/quicktime
Requires libmpeg3 from heroinewarrior.com
------------------------------------------------------------------------

This is a Quicktime front end for UNIX in a library.



Building:
Quicktime for Linux requires a built copy of of libmpeg3 in a directory next to 
itself.
This is used for the mp3 interface.

Your directory structure should thus be:
/my_directory
/my_directory/libmpeg3-*.*.*
/my_directory/quicktime4linux-*.*.*


type "make" in the libmpeg3 directory.
type "make" in the quicktime directory.
type "make util" to get quicktime to build some utilities.



The makefiles automatically configure themselves.  The library is in
i686/libquicktime.a. You should manually set the CFLAGS environment
variable with the optimum optimization parameters for your i686
derivative.
..Note that this means you do not need to run configure, but you do need to have libmpeg3. However, I do not think installing this will solve your problem. The previous post is the correct way to go IMHO.

---

### Post by madmatrixz3000 on 2007-11-21
Yeah i'm trying to install quicktime too.

I am in the file and get this.

> root@Gamer:~/Quicktime/quicktime4linux-2.2# ./configure
./configure: 22: arch: not found
[: 22: i686: unexpected operator
[: 27: ==: unexpected operator
./configure: 39: Syntax error: Bad fd number
root@Gamer:~/Quicktime/quicktime4linux-2.2# make
/bin/sh: Syntax error: end of file unexpected (expecting "then")
/bin/sh: cannot create i686/c_flags: Directory nonexistent
/bin/sh: cannot create i686/lame_flags: Directory nonexistent
/bin/sh: cannot create i686/objs: Directory nonexistent
make: *** No rule to make target `i686', needed by `all'.  Stop.
root@Gamer:~/Quicktime/quicktime4linux-2.2# sudo make
/bin/sh: Syntax error: end of file unexpected (expecting "then")
/bin/sh: cannot create i686/c_flags: Directory nonexistent
/bin/sh: cannot create i686/lame_flags: Directory nonexistent
/bin/sh: cannot create i686/objs: Directory nonexistent
make: *** No rule to make target `i686', needed by `all'.  Stop.
root@Gamer:~/Quicktime/quicktime4linux-2.2# make install
/bin/sh: Syntax error: end of file unexpected (expecting "then")
/bin/sh: cannot create i686/c_flags: Directory nonexistent
/bin/sh: cannot create i686/lame_flags: Directory nonexistent
/bin/sh: cannot create i686/objs: Directory nonexistent
cp i686/qtdump i686/make_streamable i686/qtinfo i686/dechunk i686/yuv2mov i686/yuv4toyuv i686/recover i686/rechunk /usr/bin
cp: cannot stat `i686/qtdump': No such file or directory
cp: cannot stat `i686/make_streamable': No such file or directory
cp: cannot stat `i686/qtinfo': No such file or directory
cp: cannot stat `i686/dechunk': No such file or directory
cp: cannot stat `i686/yuv2mov': No such file or directory
cp: cannot stat `i686/yuv4toyuv': No such file or directory
cp: cannot stat `i686/recover': No such file or directory
cp: cannot stat `i686/rechunk': No such file or directory
make: *** [install] Error 1
root@Gamer:~/Quicktime/quicktime4linux-2.2# 


---

