---
title: "Installation of LDGLite"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by LoneStar++ on 2010-10-17
I am trying to install LDGLite by following the instructions found here

[http://www.ldraw.org/GetStarted-Linux.html](http://www.ldraw.org/GetStarted-Linux.html)

I followed these steps
```

[SIZE=1]user$ cd /tmp
user$ wget http://ldglite.sourceforge.net/ldglitesrc0_9_5.zip
user$ unzip -uoa ldglitesrc0_9_5.zip
user$ cd ldglite
user$ make -f makefile.linux && echo OK
[/SIZE]
```But then I get the following error

```

gcc -g -DUNIX -DUSE_OPENGL -DUSE_L3_PARSER -DUSE_BMP8 -DNEED_MIN_MAX -DUSE_PNG  -DTILE_RENDER_OPTION -DOSMESA_OPTION    -c -o ldliteVR_main.o ldliteVR_main.c
gcc -g -DUNIX -DUSE_OPENGL -DUSE_L3_PARSER -DUSE_BMP8 -DNEED_MIN_MAX -DUSE_PNG  -DTILE_RENDER_OPTION -DOSMESA_OPTION    -c -o platform.o platform.c
platform.c: In function &#8216;platform_comment&#8217;:
platform.c:335: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
gcc -g -DUNIX -DUSE_OPENGL -DUSE_L3_PARSER -DUSE_BMP8 -DNEED_MIN_MAX -DUSE_PNG  -DTILE_RENDER_OPTION -DOSMESA_OPTION    -c -o dirscan.o dirscan.c
dirscan.c: In function &#8216;CheckFile&#8217;:
dirscan.c:354: warning: passing argument 2 of &#8216;strcpy&#8217; makes pointer from integer without a cast
/usr/include/string.h:127: note: expected &#8216;const char * __restrict__&#8217; but argument is of type &#8216;int&#8217;
gcc -g -DUNIX -DUSE_OPENGL -DUSE_L3_PARSER -DUSE_BMP8 -DNEED_MIN_MAX -DUSE_PNG  -DTILE_RENDER_OPTION -DOSMESA_OPTION    -c -o gleps.o gleps.c
gleps.c: In function &#8216;spewSortedFeedback&#8217;:
gleps.c:457: error: label at end of compound statement
gleps.c: In function &#8216;spewWireFrameEPS&#8217;:
gleps.c:506: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 3 has type &#8216;struct FILE *&#8217;
make: *** [gleps.o] Error 1

```I tried googling but I didn't find much useful.

Any help is much appreciated.
Thanks for your help in advance

EDIT: I started using another program, but I'm still interested in finding out whats wrong.

---

