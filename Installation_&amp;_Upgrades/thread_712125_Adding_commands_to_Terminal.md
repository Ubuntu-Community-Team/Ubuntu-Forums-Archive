---
title: "Adding commands to Terminal"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by disigma on 2008-03-01
Hi all, I'm fairly new to Linux.

Im wondering how you add commands to the Terminal. For instance when installing the Java SDK's, in Windows you add the javac executable to the list on environmental variables, to be able to java compile through command prompt.

I need to know how I can add a similar command to the Terminal, NuSMV ([http://nusmv.irst.itc.it/](http://nusmv.irst.itc.it/)). I extracted the compressed files and whenever i want to use the NuSMV command, I have to refer to it (e.g. /home/nusmv/NuSMV filename).

It would make it quicker if I could just 
NuSMV filename

Any help would be appreciated,

Many thanks to replies (if any :-) ).

---

### Post by Whiffle on 2008-03-01
Theres other ways to do it, but I would just copy NuSMV to /usr/local/bin 

sudo cp /home/nusmv/NuSMV /usr/local/bin

---

### Post by taurus on 2008-03-01
You just add a path to the PATH in ~/.bashrc and you can run the program anywhere without using the whole path.

```
gedit ~/.bashrc
```
And add these two lines to it.

```
PATH=$PATH:/home/nusmv
export PATH
```
Then, either log out and back in or rehash it.

```
source ~/.bashrc
```

---

### Post by disigma on 2008-03-01
Thanks for replies.

My terminal recognizes the command now however i get this error.

*NuSMV: error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory*


Any idea?

---

### Post by taurus on 2008-03-01
Check with synaptic to see if you have libreadline5 installed.  Also, see what other libraries it requires by running

```
ldd /home/nusmv/NuSMV
```

---

### Post by disigma on 2008-03-01
linux-gate.so.1 =>  (0xffffe000)
        libreadline.so.4 => not found
        libncurses.so.5 => /lib/libncurses.so.5 (0xb7ee3000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7def000)
        libexpat.so.0 => /usr/lib/libexpat.so.0 (0xb7dcf000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7daa000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb7d9f000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7c55000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7c51000)
        /lib/ld-linux.so.2 (0xb7f38000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7c38000)

is the result from your help. Using synaptic, i already had installed libreadline5. Maybe NuSMV only works with libreadline4?

---

### Post by santiagozky on 2008-06-20
Hi, try to link libread.so.5 to libread.so.4 with ln that worked for me:

#ln -sf libread.so.5 libread.so.4

---

