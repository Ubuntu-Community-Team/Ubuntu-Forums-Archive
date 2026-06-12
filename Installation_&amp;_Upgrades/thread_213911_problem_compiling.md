---
title: "problem compiling"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by Perfex on 2006-07-11
I have the build essestial packages and the kernal headers

To start out im rather new to linux and I ussualy avoid compiling things, been relying on the synaptic and .deb, .run packages.

Well I want to get my Logitech cam working so I downloaded spca5xx-20060501.tar.gz the drivers for my cam

to start out I:
```
cd /home/robert/Desktop/spca5xx-20060501

```

but then when I try I get
```
robert@robert-desktop:~/Desktop/spca5xx-20060501$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/robert/Desktop/spca5xx-20060501 CC=cc modules
make: *** /lib/modules/2.6.15-25-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

```

What am I doing wrong?

---

### Post by diepruis on 2006-07-11
[QUOTE=perfex]```
Remember: you must have read/write access to your kernel source tree.
```[/QUOTE]

See this? It probably means you ahve to run the command as

```

sudo make

```

---

### Post by Perfex on 2006-07-12
> **diepruis said:**
> See this? It probably means you ahve to run the command as

```

sudo make

```

well had nothing to do with it it did the same way either way, anyway I got it working.

[https://help.ubuntu.com/community/Spca5xx](https://help.ubuntu.com/community/Spca5xx)

and this guy had exactly the same problem as I did, he found a work around which I used [http://www.ubuntuforums.org/showthread.php?t=115720&highlight=source+spca5xx+driver](http://www.ubuntuforums.org/showthread.php?t=115720&highlight=source+spca5xx+driver)

---

### Post by diepruis on 2006-07-12
Now I feel all deflated! Stop stealing people's thunder! :)
Just joking. Glad you got it working.

---

