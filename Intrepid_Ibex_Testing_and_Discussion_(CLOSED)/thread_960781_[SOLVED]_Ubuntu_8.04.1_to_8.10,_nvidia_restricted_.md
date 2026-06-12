---
title: "[SOLVED] Ubuntu 8.04.1 to 8.10, nvidia restricted driver issue"
date: 2008-10-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kingtaurus on 2008-10-27
Hi,

I just upgraded to the 8.10 rc. However the nvidia restricted drivers/modules fail to load. At the end of my Xorg.0.log I get the following (these are the only errors I get):
```

(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

```

```

lsmod | grep nvidia

```
Returns nothing.

However when I (from TTY), with the same xorg.conf file:
```

sudo /etc/init.d/gdm stop
sudo insmod /lib/modules/2.6.27-7-generic/updates/dkms/nvidia.ko

```

The module gets insert properly and when I start gdm it detects the display settings properly. Further, GLX works properly and I can run compiz. 

Note, when I do the command ```
modprobe nvidia
``` it responds:
with:
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia

Does anyone know how to correct this so that it will insert the module properly on boot?

---

### Post by mocoloco on 2008-10-27
That's why it pays to read the [known issues]("http://www.ubuntu.com/testing/810rc#Known%20Issues") for pre-release software (first bullet point).  They say it will be fixed before final release, follow the launchpad bug linked there.

---

### Post by kingtaurus on 2008-10-27
I believe that this is a different issue.

However, I managed to find a work around. Files starting with lrm-video (in /etc/modprobe.d) are apparently parsed when modprobe is being issued at boot time). If I comment out any line with just 'nvidia' appearing, like:
```

install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS

```
e.g. this becomes
```

#install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS

```

modprobe functions properly at boot and inserts the module.

---

