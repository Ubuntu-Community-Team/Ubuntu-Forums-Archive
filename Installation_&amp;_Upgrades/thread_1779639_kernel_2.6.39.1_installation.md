---
title: "kernel 2.6.39.1 installation"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by victor_sk on 2011-06-10
Hi everyone,

I've got a bit of a problem here installing kernel 2.6.39.  I'm a CS student curious about OS and its inner workings so I attempted to build and install kernel on my own.  The book which I read advised that I don't install kernel as root but most of the commands still required me to execute using 'sudo'.

- using 'make menuconfig' tool "Device Drivers" I've added device support for my Dell machine (but I don't think this could cause any problems).

- I executed the 'make ARCH=x86_64 defconfig' and compiled with 'make -j4' command because I have a dual core processor.

When I try to select the new kernel from boot menu and run it in "Recovery Mode" I get these errors:

```

No filesystem could mount root, tried: ext3 vfat msdos
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8, 2)

```

I can still load my original Ubuntu installation but need some advise on how to build kernel in Ubuntu.  Perhaps there are some specific steps I need to follow to install a kernel in Ubuntu or could it be a bug in kernel itself?

Thank you,
Victor.

---

### Post by dabl on 2011-06-10
If you want a 2.6.39 kernel, just install a Ubuntu 11.10 daily build.

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)


Alternatively, if your goal is to build a Gnu/Linux OS from scratch, then you don't want Ubuntu, you want Linux From Scratch:  [http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

---

### Post by sbraz on 2011-06-11
this is one of my build scripts called "buildonly". i often start it in single user mode to have the least amount of processes running (=save time). i'm not sure "fakeroot" is needed but it surely won't cause any harm. :)

```

#
# cleanup
#
make clean
make-kpkg clean
#
# build new kernel
#
date > /usr/src/compile-time
fakeroot make deb-pkg
date >> /usr/src/compile-time
#
# choose your preferred deus-ex-machina
#
shutdown -h now
#reboot

```

optionally, you can **fakeroot make deb-pkg _> /somepath/somelogfile_** to redirect stdout to a file: should the compiling process break at least you know where it stopped. notice that stderr isn't redirected to the logfile - i'm not a developer so for now i don't care, but just in case here's some tips about redirection: [http://tldp.org/LDP/abs/html/io-redirection.html](http://tldp.org/LDP/abs/html/io-redirection.html)

compiling a kernel takes some practice, just keep 1-2 stock kernels as a backup/fallback (i learnt this the hard way).
you can find and when you get a good one remember to **cp .config config.OK** so should you screw up something (you *have to* in order to fully understand the process) you can always go back.

my 2.6.39.1 config file comes from /boot/config-2.6.35-28-generic, which has been violently experimented and developed through more or less every version inbetween. :D

about root or not root: i just **sudo su**.

---

### Post by dabl on 2011-06-11
> **dabl said:**
> If you want a 2.6.39 kernel, just install a Ubuntu 11.10 daily build.


Actually, as of today, Oneiric is offereing a Linux 3.0.0 kernel.  :D

---

