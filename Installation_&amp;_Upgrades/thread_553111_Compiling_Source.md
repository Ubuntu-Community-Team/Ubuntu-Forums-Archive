---
title: "Compiling Source"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by measekite on 2007-09-17
[B]I would like to compile and then install ndiswrapper.  I have never used a C compiler before.  Part of the instructions are below and are not clear.  Could someone clarify a line by line instruction.  There appears to be 3 separate instructions that I made in red.  The second "make" has no argument. Thank you.



Compile and install[/B]

Go to the source-directory and run [COLOR=Red]make distclean[/COLOR] and [COLOR=Red]make[/COLOR]. As root, run [COLOR=Red]make install[/COLOR]. This should compile and install both the kernel module and the userspace utilities. If you don’t need USB support in ndiswrapper, with recent versions, you can compile with make DISABLE_USB=1 and install with make DISABLE_USB=1 install.

---

### Post by Pumalite on 2007-09-17
They seem to be three different commands that you have to run one after the other.

---

### Post by finferflu on 2007-09-17
After you download the compressed package, you uncompress it (usually with tar). This will create a folder with the corresponding name. 

From a terminal, you have to cd into that directory, this is done with the command:
```

cd <path to the just uncompressed folder>
```

This is your source directory.
Now, you can run the commands indicated in the instructions. So:

```
make distclean
```

Then,

```
make
```

Now, for the last command you need sudo to gain root privileges:

```
sudo make install
```

The instructions also indicate a particular option, needed to disable USB support, in case your wireless device doesn't need it. So, instead of make and sudo make install, you should run:
```

make DISABLE_USB=1
```

and 
```

sudo make DISABLE_USB=1 install
```

I hope this is what you needed to know...

---

### Post by measekite on 2007-09-18
Thanks!  Great Reply and Help

Even if you card does not need USB does it make any difference if you disable it.

---

