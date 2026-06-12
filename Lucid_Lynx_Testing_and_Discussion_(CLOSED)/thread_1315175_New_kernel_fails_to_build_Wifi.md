---
title: "New kernel fails to build Wifi"
date: 2009-11-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Peter09 on 2009-11-05
Just done an update this morning and noticed two build failures from the kernel which was included. It has resulted in me having no Wifi connection, whether there is a direct connection - I don't know.

---

### Post by SevenMachines on 2009-11-05
Do you mean dkms is failing to build some modules on the new kernel? If so you could post the make.log for the failed dkms builds

---

### Post by Peter09 on 2009-11-05
Where do I find that make log

---

### Post by paul_in_london on 2009-11-05
May be related to a similar problem I'm having:

```
paul@lucid:~$ cat /var/lib/dkms/nvidia/190.42/build/make.log

DKMS make.log for nvidia-190.42 for kernel 2.6.32-020632rc6-generic (i686)

Thu Nov  5 11:20:20 GMT 2009



The C compiler 'cc' does not appear to be able to

create executables.  Please make sure you have 

your Linux distribution's gcc and libc development

packages installed.



*** Failed CC sanity check. Bailing out! ***



make: *** [select_makefile] Error 1
paul@lucid:~$ 

```

I have libc6, libc6-i686 and libc6-dev installed (all v2.10.1-3-ubuntu1)  and gcc v4.4.4.1-1ubuntu2.

---

### Post by SevenMachines on 2009-11-05
general format for dkms build log locations is
/var/lib/dkms/<modulename>/<kernelversion>/log/make.log

for example,
/var/lib/dkms/nvidia/kernel-2.6.31-14-generic-x86_64/log/make.log

These are actually symlinks to the full location
/var/lib/dkms/<modulename>/<moduleversion>/<kernelversion>/log/make.log

---

### Post by SevenMachines on 2009-11-05
oh, and 
$sudo dkms status
will show if any/which modules haven't built on which kernel

---

### Post by RickvanderZwet on 2010-01-13
Try to install the build-essential and try again

```
sudo apt-get install build-essential
```

If that is already installed (my case, after upgrade) remove all build tools traces 

```
sudo apt-get remove cc gcc libc6-dev linux-libc-dev
sudo apt-get autoremove
```

and install build-essential again

```
sudo apt-get install build-essential
```

---

