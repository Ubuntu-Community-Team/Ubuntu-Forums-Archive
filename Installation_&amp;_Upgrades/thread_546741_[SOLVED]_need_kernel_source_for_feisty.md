---
title: "[SOLVED] need kernel source for feisty"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by JBAlaska on 2007-09-09
I'm trying to install Acronis True Image for linux and need the kernel source that's supposed to be in /usr/src

Here are the instructions I'm working with;

[b]- Build and install the new module:

# dkms build -m snapapi26 -v 0.7.24 \
-k 2.6.20-16-generic --config /boot/config-2.6.20-16-generic --arch i686 \
--kernelsourcedir /usr/src/linux-source-2.6.20
# dkms install -m snapapi26 -v 0.7.24 \
-k 2.6.20-16-generic --config /boot/config-2.6.20-16-generic --arch i686 \
--kernelsourcedir /usr/src/linux-source-2.6.20

- Please note that:

<KERNEL_VERSION> is the version of your running kernel, you may detect it by "uname -r" command.

<CONFIG_FILE> - path to the config file of your running kernel. It's usually located in your /boot/ directory.

<KERNEL_ARCH> - kernel package architecture, you may detect it with "uname -m" command.

<PATH_TO_KERNEL_SOURCES> is the directory with the sources of your running kernel. For example on red-hat based Linux distribution you should be able to find the sources in /lib/modules/<KERNEL_VERSION>/build directory.[/b]

I've filled in the path based on a example I got online, the problem is I don't have [b]linux-source-2.6.20
[/b] at /usr/src (or anywhere else I can locate).

I tried to find a link to the kernel sources listed in other threads but I'm getting confused as to which version / build to use.

Any help would be appreciated.

[color=blue]Edit: this is what I got from thryng to run dkms: 
Error! Your kernel source for kernel 2.6.20-16-generic cannot be found at
/lib/modules/2.6.20-16-generic/build or /lib/modules/2.6.20-16-generic/source.
You can use the --kernelsourcedir option to tell DKMS where it's located.

When I get the source, Should they be in /usr/src or /lib/modules/2.6.20-16-generic/build or /lib/modules/2.6.20-16-generic/source.?[/color]
Thanks

---

### Post by PeterF on 2007-09-09
The kernel source, or Kernel headers aren't in the default install. You also need the build essentials to be able to compile the source.

```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

Or use synaptic to install.

---

### Post by az on 2007-09-09
Just install the headers.  To compile stuff for any kernel, you don't need the full source anyway, just the headers.  It's easier to use the linux-headers package since using the full source would require your configure it to match your running kernel anyway.

sudo apt-get install linux-headers-generic


The linux-headers-generic package providers the /lib/modules/(whateverversion)/build link so that your source can use it.

---

### Post by JBAlaska on 2007-09-09
Thanks for the reply's, I think I installed build-essential sometime in the past as I DO have the linux-headers-2.6.20-16-generic in /usr/src and the build link at: /lib/modules.
And I get this when I try to install build essential anyway "linux-headers-generic is already the newest version."

So I tried: dkms build -m snapapi26 -v 0.7.24 \
-k 2.6.20-16-generic --config /boot/config-2.6.20-16-generic --arch i686 \
--kernelsourcedir /lib/modules/2.6.20-16-generic/build

And that did it! Thanks very much! 
Now if I can recover from a dist-upgrade that happened this morning to my main account (I'm logged on as root for this install) I'll be  good to go, I'll start a new thread for that & mark this one "Solved"

It's alot easer to learn linux when you have a great support group, Thanks Again.

---

