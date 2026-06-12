---
title: "problems compiling from source"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by yiddski on 2008-03-08
i am trying to compile cinelerra. ive extracted the source code, but when i try to make i get this

```
yid@yid-desktop:~/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: Syntax error: end of file unexpected (expecting "then")
make[1]: Entering directory `/home/yid/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
soundtest.c:13:27: error: sys/soundcard.h: No such file or directory
soundtest.c:14:19: error: stdio.h: No such file or directory
soundtest.c:15:20: error: stdlib.h: No such file or directory
soundtest.c:16:20: error: unistd.h: No such file or directory
soundtest.c:17:19: error: fcntl.h: No such file or directory
soundtest.c:18:23: error: sys/ioctl.h: No such file or directory
soundtest.c:19:18: error: math.h: No such file or directory
soundtest.c: In function ‘main’:
soundtest.c:24: error: ‘audio_buf_info’ undeclared (first use in this function)
soundtest.c:24: error: (Each undeclared identifier is reported only once
soundtest.c:24: error: for each function it appears in.)
soundtest.c:24: error: expected ‘;’ before ‘playinfo’
soundtest.c:28: error: ‘AFMT_S16_LE’ undeclared (first use in this function)
soundtest.c:40: warning: incompatible implicit declaration of built-in function ‘log’
soundtest.c:94: warning: incompatible implicit declaration of built-in function ‘printf’
soundtest.c:96: error: ‘O_WRONLY’ undeclared (first use in this function)
soundtest.c:102: error: ‘SNDCTL_DSP_SETFRAGMENT’ undeclared (first use in this function)
soundtest.c:105: error: ‘SNDCTL_DSP_SETDUPLEX’ undeclared (first use in this function)
soundtest.c:110: error: ‘SNDCTL_DSP_SETFMT’ undeclared (first use in this function)
soundtest.c:112: error: ‘SNDCTL_DSP_CHANNELS’ undeclared (first use in this function)
soundtest.c:114: error: ‘SNDCTL_DSP_SPEED’ undeclared (first use in this function)
soundtest.c:117: error: ‘SNDCTL_DSP_GETOSPACE’ undeclared (first use in this function)
soundtest.c:117: error: ‘playinfo’ undeclared (first use in this function)
soundtest.c:126: error: ‘O_RDONLY’ undeclared (first use in this function)
soundtest.c:157: error: ‘SNDCTL_DSP_GETISPACE’ undeclared (first use in this function)
soundtest.c:157: error: ‘recinfo’ undeclared (first use in this function)
soundtest.c:162: error: ‘SNDCTL_DSP_RESET’ undeclared (first use in this function)
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/yid/cinelerra-2.1'
make: *** [all] Error 2

```

---

### Post by jeffus_il on 2008-03-08
You are missing the c development environment, libraries etc. probably the libc6-dev package, there may be other stuff missing as well...

---

### Post by yiddski on 2008-03-08
> **jeffus_il said:**
> You are missing the c development environment, libraries etc. probably the libc6-dev package, there may be other stuff missing as well...

touche. installed the ibc6-dev package

now i get a different, smaller error

```
yid@yid-desktop:~/cinelerra-2.1$ make
make -f build/Makefile.cinelerra
sh: Syntax error: end of file unexpected (expecting "then")
make[1]: Entering directory `/home/yid/cinelerra-2.1'
gcc -c -O2 -fomit-frame-pointer -falign-loops=2 -falign-jumps=2 -falign-functions=2 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -I../../freetype-2.1.4/include -I../../ -DHAVE_OSS -DHAVE_FIREWIRE  soundtest.c -o i686/soundtest.o
Assembler messages:
Fatal error: can't create i686/soundtest.o: No such file or directory
make[1]: *** [i686/soundtest.o] Error 1
make[1]: Leaving directory `/home/yid/cinelerra-2.1'
make: *** [all] Error 2
yid@yid-desktop:~/cinelerra-2.1$ 


```

---

### Post by jeffus_il on 2008-03-08
Are you following instructions to build cinelerra?
Do you have to run .configure first?

---

### Post by yiddski on 2008-03-08
> **jeffus_il said:**
> Are you following instructions to build cinelerra?
Do you have to run .configure first?

i was. it told me to use the make command. thats how i got here. apparently i dont have the right stuff. i dont remember having to use configure

---

### Post by markekeller on 2008-03-08
yiddski, try this manual:

[http://cv.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html](http://cv.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html)

Near the beginning are very detailed instructions for installation.

---

