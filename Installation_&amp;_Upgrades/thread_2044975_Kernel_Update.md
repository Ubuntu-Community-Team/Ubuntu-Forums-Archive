---
title: "Kernel Update"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by mamboknave on 2012-08-20
I'm wondering why the Update Manager on my laptop does not list Kernel updates since a long time, It just lists updates for all other SW.

Last time it offered Kernel update was in February for the Kernel version 2.6.32-39

Since then, several new updates came out and were all detected and installed by the Update Manager of my desktop, but nothing on the laptop.

I'm wondering why that happens and how to make the Update Manager detecting kernel updates again.

I'm on 10.04 64b

Thanks!

---

### Post by matt_symes on 2012-08-20
Hi

Do you have the kernel meta-package installed ? The kernels rely on having the kernel meta-package installed to know when there is a kernel update.

Depending on what kernel and version of Ubuntu you have installed, you'll be looking for one of these...

```
linux-image-extra-virtual - Transitional package.
**linux-image - Linux kernel** **image**
**linux-image-generic - Generic Linux kernel image**
linux-image-generic-pae - Transitional package
linux-image-lowlatency - lowlatency Linux kernel image
linux-image-lowlatency-pae - lowlatency Linux kernel image
linux-image-server - Transitional package.
linux-image-virtual - This package will always depend on the latest minimal generic kernel image.
linux-virtual - Minimal Generic Linux kernel and headers

```The ones highlighted in bold are the usual ones most people need. Depending on what you have installed, it is usually one or the other.

You can see what is installed using..

```
dpkg -l | grep linux-image
```That is a small L after dpkg.

Kind regards

---

### Post by vandorjw on 2012-08-20
If you suspect that there is a kernel update, then run

```

sudo apt-get dist-upgrade

```

but since you are running 10.04, which is a long-time-support version of Ubuntu, I think you are already using the most up-to-date version available.

LTS is great for developers. Packages remain mostly unchanged, other than bug-fixes and security-fixes. New features are not needed.

IF your system is running fine, there is no real need to upgrade, unless you require a new feature made available in a newer kernel.

[http://packages.ubuntu.com/lucid/admin/](http://packages.ubuntu.com/lucid/admin/)

I see in the above link that kernel 3.0.0-x is the highest version number available for lucid. Upgrade to it if you wish :)

More specifically, this one,
[http://packages.ubuntu.com/lucid/admin/linux-image-3.0.0-24-generic](http://packages.ubuntu.com/lucid/admin/linux-image-3.0.0-24-generic)


Linux Kenel 2.6.32 and 3.0.0 were both LTS kernels if I am not mistaken, so they will receive security updates and bug fixes for a while.
Cheers -cc7

---

### Post by mamboknave on 2012-08-20
Thanks to you both.

Since the various updated kernel version 2.6.32-xx with xx > 39 are listed in the Synaptic Manager, I've hard time to understand why the Update Manager does not list them for updates.
The only reason I can think of is that this image was not installed: 'linux-image-generic' (with no 2.6.32-39 in the name).

But that's just a guess.

Regards.

---

### Post by matt_symes on 2012-08-21
Hi
> 
The only reason I can think of is that this image was not installed: 'linux-image-generic' (with no 2.6.32-39 in the name).

Install it then, as that may be your problem.

Open a terminal and type...

```
sudo apt-get install linux-image-generic
```

```
sudo apt-get update
```

```
^date^grade
```

In the past i have uninstalled the kernel meta packages to ensure i do not get offered kernel updates.

Kind regards

---

