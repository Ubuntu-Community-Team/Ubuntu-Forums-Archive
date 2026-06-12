---
title: "Installing Ubuntu in an LXC container"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2011-06-03
I was wondering if there is a way to install Ubuntu in an LXC container (assuming the host is 10.04.2LTS amd64 and the guest will be any recent version of Ubuntu on an ISO).  I have successfully installed many versions of Ubuntu as guests under a qemu-kvm virtual machine.  In theory, I could just extract those post-install files from the saved images, and populate a directory tree with them for LXC.  But I was wondering if there was a way to do the install direct, or indirectly, from the ISO, given that in LXC one does not actually boot a kernel (if you didn't know that, you're unlikely to have an answer for this).

---

### Post by Rubi1200 on 2011-06-03
I wonder if this might interest you:
[http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/](http://blog.bodhizazen.net/linux/lxc-configure-ubuntu-lucid-containers/)

---

### Post by Skaperen on 2011-06-03
Not exactly what I am looking for, but it is interesting and has useful info that can apply to other stuff I'll be doing.  My goal is to make a container that is as close to being a Ubuntu install as possible.  I could use the file tree I extracted from a VM based install to do LXC.  It already works with chroot (have done apt-get update and apt-get upgrade under a legacy chroot and that works).  That's probably the direction I will have to take.  But I was wondering if someone had worked out how to take the ISO apart and drop pieces of it into an LXC tree so it thinks it just booted up from a CD/DVD/ISO.

---

