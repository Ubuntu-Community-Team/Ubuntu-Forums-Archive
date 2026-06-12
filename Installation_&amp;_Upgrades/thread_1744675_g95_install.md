---
title: "g95 install"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by edward_thomas on 2011-04-30
Hello,

I just realised that I posted this in the wrong section....

I'm new to this forum and this thread. I tried installing the g95 compiler like this...

[COLOR=Black]edward@edward:~/Desktop$ tar -zxvf g95-x86-linux.tgz[/COLOR]
g95-install/
g95-install/INSTALL
g95-install/G95Manual.pdf
g95-install/bin/
g95-install/bin/i686-pc-linux-gnu-g95
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/f951
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/cc1
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/crtbegin.o
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/crtbeginS.o
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/crtbeginT.o
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/crtend.o
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/crtendS.o
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/libgcc.a
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/libgcc_eh.a
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/libgcc_s.so
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/libgcc_s.so.1
g95-install/lib/gcc-lib/i686-pc-linux-gnu/4.0.3/libf95.a
edward@edward:~/Desktop$ ls
g95-install  g95-x86-linux.tgz
edward@edward:~/Desktop$ ln -s $PWD/g95-install/bin/*g95* ~/bin/g95  
ln: creating symbolic link `/home/edward/bin/g95': No such file or directory

I don't understand what I am doing wrong, I tried using the Sudo command as well. 

Any ideas?

Thank you

---

### Post by dino99 on 2011-04-30
have you followed the manual/doc/readme ?

---

