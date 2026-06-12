---
title: "Help with wifi drivers on system w/out make/gcc/etc"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by rchille on 2007-04-18
Hello all

I am working on a Ubuntu variant [Pyramid] that is based on Breezy but rolled with the 2.6.17.8 kernel.

My trouble with it is that is doesn't have the rt2500 drivers for my wifi card. [Even though they are suppose to come with BB]

I have installed Breezy [on which Pyramid is built] on another computer and upgraded the kernel and headers to 2.6.17 thanks to awesome [guides]("http://ubuntuforums.org/showthread.php?t=56835")!
I then downloaded and compiled the drivers following the instructions outlined [here.]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#apt").

I used the insmod command to see if the the drivers worked with my test system. [It did]
Then I copied the driver over to Pyramid and tried same thing at which I got the following:

```

rt2500: Unknown symbol malloc_sizes
rt2500: Unknown symbol __kmalloc
insmod: error inserting 'rt2500.ko':-1 Unknown symbol in module

```

I did some checking and found that malloc_size is defined in a file called slab.h and slab.c which are not on my Pyramid system.  

Is there a way to add them or conversely a way to compile without needing them on the system? [I'll admin my fairly limited knowledge of C and kernels].
Or another suggestion on how to procede?

Thanks in advance!
Rob

---

### Post by rchille on 2007-04-18
Answering my own question here.... :)

I decided to try rebuilding the kernel and poke around see if I could find anything about enabling/disabling the malloc symbols [links to the slab files]

Inside the Kernel configs I found a listing for:
```

General setup--->
     Configure standard kernel features (for small systems)--->
        [*]Use full SLAB allocator

```

Since the slab.c and slab.h files contained the references for malloc_size and __kalloc I decided to try removing this from the kernel

One brief [45min recompile later] and I have an installable module!

---

