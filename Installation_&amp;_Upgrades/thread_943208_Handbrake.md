---
title: "Handbrake"
date: 2008-10-10
forum: Installation &amp; Upgrades
---

### Post by Firedude88 on 2008-10-10
I was wondering if anyone knew how to install handbrake on ubuntu. im still new to ubuntu and i cant figure it out. thanks in advance

---

### Post by Partyboi2 on 2008-10-10
You could follow [[COLOR=Blue]this[/COLOR]]("http://onlyubuntu.blogspot.com/2008/07/howto-setup-handbrake-including-gui.html") tutorial. If you get stuck post where you get stuck at.

---

### Post by Firedude88 on 2008-10-10
when i reach the 14th step down on the list it tells me to type in make.  i do this and it took about 5 minutes or so of what appeared to be installation then it read this.

:~/Desktop/HandBrake$ make
( cd .. ; ./configure ; cd contrib ; cp -f ../config.jam . ; jam )

System: Linux
Endian: little

Don't run configure by hand, make runs it automatically.

No, really. That's it. Just type 'make' and hit return.

You're supposed to be building with make, not jam.
If you were going to use jam--which you shouldn't--you'd run:
 './jam' on a Mac, or
 'jam' on Linux or Windows

To make jam, boil fruit with sugar and an acid until pectins are released.

...found 59 target(s)...
...updating 1 target(s)...
LibX264 ./lib/libx264.a 
patching file encoder/slicetype.c
Hunk #1 succeeded at 493 (offset 114 lines).
Found yasm 0.5.0.1591
Minimum version is yasm-0.6.1 or nasm-2.0
If you really want to compile without asm, configure with --disable-asm.

    cd `dirname ./x264.tar.gz` && CONTRIB=`pwd` &&
    rm -rf x264 && (gzip -dc x264.tar.gz | tar xf - ) && 
    cd x264 &&  patch -p0 < ../patch-x264-idr.patch && 
    bash ./configure --prefix=$CONTRIB --enable-pthread &&
    make libx264.a && cp libx264.a $CONTRIB/lib/ && cp x264.h $CONTRIB/include/ && strip -S $CONTRIB/lib/libx264.a

...failed LibX264 ./lib/libx264.a ...
...failed updating 1 target(s)...
make[1]: *** [.contrib] Error 1
make: *** [contrib/.contrib] Error 2

---

### Post by Partyboi2 on 2008-10-10
Maybe you need libx264-dev installed, you can try it by typing
```
sudo apt-get install libx264-dev
``` After it has installed you will need to 
run ./configure again before make.

---

### Post by Firedude88 on 2008-10-10
It still gives me the same error message and it also gave me one when i tryed installing that thing you just had me try.

---

### Post by Partyboi2 on 2008-10-10
What was the error message you were getting when you tried installing libx264-dev?
Can you post the output from 
```
sudo apt-get install libx264-dev
```

---

### Post by Firedude88 on 2008-10-10
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libx264-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


this time it didnt error.  it gave me this.  then i typed back in ./configure and it gave me this

:~/Desktop/HandBrake$ ./configure

System: Linux
Endian: little

Don't run configure by hand, make runs it automatically.

No, really. That's it. Just type 'make' and hit return.

You're supposed to be building with make, not jam.
If you were going to use jam--which you shouldn't--you'd run:
 './jam' on a Mac, or
 'jam' on Linux or Windows

To make jam, boil fruit with sugar and an acid until pectins are released.




so then i typed in make and this came up


:~/Desktop/HandBrake$ make
( cd .. ; ./configure ; cd contrib ; cp -f ../config.jam . ; jam )

System: Linux
Endian: little

Don't run configure by hand, make runs it automatically.

No, really. That's it. Just type 'make' and hit return.

You're supposed to be building with make, not jam.
If you were going to use jam--which you shouldn't--you'd run:
 './jam' on a Mac, or
 'jam' on Linux or Windows

To make jam, boil fruit with sugar and an acid until pectins are released.

...found 59 target(s)...
...updating 1 target(s)...
LibX264 ./lib/libx264.a 
patching file encoder/slicetype.c
Hunk #1 succeeded at 493 (offset 114 lines).
Found yasm 0.5.0.1591
Minimum version is yasm-0.6.1 or nasm-2.0
If you really want to compile without asm, configure with --disable-asm.

    cd `dirname ./x264.tar.gz` && CONTRIB=`pwd` &&
    rm -rf x264 && (gzip -dc x264.tar.gz | tar xf - ) && 
    cd x264 &&  patch -p0 < ../patch-x264-idr.patch && 
    bash ./configure --prefix=$CONTRIB --enable-pthread &&
    make libx264.a && cp libx264.a $CONTRIB/lib/ && cp x264.h $CONTRIB/include/ && strip -S $CONTRIB/lib/libx264.a

...failed LibX264 ./lib/libx264.a ...
...failed updating 1 target(s)...
make[1]: *** [.contrib] Error 1
make: *** [contrib/.contrib] Error 2

---

### Post by Partyboi2 on 2008-10-11
I found out that error message is caused by using the yasm 0.5.0 package in the ubuntu repo's You can  try installing the 0.7.1 version from [[COLOR=Blue]here[/COLOR]]("http://lug.mtu.edu/ubuntu/pool/universe/y/yasm/yasm_0.7.1-0ubuntu1_i386.deb")  Once it has downloaded double click on it to install. If you have problems installing the deb package you may need to compile yasm, which you can download the source from [[COLOR=Blue]here[/COLOR]]("http://www.tortall.net/projects/yasm/wiki/Download").

---

### Post by hugmenot on 2008-10-11
You can also save all the hassle and just install this recent snapshot for Hardy:
[http://handbrake.fr/?article=snapshot](http://handbrake.fr/?article=snapshot)

---

### Post by Firedude88 on 2008-10-11
Hugmenot i tryed your way and it said wrong architecture 'i386'

---

### Post by Firedude88 on 2008-10-11
partyboi same with the yasm  it said the same thing about architecture i38etc

---

### Post by hugmenot on 2008-10-13
> **Firedude88 said:**
> Hugmenot i tryed your way and it said wrong architecture 'i386'

I&#8217;m sorry. You didn&#8217;t mention that you run 64 bit.

---

### Post by Partyboi2 on 2008-10-13
> **Firedude88 said:**
> partyboi same with the yasm  it said the same thing about architecture i38etc
You can download the 64 bit version of yasm from [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/intrepid/amd64/yasm/download") Or you can compile it from source  as I previously posted.

---

### Post by Firedude88 on 2008-10-14
sudo make install

at this step about the 10-12 down the list it says that there are 

:~/Desktop/HandBrake$ sudo make install
make: *** No rule to make target `install'.  Stop.

and sry for not mentioning i run 64 bit i forgot about it.  i installed the new yasm you mentioned and that worked so now im not sure where the hitch is.

---

### Post by Partyboi2 on 2008-10-14
After you installed yasm did you re-run ./configure and make before trying
sudo make install

---

### Post by Firedude88 on 2008-10-15
yes i actually started from the beginning just to be sure

---

### Post by Fidju on 2008-10-20
> **hugmenot said:**
> You can also save all the hassle and just install this recent snapshot for Hardy:
[http://handbrake.fr/?article=snapshot](http://handbrake.fr/?article=snapshot)

you are my hero hugmenot.  this worked like a charm, and terminal was never needed.  :)

---

### Post by tilapia on 2008-10-22
I was having a tough time compiling the Handbrake GUI from source on my Intrepid 64 bit machine. However, I found these [debs]("http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html") which are for 32 bit and 64 bit machines and work a treat. 

I recently built a new Core 2 Quad Q9550 machine and it's encoding at a rate of 160 fps. My PowerMac G5 Dual 2GHz can manage about 16 fps. Great little application.

---

### Post by cj100570 on 2008-11-14
> **Firedude88 said:**
> I was wondering if anyone knew how to install handbrake on ubuntu. im still new to ubuntu and i cant figure it out. thanks in advance

I know I'm a bit late but I recently found this and it works like a charm;


[http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html](http://filthypants.blogspot.com/2008/09/32-bit-handbrake-gtk-gui-and-yasm-deb.html)

---

