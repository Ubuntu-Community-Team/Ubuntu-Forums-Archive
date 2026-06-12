---
title: "Kernel issues"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by moonshnr on 2007-09-29
Due to a bug iin the current kernel that I am using, 2.6.15-29, I need to add a patch for nfs ([https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58170](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/58170)).  I have found several How-to's and guides on how to compile the kernel but they havent answered all of my questions. I am fairly comfortable using linux but workng with the kernel is something new for me.

1. If I am correct, the installer package for Ubuntu Server installs the amd64 kernel version.  I am running a quad core xeon, so is the 686 a better version to use?  As I understand it the differnt versions are mainly for optimizations?

2. How do I know the kernel I downloaded has all the current patches?  When I download it using apt-get source and look at the Makefile and when it compiles, it says 2.6.15.7-ubuntu1.  I would like to make sure I am using 2.6.15-29.

3. When I restart after compiling and installing (make-kpkg and dpkg -i), I cannot get access to the network.  Does this have anything to do with the linux-restricted-modules? I am running a Dell PE 1950.

4. This is going to be a server supporting VM's in a production enviornment so I am trying to stick with 6.06 for the LTS. Seems like the nfs issue is fixed in 7.04 along with some other issues I have had installing it on my Dell PE 1950, mainly RAID and network issues.  Would you recommend just going to 7.04?  What is the release schedule for the LTS versions and when is the next release expected?

Thanks for the help.

---

### Post by kidders on 2007-09-30
Hi there,

> **moonshnr said:**
> If I am correct, the installer package for Ubuntu Server installs the amd64 kernel version.That seems suspicious to me. I doubt a kernel compiled for AMDs would run very well on a Xeon.

> **moonshnr said:**
> How do I know the kernel I downloaded has all the current patches?You'd need to read the documentation accompanying whatever kernel you choose, to be sure about what's in it and what's not. For patching, you'll need to use exactly what the patch is intended to be applied to though, so you may not have much choice.

> **moonshnr said:**
> When I restart after compiling and installing (make-kpkg and dpkg -i), I cannot get access to the network.  Does this have anything to do with the linux-restricted-modules? I am running a Dell PE 1950.You may have forgotten to compile support for something into your kernel.

> **moonshnr said:**
> This is going to be a server supporting VM's in a production enviornmentI can't over-emphasise how ill-advised it is to run a patched, custom-built kernel in a production environment, unless you really know what you're doing. I imagine you probably need to be fairly certain that kernels you run are safe, stable & appropriately configured!

It's quite probable that you just can't live without NFS. In that case, I would suggest a compromise of sorts ... something in between "long-term support" (ie Dapper) and "totally unsupported" (ie a patched, custom-built kernel). What you'd end up with won't be ideal, but should something go wrong, at least you'd have the security of knowing that you're using exactly the same kernel as thousands of other people.

I hope that helps a little.

---

### Post by moonshnr on 2007-09-30
> **kidders said:**
> 
That seems suspicious to me. I doubt a kernel compiled for AMDs would run very well on a Xeon.


I made this assumption by looking at the filename of the download (ubuntu-6.06.1-server-amd64.iso).  I believe output from uname also said amd64.

> **kidders said:**
> 
You may have forgotten to compile support for something into your kernel.


I thought as much.  But if I downloaded the source that was used to compile my current kernel (apt-get source linux-source) then should that give me the source that my current kernel was compiled from including everything it was compiled to support?  I will look elsewhere to read up on the linux-restricted-modules but a short explination of them would be helpful.

> **kidders said:**
> 
I can't over-emphasise how ill-advised it is to run a patched, custom-built kernel in a production environment, unless you really know what you're doing. I imagine you probably need to be fairly certain that kernels you run are safe, stable & appropriately configured!


Point taken and I completely agree.  However since the most current kernel that I seem to be able to install directly from apt (2.6.15-29 in 6.06?) will not work for my purposes then I am limited in options.  I run the VM's over NFS so that they can be moved between physical servers when needed (which is itself not the best solution it would seem).  I feel confident that the patch will work for what I need if I am able to figure out how to compile the kernel reliably. I will definately test it before it actually reaches production.

> **kidders said:**
> 
I would suggest a compromise of sorts ... something in between "long-term support" (ie Dapper) and "totally unsupported" (ie a patched, custom-built kernel). What you'd end up with won't be ideal, but should something go wrong, at least you'd have the security of knowing that you're using exactly the same kernel as thousands of other people.

I hope that helps a little.

I guess I might have to give 7.04 a shot and ditch the LTS but I do enjoy taking the time (and headache) to figure out how to compile this correctly rather than being a MS drone and just having to rely on what I am fed.

---

### Post by kidders on 2007-10-01
> **moonshnr said:**
> But if I downloaded the source that was used to compile my current kernel (apt-get source linux-source) then should that give me the source that my current kernel was compiled from including everything it was compiled to support?  I will look elsewhere to read up on the linux-restricted-modules but a short explination of them would be helpful.What a kernel can do depends entirely on how it's configured. It would be worth double-checking that support for all the hardware you need is switched on. "Restricted" software is stuff that doesn't conform to Ubuntu's licensing requirements ... restricted kernel modules don't form part of the standard kernel source tree.

> **moonshnr said:**
> I do enjoy taking the time (and headache) to figure out how to compile this correctly rather than being a MS drone and just having to rely on what I am fed.Yep... I can certainly understand that. :-) Unfortunately, building kernels is fraught with pitfalls. Personally, I enjoy experimenting with Linux on my *own* PC, but I would be decidedly uncomfortable doing something I hadn't done a hundred times before, in the likes of a commercial setting.

Anyhow, this doesn't apply to a server install, but taking graphics drivers for the sake of example...

[LIST]
[*]Nvidia's proprietary graphics drivers are not part of the kernel tree.
[*]They are, however, built "against" it, in that parts of Ubuntu's kernel source are used in the process of compiling the drivers.
[*]The build process produces a kernel module compatible only with the specific kernel it was built against.
[*]Since Ubuntu is a binary distro, the devs can pre-package drivers that can simply be copied into place on users' PCs, because everybody's using exactly the same kernels.
[*]Once you alter your kernel, you can't take it for granted that anything that depends directly on your old one will work with the new one.[/LIST]So, when it comes to restricted kernel modules, at the very least, you will need to reinstall them after rebuilding your kernel ... and you may need to recompile them from scratch.

---

