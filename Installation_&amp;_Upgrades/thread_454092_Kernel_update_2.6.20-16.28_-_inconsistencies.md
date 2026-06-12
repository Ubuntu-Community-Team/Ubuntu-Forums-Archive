---
title: "Kernel update 2.6.20-16.28 - inconsistencies"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by heldal on 2007-05-25
Todays kernel-update (notification USN-464-1) seems incomplete/inconsistent and can potentially cause serious problems. 

A standard update went as follows:

```
Commit Log for Fri May 25 08:44:02 2007


Upgraded the following packages:
linux-doc-2.6.20 (2.6.20-15.27) to 2.6.20-16.28
linux-libc-dev (2.6.20-15.27) to 2.6.20-16.28
linux-restricted-modules-common (2.6.20.5-15.20) to 2.6.20.5-16.28
linux-source-2.6.20 (2.6.20-15.27) to 2.6.20-16.28
nvidia-glx-new (1.0.9755+2.6.20.5-15.20) to 1.0.9755+2.6.20.5-16.28
nvidia-glx-new-dev (1.0.9755+2.6.20.5-15.20) to 1.0.9755+2.6.20.5-16.28
```

Notably, the kernel itself (kernel-image) is not included, nor is most of the restricted-modules. The distributed advisory indicate that everything kernel-related should be updated to 2.6.20-16.28 while several packages remain at version 2.6.20-15.27. The new versions of packages are in the repository, but all are not yet included through dependencies.

Finally, it is also disappointing to see that the updated nvidia-glx-new package included with this update fail to address the missing WFB X-server-module that is required to support 8800GTS/GTX GPUs. This is a precompiled xorg-module (libwfb.so.*) supplied in the original driver-package from Nvidia that has been forgotten in Ubuntu's repackaged version.

---

### Post by ruy_lopez on 2007-05-25
I think it just wants to update your source, and holds back the image and headers until you are ready. Was the image listed as held back by apt-get upgrade?

---

### Post by rdoolen on 2007-05-25
I noticed something odd too. Synaptic showed packages as 'new in the repository and it seemed they should have been upgrades. For instance,  I have linux-image-2.6.20-15-generic installed, and there is a linux-image-2.6.20-16-generic "new in the respository." This is one of a few similar packages, maybe 5-10 that appear that way.

Is this a different manifestation of the issue in the original post?

---

### Post by heldal on 2007-05-25
> **ruy_lopez said:**
> I think it just wants to update your source, and holds back the image and headers until you are ready. Was the image listed as held back by apt-get upgrade?

Nothing is listed as being held back. 

```
sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

I suspect that all the new packages haven't been propaged everywhere yet. Once a new version of linux-image-generic it should pick up the rest via dependencies.

---

### Post by heldal on 2007-05-25
> **rdoolen said:**
> I noticed something odd too. Synaptic showed packages as 'new in the repository and it seemed they should have been upgrades. For instance,  I have linux-image-2.6.20-15-generic installed, and there is a linux-image-2.6.20-16-generic "new in the repository." This is one of a few similar packages, maybe 5-10 that appear that way.

Different versions of Kernel-images and related modules are treated as individual packages to make it possible to have several installed at the same time (choose at boottime). In such cases there is one "master package" that pulls the others in via dependencies during upgrade. For kernels in a workstation-install that is the linux-image-generic package which has dependencies to different kernel-packages based on which version is being installed.  

(The downside of this is behaviour is that dependecies to old kernels and modules are lost in upgrades and the old packages must be removed manually later.)

---

### Post by ruy_lopez on 2007-05-25
for powerpc at least, there wasn't anything new in the new .config, so I could have recompiled using the old config. In other words, the new source would have been sufficient (I didn't really need the new image or header). Still, it is odd you don't have the new image and headers listed.

---

### Post by heldal on 2007-05-25
> **ruy_lopez said:**
> for powerpc at least, there wasn't anything new in the new .config, so I could have recompiled using the old config. In other words, the new source would have been sufficient (I didn't really need the new image or header). Still, it is odd you don't have the new image and headers listed.

Don't get confused by the source-package listed in the update-log. I've only got installed to poke around from time2time when I need to check something in the source, not to compile the kernel myself. I run the kernel supplied in the kernel-image package. Knowing there is no change to the.config I can of course compile the new kernel myself from source, but I'd rather let apt take care of it by upgrading the binary package ;)

---

### Post by ruy_lopez on 2007-05-25
Yeah, that linux-source did throw me a little.

---

### Post by roccolord on 2007-05-25
Looks like the linux-meta packages which provides linux-image-generic hasn't been updated correctly for some reason.

---

### Post by holli on 2007-05-26
Yes, looks like they forgot to build the linux-meta packages: [https://launchpad.net/+builds/+build/340143](https://launchpad.net/+builds/+build/340143) (i386) and [https://launchpad.net/+builds/+build/340142](https://launchpad.net/+builds/+build/340142) (amd64). Should we wait or file a bug?

---

### Post by heldal on 2007-05-26
> **holli said:**
> Should we wait or file a bug?

It should imho be treated as a bug as the upgrade has been announced with notifications to various lists and forums.  

Strange it hasn't been fixed yet as it appear to affect everybody on i386 and amd64 platforms. Only sparc, powerpc and ia64 architectures have been built according to [Launchpad]("https://launchpad.net/ubuntu/+source/linux-meta/2.6.20.16.28"), while it is 2 days since it was announced for all platforms.

---

### Post by holli on 2007-05-26
Someone already filed a bug for the kernel issue: [https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/117024](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/117024)

---

