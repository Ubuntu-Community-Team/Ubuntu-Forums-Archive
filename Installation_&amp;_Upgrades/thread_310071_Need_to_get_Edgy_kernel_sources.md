---
title: "Need to get Edgy kernel sources"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by Fabratas on 2006-11-30
Hello,

I need to get the linux-source package on a machine (Xubuntu edgy) that _does not have access to the internet_, however there's a windows machine that I can use to download files.

uname -r answers: "2.6.17-10-generic"
but I can't find any package named "linux-source-2.6.17-10-generic" on the install CD (xubuntu alternate) or the repository at 

[http://fr.archive.ubuntu.com/ubuntu/](http://fr.archive.ubuntu.com/ubuntu/) (first repo in sources.list);

Where do I need to go to get this package ?

Thanks

Fab

---

### Post by az on 2006-11-30
The linux-headers package should be on the disk - just boot into Ubuntu and then boot the disk in.  The package manager should start and you will be able to install that package from the disk.

The full source is not on the cd, but all you need to compile extra modules are build-essential and linux-headers-(whatever version)

---

### Post by Fabratas on 2006-12-01
Thanks.

The reason I need access to the full sources in order to investigate a problem with some pcmcia cards drivers (and to understand more about the pcmcia architecture).

I read somewhere that I cannot use the source straight from kernel.org because the kernel in the distribution usually has different patches added to it by the distribution maintainers.

I hope the full source for the Ubuntu kernel exist somewhere, every other distribution I've used before (RH, slackware,...) provided the distribution's own kernel source as a package.

I could go to the kernel.org source but I need the patches anyway.

Regards,

Fab

---

### Post by Fabratas on 2006-12-01
Never mind, I found

[http://packages.ubuntu.com/edgy/devel/linux-source-2.6.17](http://packages.ubuntu.com/edgy/devel/linux-source-2.6.17)

which seems to have the sources + the diffs from 2.6.17 to 2.6.17-10.33 which I suppose is what is running on my machine.

why uname responds with "-generic" instead of the exact version name is still to be determined.

regards,

/Fa

---

### Post by az on 2006-12-01
The generic tag is just a build of the kernel.

If you are connected to the net, and you have the source repositories enabled in your sources.list (you can use synaptic) get the source by running

apt-get-source linux-generic


Once you get the source, it must be configured to match your running kernel (if you want to build your exact kernel).  Getting the source this way does that.   Getting the source from upstream doesn't - you just end up with a tarball.

---

