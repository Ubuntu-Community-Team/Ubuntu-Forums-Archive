---
title: "Todays update: nvidia-current, Cannot find /lib/modules/2.6.31-19-generic"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by philinux on 2010-02-18
Got these errors.

```
Setting up nvidia-current (195.36.03-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-2.6.31-19-generic
Cannot find /lib/modules/2.6.31-19-generic
update-initramfs: failed for /boot/initrd.img-2.6.31-19-generic
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-13-generic
Errors were encountered while processing:
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dino99 on 2010-02-18
got these too

---

### Post by philinux on 2010-02-18
> **dino99 said:**
> got these too

It wont find that file as there isn't one.
/lib/modules# ls
2.6.32-12-generic  2.6.32-13-generic

2.6.31-19-generic is my current karmic kernel.

---

### Post by philinux on 2010-02-18
Booted ok in apart from low graphics message. But system must be using nv.

Apport sprung to life so I raised this bug.

Can someone confirm it. 

Cheers.

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/523903](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/523903)

---

### Post by philinux on 2010-02-19
Still cant activate nvidia-current. Anyone know whats up.

I'm not getting the above error now.
This is from jockey.log
```
2010-02-19 13:11:09,848 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: **could not find module nvidia_current**

2010-02-19 13:11:09,848 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
2010-02-19 13:11:31,347 WARNING: /sys/module/lbm_nouveau/drivers does not exist, cannot rebind lbm_nouveau driver
2010-02-19 13:11:31,593 DEBUG: handler xorg:nvidia_173 previously unseen
2010-02-19 13:11:31,594 DEBUG: handler xorg:nvidia_current previously unseen
2010-02-19 13:11:31,699 DEBUG: handler kmod:lbm_nouveau previously unseen
2010-02-19 13:11:31,699 DEBUG: handler kmod:lbm_nouveau previously unused
2010-02-19 13:11:31,699 DEBUG: writing back check cache /var/cache/jockey/check
2010-02-19 13:11:31,910 DEBUG: kmod:lbm_nouveau is already enabled or not available, not announcing
2010-02-19 13:13:41,486 WARNING: modinfo for module nvidia_current failed: ERROR: modinfo: could not find module nvidia_current

2010-02-19 13:13:41,487 ERROR: XorgDriverHandler.enable(): package or module not installed, aborting
```

From term.log
```
Setting up nvidia-current (195.36.03-0ubuntu1) ...

update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.

update-initramfs: deferring update (trigger activated)

Loading new nvidia-current-195.36.03 DKMS files...

Building only for 2.6.32-13-generic

Building for architecture x86_64

[B]Module build for the currently running kernel was skipped since the

kernel source for this kernel does not seem to be installed[/B].



Processing triggers for initramfs-tools ...

update-initramfs: Generating /boot/initrd.img-2.6.32-13-generic

Log ended: 2010-02-19  13:08:32
```

---

