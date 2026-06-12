---
title: "WCStools Installation in Edgy"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by magd1319 on 2007-08-08
Hello All, 

I am just wondering if anyone has successfully installed the WCStools utilities for (amongst other things) dealing with .fits headers from the command line. It can be found at:

[http://tdc-www.harvard.edu/software/wcstools/index.html]("http://tdc-www.harvard.edu/software/wcstools/index.html")

It would be great if anyone can work out how to get it working on Ubuntu Edgy. When I run the "make all" command, i get a huge list of errors: 

> 
magd1319@machine:~/Desktop/wcstools-3.6.8$ make all
cd libwcs; make
make[1]: Entering directory `/home/magd1319/Desktop/wcstools-3.6.8/libwcs'
cc -g   -c -o imsetwcs.o imsetwcs.c
imsetwcs.c:30:19: error: stdio.h: No such file or directory
imsetwcs.c:31:20: error: stdlib.h: No such file or directory
imsetwcs.c:32:18: error: math.h: No such file or directory
imsetwcs.c:33:20: error: string.h: No such file or directory
In file included from wcs.h:34,
                 from imsetwcs.c:35:
fitshead.h:35:23: error: sys/types.h: No such file or directory
In file included from imsetwcs.c:37:
fitsfile.h:400: error: expected ‘)’ before ‘*’ token
fitsfile.h:461: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘doy2tsu’
fitsfile.h:514: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘dt2tsu’
fitsfile.h:642: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘fd2tsu’
fitsfile.h:676: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘jd2tsu’
fitsfile.h:688: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘lt2tsu’
fitsfile.h:765: error: expected ‘)’ before ‘isec’
fitsfile.h:769: error: expected ‘)’ before ‘isec’
fitsfile.h:771: error: expected ‘)’ before ‘isec’
fitsfile.h:773: error: expected ‘)’ before ‘isec’
fitsfile.h:797: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ut2tsu’
In file included from imsetwcs.c:38:
wcscat.h:87: error: expected specifier-qualifier-list before ‘FILE’
wcscat.h:158: error: expected specifier-qualifier-list before ‘FILE’
wcscat.h:1210: error: expected declaration specifiers or ‘...’ before ‘FILE’
imsetwcs.c:88: error: ‘NULL’ undeclared here (not in a function)
imsetwcs.c: In function ‘SetWCSFITS’:
imsetwcs.c:207: warning: incompatible implicit declaration of built-in function ‘strlen’
imsetwcs.c:230: warning: incompatible implicit declaration of built-in function ‘calloc’
imsetwcs.c:236: warning: incompatible implicit declaration of built-in function ‘fprintf’
imsetwcs.c:236: error: ‘stderr’ undeclared (first use in this function)
imsetwcs.c:236: error: (Each undeclared identifier is reported only once
imsetwcs.c:236: error: for each function it appears in.)
imsetwcs.c:308: warning: incompatible implicit declaration of built-in function ‘calloc’
imsetwcs.c:309: warning: incompatible implicit declaration of built-in function ‘fprintf’
imsetwcs.c:430: warning: incompatible implicit declaration of built-in function ‘strncpy’
imsetwcs.c:439: error: ‘struct StarCat’ has no member named ‘nndec’
imsetwcs.c:607: warning: incompatible implicit declaration of built-in function ‘printf’
imsetwcs.c:708: warning: incompatible implicit declaration of built-in function ‘printf’
imsetwcs.c:828: warning: incompatible implicit declaration of built-in function ‘printf’
imsetwcs.c: In function ‘PrintRes’:
imsetwcs.c:923: warning: incompatible implicit declaration of built-in function ‘printf’
imsetwcs.c:953: warning: incompatible implicit declaration of built-in function ‘sqrt’
imsetwcs.c:956: warning: incompatible implicit declaration of built-in function ‘cos’
imsetwcs.c:985: warning: incompatible implicit declaration of built-in function ‘sqrt’
imsetwcs.c: In function ‘setmatch’:
imsetwcs.c:1040: warning: incompatible implicit declaration of built-in function ‘strcpy’
make[1]: *** [imsetwcs.o] Error 1
make[1]: Leaving directory `/home/magd1319/Desktop/wcstools-3.6.8/libwcs'
make: *** [libwcs/libwcs.a] Error 2
magd1319@machine:~/Desktop/wcstools-3.6.8$ 


Can anyone suggest a workaround? Has anyone managed to get this working correctly? I'd rather not have to use iraf if i can avoid it.

Cheers,

Dan

---

### Post by laurad on 2007-09-11
Not sure if you fixed the problem but this is what I did to install wcstools:

Download from [http://tdc-www.harvard.edu/software/wcstools/wcstools-3.7.0.tar.gz](http://tdc-www.harvard.edu/software/wcstools/wcstools-3.7.0.tar.gz)
```
zcat wcstools-3.70.tar.gz | tar xvf -
```
This is assuming you are using tcsh shell:
```
cd wcstools-3.70
setenv CC gcc
setenv CFLAGS "-O2 -pipe -fomit-frame-pointer"

```


```
make
sudo mkdir -p /usr/wcstools/
sudo mv bin /usr/wcstools
```

Then add /usr/wcstools/bin to your PATH in .tcshrc file
```
source .tcshrc
rehash
```

And that should work.  Restart the xterm just to be safe if this doesn't work.
Hope this is helpful!
Laura

---

