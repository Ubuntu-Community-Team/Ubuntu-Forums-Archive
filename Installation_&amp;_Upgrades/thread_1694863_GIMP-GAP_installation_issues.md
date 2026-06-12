---
title: "GIMP-GAP installation issues"
date: 2011-02-25
forum: Installation &amp; Upgrades
---

### Post by Lurker4hire on 2011-02-25
When I run ./configure for gimp-gap it doesn't find these libraries.  

>  ... 

 checking for x264_encoder_open in -lx264... no 
checking for xvid_global in -lxvidcore... no 

...   

x264 library (libx264) not found (not critical, but no open H264 video codec support)
 xvid library (libxvidcore) not found (not critical, but no open xvid video codec support)

 ** WARNING: xvid library (libxvidcore) not found    The AVI encoder  plug-in is built without MPEG4 support.    You can get the xvid codec  at:  [http://www.xvid.org/downloads.html](http://www.xvid.org/downloads.html)   I have installed xvidcore manually through their website and  the libx264-dev through apt-get. I'm not sure why gap is not finding  these libraries.

 I was doing some research with no avail. Think it might have something  to do with "--enable-shared" and static libraries. I'm a noob though and  can't figure it out. Any help would be much appreciated.

 I'm on Ubuntu 10.10, btw.

---

### Post by Lurker4hire on 2011-02-25
Bump.. was back on page 7. 

Any ideas?

---

