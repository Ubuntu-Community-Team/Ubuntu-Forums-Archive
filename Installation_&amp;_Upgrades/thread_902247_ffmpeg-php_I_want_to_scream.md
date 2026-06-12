---
title: "ffmpeg-php: I want to scream"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by abasel on 2008-08-27
I am pulling my hair out. After two days of googling and trying almost all links I can find, I still can't install ffmpeg-php

The following is the closest that I get

[https://wiki.ubuntu.com/ffmpeg]("https://wiki.ubuntu.com/ffmpeg")

or

[http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation]("http://linux.justinhartman.com/FFmpeg,_FFmpeg-PHP,_Lame,_Libogg,_Libvorbis,_FLVtool2,_Mplayer,_Mencoder,_AMR_Installation")

But I always get the following type of error:
```
root@vserver:/usr/local/src/ffmpeg-php-0.5.0# make
/bin/bash /usr/local/src/ffmpeg-php-0.5.0/libtool --mode=compile gcc  -I. -I/usr/local/src/ffmpeg-php-0.5.0 -DPHP_ATOM_INC -I/usr/local/src/ffmpeg-php-0.5.0/include -I/usr/local/src/ffmpeg-php-0.5.0/main -I/usr/local/src/ffmpeg-php-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/ffmpeg  -DHAVE_CONFIG_H  -g -O2 -Wall -fno-strict-aliasing   -c /usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c -o ffmpeg-php.lo
 gcc -I. -I/usr/local/src/ffmpeg-php-0.5.0 -DPHP_ATOM_INC -I/usr/local/src/ffmpeg-php-0.5.0/include -I/usr/local/src/ffmpeg-php-0.5.0/main -I/usr/local/src/ffmpeg-php-0.5.0 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/include/ffmpeg -DHAVE_CONFIG_H -g -O2 -Wall -fno-strict-aliasing -c /usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c  -fPIC -DPIC -o .libs/ffmpeg-php.o
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c:26:22: error: avformat.h: No such file or directory
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c: In function âzm_startup_ffmpegâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c:76: warning: implicit declaration of function âav_register_allâ
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c: In function âzm_info_ffmpegâ:
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c:118: error: âLIBAVFORMAT_IDENTâ undeclared (first use in this function)
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c:118: error: (Each undeclared identifier is reported only once
/usr/local/src/ffmpeg-php-0.5.0/ffmpeg-php.c:118: error: for each function it appears in.)
make: *** [ffmpeg-php.lo] Error 1
```

I really need to get this installed... any ideas
:confused:

---

### Post by abasel on 2008-08-27
I finally got it by the following:

```
wget http://downloads.sourceforge.net/ffmpeg-php/ffmpeg-php-0.5.3.1.tbz2; \
tar -jxvf ffmpeg-php-0.5.3.1.tbz2; \
cd ffmpeg-php-0.5.3.1; \
phpize; \
./configure --prefix=/usr; \
make; \
make install; \
cd ..;
```

---

### Post by forger on 2008-08-27
uh..:lolflag:
> $ apt-cache search ffmpeg.*php
php5-ffmpeg - ffmpeg support for php5

```
sudo apt-get install php5-ffmpeg
```

---

### Post by de0xyrib0se on 2008-08-27
Some die hard fans prefer the do-it-yourself way :)

---

### Post by kendre_paresh on 2009-04-03
> **abasel said:**
> I finally got it by the following:

```
wget http://downloads.sourceforge.net/ffmpeg-php/ffmpeg-php-0.5.3.1.tbz2; \
tar -jxvf ffmpeg-php-0.5.3.1.tbz2; \
cd ffmpeg-php-0.5.3.1; \
phpize; \
./configure --prefix=/usr; \
make; \
make install; \
cd ..;
```


Hi, am also facing the same problem. I have tried the way you have shown ablve, but then too hard luck for me.

I am copying the complete output here, Please have a look and suggest me what i have to do further, i am going crazy, since i am working on this last week, please help.


root@ckumari:~/paresh/ffmpeg-php-0.5.3.1# make
/bin/bash /root/paresh/ffmpeg-php-0.5.3.1/libtool --mode=compile gcc  -I. -I/root/paresh/ffmpeg-php-0.5.3.1 -DPHP_ATOM_INC -I/root/paresh/ffmpeg-php-0.5.3.1/include -I/root/paresh/ffmpeg-php-0.5.3.1/main -I/root/paresh/ffmpeg-php-0.5.3.1 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/local/include/libavcodec/ -I/usr/local/include/libavformat/ -I/usr/local/include/libavutil/ -I/usr/local/include/libswscale/ -I/usr/local/include/libavfilter/ -I/usr/local/include/libavdevice/  -DHAVE_CONFIG_H  -g -O2 -Wall -fno-strict-aliasing   -c /root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c -o ffmpeg_frame.lo 
 gcc -I. -I/root/paresh/ffmpeg-php-0.5.3.1 -DPHP_ATOM_INC -I/root/paresh/ffmpeg-php-0.5.3.1/include -I/root/paresh/ffmpeg-php-0.5.3.1/main -I/root/paresh/ffmpeg-php-0.5.3.1 -I/usr/include/php5 -I/usr/include/php5/main -I/usr/include/php5/TSRM -I/usr/include/php5/Zend -I/usr/include/php5/ext -I/usr/include/php5/ext/date/lib -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -I/usr/local/include/libavcodec/ -I/usr/local/include/libavformat/ -I/usr/local/include/libavutil/ -I/usr/local/include/libswscale/ -I/usr/local/include/libavfilter/ -I/usr/local/include/libavdevice/ -DHAVE_CONFIG_H -g -O2 -Wall -fno-strict-aliasing -c /root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c  -fPIC -DPIC -o .libs/ffmpeg_frame.o
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c: In function ‘_php_convert_frame’:
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:202: warning: implicit declaration of function ‘img_convert’
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c: In function ‘_php_crop_frame’:
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:260: warning: implicit declaration of function ‘img_copy’
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c: In function ‘_php_resample_frame’:
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:282: error: ‘ImgReSampleContext’ undeclared (first use in this function)
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:282: error: (Each undeclared identifier is reported only once
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:282: error: for each function it appears in.)
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:282: error: ‘img_resample_ctx’ undeclared (first use in this function)
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:308: warning: implicit declaration of function ‘img_resample_full_init’
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:321: warning: implicit declaration of function ‘img_resample’
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:326: warning: implicit declaration of function ‘img_resample_close’
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c: In function ‘zif_toGDImage’:
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:448: error: ‘PIX_FMT_RGBA32’ undeclared (first use in this function)
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c: In function ‘zif_ffmpeg_frame’:
/root/paresh/ffmpeg-php-0.5.3.1/ffmpeg_frame.c:533: error: ‘PIX_FMT_RGBA32’ undeclared (first use in this function)
make: *** [ffmpeg_frame.lo] Error 1
root@ckumari:~/paresh/ffmpeg-php-0.5.3.1#

---

### Post by thewolfman on 2009-04-03
Hi,

open synaptic and go to search then type "php5-ffmpeg" then mark and apply and download >> then you are done; simple.

Have a good one

---

### Post by kendre_paresh on 2009-04-03
> **thewolfman said:**
> Hi,

open synaptic and go to search then type "php5-ffmpeg" then mark and apply and download >> then you are done; simple.

Have a good one

I have tried both, I have installed it from Synaptic and from command line as well. In Synaptic i get that php5-ffmpeg is unstalled.

But when i go to upload any video am getting error 

Fatal error: Class 'ffmpeg_movie' not found in /var/www/.....


Any idea, pleaseeeeeee :(

---

### Post by Arvand on 2009-04-06
I got to this using Google. We had this issue on CentOS but its the same error so I'm pretty sure it will solve your issues as well --

With the latest version of ffmpeg-php (0.6.0), update ffmpeg_frame.c and replace every instance of PIX_FMT_RGBA32 with PIX_FMT_RGB32

then it compiled fine.

For those who don't know how to do this -

vi ffmpeg_frame.c
:%s/PIX_FMT_RGBA32/PIX_FMT_RGB32
:w
:q!
./configure
make
make install

add extension="ffmpeg.so" inside php.ini .

---

### Post by Bentis on 2009-04-08
> **Arvand said:**
> With the latest version of ffmpeg-php (0.6.0), update ffmpeg_frame.c and replace every instance of PIX_FMT_RGBA32 with PIX_FMT_RGB32

then it compiled fine.

Thank you! had the same problem and this fixed it :)

---

### Post by StarkHalo on 2009-08-12
> **arvand said:**
> i got to this using google. We had this issue on centos but its the same error so i'm pretty sure it will solve your issues as well --

with the latest version of ffmpeg-php (0.6.0), update ffmpeg_frame.c and replace every instance of pix_fmt_rgba32 with pix_fmt_rgb32

then it compiled fine.

For those who don't know how to do this -

vi ffmpeg_frame.c
:%s/pix_fmt_rgba32/pix_fmt_rgb32
:w
:q!
./configure
make
make install

add extension="ffmpeg.so" inside php.ini .

:ks:ks i love you!!!!!!!! Really!!! :ks:ks

---

