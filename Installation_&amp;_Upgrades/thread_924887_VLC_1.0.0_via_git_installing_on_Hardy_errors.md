---
title: "VLC 1.0.0 via git installing on Hardy errors"
date: 2008-09-20
forum: Installation &amp; Upgrades
---

### Post by Neo_The_User on 2008-09-20
***SOLVED!!!***

[http://ubuntuforums.org/showthread.php?t=950927](http://ubuntuforums.org/showthread.php?t=950927) will be a much better guide / thread regarding VLC compilation.

After spending about a whole week of trying to get VLC 1.0.0 on Hardy I get these errors.

make[5]: *** [libspeex_plugin_la-speex.lo] Error 1
make[5]: Leaving directory `/home/neo/vlc/build/modules/codec'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/neo/vlc/build/modules/codec'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/neo/vlc/build/modules/codec'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/neo/vlc/build/modules'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/neo/vlc/build'
make: *** [all] Error 2

I edited the speex.c file ([http://pastebin.ca/1229915](http://pastebin.ca/1229915)) and the x264.c file ([http://pastebin.ca/1219422](http://pastebin.ca/1219422)) and it works. VLC 1.0.0 now works for Ubuntu 8.04. BEWARE! VLC 1.0 IS NOT STABLE AND I HAVE NOTICED MANY BUGS!

I DO NOT recommend getting vlc this way:

System > Administration > Software Sources > Third-Party Software and add:

deb [http://ppa.launchpad.net/c-korn/ubuntu](http://ppa.launchpad.net/c-korn/ubuntu) hardy main

sudo apt-get install vlc

(broken package error might occur. Go to synaptic > top left corner hit edit > fix broken packages > Apply)

---

### Post by Neo_The_User on 2008-09-20
I'm going to bed soon so I'll provide with any info you MIGHT need.

I did these commands into the terminal

sudo apt-get install vlc
sudo apt-get build-dep vlc
sudo apt-get install cvs build-essential subversion git git-core automake1.9 libtool
sudo apt-get install libgcrypt-dev
sudo apt-get install libfaad-dev libtwolame-dev libqt4-dev libjack-dev
sudo apt-get install libxpm-dev libcddb2-dev liblua5.1-0-dev libzvbi-dev libshout-dev

cd to my home directory

git clone git://git.videolan.org/vlc.git

cd vlc

./bootstrap

cd extras/

git clone git://git.videolan.org/x264.git

cd x264

make

sudo make install

cd ..

cd ..

mkdir build

cd build

../configure --prefix=/usr \

a > shows up

Copy and paste this entire thing

--enable-snapshot --enable-debug \
--enable-dbus-control --enable-musicbrainz \
--enable-shared-libvlc --enable-mozilla \
--enable-lirc \
--with-ffmpeg-tree=../extras/ffmpeg \
--enable-x264 --with-x264-tree=../extras/x264 \
--enable-shout --enable-taglib \
--enable-v4l  \
--enable-dvb  \
--enable-realrtsp --disable-xvmc \
--enable-svg   --enable-dvdread \
--enable-dc1394 --enable-dv \
--enable-theora --enable-faad \
--enable-twolame --enable-real \
--enable-flac --enable-tremor \
--enable-skins2 --enable-qt4 \
--enable-ncurses \
--enable-aa --enable-caca \
--enable-esd --disable-portaudio \
--enable-jack --enable-xosd \
--enable-galaktos --enable-goom \
--enable-ggi \
--disable-cddax --disable-vcdx \
--disable-quicktime --enable-lua \
--disable-live555

hit enter and wait (the slash should not be on the last line)

Now type in

make

If you get any errors about speex.c please replace the speex.c file with my speex.c file that I uploaded on pastebin.

[http://pastebin.ca/1229915](http://pastebin.ca/1229915)

If you get an error about the x264.c file, replace it with:

[http://pastebin.ca/1219422](http://pastebin.ca/1219422)

Thank you!

---

### Post by Neo_The_User on 2008-09-20
This is what error I recieved near the end of compiling it using ./compile

ERROR   : ../../../modules/codec/speex.c: 991:  'SPEEX_SET_VBR_MAX_BITRATE' undeclared (first use in this function)
ERROR   : ../../../modules/codec/speex.c: 991:  (Each undeclared identifier is reported only once
ERROR   : ../../../modules/codec/speex.c: 991:  for each function it appears in.)
make: *** [all] Error 2

speex.c file > fixed at [http://pastebin.ca/1229915](http://pastebin.ca/1229915)

x264.c file > fixed at [http://pastebin.ca/1219422](http://pastebin.ca/1219422)

Replace the following files with my pastebin post to successfully make vlc.

---

### Post by dsgallo on 2008-10-03
Hi,

could you solve this issue somehow? I'm having the same issue and can't find how to solve it anywhere...

Thanks,
Diego

---

### Post by prostar on 2008-10-03
This may not be the most helpful answer, but that error usually comes from a missing header file.  You have to find what package "SPEEX_SET_VBR_MAX_BITRATE" comes from, and make sure you have the "xxx-dev" package installed.  You can probably look in the mentioned "./../../modules/codec/speex.c" to see what headers it's looking for.

---

### Post by Neo_The_User on 2008-10-04
> **prostar said:**
> This may not be the most helpful answer, but that error usually comes from a missing header file.  You have to find what package "SPEEX_SET_VBR_MAX_BITRATE" comes from, and make sure you have the "xxx-dev" package installed.  You can probably look in the mentioned "./../../modules/codec/speex.c" to see what headers it's looking for.

Thanks! I'll go check it out! I'm so happy that this subject is on the first page on google when doing a search for vlc 1.0 hardy.

---

### Post by Neo_The_User on 2008-10-04
I uploaded the speex.c file

[http://pastebin.ca/1229915](http://pastebin.ca/1229915)

The only thing I ever programmed / re-programmed that was written in C were Playstation 3 and Playstation portable applications and a few drivers for windows. I'll see what I can do with the C file and figure out a work-around. ...Developers welcome to contribute.

Lines 991 and 473 are the lines it complaining about.

---

### Post by Neo_The_User on 2008-10-04
speex.c file is now fixed. ;)
x264.c is now fixed as well. ;)

replace your speex.c file with this

[http://pastebin.ca/1229915](http://pastebin.ca/1229915)

Scroll all the way down to the box with my fixed code in it and right click > select all > copy

Replace vlc > modules > codec > speex.c with the code you copied. overwrite the speex.c file with the code.

x264.c file fixed. replace the x264.c file with the pastebin code.

[http://pastebin.ca/1219422](http://pastebin.ca/1219422)

If you have any problems or questions, please inform me immediately. Thank you all so much for your support and feedback!

I tested out vlc 1.0.0 on Hardy and it works. Follow this guide carefully and I'm sure you'll be able to as well.

(I feel so proud!!!)

---

### Post by psychok9 on 2009-04-12
Hello neo,
I've tried to compile last git vlc but I get always the same errors (with or without your great guide!).
```
libtool: link: gcc -std=gnu99 -shared  .libs/libavcodec_plugin_la-avcodec.o .libs/libavcodec_plugin_la-video.o .libs/libavcodec_plugin_la-audio.o .libs/libavcodec_plugin_la-deinterlace.o .libs/libavcodec_plugin_la-fourcc.o .libs/libavcodec_plugin_la-chroma.o .libs/libavcodec_plugin_la-encoder.o  -Wl,--whole-archive ../../../compat/.libs/libcompat.a -Wl,--no-whole-archive  -Wl,-rpath -Wl,/home/gianluca/vlc/build/src/.libs -L/usr/local/lib -lavcodec -lavutil ../../../src/.libs/libvlccore.so -L//lib -lhal -ldbus-1 -lrt -lpthread -ldl -lm  -mtune=athlon64   -Wl,-soname -Wl,libavcodec_plugin.so -o .libs/libavcodec_plugin.so
/usr/bin/ld: /usr/local/lib/libavcodec.a(allcodecs.o): relocation R_X86_64_32 against `aasc_decoder' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[6]: *** [libavcodec_plugin.la] Errore 1
make[6]: uscita dalla directory «/home/gianluca/vlc/build/modules/codec/avcodec»
make[5]: *** [all] Errore 2
make[5]: uscita dalla directory «/home/gianluca/vlc/build/modules/codec/avcodec»
make[4]: *** [all-recursive] Errore 1
make[4]: uscita dalla directory «/home/gianluca/vlc/build/modules/codec»
make[3]: *** [all] Errore 2
make[3]: uscita dalla directory «/home/gianluca/vlc/build/modules/codec»
make[2]: *** [all-recursive] Errore 1
make[2]: uscita dalla directory «/home/gianluca/vlc/build/modules»
make[1]: *** [all-recursive] Errore 1
make[1]: uscita dalla directory «/home/gianluca/vlc/build»
make: *** [all] Errore 2

```

I've Jaunty, maybe it's a problem with the Jaunty libavcodec library?
I remember similar problems with Intrepid... I couldn't get never a VLC 1.0 compiled... :(

---

