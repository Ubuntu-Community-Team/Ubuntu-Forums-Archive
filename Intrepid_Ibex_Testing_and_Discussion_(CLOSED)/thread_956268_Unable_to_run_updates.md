---
title: "Unable to run updates"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by SSamiK on 2008-10-23
I've hit a snag while trying to run a update:
```

Preparing to replace libgl1-mesa-glx 7.2-1ubuntu1 (using .../libgl1-mesa-glx_7.2-1ubuntu2_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-glx_7.2-1ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libGL.so.1', which is also in package nvidia-glx-173
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-glx_7.2-1ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libgl1-mesa-dri:
 libgl1-mesa-dri depends on libgl1-mesa-glx (= 7.2-1ubuntu2); however:
  Version of libgl1-mesa-glx on system is 7.2-1ubuntu1.
dpkg: error processing libgl1-mesa-dri (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libgl1-mesa-dri

```

The same thing also happens with; Synaptic when trying to fix broken packages, sudo aptitude install anypackage. 

Anyone else gotten this, or knows how to fix?

---

### Post by SSamiK on 2008-10-23
Seems I got around the problem by forcing installation of the troublesome update. 
```

cd /var/cache/apt/archives/
sudo dpkg --force-all -i libgl1-mesa-glx_7.2-1ubuntu2_i386.deb

```
then progressing with updates as usual. No ill effects discovered yet, will report back if anything shows up.

---

