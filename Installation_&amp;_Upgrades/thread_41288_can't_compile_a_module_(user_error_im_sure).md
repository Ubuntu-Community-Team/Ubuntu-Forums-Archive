---
title: "can't compile a module (user error im sure)"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by linTrog on 2005-06-12
Hi 

I'm trying to get my orinoco card to function and function in monitor mode for kismet.

I've been following some other threads but I can't seem to get past this.  I'm trying to compile a module and I've installed gcc3 but it's a nogo.

instructions that I was following :: [http://www.ubuntulinux.org/wiki/OrinocoMonitorKismet2005Hoary/](http://www.ubuntulinux.org/wiki/OrinocoMonitorKismet2005Hoary/)

(everything up to make module worked fine)

_______________________________________________ ______________________________
root@ubuntupo:/usr/src/linux # make modules
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: No such file or directory
CHK include/linux/version.h
SYMLINK include/asm -> include/asm-i386
/bin/sh: /usr/src/linux-source-2.6.10/scripts/gcc-version.sh: No such file or directory
make[2]: scripts/Makefile.build: No such file or directory
make[2]: *** No rule to make target `scripts/Makefile.build'. Stop.
make[1]: *** [scripts_basic] Error 2
make: *** [include/linux/autoconf.h] Error 2
root@ubuntupo:/usr/src/linux #
__________________________________________________ ________________________________


Anyone know why it doesn't compile?

 thanks

 ](*,)

---

### Post by jshein on 2005-06-13
I have noticed some discrepancies on different systems since I originally wrote that thread. the biggest being on systems that upgraded from the beta releases to current, versus a fresh install.

In order to compile I installed:

gcc
gcc-3.3
gcc-3.3-base
gcc-4.0-base
libgcc1

Let me know if this helps

---

### Post by linTrog on 2005-06-13
I've double checked to make sure I have all of those gcc's installed.  Still nothing. 

I don't know enough of the system to begin to speculate why it's not working.  =]  But I've been happily banging my head on the wall for a few days now.  Well, not happily I guess.

---

### Post by jshein on 2005-06-13
I hate to ask the obvious but did you remember to decompress the source and link to it?

try 
#ls -lh /usr/src/linux/

and 

#ls -lh /usr/src/linux-source-2.6.10/scripts/

---

### Post by linTrog on 2005-06-13
it's fixed, up and running.  

I didn't get any files when I checked 
"#ls -lh sr/src/linux-source-2.6.10/scripts/"

I went through the instructions again, slowly, using verbose and checking to see if I had the desired output.  I think I missed something in the unpacking..

I'd almost say this is an embarassing mistake except I'm so used to finding my own dumb mistakes that it doesn't phase me anymore LOL

Thanks all for your help!  mucho apreciation!

- linTrog

 \\:D/

---

