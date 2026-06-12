---
title: "Can You Configure a Kernel Using Ubuntu's .deb Packages?"
date: 2011-12-16
forum: Installation &amp; Upgrades
---

### Post by GreenRaccoon on 2011-12-16
I've been searching all over but haven't been able to find an answer to this.  I was wondering if there's a way to configure/customize a kernel using Ubuntu's .deb kernel packages ([http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/")) instead of the basic Linux kernel from [kernel.org]("kernel.org").  I believe that Ubuntu developers take their kernels from kernel.org and customize them for Ubuntu specifically.  I really don't know that much about compiling kernels (or compiling anything, really), so please bear with me.

I was looking at this guide: [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html").  Basically, it has you extract the .tar.bz2 file from kernel.org into the /usr/src folder and configure it from there.  Then you compile it into a compressed image, compile the modules, install the modules, and install the image.  Then you create an initrd image in /boot and run a "sudo update-grub".

This article shows a different (easier) method: [http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/]("http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/")  After configuring the kernel, it simply has you compile the kernel into two .deb files: a "kernel_image" one and a "kernel_headers" one.  Then you install them, of course.

The three .deb kernel packages that Ubuntu has you install are "linux-headers...generic...all", "linux-headers...amd64" (or i386), and "linux-image...amd64" (or i386).  After installing these packages (which creates two folders in /usr/src), could you configure them from /usr/src?  And then use one of the two above methods to make another kernel?  If this is possible, would I configure the Kconfig file in "linux-headers..." or "linux-headers...generic..."? (I would guess that it's the generic one, but I really don't know)

I don't see why this wouldn't work, but the fact that there are two different folders in /usr/src is messing me up.

---

### Post by MAFoElffen on 2011-12-16
> **GreenRaccoon said:**
> I've been searching all over but haven't been able to find an answer to this.  I was wondering if there's a way to configure/customize a kernel using Ubuntu's .deb kernel packages ([http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")) instead of the basic Linux kernel from [kernel.org]("http://kernel.org").  I believe that Ubuntu developers take their kernels from kernel.org and customize them for Ubuntu specifically.  I really don't know that much about compiling kernels (or compiling anything, really), so please bear with me.

I was looking at this guide: [http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html).  Basically, it has you extract the .tar.bz2 file from kernel.org into the /usr/src folder and configure it from there.  Then you compile it into a compressed image, compile the modules, install the modules, and install the image.  Then you create an initrd image in /boot and run a "sudo update-grub".

This article shows a different (easier) method: [http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)  After configuring the kernel, it simply has you compile the kernel into two .deb files: a "kernel_image" one and a "kernel_headers" one.  Then you install them, of course.

The three .deb kernel packages that Ubuntu has you install are "linux-headers...generic...all", "linux-headers...amd64" (or i386), and "linux-image...amd64" (or i386).  After installing these packages (which creates two folders in /usr/src), could you configure them from /usr/src?  And then use one of the two above methods to make another kernel?  If this is possible, would I configure the Kconfig file in "linux-headers..." or "linux-headers...generic..."? (I would guess that it's the generic one, but I really don't know)

I don't see why this wouldn't work, but the fact that there are two different folders in /usr/src is messing me up.
You realize that the "mainline" PPA is the straight from kernel.org with no alterations nor additions? Standard. "Mainline..." (As explained to me by the kernel team)

When we do dev testing on dev builds, we also test those kernels. On bugs, the launchpad team has me test those and Debian. Last I tested was 3.2-rc5...

Now if you need a specialty kernel, with modules added or security locked down, etc., then compile them in yourself. Otherwise... Why?

---

### Post by GreenRaccoon on 2011-12-17
> **MAFoElffen said:**
> You realize that the "mainline" PPA is the straight from kernel.org with no alterations nor additions? Standard. "Mainline..." (As explained to me by the kernel team)

When we do dev testing on dev builds, we also test those kernels. On bugs, the launchpad team has me test those and Debian. Last I tested was 3.2-rc5...

Now if you need a specialty kernel, with modules added or security locked down, etc., then compile them in yourself. Otherwise... Why?

I took the kernel from the Ubuntu PPA and the one from kernel.org and compared the default configuration.  I thought that they would be different, but they looked the same, as you said.  So I guess I'll just use the one from kernel.org if I want to configure it.  Thanks!

---

### Post by xyzzyman on 2011-12-17
That PPA does have some ubuntu specific things applied. The 3 patch files are sitting right there in the directory, and the third patch changes the .configs. I'm compiling a 3.2-rc6 kernel at the moment using just the first two patches, what I think is the correct ureadahead patch and my custom config file. If ureadahead doesn't work then I'm sticking with my 3.0 series kernel I compiled with my custom config from ubuntu sources. w/o ureadahead takes a minute to boot on my system. 25 seconds with.

EDIT: If you want to build an ubuntu kernel, you might want to follow these instructions just modified a little bit: [http://duopetalflower.blogspot.com/2011/10/custom-64-bit-ubuntu-kernel-31.html](http://duopetalflower.blogspot.com/2011/10/custom-64-bit-ubuntu-kernel-31.html)

Use the tar.gz file listed here: [https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-5.11](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-5.11). It's RC-5 but I'm sure in a few days it'll be superseded by RC-6. Skip the patch settings in the tutorial, and adjust the CPU settings accordingly. I do mine for a Core2, and I build all my drivers into the kernel instead of modules and turn off all the drivers not applicable to me, insert a custom DSDT file for my laptop, and some other tweaks.

---

