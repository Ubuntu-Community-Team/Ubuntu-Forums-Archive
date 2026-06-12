---
title: "Nvidia nforce 430, network problems and kernel 2.6.19"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by sampan74 on 2007-01-08
I have been reading a zillion posts regarding the networking problems with Ubuntu and the Nvidia nforce 430 chipset for the Athlon64 family. It seems to me like the might problem be solved by compiling the 2.6.19 version of the kernel. However, compiling the kernel on a fresh Ubuntu installation without network support is not an easy task, in my opinion. :-k 

I've been banging my head for a few days with this now and I am beginning to think that I'll just have to wait for an official Ubuntu release of the kernel-version 2.6.19. 

Therefore I have two questions to all you guys out there:

1. When can we expect to get an official Ubuntu update of the kernel to version 2.6.19?

2. Is there someone out there that has a link to a good howto, or can help me with instructions, for any of the below tasks?
   a.) Downloading the packages needed (which ever they are?) for kernel compilation to another computer and then moving them to the computer that needs the new kernel for compilation there.

   b.) Compiling the kernel and making a debian package on another computer (with totally different hardware) and then moving it to the computer that needs it for installation there.

   c.) Any other solution to my problem.

---

### Post by teaker1s on 2007-01-08
you could copy packages from apt cache on another pc then burn to cd
then
[COLOR="Red"]sudo apt-cdrom add[/COLOR]
[COLOR="Red"]sudo apt-get update[/COLOR]

then install package

---

### Post by sampan74 on 2007-01-09
i have investigated this a little bit more now and I have decided to compile the kernel on another computer running Ubuntu. Is there anyone out there that can point me to a good howto for doing that. All the howtos that i find seem to deal with compiling the kernel using the old config.

---

### Post by ra1n on 2007-01-26
> **sampan74 said:**
> i have investigated this a little bit more now and I have decided to compile the kernel on another computer running Ubuntu. Is there anyone out there that can point me to a good howto for doing that. All the howtos that i find seem to deal with compiling the kernel using the old config.

Get Feisty packages of :
linux-image-2.6.20-5-generic_2.6.20-5.7_i386.deb
linux-restricted-modules-2.6.20-5-generic_2.6.20.1-6_i386.deb
linux-restricted-modules-common-2.6.20.1-6_all.deb

or for your architecture, it should boot with ethernet and audio support, then you could recompile your own kernel package, or stick with that.

Beware that nvidia-glx won't work, to use that you need to recompile it (from the linux-restricted-modules source package I think) or modify the binary one (removing dependencies from the control file then rebuilding it, since dependencies only affects gtk setup programs)

---

### Post by sampan74 on 2007-01-31
Ok! Thanks a lot! I'll try that as soon as I get some time for it. I have a one year old son here, who consumes all my time... ;-)

---

