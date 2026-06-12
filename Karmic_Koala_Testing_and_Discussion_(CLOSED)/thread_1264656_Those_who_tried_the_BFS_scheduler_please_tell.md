---
title: "Those who tried the BFS scheduler please tell"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by knarf on 2009-09-12
If you have tried the [BFS scheduler]("http://ck.kolivas.org/patches/bfs/bfs-faq.txt") please tell the rest of the world what your reason was for trying this new scheduler (misbehaving apps, desktop response time, etc), what your experiences are, what hardware (CPU and memory) you tried it on, if it has behaved in some weird way, etc.

I'll give the kick-off with my humble IBM Thinkpad T23 which comes equipped with a 1.2GHz Pentium III-m and 768 MB of SDRAM. While testing Chromium (the browser) I noticed that it frequently stalls while loading a page in a background tab. The symptom is the same every time: the busy-indicator in the background tab spins while the rest of the tab group that tab is part of is stalled. As Chromium uses individual processes for tabs I thought I'd give BFS a try to see if it changed this behaviour somewhat.

The result seems to be that Chromium is a bit more responsive in that it does not take as long for it to react to user actions (mouse clicks, keyboard activity) BUT the interface itself feels more sluggish: it takes more time to repaint the browser window and the process of repainting seems to be interrupted more often leading to a 'choppy' interface.

GDM seems to be satisfied by this scheduler as the chooser window gets populated with user names much (and I mean much) faster. Before the patch there was a period of some 5 seconds during which GDM seemed to be in deep thought mode, trying to decide which users to show in this list. After the patch the list appears almost immediately. As to whether this change is caused by the scheduler or another update which happened at the same time remains to be seen but that is why it is interesting to know others' experiences.

If you want to try this scheduler you should be aware of the fact that it is in its very early days and most likely contains some bugs. Which might make your system crash. Which means you should not use it on a production system. Which is why you are here in the first place as nobody uses Karmic on production systems, right?

You should also be able to patch and compile the kernel of course, but I guess you already knew that. Some experience in debugging might also come in handy but is not required.

---

### Post by nperry on 2009-09-16
I've got BFS running on my android, [Rom Info Here]("http://en.wikipedia.org/wiki/CyanogenMod")) I've noticed a very speedy response to anything I know do on my phone. I would very much like to run this on my netbook and see what happens then, but never complied my own kernel, I need a basic tutorial to teach myself - any ideas?

---

### Post by MacUntu on 2009-09-16
Maybe Arjan van de Ven's 'Timechart' would be an interesting addition: [http://blog.fenrus.org/?p=5](http://blog.fenrus.org/?p=5)

---

### Post by knarf on 2009-09-16
About compiling kernels: I find it most convenient to totally ignore the official kernel packages and just use make-kpkg in my own updated tree.

In short, just a) clone Linus' tree, b) create a new branch for BFS, c) apply the patch and d) build the binary package.

Somewhat longer:

a) Clone Linus' tree

First read [http://linux.yyz.us/git-howto.html](http://linux.yyz.us/git-howto.html) for an overview of how to use git. If you don't have git installed install it now (sudo apt-get install git-core)

```
cd /usr/src
git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git linux-2.6
```

b) create a branch for BFS

```
cd /usr/src/linux-2.6
git checkout -b BFS master
```

c) apply the patch

First do a test run...

```
cd /usr/src/linux-2.6
patch -p1 --dry-run < wherever_you_stored_the_patch
```

look for errors... none found? Good, then patch for real this time

```
patch -p1 < wherever_you_stored_the_patch
```

d) build a binary kernel package

You need to have make-kpkg installed, this is part of the kernel-package package. If you don't have it, install it now.

You need to configure the kernel before you use make-kpkg to build it. If you are not that well-versed in configuring kernels you'd be well-advised to start with an existing, known working configuration. You'll find the config files for your current kernels in /boot, they are named config-<kernel_version>. Copy the one for your currently running kernel to .config in the root of the source tree:

```
cp /boot/config-2.6.31-10-generic /usr/src/linux-2.6/.config
```

If you want to roll your own config you can of course skip the last step and do a complete make menuconfig (or xconfig or gconfig or config).

Once that is done you can build the package...

```
cd /usr/src/linux-2.6
export now=$(date +%Y%m%d%H%M)
export version="name_for_your_kernel_version"
rm -rf debian
make oldconfig
fakeroot make-kpkg --initrd --append-to-version -$version-$now kernel-image kernel-headers
```

You should now have a few .deb packages in /usr/src named 'linux-image-<kernel_version>-<extra_version_info>_<architecture>.deb' and a similar 'linux-headers' package. Install these using dpkg and you should be good to go.

---

### Post by knarf on 2009-09-16
To make all this even easier here is a script I use to build kernel packages for various systems. Copy it somewhere under the name 'rebuild_kernel' (without the .sh extension which was forced upon me by the braindead file upload logic of this forum), eg.

```
cp wherever_you_downloaded/rebuild_kernel.sh ~/bin/rebuild_kernel
```

Now for every system you want to use this on you make a link to the script using the name 'rebuild_kernel', an underscore '_' and a descriptive name. In this example I have three systems named 't23', 'cbm64' and 'server' for which I use the script.

```
cd ~/bin
ln rebuild_kernel rebuild_kernel_t23
ln rebuild_kernel rebuild_kernel_cbm64
ln rebuild_kernel rebuild_kernel_server
```

For each of these systems you create a kernel config file in /usr/src/LINUX_KERNEL_CONFIG named 'config' followed by an underscore '_' and the descriptive name. As to how you create these config files is up to you, either by copying working examples or creating them from scratch. In the latter case you'd copy it from the kernel source tree where it is present as a hidden file (.config) to the named directory. For this example these would be:

> /usr/src/LINUX_KERNEL_CONFIG/config_t23
/usr/src/LINUX_KERNEL_CONFIG/config_cbm64
/usr/src/LINUX_KERNEL_CONFIG/config_server

Once you have done this you can ask the script for help:

```
rebuild_kernel_t23 -h

	rebuild_kernel_model

	A generic Linux kernel build script which can be used to rebuild
	kernel .deb packages for '_model' systems. Kernel config files
	are kept in /usr/src/LINUX_KERNEL_CONFIG and named 'config_"model"'

	The kernel is built from a git tree which can be synchronised with
	Linus' tree using the -s parameter.

	Kernel packages are named linux-version-model-date (current date
	code is 200909161605). The script knows when to require an initrd by parsing
	the config file. If you don't want an initrd, disable it in the config
	file...

	-h	this help message
	-s	synchronise with Linus's git tree
	-c	configure kernel (make menuconfig)
	-b	rebuild kernel packages
	-i	install kernel packages (only works in combination with -b)
	-I	install kernel packages with --force-all (> 2.6.27, for firmware files))
```

The rest should be self-explanatory. You can change the used paths in the script if you keep your source tree or configuration files elsewhere.

Of course there are many other ways to configure and build kernels, this is just the way I happen to do it on anything Debian-related...

---

### Post by amano on 2009-09-16
Come on. Your post is totally off topic and not related to the karmic development at all. 

Please use more appropriate channels for that.

---

### Post by MacUntu on 2009-09-16
For multicore systems you can export CONCURRENCY_LEVEL=<number of cores + 1> to speed things up.

---

### Post by VMC on 2009-09-16
Thanks for this tip knarf. That's a brilliant idea you have. I'll have to try git. I've heard about it but no personal experience using it. I'm reading the "Hackers' Guide to git" right now.

edit: sometimes someone being off-topic can be a good thing :) I've had a few readings of such and it has help me, when otherwise I would never have found it.

---

### Post by knarf on 2009-09-16
I'd say development-related subjects are on-topic in the 'Development & Programming > Karmic Koala Testing and Discussion' section. Nobody forces you to read this thread now do they?

---

### Post by VMC on 2009-09-16
> **knarf said:**
> I'd say development-related subjects are on-topic in the 'Development & Programming > Karmic Koala Testing and Discussion' section. Nobody forces you to read this thread now do they?
I think you mixed me up with someone else if your last message was directed at me. Your right though, we are in the development arena.

---

### Post by knarf on 2009-09-16
I did not mix up, it is just that the forum is sequential and your and MacUntu's posts got crammed betwixt Amano's and mine... Maybe if there were some way to thread the threads... no, that way lies madness...

---

### Post by taavikko on 2009-09-16
> **knarf said:**
> I did not mix up, it is just that the forum is sequential and your and MacUntu's posts got crammed betwixt Amano's and mine... Maybe if there were some way to thread the threads... no, that way lies madness...

Seriously offtopic, that's why it's better to use "quotes" when responding.

---

### Post by gnomeuser on 2009-09-16
People may find the following LKML thread useful [BFS vs. mainline scheduler benchmarks and measurements](http://thread.gmane.org/gmane.linux.kernel/886319/)

Basically the testing done has uncovered some important areas that got fixed in the mainline scheduler. They are not as I understand merged into the kernel yet but with those fixes you may experience a more consistent latency than normally.

This code is going into the kernel soon I suspect so (probably for .32) so we might be able to convince our darling kernel maintainers to merge it for Karmic. This should significantly improve the desktop experience without trading off server use cases which is important.

---

### Post by dave11980 on 2009-09-23
I just compiled and installed a bfs patched 2.6.31 kernel on xubuntu 9.04 running on a PIII 500 laptop.  I'm seeing maybe a small performance boost, but then again I think this is mainly for dual and quad core machines.

---

### Post by knarf on 2009-09-23
It is not a 'boost' in performance I see, actual performance has probably gone down slightly compared to CFS. What I do see is a slightly more predictable performance in interactive applications like the before-mentioned Chromium browser. I say 'slightly' as it is difficult to quantify these improvements, especially in the presence of multiple variable factors (network latency etc.). I test BFS on a 1.2GHz Pentium III-m by the way...

The best result of BFS' appearance would be the improvement of CFS' performance on small systems. I'll continue testing and comparing for a while to see if those promised improvements in 2.6.32 come true...

---

