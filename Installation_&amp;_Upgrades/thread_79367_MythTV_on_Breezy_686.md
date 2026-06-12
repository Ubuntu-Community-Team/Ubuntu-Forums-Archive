---
title: "MythTV on Breezy 686"
date: 2005-10-20
forum: Installation &amp; Upgrades
---

### Post by andrewsawyer on 2005-10-20
Hiya,

Am I missing something, or is there no MythTV available via apt-get?  I'm on Breezy, using the 686 kernel.  I have all the sources in the sources.list available with the exception of the backports as they aren't up yet anyway.

Can someone please tell me what the easiest way is to get MythTV installed on Breezy is?  I've currently got it installed as a server install, however I have also downloaded lynx for if I need to get anything off the net.

Many thanks,

Andy

---

### Post by andrewsawyer on 2005-10-20
Update:

I have downloaded the source from mythtv.org.  I stuck it in my /home directory and extracted out the tarball.

I then downloaded the build-essentials and qt3-dev-tools.

I typed:
```
qmake mythtv.pro
```
There was no error message (or any message at all), and it just went back to the prompt.  I then typed:
```
sudo make
```
and got the following:
```

andrew@mediacentre:~/mythtv-0.18.1$ sudo make
cd libs && make -f Makefile
make[1]: Entering directory `/home/andrew/mythtv-0.18.1/libs'
cd libavcodec && make -f Makefile
make[2]: Entering directory `/home/andrew/mythtv-0.18.1/libs/libavcodec'
gcc -c -pipe -march=pentium4 -w -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr/local\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/usr/share/qt3/include -o utils.o utils.c
In file included from avcodec.h:14,
                 from utils.c:27:
common.h:61: error: array type has incomplete element type
common.h:65: error: array type has incomplete element type
make[2]: *** [utils.o] Error 1
make[2]: Leaving directory `/home/andrew/mythtv-0.18.1/libs/libavcodec'
make[1]: *** [sub-libavcodec] Error 2
make[1]: Leaving directory `/home/andrew/mythtv-0.18.1/libs'
make: *** [sub-libs] Error 2
andrew@mediacentre:~/mythtv-0.18.1$
```

Would anyone be able to tell me what went wrong?  Am I missing a program/install/dependency?

Any help would be much appreciated.

---

### Post by Stealth on 2005-10-20
Don't you have to ./configure first?

---

### Post by andrewsawyer on 2005-10-20
Sorry - I forgot to put that.  Yes you do, and yes I did.

Thank you though.

---

### Post by SickTwist on 2005-10-20
So did it work after you ran configure?

---

### Post by oblib on 2005-10-21
You might want to try rolling back your gcc version. It's helped me with other problems:
```

sudo apt-get install gcc-3.4
CC=gcc-3.4
export CC

```
Then you have to run the configure script again.

Maybe it will help, let us know.

---

### Post by andrewsawyer on 2005-10-21
Well, I thought all was going ok, but unfortunately I am still getting an error.  I've not posted below the entire thing - sorry it's too long to fit, however the bit that I've cut out is well labelled and is from within the 'make' section:

```
andrew@mediacentre:~$ sudo apt-get install gcc-3.4
Password:
Reading package lists... Done
Building dependency tree... Done
gcc-3.4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
andrew@mediacentre:~$ CC=gcc-3.4
andrew@mediacentre:~$ export CC
andrew@mediacentre:~$ ls
dead.letter  mythtv-0.18.1  mythtv-0.18.1.tar.bz2
andrew@mediacentre:~$ cd mythtv-0.18.1
andrew@mediacentre:~/mythtv-0.18.1$ ./configure
cat: /etc/ld.so.conf: No such file or directory
cat: /etc/ld.so.conf: No such file or directory
cat: /etc/ld.so.conf: No such file or directory
cat: /etc/ld.so.conf: No such file or directory
cat: /etc/ld.so.conf: No such file or directory
cat: /etc/ld.so.conf: No such file or directory
# Basic Settings
Compile type     release
Compiler cache   no
DistCC           no
Install prefix   /usr/local
CPU              x86 (model name        : Intel(R) Celeron(R) CPU 2.40GHz)
Big Endian       no
MMX enabled      yes
Vector Builtins  no

# Input Support
Joystick menu    yes
lirc support     no
ivtv support     yes
FireWire support no
DVB support      no [/usr/src/linux-2.6.12-9-686/include]

# Sound Output Support
OSS support      yes
ALSA support     no
aRts support     no
JACK support     no

# Video Output Support
x11 support      no
xrandr support   no
xv support       no
XvMC support     no
XvMC VLD support no
OpenGL vsync     no
DirectFB         no

Creating config.mak and config.h
config.h is unchanged
andrew@mediacentre:~/mythtv-0.18.1$ qmake mythtv.pro
andrew@mediacentre:~/mythtv-0.18.1$ sudo make
cd libs && make -f Makefile
make[1]: Entering directory `/home/andrew/mythtv-0.18.1/libs'
cd libavcodec && make -f Makefile
make[2]: Entering directory `/home/andrew/mythtv-0.18.1/libs/libavcodec'
qmake -o Makefile libavcodec.pro
make[2]: Leaving directory `/home/andrew/mythtv-0.18.1/libs/libavcodec'
make[2]: Entering directory `/home/andrew/mythtv-0.18.1/libs/libavcodec'
gcc-3.4 -c -pipe -march=pentium4 -w -O3 -Wall -Wno-switch -fomit-frame-pointer - D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_ BITS=64 -DPREFIX=\"/usr/local\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_D EBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/us r/share/qt3/include -o utils.o utils.c
gcc-3.4 -c -pipe -march=pentium4 -w -O3 -Wall -Wno-switch -fomit-frame-pointer - D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_ BITS=64 -DPREFIX=\"/usr/local\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_D EBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/us r/share/qt3/include -o mem.o mem.c
gcc-3.4 -c -pipe -march=pentium4 -w -O3 -Wall -Wno-switch -fomit-frame-pointer - D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_ BITS=64 -DPREFIX=\"/usr/local\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_D EBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/us r/share/qt3/include -o allcodecs.o allcodecs.c
gcc-3.4 -c -pipe -march=pentium4 -w -O3 -Wall -Wno-switch -fomit-frame-pointer - D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_ BITS=64 -DPREFIX=\"/usr/local\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_D EBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/us r/share/qt3/include -o mpegvideo.o mpegvideo.c


...CUT SECTION...


gcc-3.4 -c -pipe -march=pentium4 -w -O3 -Wall -Wno-switch -fomit-frame-pointer -D_REENTRANT -DPIC -fPIC  -DMMX -Di386 -DUSING_IVTV -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -DPREFIX=\"/usr/local\" -DHAVE_AV_CONFIG_H -D_LARGEFILE_SOURCE -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I.. -I../.. -I/usr/share/qt3/include -o vp3dsp_sse2.o i386/vp3dsp_sse2.c
rm -f libmythavcodec-0.18.1.so.0.18.1 libmythavcodec-0.18.1.so libmythavcodec-0.18.1.so.0 libmythavcodec-0.18.1.so.0.18
g++ -shared -Wl,-soname,libmythavcodec-0.18.1.so.0 -o libmythavcodec-0.18.1.so.0.18.1 utils.o mem.o allcodecs.o mpegvideo.o h263.o jrevdct.o jfdctfst.o mpegaudio.o ac3enc.o mjpeg.o audresample.o dsputil.o motion_est.o imgconvert.o imgresample.o msmpeg4.o mpeg12.o h263dec.o svq1.o rv10.o mpegaudiodec.o pcm.o simple_idct.o ratecontrol.o adpcm.o eval.o jfdctint.o dv.o error_resilience.o wmadec.o fft.o mdct.o mace.o huffyuv.o opts.o cyuv.o golomb.o h264.o raw.o indeo3.o asv1.o vp3.o 4xm.o cabac.o ra144.o ra288.o vcr1.o cljr.o roqvideo.o dpcm.o tscc.o interplayvideo.o xan.o rpza.o cinepak.o msrle.o msvideo1.o vqavideo.o idcinvideo.o adx.o rational.o faandct.o snow.o sonic.o 8bps.o parser.o smc.o flicvideo.o truemotion1.o vmdav.o lcl.o qtrle.o g726.o flac.o vp3dsp.o integer.o h261.o resample2.o h264idct.o png.o pnm.o qdrw.o qpeg.o rangecoder.o ulti.o xl.o bitstream.o vc9.o postprocess.o a52dec.o bit_allocate.o a52_bitstream.o downmix.o imdct.o parse.o crc.o resample.o fdct_mmx.o cputest.o dsputil_mmx.o mpegvideo_mmx.o idct_mmx.o motion_est_mmx.o simple_idct_mmx.o fft_sse.o vp3dsp_mmx.o vp3dsp_sse2.o   -L/usr/share/qt3/lib -L/usr/X11R6/lib -lqt-mt -lXext -lX11 -lm -lpthread
/usr/bin/ld: cannot find -lqt-mt
collect2: ld returned 1 exit status
make[2]: *** [libmythavcodec-0.18.1.so.0.18.1] Error 1
make[2]: Leaving directory `/home/andrew/mythtv-0.18.1/libs/libavcodec'
make[1]: *** [sub-libavcodec] Error 2
make[1]: Leaving directory `/home/andrew/mythtv-0.18.1/libs'
make: *** [sub-libs] Error 2
```

FYI: My graphics card and sound card are built into the motherboard (I'm outputting to a widescreen tft TV with vga input).  I also don't have a capture card installed - not sure if I will or not at a later date, however my reason for MythTV was to have an easy to use front end for my existing music/movies/tv series/holiday snaps.

Any help would be appreciated.

---

### Post by MySchizoBuddy on 2005-10-21
why don't u try this

# MythTV
deb [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) unstable mythtv
deb-src [http://dijkstra.csh.rit.edu/~mdz/debian](http://dijkstra.csh.rit.edu/~mdz/debian) unstable mythtv

then, from the command line run the following commands:

apt-get update
apt-get build-dep mythtv
apt-get source -b mythtv

---

### Post by pelago on 2005-10-21
MythTV's already in the breezy repositories (universe, I think). I've heard there are problems with AMD64, but 686 should be ok (I'm on 686).

---

### Post by MySchizoBuddy on 2005-10-24
when u install MythTv it also install Mysql. anyone knows the default password of root to create database in mysql

---

### Post by pelago on 2005-10-24
[QUOTE=MySchizoBuddy]when u install MythTv it also install Mysql. anyone knows the default password of root to create database in mysql[/QUOTE]
The default password is blank.

---

### Post by Az7 on 2005-11-04
You might try this site 
[http://www.abarbaccia.com/](http://www.abarbaccia.com/)

---

### Post by adrianhensler on 2005-11-04
Just as a heads up; I've been running mythtv on a pretty much stock Kubuntu 5.10 with very few issues. I used the mythtv available in the standard sources list.

The hardest part was getting the bt878 ATI TV-Wonder working (it still won't record audio on a few channels for some ungoldy reason; but I can watch them fine which makes no sense at all to me; haven't had time to troubleshoot that one.)

I was taking some notes as I went and was planning on making a nice document or post about it; but I ended up getting so excited at the actual progress I was making; that I neglected to continue taking notes. I had fully anticipated that this first attempt would fail with me hosing the installation and starting over; but it worked so well that I left it. I'll attach my sparse notes on the off chance someone finds something useful.

These notes are really messy and not intented for anything other than amusement really. Note that I never did get the audio out working properly on my Abit IC7-G (lots of audio hiss; like it's got too much gain or something goofy) and I gave up on the remote although I am certain I could use xmodmap to do what I want. The keyboard is fine; and people ask about it; giving me a chance to show off my setup. I also gave up on the mythweb; but I should give that another attempt...

> [http://ubuntuforums.org/archive/index.php/t-8387.html](http://ubuntuforums.org/archive/index.php/t-8387.html)

did this:
sudo /usr/bin/mysqladmin -u root password your_db_user_password

really did this:
[http://wilsonet.com/mythtv/fcmyth.php#mysql](http://wilsonet.com/mythtv/fcmyth.php#mysql)
# mysql -u root mysql
mysql> UPDATE user SET Password=PASSWORD('ROOT_PWD') WHERE user='root';
mysql> FLUSH PRIVILEGES;
mysql> quit

[http://wilsonet.com/mythtv/fcmyth.php#mysql](http://wilsonet.com/mythtv/fcmyth.php#mysql)
tried to add the database; didn't work? (Does it already exist?) (YES!)


Back to real docs at: [http://www.mythtv.org/docs/mythtv-HOWTO-6.html](http://www.mythtv.org/docs/mythtv-HOWTO-6.html)

If you create a /var/video subdirectory, change /mnt/store/ to /var/video/ in the setup screens.

    $ su
    # mkdir /var/video
    # chmod a+rwx /var/video
    # exit

also tried to install:
libqt3-mt-mysql is already the newest version.


NOTE: The last slash "/" is not required.

ah: from here: [http://www.pvrguide.no-ip.com/bbs/lofiversion/index.php?t4853.html](http://www.pvrguide.no-ip.com/bbs/lofiversion/index.php?t4853.html)
# mysql -u root mysql
mysql> UPDATE user SET Password=PASSWORD('mythtv') WHERE user='mythtv';
mysql> FLUSH PRIVILEGES;
mysql> quit

except I had to do this from: [http://diy.prettymad.net/index.php/How_to_Build_a_MythTV_Box_-_Revised/New/20050918](http://diy.prettymad.net/index.php/How_to_Build_a_MythTV_Box_-_Revised/New/20050918) (has lots of good stuff; how to make it autologin as the correct user)
: $ su -
$ mysql
$ mysql> GRANT ALL PRIVILEGES ON *.* TO 'mythtv'@'localhost'
   ->     IDENTIFIED BY 'mythtv' WITH GRANT OPTION;

I could then start mythtv-setup (as non-root). cleared all databases.

Now I have to configure the card (I've gone through the general setup)
Card is ATI Wonder and remote wonder. Lircd is already setup and running (don't know if it is working).

OKay; video card setup (as far as I can tell) in mythtv. now onto data sources
DataDirect? wtf.
Followed these directions: [http://www.mythtv.info/moin.cgi/DataDirectHowTo](http://www.mythtv.info/moin.cgi/DataDirectHowTo)
registered using that code; entered data into mythtv
gah; still access denied for mythtv user; I think it's the pasword?

Okay; just blew 20 minutes playing with it. not sure if the audio is working or not; just playing with video.
Weather works; videos play; I can switch inputs. No DVD yet. Music looks like it should work; ripping audio etc.

I want the directory update to work though... user not authenticated. ok.. so why does mythfilldatabase work? I think I am seeing some old directions. The schedule is not populated; but the program database has stuff in the right places?

Ok; tomorrow: verify audio. Try getting DVD to work. Put some programs in there to play; or test-play. Fix schedule. Neat!

Day2 :
In a hurry to see mythweb:
went here: [http://www.mythtv.org/docs/mythtv-HOWTO-13.html](http://www.mythtv.org/docs/mythtv-HOWTO-13.html)
Did:
# cd /var/www
# htpasswd -c htpasswd mythtv
New password:
Re-type new password:
Adding password for user mythtv
Argh; it's broken; when I access [http://192.168.1.12/mythweb/](http://192.168.1.12/mythweb/) I get:
Fatal error: Call to undefined function: mysql_connect() in /usr/share/mythtv/mythweb/includes/init.php on line 54

And the remote is not working; doing two keypresses for each of mine... ugh. But it does work...
maybe this: [http://mythtv.org/pipermail/mythtv-users/2005-February/076556.html](http://mythtv.org/pipermail/mythtv-users/2005-February/076556.html)
will fix it:
 however it is also feasible to just
rename the ati_remote.ko file to something else.  I do this such that
I can use Axel's packages...


ehhh remote still not working; I'll have to use xmodmap I think.

Still fighting audio out on optical:
[http://forums.gentoo.org/viewtopic.php?t=277801&highlight=alsa](http://forums.gentoo.org/viewtopic.php?t=277801&highlight=alsa)

grr - it's painful.... so far anyways; it's been a big mystery where to find settings and how to change them.



I'd be happy to try to answer any questions regarding getting bt878 cards working; getting audio working; or basic setup questions. There is a lot of stuff that didn't make it into my notes that might still be in my head.

---

