---
title: "Is the fuse package fully installed by default?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by penredhill on 2010-01-20
Hi,

I am trying to install a package (owfs) which requires fuse (user space file system). Fuse requires the fuse kernel module. Fuse seems to be persent in my Karmic (9.10) system, but modprobe fuse says "FATAL: Module fuse not found". I am not very familiar with kernel modules, but I looked in /lib/modules/2.6.31-17-generic/kernel/fs/fuse and found a file named cuse.ko, where I expected to find fuse.ko. 

It seems as if fuse is nearly, but not quite installed, or is there something I have not understood.

uname -r says 2.6.31-17-generic.

Any help would be appreciated.

David

---

### Post by penredhill on 2010-01-22
Problem solved.

Firstly, fuse is compiled into the kernel nowadays, and thus isn't a loadable module.

Secondly, the reason why the owfs install wasn't working was the need for additional packages to be installed (such as fuse-dev and usb-dev).

---

### Post by jkugler on 2010-05-05
Howdy!

I saw your message was dated recently (January).

I am trying to find the owfs package, and am not seeing anything in the repositories.

[http://packages.ubuntu.com/search?keywords=owfs](http://packages.ubuntu.com/search?keywords=owfs)

does not return anything meaningful.

What is the package name you were using to install?

Thanks!

---

### Post by penredhill on 2010-05-11
Hi,

The owfs package is not downloadable from ubuntu as far as I know.

I believe I got it from [http://owfs.org/](http://owfs.org/).

It took a while to sort it all out. You need the fuse-dev and usb-dev (if you are planning to use USB interfaced 1-wire devices) packages which are available from ubuntu.

It is now working reliably and helping to monitor electricity, water and gas usage around my house and garden. Hopefully soon, also greenhouse temperatures.

I hope it works for you

David

---

### Post by jkugler on 2010-05-11
Yeah, I did figure that out, and got the correct devel libs installed. Seems to be working well.  Hmm...water and gas usage, eh? I take it OneWire does flow meters as well? That would be really cool. I'd love to monitor daily water and fuel oil usage.  Now, if they did electrical meters, that would be ideal. :)

---

