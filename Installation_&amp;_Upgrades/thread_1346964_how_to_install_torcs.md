---
title: "how to install torcs"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by basdebaas888 on 2009-12-05
hello,

im a ubuntu newbie so i have no idea what im doing, i have recently installed ubuntu 9.10 on a packard bell laptop and haven't done anything with it yet.

So, i decided to install a racing game and after a time searching the internet i saw this game torcs. so i downloaded it but i didn't knew what to do with it.
i allready discovered the Terminal:P but do i have to insert codes in this or can i just open a file and install it?

i hope somebody can help me install torcs.

btw: this is the site i got the files from: [http://torcs.sourceforge.net/index.php?name=Sections&op=viewarticle&artid=3](http://torcs.sourceforge.net/index.php?name=Sections&op=viewarticle&artid=3)  --> For Linux and FreeBSD from "all-in-one" Source Package.

Basdebaas

---

### Post by Leppie on 2009-12-05
Hoi Bas,

This is from the sourceforge page:
> Check the dependencies
Download the source package torcs-1.3.1.tar.bz2.
Unpack the package with "tar xfvj torcs-1.3.1.tar.bz2".
Run the following commands: 

$ cd torcs-1.3.1
$ ./configure        # --prefix="target dir", --enable-debug or --disable-xrandr might be of interest
$ make
$ make install
$ make datainstall

These are commands to be executed in a terminal. Go to Applications>Accessories>Terminal
The "make" commands often need to be executed with adminstrator rights, in Ubuntu this is done by putting "sudo" in front of the command:
```
$sudo make install
```

You can also download the binary and installer package from the Torcs download page. You will only have to launch it, once downloaded.

**_HOWEVER_**, the best solution is to launch synaptic (System>Administration>Synaptic) click the search button, type in torcs, select the torcs package and click the apply button. This will take care of all dependencies as well and is easier to remove from the system if you don't like the game.

---

### Post by basdebaas888 on 2009-12-06
ok, thanks

il try it. 
i will let you know if it worked.

basdebaas888

---

### Post by basdebaas888 on 2009-12-06
it worked! :)

thanks,

basdebaas888

---

