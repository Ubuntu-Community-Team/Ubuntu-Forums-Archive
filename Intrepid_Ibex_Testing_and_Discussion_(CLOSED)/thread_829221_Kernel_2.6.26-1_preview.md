---
title: "Kernel 2.6.26-1 preview"
date: 2008-06-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-06-14
Saturday fun for kernel geeks...

Image and headers for 2.6.26 are in repo now...:)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-June/001795.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-June/001795.html)

Installs without trouble and also starts.


----------------------------------

The nVidia challenge...

The driver must be patched
[http://www.nvnews.net/vbulletin/showpost.php?p=1666305&postcount=2](http://www.nvnews.net/vbulletin/showpost.php?p=1666305&postcount=2)

```
sudo sh NVIDIA-Linux-x86-173.14.05-pkg1.run --apply-patch NVIDIA_kernel-173.14.05-2419292.diff.txt

```

I am just building a new kernel source and see if it compiles and installs.

I just took the source from repo and compiles it, is there a smarter way until a
compiled source is available within repo  ??? 

:)

---

### Post by psyke83 on 2008-06-14
I'm on the new kernel now and multitasking seems a lot better. For example: [http://www.southparkstudios.com/episodes](http://www.southparkstudios.com/episodes)

Select and play an episode, and while it's playing, hover over the icons previewing other episodes. With the 2.6.24 kernels it was very jerky and slow, but it's smooth with this kernel now.

Oh and as a preemptive measure, let me warn anyone who tries this kernel: it has not been completely built and uploaded yet! That means the nvidia driver does not work out of the box (it needs nvidia-glx-new and *-restricted-modules too), and many sound cards & most wireless cards will not work either (they require the firmware files and kernel modules in *-ubuntu-modules). When all the parts are ready, the linux-meta metapackage will be updated and the kernel will offered as a dist-upgrade. Right now, it's not ready.

---

### Post by plun on 2008-06-14
> **psyke83 said:**
> 

Oh and as a preemptive measure, let me warn anyone who tries this kernel: it has not been completely built and uploaded yet! That means the nvidia driver does not work out of the box (it needs nvidia-glx-new and *-restricted-modules too), and many sound cards & most wireless cards will not work either (they require the firmware files and kernel modules in *-ubuntu-modules). When all the parts are ready, the linux-meta metapackage will be updated and the kernel will offered as a dist-upgrade. Right now, it's not ready.

Well... this time it can be really tricky with nvidia packages.

Soon I have my compiled kernel source and can try if its possible to build a kernel module for the nVidia driver. (rejected against a 2.6.25 source)

It takes over 2 hours for me and 2GB disk space to build this kernel source.

:)

---

### Post by plun on 2008-06-14
Follow up... this kernel was a hard one.

It is 2.6.26-rc6 "under the hood" (Debian change log)

I must also install the debs after compiling source.
It was otherwise a Zen kernel or impossible to build
a nvidia driver  


[IMG]http://pici.se/pictures/rrUEZDeRA.png[/IMG]


:)

---

### Post by Eclipse. on 2008-06-14
Patching the nvidia driver now..

Me thinks this was one of the reasons why alpha 1 was delayed.

---

### Post by plun on 2008-06-14
> **Eclipse. said:**
> Patching the nvidia driver now..

Me thinks this was one of the reasons why alpha 1 was delayed.

Yup, the kernel for sure

I rebuilt the source following the Master Kernel procedure
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

I had a home brewed 2.6.25 kernel before and maybe that
was my extra challenge  :confused:

Patching the nVidia driver is easy done.

---

### Post by vbman11 on 2008-06-17
How does one patch the Nvidia driver exactly?:confused:

---

### Post by ronacc on 2008-06-17
well I screwed myself:( I installed the kernel and patched the nvidia driver  (173.14.05) no go on my amd64 sys ao I tried the new 173.14.09 which suposedly has prelim .26 kernel support also no go , tried purging jockey etc to see if that was blocking ,no help . tried to revert to .24-16 but now have the wrong gcc rats!

---

### Post by autocrosser on 2008-06-18
I'm not worried about the accelerated driver as of yet--I wanted to try the new kernel & just reset my xorg to the nv driver--seems to be running very nice here.

I'll wait til the repos have the new nvidia driver & install it then.....

---

### Post by Nullack on 2008-06-18
Theres a new Nvidia driver revision out too

---

### Post by plun on 2008-06-18
> **Nullack said:**
> Theres a new Nvidia driver revision out too

Well.. I know and its 2 versions, one of the drivers also a new beta.

But this is a incredible mess so its no meaning to
burn time on this for the moment.

---

### Post by Eclipse. on 2008-06-18
> **plun said:**
> Well.. I know and its 2 versions, one of the drivers also a new beta.

But this is a incredible mess so its no meaning to
burn time on this for the moment.

Does the beta driver provide any support for .26 kernel or does it still need to be patched?

---

### Post by pferraro on 2008-06-18
> **Eclipse. said:**
> Does the beta driver provide any support for .26 kernel or does it still need to be patched?

The recently released nvidia driver (173.14.09) includes support for the 2.6.26 kernel:
[http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)
[http://www.nvidia.com/object/linux_display_amd64_173.14.09.html](http://www.nvidia.com/object/linux_display_amd64_173.14.09.html)

You don't need to use the 177.13 beta unless you specifically need support for GeForce GTX 260/280.

---

### Post by ronacc on 2008-06-18
> **pferraro said:**
> The recently released nvidia driver (173.14.09) includes support for the 2.6.26 kernel:
[http://www.nvidia.com/object/linux_display_ia32_173.14.09.html](http://www.nvidia.com/object/linux_display_ia32_173.14.09.html)
[http://www.nvidia.com/object/linux_display_amd64_173.14.09.html](http://www.nvidia.com/object/linux_display_amd64_173.14.09.html)

You don't need to use the 177.13 beta unless you specifically need support for GeForce GTX 260/280.

the 173.14.09pkg2.run (amd64) does NOT work on my intrepid install with the current 2.6.26-1 generic kernel neither does the patched .05 version . they both compile and install ok but won't load .

---

### Post by plun on 2008-06-18
> **ronacc said:**
> the 173.14.09pkg2.run (amd64) does NOT work on my intrepid install with the current 2.6.26-1 generic kernel neither does the patched .05 version . they both compile and install ok but won't load .

Well some findings...

- We probably needs a source for the kernel,  linux-source-2.6.26

- Kernel wrong built, Zen is included ? 

- Both 173.14 and 177.13 is broken against Ubuntus kernel

- sbin/lrm-video  was gone :confused:

-  At least 177.13 seems to be build against Xorg 1.5....with servers.
(I havent checked 173.14)  X starts with blank xorg.conf.


- I managed to build it a few days ago after compiling the kernel tarball.
But not today...

So this is just a mess...:)


EDIT

Probably found my error  /var/logs/nvidia-installer

```
 /NVIDIA-Linux-x86-177.13-pkg1/usr/src/nv modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
```

But my solution is special....

---

### Post by ronacc on 2008-06-18
since I expect things to change rapidly over the next few days I didn't try to dig into it too much , I can live with NV and wait until ater the first alpha is out .

---

### Post by Eclipse. on 2008-06-18
> **plun said:**
> Well some findings...

- We probably needs a source for the kernel,  linux-source-2.6.26

- Kernel wrong built, Zen is included ? 

- Both 173.14 and 177.13 is broken against Ubuntus kernel

- sbin/lrm-video  was gone :confused:

-  At least 177.13 seems to be build against Xorg 1.5....with servers.
(I havent checked 173.14)  X starts with blank xorg.conf.


- I managed to build it a few days ago after compiling the kernel tarball.
But not today...

So this is just a mess...:)





I would basically just about to post everything you just said there.;)

---

### Post by ElevenWarrior on 2008-09-15
how do you isntall this kernel?

---

### Post by MALEADt on 2008-09-15
> **ElevenWarrior said:**
> how do you isntall this kernel?

Err, this is a way old kernel of the testing version of ubuntu, currently we are at 2.6.27-3 :-?
If you came up this thread by a search, and you're running Hardy, there is no easy way to run this kernel. Or you take your config and recompile a new kernel with it, or you wait 2 months (1 month and a half) till ibex comes out.

---

