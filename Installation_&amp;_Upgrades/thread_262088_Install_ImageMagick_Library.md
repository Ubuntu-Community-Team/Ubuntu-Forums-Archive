---
title: "Install ImageMagick Library"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by Firestar on 2006-09-21
Hi Everyone,

Sorry for all the threads (and mods, feel free to merge them if you think it's better that way).

I'm trying to install ImageMagick on my ubuntu server running the 6.06 AMD64 server edition.

However, after trying to install it with apt-get and aptitude (apt-get/aptitude install imagemagick) and that not working, I tried to install it by compiling the source with ./configure, make and then make install. However, during the make install command, I get the following:

```
make  install-am
make[1]: Entering directory `/home/firestar/ImageMagick v6/ImageMagick-6.2.3'
depbase=`echo wand/drawing-wand.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/drawing-wand.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/drawing-wand.lo wand/drawing-wand.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
depbase=`echo wand/magick-attribute.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/magick-attribute.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/magick-attribute.lo wand/magick-attribute.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
depbase=`echo wand/magick-image.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/magick-image.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/magick-image.lo wand/magick-image.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
depbase=`echo wand/magick-wand.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/magick-wand.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/magick-wand.lo wand/magick-wand.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
depbase=`echo wand/pixel-iterator.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/pixel-iterator.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/pixel-iterator.lo wand/pixel-iterator.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
depbase=`echo wand/pixel-wand.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/pixel-wand.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/pixel-wand.lo wand/pixel-wand.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
depbase=`echo wand/wand.lo | sed 's|[^/]*$|.deps/&|;s|\.lo$||'`; \
        if /bin/sh ./libtool --silent --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I./magick  -I. -I. -I./Magick++/lib -I/usr/include/freetype2  -g -O2 -Wall -pthread -MT wand/wand.lo -MD -MP -MF "$depbase.Tpo" -c -o wand/wand.lo wand/wand.c; \
        then mv -f "$depbase.Tpo" "$depbase.Plo"; else rm -f "$depbase.Tpo"; exit 1; fi
/bin/sh ./libtool --silent --tag=CC --mode=link gcc  -g -O2 -Wall -pthread  -lfreetype -lz -o wand/libWand.la -rpath /usr/local/lib -no-undefined -version-info 8:3:2 wand/drawing-wand.lo wand/magick-attribute.lo wand/magick-image.lo wand/magick-wand.lo wand/pixel-iterator.lo wand/pixel-wand.lo wand/wand.lo magick/libMagick.la -lm 
libtool: link: warning: `/usr/lib64/libjpeg.la' seems to be moved
./libtool: line 3131: cd: v6/ImageMagick-6.2.3/ltdl: No such file or directory
libtool: link: warning: cannot determine absolute directory name of `v6/ImageMagick-6.2.3/ltdl'
grep: v6/ImageMagick-6.2.3/ltdl/libltdl.la: No such file or directory
/bin/sed: can't read v6/ImageMagick-6.2.3/ltdl/libltdl.la: No such file or directory
libtool: link: `v6/ImageMagick-6.2.3/ltdl/libltdl.la' is not a valid libtool archive
make[1]: *** [wand/libWand.la] Error 1
make[1]: Leaving directory `/home/firestar/ImageMagick v6/ImageMagick-6.2.3'
make: *** [install] Error 2
```

I have no idea what this means, or how to fix it. If somone could please help me, I'd much appreciate it.

I need ImageMagick for a new e-commerce shop that I'm setting up and I need to get this library installed to get the product images properly resized.

Thanks again for all your help and patience with me. Once again, I'm a complete linux noob, so please be gentle.

Thanks
Firestar

---

### Post by LotsOfPhil on 2006-09-21
Are you running apt-get with sudo? Same with the compiling?

---

### Post by Firestar on 2006-09-21
Well, no. Reason being I have activated the root user and am using that. but I have even su - when logged in as root, so it should just work, not?

Otherwise, I can try again...

---

### Post by Firestar on 2006-09-21
Ok, just tested with sudo and it's also not working. Giving the same errors.

---

### Post by geoffree on 2007-03-30
I too want to use Image Magick and am having problems.  I went to their site and got some answers that involved compiling source code.  But it should be easier.  I used the Synaptic Package snatcher and it indicates that I do have I.M. installed. When I use the test to produce the logo, it works.  But how to launch the app? And then, how to apply an icon?

If anyone will answer I will be very grateful.  Especially if they can provide a solution.

Geoffrey

[email]zeno@empire.net[/email]

---

