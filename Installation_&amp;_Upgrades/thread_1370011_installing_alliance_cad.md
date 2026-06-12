---
title: "installing alliance cad???"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by abhiii on 2010-01-01
Hi,
I'm new to linux and wanted to install the alliance cad tools on ubuntu but i'm not able to get the package on synaptic package manager and i'm not able to install it using the tar.gz package also.
So if anyone knows how to install it plz let me know

---

### Post by 4asic on 2010-02-01
Hi,

Sorry for the late reply, but I only just joined.

I managed to get Alliance running on ubuntu 9.1 (Karmic), but I used the binary version. The 'source' version did not completely compile on my system and the binary version worked just fine.
Have you tried the binary version:
[http://www-asim.lip6.fr/pub/alliance/distribution/5.0/alliance-5.0-20090901-i386-sl5soc.i386.tar.gz](http://www-asim.lip6.fr/pub/alliance/distribution/5.0/alliance-5.0-20090901-i386-sl5soc.i386.tar.gz)

Before using the binary version you should also install the latest motif library. For ubuntu (9.1) this is version 3. There is a newer version of motif, but that one is not yet available for ubuntu (as far as I know of). 
I think alliance does look for the newer version of motif, so you should 'trick' alliance into using the older version of motif by creating a symbolic link to the older version.
   

Installing libmotif3:

sudo apt-get install libmotif3


Creating symbolic link:
    
sudo ln -s /usr/lib/libXm.so.3.0.2 /usr/lib/libXm.so.4
  
  

Also, you will need the alc_env.sh script to set some environment variables. I could not find it with the binary distibution, so I also downloaded and 'configured' the source version. After running the 'configure' step, the alc_env.sh file can be found in the 'distrib/etc/' directory (of the source version). Copy this file to your home directory or project directory and make sure you 'source' it before running alliance.

Hope this helps.
Good luck!

---

### Post by lee-anna-loo on 2011-02-09
> **4asic said:**
> 
...

Installing libmotif3:

sudo apt-get install libmotif3

...




for future users :) - also you need to install libmotif-dev

```
sudo apt-get install libmotif-dev
```


@4asic - great explanation, it helped me a lot!

---

