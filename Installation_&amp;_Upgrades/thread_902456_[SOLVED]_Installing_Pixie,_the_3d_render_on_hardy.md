---
title: "[SOLVED] Installing Pixie, the 3d render on hardy"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by afbase on 2008-08-27
I downloaded Pixie source 2.2.4 (             [Pixie-src-2.2.4.tgz]("http://downloads.sourceforge.net/pixie/Pixie-src-2.2.4.tgz?modtime=1214203129&big_mirror=1")             &nbsp;) from Source Forge. I then
```

tar -xf Pixie-src-2.2.4.tgz
cd Pixie
CC="gcc-3.3" CXX="g++-3.3" ./configure
make

```When i did the "CC="gcc-3.3" CXX="g++-3.3" ./configure"  it stated I didn't have FLTK nor OpenEXR installed but I installed them.  I installed FLTK using the guidelines found below this code and OpenEXR with Synaptic. Ignoring this I did the make.  i got this set of errors:
```

clinton@clinton-laptop:~/Pixie$ make
make  all-recursive
make[1]: Entering directory `/home/clinton/Pixie'
Making all in src
make[2]: Entering directory `/home/clinton/Pixie/src'
Making all in common
make[3]: Entering directory `/home/clinton/Pixie/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/common'
Making all in file
make[3]: Entering directory `/home/clinton/Pixie/src/file'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/file'
Making all in framebuffer
make[3]: Entering directory `/home/clinton/Pixie/src/framebuffer'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/framebuffer'
Making all in openexr
make[3]: Entering directory `/home/clinton/Pixie/src/openexr'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/openexr'
Making all in precomp
make[3]: Entering directory `/home/clinton/Pixie/src/precomp'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/precomp'
Making all in gui
make[3]: Entering directory `/home/clinton/Pixie/src/gui'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/gui'
Making all in rgbe
make[3]: Entering directory `/home/clinton/Pixie/src/rgbe'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/rgbe'
Making all in sdr
make[3]: Entering directory `/home/clinton/Pixie/src/sdr'
make  all-am
make[4]: Entering directory `/home/clinton/Pixie/src/sdr'
make[4]: *** No rule to make target `sdr.lo', needed by `libsdr.la'.  Stop.
make[4]: Leaving directory `/home/clinton/Pixie/src/sdr'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/clinton/Pixie/src/sdr'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/clinton/Pixie/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/clinton/Pixie'
make: *** [all] Error 2


```NOTE:I am following the guidelines from [http://www.degrendel.com/news/2008/8/4/compiling-pixie](http://www.degrendel.com/news/2008/8/4/compiling-pixie).  This is for a math class at my university. any help is appreciated.

---

### Post by Partyboi2 on 2008-08-27
Do you have g++-3.3 installed?
For me to get this to work I needed to install
```
libxext-dev libtiff4-dev libopenexr-dev flex bison gawk g++-3.3
```
If  g++-3.3 is not installed it will state that you don't have 
FLTK nor OpenEXR installed.
Also when you compiled fltk did it install without errors?

---

### Post by afbase on 2008-08-28
> **Partyboi2 said:**
> Do you have g++-3.3 installed?
For me to get this to work I needed to install
```
libxext-dev libtiff4-dev libopenexr-dev flex bison gawk g++-3.3
```If  g++-3.3 is not installed it will state that you don't have 
FLTK nor OpenEXR installed.
Also when you compiled fltk did it install without errors?
Thank you for your help i didn't have  flex, bison , or gawk installed. I just installed them through synaptic.  I retried everything over again . on 'make' i got this set of errors
```

clinton@clinton-laptop:~/Pixie$ make
make  all-recursive
make[1]: Entering directory `/home/clinton/Pixie'
Making all in src
make[2]: Entering directory `/home/clinton/Pixie/src'
Making all in common
make[3]: Entering directory `/home/clinton/Pixie/src/common'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/common'
Making all in file
make[3]: Entering directory `/home/clinton/Pixie/src/file'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/file'
Making all in framebuffer
make[3]: Entering directory `/home/clinton/Pixie/src/framebuffer'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/framebuffer'
Making all in openexr
make[3]: Entering directory `/home/clinton/Pixie/src/openexr'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/openexr'
Making all in precomp
make[3]: Entering directory `/home/clinton/Pixie/src/precomp'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/precomp'
Making all in gui
make[3]: Entering directory `/home/clinton/Pixie/src/gui'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/gui'
Making all in rgbe
make[3]: Entering directory `/home/clinton/Pixie/src/rgbe'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/clinton/Pixie/src/rgbe'
Making all in sdr
make[3]: Entering directory `/home/clinton/Pixie/src/sdr'
make  all-am
make[4]: Entering directory `/home/clinton/Pixie/src/sdr'
make[4]: *** No rule to make target `sdr.lo', needed by `libsdr.la'.  Stop.
make[4]: Leaving directory `/home/clinton/Pixie/src/sdr'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/clinton/Pixie/src/sdr'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/clinton/Pixie/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/clinton/Pixie'
make: *** [all] Error 2


```
To answer your question about FLTK installation.  I ran into some problems initially, but did get it to install properly without any errors.

i haven't built much from source before.  I'm somewhat of a noob in this aspect of linux (pretty much with everything else too).

---

### Post by BLTicklemonster on 2008-08-28
> **Partyboi2 said:**
> Do you have g++-3.3 installed?
For me to get this to work I needed to install
```
libxext-dev libtiff4-dev libopenexr-dev flex bison gawk g++-3.3
```
If  g++-3.3 is not installed it will state that you don't have 
FLTK nor OpenEXR installed.
Also when you compiled fltk did it install without errors?

And installed fltk, and I get this:

--->            FLTK not found.
---> You can download it from [www.fltk.org](www.fltk.org)
---> show will not be built.

---

### Post by afbase on 2008-08-28
> **Partyboi2 said:**
> Do you have g++-3.3 installed?
For me to get this to work I needed to install
```
libxext-dev libtiff4-dev libopenexr-dev flex bison gawk g++-3.3
```If  g++-3.3 is not installed it will state that you don't have 
FLTK nor OpenEXR installed.
Also when you compiled fltk did it install without errors?
[quote=BLTicklemonster;5678715]And installed fltk, and I get this:

--->            FLTK not found.
---> You can download it from [www.fltk.org]("http://www.fltk.org/")
---> show will not be built.
[/quote]



According to this [blog]("http://www.degrendel.com/news/2008/8/4/compiling-pixie")

there are other packages that need to be installed. here is a quote from the blog.
> 
[LIST=1]
[*]Dependencies needed: libjpeg, libpng, libtiff, libice, libopenexr, libxext and their respective development packages. Note that there are probably others, but these are the only ones I recall.
[*]Compile and install [FLTK]("http://fltk.org/").  The Ubuntu package doesn't have OpenGL support, which Pixie needs.  Also, FLTK's configure script will by default install to */usr/local/*.  You might need to add */usr/local/lib* to a new file in */etc/ld.so.conf.d/*.  Make sure you run **ldconfig** as root after installation.
[/LIST]
This second step was confusing to me.  I wasn't sure what to do there.  I skipped most of this step besides a simple ordinary compile and install.  

I tried both methods of step 3.  In both cases the ./configure commands worked.  The only trouble I ran into was the 'make' command.

I believe this is the blog of SirNuke on the ubuntu forums.

---

### Post by Partyboi2 on 2008-08-28
> **BLTicklemonster said:**
> And installed fltk, and I get this:

--->            FLTK not found.
---> You can download it from [www.fltk.org]("http://www.fltk.org")
---> show will not be built.
Did you download and compile FLTK from [[COLOR=Blue]here[/COLOR]]("http://fltk.org/") or did you use the libfltk1.1-dev package from the repo's?

---

### Post by BLTicklemonster on 2008-08-28
Downloaded and installed from the site.

---

### Post by afbase on 2008-08-28
> **Partyboi2 said:**
> Did you download and compile FLTK from [[COLOR=Blue]here[/COLOR]]("http://fltk.org/") or did you use the libfltk1.1-dev package from the repo's?
I downloaded the source from [http://www.fltk.org](http://www.fltk.org).  I managed to install it with no errors after several attempts.

---

### Post by Partyboi2 on 2008-08-28
There is a fltk1.1.9 deb package that can be downloaded from [[COLOR=Blue]here[/COLOR]]("http://www.mediafire.com/file/ymwm5i3zj93/fltk_1.1.9-1_i386.deb")
and a pixie2.2.4 deb package from [[COLOR=Blue]here[/COLOR]]("http://www.mediafire.com/file/kghkddmmvnq/pixie_2.2.4.1_i386.deb"). Alot easier then trying to compile.

---

### Post by afbase on 2008-08-29
I just want to say pixie works just fine.  I tested a rib file to see if it works.  here is the result!

---

### Post by render_man_ on 2009-11-12
I've been trying to install Pixie but it just won't let me. 
After solving some initial errors on fltk I now have the following errors:[INDENT]usr/bin/install: `shaders/spotlight.sdr' and `/home/priyamvad/lib/Pixie/shaders/spotlight.sdr' are the same file                                                                   
 /usr/bin/install -c -m 644 'shaders/spotlight.sl' '/home/priyamvad/lib/Pixie/shaders/spotlight.sl'                                                                                 
/usr/bin/install: `shaders/spotlight.sl' and `/home/priyamvad/lib/Pixie/shaders/spotlight.sl' are the same file                                                                     
make[2]: *** [install-shaderDATA] Error 1                                                                                                                                           
make[2]: Leaving directory `/home/priyamvad/lib/Pixie'                                                                                                                              
make[1]: *** [install-am] Error 2                                                                                                                                                   
make[1]: Leaving directory `/home/priyamvad/lib/Pixie'                                                                                                                              
make: *** [install-recursive] Error 1                 


[/INDENT]Just to be clear I'm trying to install pixie 2.2.6 with fltk2.2 on a 64bit machine.
Any help is appreciated!!

---

### Post by afbase on 2009-11-13
render_man_,

it's best to make a new thread for this issue you are having.  This was an issue I had on Hardy Heron well over a year ago.

---

