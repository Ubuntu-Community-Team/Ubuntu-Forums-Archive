---
title: "How to install development headers from source?"
date: 2015-09-03
forum: MINT
---

### Post by dansk on 2015-09-03
This question has been asked elsewhere, but due to my unusual circumstances none of the answers will work for me.

The general version of what I'm trying to do is this:

Installing package X requires the development headers for package Y (Y-dev).  For various reasons, I'm forced to compile and install package Y from source.  The binaries install just fine, but I have no idea how to also compile the -dev package at the same time.

Now, the answers I've found elsewhere on the internet generally give the same advice: "It's simple, just use $ sudo apt-get install Y-dev!"  The problem is, the computer I'm trying to install this on is not connected to the internet, and it's not possible for me to connect it to the internet due to the security restrictions of my current residence.  My only access to the internet here is via a public computer, where I download files and manually copy them to my personal computer via a USB flash drive.

I feel like this should be extremely easy to do, but for the life of me I can't figure out how to do it.  How do I compile a -dev package from source??

---

### Post by mc4man on 2015-09-03
Naming a package "y" would prove more fruitful, also there is a difference between 'packaging' a  compiled source & installing a compiled source, which are you doing?

Generically speaking when you compile a source headers & includes are created & if installing the compiled source they are also installed, typical default locations of /usr/local/lib & /usr/local/include
(the configure could have some effect also

---

### Post by dansk on 2015-09-03
I'm trying to install liblcms2-dev in order to install libcdr.

Sorry for the confusion over terminology, I'm installing a source that I've compiled myself.

If those headers should already be installed, is there some way I can tell the system that when it looks for liblcms2-dev, it should go to those locations?

---

### Post by mc4man on 2015-09-03
sometimes you can add PKG_CONFIG_PATH=/path/to/the/pkgconfig folder in your ./configure line. 
Generally using export first in your terminal works also - so,
when you open the terminal at your source to configure first run an export(s)

export PKG_CONFIG_PATH=/path/to/pkgconfig

Sometimes you also need to export the library path, ie.
export LIBRARY_PATH=/path/to/lib

What's in /usr/local/include & /usr/local/lib?

What version of lcms2 do you need & what release of Ubuntu?
(I provide lcms2-2 (2.6-3) in a ppa for 14.04

---

### Post by dansk on 2015-09-03
I'm using Linux Mint 17.2, which is based on Trusty-updates, I believe.

I've already installed lcms2-2.7.  I decided to compile it from source because I couldn't find a pre-built package that would install on my computer.

Give me a few minutes to go to my room and find out what's in /usr/local/include and /usr/local/lib...

---

### Post by PaulW2U on 2015-09-03
*Thread moved to **MINT**.*

---

### Post by dansk on 2015-09-03
```
/usr/local/include $ lsFlexLexer.h  gc  gc.h  gstreamer-1.0  lcms2.h  lcms2_plugin.h  pygobject-3.0




/usr/local/lib $ ls
gstreamer-1.0            libgstallocators-1.0.so          libgstcontroller-1.0.so.0.502.0  libgstrtp-1.0.so            libhpip.so.0.0.1
libcord.a                libgstallocators-1.0.so.0        libgstfft-1.0.la                 libgstrtp-1.0.so.0          libhpmud.la
libcord.la               libgstallocators-1.0.so.0.502.0  libgstfft-1.0.so                 libgstrtp-1.0.so.0.502.0    libhpmud.so
libcord.so               libgstapp-1.0.la                 libgstfft-1.0.so.0               libgstrtsp-1.0.la           libhpmud.so.0
libcord.so.1             libgstapp-1.0.so                 libgstfft-1.0.so.0.502.0         libgstrtsp-1.0.so           libhpmud.so.0.0.6
libcord.so.1.0.3         libgstapp-1.0.so.0               libgstnet-1.0.la                 libgstrtsp-1.0.so.0         liblcms2.a
libfl.a                  libgstapp-1.0.so.0.502.0         libgstnet-1.0.so                 libgstrtsp-1.0.so.0.502.0   liblcms2.la
libfl.la                 libgstaudio-1.0.la               libgstnet-1.0.so.0               libgstsdp-1.0.la            liblcms2.so
libfl_pic.a              libgstaudio-1.0.so               libgstnet-1.0.so.0.502.0         libgstsdp-1.0.so            liblcms2.so.2
libfl_pic.la             libgstaudio-1.0.so.0             libgstpbutils-1.0.la             libgstsdp-1.0.so.0          liblcms2.so.2.0.7
libfl_pic.so             libgstaudio-1.0.so.0.502.0       libgstpbutils-1.0.so             libgstsdp-1.0.so.0.502.0    libpyglib-gi-2.0-python3.la
libfl_pic.so.2           libgstbase-1.0.la                libgstpbutils-1.0.so.0           libgsttag-1.0.la            libpyglib-gi-2.0-python3.so
libfl_pic.so.2.0.0       libgstbase-1.0.so                libgstpbutils-1.0.so.0.502.0     libgsttag-1.0.so            libpyglib-gi-2.0-python3.so.0
libfl.so                 libgstbase-1.0.so.0              libgstreamer-1.0.la              libgsttag-1.0.so.0          libpyglib-gi-2.0-python3.so.0.0.0
libfl.so.2               libgstbase-1.0.so.0.502.0        libgstreamer-1.0.so              libgsttag-1.0.so.0.502.0    liby.a
libfl.so.2.0.0           libgstcheck-1.0.la               libgstreamer-1.0.so.0            libgstvideo-1.0.la          pkgconfig
libgc.a                  libgstcheck-1.0.so               libgstreamer-1.0.so.0.502.0      libgstvideo-1.0.so          python2.7
libgc.la                 libgstcheck-1.0.so.0             libgstriff-1.0.la                libgstvideo-1.0.so.0        python3.4
libgc.so                 libgstcheck-1.0.so.0.502.0       libgstriff-1.0.so                libgstvideo-1.0.so.0.502.0  sane
libgc.so.1               libgstcontroller-1.0.la          libgstriff-1.0.so.0              libhpip.la                  site_ruby
libgc.so.1.0.3           libgstcontroller-1.0.so          libgstriff-1.0.so.0.502.0        libhpip.so                  soundconverter
libgstallocators-1.0.la  libgstcontroller-1.0.so.0        libgstrtp-1.0.la                 libhpip.so.0

```

---

### Post by mc4man on 2015-09-03
Try - 
```
export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig
```
Then in same terminal try your ./configure again
If not, in same terminal run - 
```
export LIBRARY_PATH=/usr/local/lib
```
and try again
If still failing see if there is a configure log in your source, look thru

Note that an export is only good in the terminal it is run in so they must be re-run in new terminal instances.
Also note that one should run a sudo ldconfig after manually installing libs (sudo make install method), you should do that in addition to above (or even before

(I'll have to take a look to see if lcms2-2.7 provides any advantage to 14.04 & if it breaks anything as many sources use.

---

### Post by dansk on 2015-09-03
When I tried it this time, it's asking specifically for liblcms2-2.6.  I may have to just remove lcms and start over...

---

### Post by dansk on 2015-09-03
Thank you very much for your help, I eventually got it working with a different version of lcms.

---

### Post by mc4man on 2015-09-03
> **dansk said:**
> When I tried it this time, it's asking specifically for liblcms2-2.6.  I may have to just remove lcms and start over...

If you want a packaged build of 2.6 there are packages here or grab the source & build via debian/rules. This way the packages will  be installed in the current multi-arch locations & will be found with no problems 
[https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests](https://launchpad.net/~mc3man/+archive/ubuntu/mpv-tests)

---

