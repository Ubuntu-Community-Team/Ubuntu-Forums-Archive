---
title: "farsight2 and pidgin"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by biasquez on 2009-07-24
on ubuntu, it's impossible to compile pidgin 2.6.0 with voice and video supporto because there isn't farsight.

maybe it depends on [https://bugs.launchpad.net/ubuntu/+source/gst-plugins-farsight/+bug/372829](https://bugs.launchpad.net/ubuntu/+source/gst-plugins-farsight/+bug/372829)

why package deleted?

---

### Post by MadMan2k on 2009-07-24
farsight, not farsight**2**

---

### Post by biasquez on 2009-07-24
> **MadMan2k said:**
> farsight, not farsight**2**


sorry, where is farsight to compile pidgin with voice and video support?
i installed all packages about farsight available from repository but this doesn't fix the problem.

---

### Post by MadMan2k on 2009-07-24
make sure you have libgstfarsight0.10-dev installed.

---

### Post by biasquez on 2009-07-25
i have installed these packages:

ii  libgstfarsight0.10-0                       0.0.12-1ubuntu2                                  Audio/Video communications framework: core l
ii  libgstfarsight0.10-dev                     0.0.12-1ubuntu2                                  Audio/Video communications framework: develo
ii  libtelepathy-farsight-dev                  0.0.7-1                                          Glue library between telepathy and farsight2
ii  libtelepathy-farsight0                     0.0.7-1                                          Glue library between telepathy and farsight2
ii  python-farsight                            0.0.12-1ubuntu2                                  Audio/Video communications framework: Python


but errors stills..

---

### Post by MadMan2k on 2009-07-25
could you post the error message?

---

### Post by biasquez on 2009-07-26
checking for GSTREAMER... yes
checking for gst_registry_fork_set_enabled in -lgstreamer-0.10... yes
checking for GSTINTERFACES... yes
checking for FARSIGHT... no
configure: error:
Dependencies for voice/video were not met.
Install the necessary gstreamer and farsight packages first.
Or use --disable-vv if you do not need voice/video support.

---

### Post by MadMan2k on 2009-07-26
what does
> pkg-config farsight2-0.10 --modversion
say?

---

### Post by biasquez on 2009-07-26
pkg-config farsight2-0.10 --modversion 

Package farsight2-0.10 was not found in the pkg-config search path.
Perhaps you should add the directory containing `farsight2-0.10.pc'
to the PKG_CONFIG_PATH environment variable
No package 'farsight2-0.10' found

---

### Post by khc on 2009-07-27
libgstfarsight0.10-dev. You will also need the various gstreamer codec plugins.

---

### Post by biasquez on 2009-07-28
> **khc said:**
> libgstfarsight0.10-dev. You will also need the various gstreamer codec plugins.

libgstfarsight0.10-dev is already installed on my system

---

### Post by MadMan2k on 2009-07-28
> **biasquez said:**
> libgstfarsight0.10-dev is already installed on my system
then something is <snip> up either with the package or your path. libgstfarsight0.10-dev should install /usr/lib/pkgconfig/farsight2-0.10.pc

---

### Post by biasquez on 2009-07-28
reinstalling libgstfarsight0.10-dev, it fixed my problem. Thanks for corporation! :D

---

### Post by kal on 2009-08-19
I have exactly the same problem. All packages are installed, but I get this error : 
> checking for FARSIGHT... no
configure: error:
Dependencies for voice/video were not met.
Install the necessary gstreamer and farsight packages first.
Or use --disable-vv if you do not need voice/video support.


These packages are installed :  gstreamer0.10-plugins-farsight, libgstfarsight0.10-0, libgstfarsight0.10-dev

Oh, and i'm on jaunty

---

### Post by maurom on 2009-08-19
Try installing the following packages:

libfarsight0.1-dev
libgstfarsight0.10-dev
libgstreamer-plugins-base0.10-dev

---

### Post by dcatdemon on 2009-08-19
Assuming that you are trying to compile pidgin 2.6.x, if you look at your configure.log, you should notice that pidgin requires farsight2-0.10 to be at least 0.0.9, the one that jaunty ships is 0.0.7.

Perhaps that might be the reason, I faced the same issue while compiling 2.6.1.

---

### Post by khc on 2009-08-20
> **dcatdemon said:**
> Assuming that you are trying to compile pidgin 2.6.x, if you look at your configure.log, you should notice that pidgin requires farsight2-0.10 to be at least 0.0.9, the one that jaunty ships is 0.0.7.

Perhaps that might be the reason, I faced the same issue while compiling 2.6.1.

The deb from karmic should work fine.

---

### Post by korin43 on 2009-08-20
I covered this here: [http://ubuntuforums.org/showthread.php?t=1244589&highlight=pidgin+compiling](http://ubuntuforums.org/showthread.php?t=1244589&highlight=pidgin+compiling)

You can get the versions you need for farsight2, libnice and gstreamer from this ppa: [https://launchpad.net/~kalon33/+archive/ppa](https://launchpad.net/~kalon33/+archive/ppa)

---

