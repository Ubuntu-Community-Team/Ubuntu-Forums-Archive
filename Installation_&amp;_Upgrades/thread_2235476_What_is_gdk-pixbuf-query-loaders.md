---
title: "What is gdk-pixbuf-query-loaders?"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by Mariane on 2014-07-21
Hi, 

I attempted an upgrade from precise to saucy, by adding urls to sources.list and doing update/upgrade/dist-upgrade.

To sources.list I added:
```

deb http://us.archive.ubuntu.com/ubuntu/ saucy main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ saucy-updates main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu/ saucy-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu saucy-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu saucy partner
deb http://extras.ubuntu.com/ubuntu saucy main

```

I got a strange error message, telling me the system was broken and that I should type:

```

sudo gdk-pixbuf-query-loaders > /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders.cache

```

I typed it. It returned. Then I did update/upgrade again. Upgrade told me several packages had not installed properly, and apparently it installed them. I did update/upgrade again and this time it told me everything was up-to-date. 

Then I typed "startx" and it worked. It had previously failed and I was stuck with the terminal. But now I don't dare reboot the computer... 

The output of "gdk-pixbuf-query-loaders" is:

```

# GdkPixbuf Image Loader Modules file
# Automatically generated file, do not edit
# Created by gdk-pixbuf-query-loaders from gdk-pixbuf-2.28.1
#
# LoaderDir = /usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders
#
"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ani.so"
"ani" 4 "gdk-pixbuf" "The ANI image format" "LGPL"
"application/x-navi-animation" ""
"ani" ""
"RIFF    ACON" "    xxxx    " 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ico.so"
"ico" 5 "gdk-pixbuf" "The ICO image format" "LGPL"
"image/x-icon" "image/x-ico" "image/x-win-bitmap" ""
"ico" "cur" ""
"  \001   " "zz znz" 100
"  \002   " "zz znz" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xpm.so"
"xpm" 4 "gdk-pixbuf" "The XPM image format" "LGPL"
"image/x-xpixmap" ""
"xpm" ""
"/* XPM */" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-png.so"
"png" 5 "gdk-pixbuf" "The PNG image format" "LGPL"
"image/png" ""
"png" ""
"\211PNG\r\n\032\n" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tga.so"
"tga" 4 "gdk-pixbuf" "The Targa image format" "LGPL"
"image/x-tga" ""
"tga" "targa" ""
" \001\001" "x  " 100
" \001\t" "x  " 100
"  \002" "xz " 99
"  \003" "xz " 100
"  \n" "xz " 100
"  \v" "xz " 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-gif.so"
"gif" 4 "gdk-pixbuf" "The GIF image format" "LGPL"
"image/gif" ""
"gif" ""
"GIF8" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-wbmp.so"
"wbmp" 4 "gdk-pixbuf" "The WBMP image format" "LGPL"
"image/vnd.wap.wbmp" ""
"wbmp" ""
"  " "zz" 1
" `" "z " 1
" @" "z " 1
"  " "z " 1

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jpeg.so"
"jpeg" 5 "gdk-pixbuf" "The JPEG image format" "LGPL"
"image/jpeg" ""
"jpeg" "jpe" "jpg" ""
"\377\330" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-pcx.so"
"pcx" 4 "gdk-pixbuf" "The PCX image format" "LGPL"
"image/x-pcx" ""
"pcx" ""
"\n \001" "" 100
"\n\002\001" "" 100
"\n\003\001" "" 100
"\n\004\001" "" 100
"\n\005\001" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-jasper.so"
"jpeg2000" 4 "gdk-pixbuf" "The JPEG 2000 image format" "LGPL"
"image/jp2" "image/jpeg2000" "image/jpx" ""
"jp2" "jpc" "jpx" "j2k" "jpf" ""
"    jP" "!!!!  " 100
"\377O\377Q" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-tiff.so"
"tiff" 5 "gdk-pixbuf" "The TIFF image format" "LGPL"
"image/tiff" ""
"tiff" "tif" ""
"MM *" "  z " 100
"II* " "   z" 100
"II* \020   CR\002 " "   z zzz   z" 0

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-qtif.so"
"qtif" 4 "gdk-pixbuf" "The QTIF image format" "LGPL"
"image/x-quicktime" "image/qtif" ""
"qtif" "qif" ""
"abcdidsc" "xxxx    " 100
"abcdidat" "xxxx    " 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-xbm.so"
"xbm" 4 "gdk-pixbuf" "The XBM image format" "LGPL"
"image/x-xbitmap" ""
"xbm" ""
"#define " "" 100
"/*" "" 50

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-ras.so"
"ras" 4 "gdk-pixbuf" "The Sun raster image format" "LGPL"
"image/x-cmu-raster" "image/x-sun-raster" ""
"ras" ""
"Y\246j\225" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-pnm.so"
"pnm" 4 "gdk-pixbuf" "The PNM/PBM/PGM/PPM image format family" "LGPL"
"image/x-portable-anymap" "image/x-portable-bitmap" "image/x-portable-graymap" "image/x-portable-pixmap" ""
"pnm" "pbm" "pgm" "ppm" ""
"P1" "" 100
"P2" "" 100
"P3" "" 100
"P4" "" 100
"P5" "" 100
"P6" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-bmp.so"
"bmp" 5 "gdk-pixbuf" "The BMP image format" "LGPL"
"image/bmp" "image/x-bmp" "image/x-MS-bmp" ""
"bmp" ""
"BM" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-icns.so"
"icns" 4 "gdk-pixbuf" "The ICNS image format" "GPL"
"image/x-icns" ""
"icns" ""
"icns" "" 100

"/usr/lib/i386-linux-gnu/gdk-pixbuf-2.0/2.10.0/loaders/libpixbufloader-svg.so"
"svg" 2 "gdk-pixbuf" "Scalable Vector Graphics" "LGPL"
"image/svg+xml" "image/svg" "image/svg-xml" "image/vnd.adobe.svg+xml" "text/xml-svg" "image/svg+xml-compressed" ""
"svg" "svgz" "svg.gz" ""
" <svg" "*    " 100
" <!DOCTYPE svg" "*             " 100

```

What on Earth is all that and why is it so important???

---

### Post by Mariane on 2014-07-21
Tip for anyone with the same problem:

I remembered that, once upon a time, after updating the distribution a menu was automatically displayed on startup. It offered the choice between the most recent version and previous ones. So, when such upgrades failed, it was possible to boot the previous version. The program offering this choice is called grub:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

At first, this page talks about creating a grub thingy on a separate disk (usb, CD, partition...). It offers the very encouraging comment: "Installing a boot loader on a running OS may be extremely dangerous."

But, reading further, there seemed to be a very simple way to do it: 

```

cd /etc/default
sudo nano grub

```

Nano is the command-line file editing system. You scroll through the file using the arrow keys. Control-O saves the file, Control-X gets you out. 
In this file, there is a line:

```

GRUB_DEFAULT=0

```

Which should be changed to:

```

GRUB_DEFAULT=30

```

(Or another number, this number is the number of seconds you have to make your choice.) 

Then, you run:

```

sudo update-grub
sudo grub-mkconfig
sudo update-grub

```

I'm not sure you really have to run both, or to run update-grub twice, but better safe than sorry. Update-grub gives (for me): 

```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-26-generic
Found initrd image: /boot/initrd.img-3.11.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-67-generic
Found initrd image: /boot/initrd.img-3.2.0-67-generic
Found linux image: /boot/vmlinuz-3.0.0-32-generic
Found initrd image: /boot/initrd.img-3.0.0-32-generic
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

So, hopefully, next time I reboot, if the upgraded system fails, I will be able to boot one of the ancient versions.

---

