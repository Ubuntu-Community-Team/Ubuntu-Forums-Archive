---
title: "Xen on Edgy 3.0"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by evuraan on 2006-11-16
Hello,

I'm trying to get Xen configured on Edgy, following [this]("https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy") howto. 

To begin with, the menu.lst modifications suggested in that page won't work, it won't boot:  ](*,) 

```
title XEN/2.6.17
root (hd0,0)
kernel /boot/xen-3.0-i386.gz
module /boot/xen0-linux-2.6.17-6-generic-xen0 root=/dev/xxx ro
module /boot/xen0-linux-2.6.17-6-generic-xen0.initrd.img
```

This is what it would boot up with:

```
title XEN
root (hd0,0)
kernel /xen-3.0-i386.gz dom0_mem=65536
module /xen0-linux-2.6.17-6-server-xen0 root=/dev/hda3 ro
savedefault
boot

```

However, it panics later, saying PAE mode mismatch. ](*,) 

Has nybody ever done Xen on Edgy? Could any body please post a decent howto here? 

Many thanks in advance..!

---

### Post by bartron on 2006-11-30
> This is what it would boot up with: [...snip...] 

This is because you have a seperate partition for boot - since (hd0,0) is your "boot" you only need / - this is an interesting point since nobody really explains this in his/her howtos - 

> However, it panics later, saying PAE mode mismatch.

The "xen generic kernel" uses the xen hypervisor without pae, only if you install the "xen server kernel" you need the hypervisor with pae. Install the xen-hypervisor-3.0-i386-pae package and update your grub.conf - but anyhow, if you have an Intel cpu with hyperthreading you will run into this bug: [https://launchpad.net/distros/ubuntu/+source/xen-source-2.6.17/+bug/71348]("https://launchpad.net/distros/ubuntu/+source/xen-source-2.6.17/+bug/71348") 

Another strange behavior: with an i810 onboard graphic card (ICH5x chipset) the system freezes completely.

Xen can be a pain in the ***!

---

### Post by Hendrixski on 2006-12-06
Hey, thanks for posting a link about Xen.  I use MS Virtual PC at work, and it's crap.  VMware is a hundred times better. So I'm eager to try out Xen to see how it compares.  I also want to be ahead of the game since Microsoft seems to be propping up XenSource as a way of marginalizing VMware (because as I said earlier, virtualPC is really bad).

Is there a beginners post about Xen?

---

### Post by Heavy Rail on 2006-12-13
Hello everybody!
I've recently got new PC, it's Core 2 Duo E6400 @ MSI P965 Neo-F.
Due to its famous external JMicron IDE chip the only Ubuntu that could be
set up in that box is Feisty.
So, after installing Feisty, I want to install Xen. There are no amd64 version in repositories, so I've had to install the tarball from Xensource website. I successfully downloaded and installed it, but I can't make it to work.
Here is a snippet of my menu.lst:
```

title           Ubuntu with Xen (2.6.16.29-xen_3.0.3.0)
root            (hd0,0)
kernel          /boot/xen-3.gz
module          /boot/vmlinuz-2.6-xen ro root=UUID=a4e1a3bd-1ad4-4df3-b5bc-b72d3f8749f6

```
When I select corresponding menu item, it boots the kernel, but then panics saying that it can't mount root device.
What should I do for Xen kernel to boot?

---

