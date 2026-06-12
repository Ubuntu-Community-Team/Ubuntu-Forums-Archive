---
title: "Vlc installection Problem"
date: 2007-11-20
forum: Installation &amp; Upgrades
---

### Post by myharshdesigner on 2007-11-20
> **nestcrw said:**
> As far as I know, it should just be the standard thing.
Once you've untared the file, you should see a text file in there that says something like INSTALL. In all caps like that. That file will walk you through installing.

I'm pretty sure it will say something like this:
```
./configure
```

then

```
make
```

then

```
sudo make install
```


according to above code i do same but i am getting som error  :-

> 
harsh@harsh-laptop:~$ cd vlc-0.8.6c/
harsh@harsh-laptop:~/vlc-0.8.6c$ ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... yes
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
harsh@harsh-laptop:~/vlc-0.8.6c$ make
make: *** No targets specified and no makefile found.  Stop.
harsh@harsh-laptop:~/vlc-0.8.6c$ make install
make: *** No rule to make target `install'.  Stop.
harsh@harsh-laptop:~/vlc-0.8.6c$ 





pl solve this problem i am new in linux

---

### Post by taurus on 2007-11-20
You need to install the build-essential package first before you can build anything from source.

```
sudo aptitude update
sudo aptitude install build-essential
```
Then, run your commands again.

p.s.  Once you get an error, no need to run the next command(s) because it's just a waste of time since it (they) will not work.

---

### Post by myharshdesigner on 2007-11-21
Thanks i will try this :)

---

