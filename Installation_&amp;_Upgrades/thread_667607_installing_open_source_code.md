---
title: "installing open source code?"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by linksolo74 on 2008-01-14
i just downloaded Cinelerra and i don't know how to install it. It is source code, and when i try to open it it just opens a unzipping thing. I'm new to Ubuntu if you cannot tell and i would really like to try out cinelerra. Thanks.

---

### Post by NICU on 2008-01-14
Usually you just unzip all of the files into a new folder.  Then open up that folder.  Inside that folder there should be README and INSTALL text files that will describe the install process.  I don't have experience with this particular program, so if this doesn't help you may need to ask a more specific group.

---

### Post by oldos2er on 2008-01-14
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by linksolo74 on 2008-01-14
well when i go to the directory /home/USERNAME/Desktop/cinelerra-2.1 
(in the terminal) and try ./configure it says

./configure: 11: arch: not found
./configure: 24: arch: not found
[: 24: i686: unexpected operator
[: 31: ==: unexpected operator
./configure: 47: Syntax error: Bad fd number


then when i try "make" it says:

make -f build/Makefile.cinelerra
sh: Syntax error: end of file unexpected (expecting "then")
make[1]: Entering directory `/home/USERNAME/Desktop/cinelerra-2.1'
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
make[1]: Leaving directory `/home/USERNAME/Desktop/cinelerra-2.1'
make: *** [all] Error 2

---

### Post by linksolo74 on 2008-01-15
finally got it working by using akirad.

---

### Post by SFinn on 2008-01-16
> **linksolo74 said:**
> finally got it working by using akirad.

I'm having the same problem. Could you explain who or what is akirad?

---

### Post by linksolo74 on 2008-01-17
> **SFinn said:**
> I'm having the same problem. Could you explain who or what is akirad?

[http://project.akirad.net/node/18](http://project.akirad.net/node/18)

Just do what it tells you to do on the site, then go into the package manager and search for "cinelerra" there should be a few different ones. i had to use "cinelerra K7gl", because i have a AMD 32bit CPU and a video card with opengl 2. 

Please note that i have still had problems, like only loading the audio or video of a file. to see more of about this go to [http://ubuntuforums.org/showthread.php?t=669562](http://ubuntuforums.org/showthread.php?t=669562). Hope this helps. If you don't understand any of this i'll be happy to help.

---

