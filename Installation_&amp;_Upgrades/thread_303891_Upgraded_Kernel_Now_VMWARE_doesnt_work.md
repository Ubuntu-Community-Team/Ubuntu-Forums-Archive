---
title: "Upgraded Kernel Now VMWARE doesnt work?"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by mep on 2006-11-21
Hello,

I upgraded my kernel to the latest stable 2.6.18.3.  Compiled it with help of this page: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

I was able to also upgraded to latest NVIDIA Drivers too and patched my kernel.  Now I can not for the life of me get VMWARE Workstation 5.5.1-19175  to reinstall again.  I had vmware working on stock kernel with the help of these docs: [https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf](https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf) but I cant seem to get it going again.  It craps out at the Where is include directory in vmware-config.pl.  I have the 2.6.18.3 headers installed ( well at least I think I do when I do a apt-get install Linux-headers-'uname -r' it says they are installed already.

Anyhow spent a couple of blank hrs looking at a blank screen.. :)

Thanks in advance,

-mep

---

### Post by ginsuedog on 2006-11-21
Why don't you try using VMWare server instead?  It's free, all you have to do is register on VMware and you get a free key.  I do not think your current VMware version can build a module for a 2.6.18 kernel.

---

### Post by mep on 2006-11-21
I am not sure I even get to the mod building part.  The vmware-config.pl cant even find my include directory ??

Do you think vmware server will be any different?

-mep

---

### Post by Biker on 2006-11-21
Do you have installed 'linux-headers-*' where * is your kernel version?

Then you can run vmware-config.pl to build a new kernel-module for your upgraded kernel. There are no differences for VMware Workstation or the free VMware Server. You must build a new kernel module after a kernel upgrade. Same here for my NVidia drivers. 

That's the reason why I locked the kernel upgrade for some time.

---

### Post by GarlicFish on 2006-11-21
If you patched and compiled your own kernel then it is no good doing an apt-get install for a stock kernel.

In the article you linked to, it says that you should end up with 2 .deb files after compilation, one for the kernel, one for the headers.

you need to install the headers package using dpkg -i then you may have to create a link so vmware-config.pl can find them.

make sure you have booted using the new kernel before using uname -r

ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux

if all else fails, re-install one of the standard ubuntu kernels and you should be up and running again.

you can practice compiling kernels and modules in vmware by getting the vmware tools to install under a dapper VM.

---

### Post by mep on 2006-11-21
Hi All,

Thanks for input.  I have made the symlink for /usr/bin/linux to pint to my dpkg -i installed headers.  I did a reboot for the heck of it and still vmware-config.pl does not see my linked headers.

Here is message:


The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.18.3).  Even if the module were to compile 
successfully, it would not load into the running kernel.

I followed the instructions ( I think ) and I am now beginning to wonder if other prgs would see the linked headers directory during their install?

Is there another way to better install a Kernel?

I understand that installing a stock ubuntu kernel would probably get things working but I am curious to why this is not working.

More help is needed to solve puzzle.

Thanks again in advance,

-mep

---

