---
title: "Booting into 2.6.16.46 kernel - is it possible?"
date: 2007-08-17
forum: Installation &amp; Upgrades
---

### Post by dscheste on 2007-08-17
Hello all, I am running Feisty on 2.6.20-15 and would like to test something.... Have a piece of code that runs on 2.6.16.46 that SLED is using. 

The idea was to recompile the kernel 2.6.16.46 for ubuntu and than boooth ubuntu into this kernel. and then I wanted to see if this peice of code is going to work on the same kernel in Ubuntu now, not on SLED?

Is it possible to recompile and boot Ubuntu into 2.6.16.46?

Thank you for your insight.

dscheste

---

### Post by ddrichardson on 2007-08-17
Yes. Just add a grub entry for the new kernel then you can boot into either.

---

### Post by dscheste on 2007-08-17
I did, the entry is picke dup, the recompiled kernel is decompressed and then everythign fails to :unable to mount root fs.

Any hints as how to get it working?

---

### Post by ddrichardson on 2007-08-18
Did you include support for the root filesystem?

---

### Post by dscheste on 2007-08-20
Not sure where I specify it. Can you give me a hint as where I have to activate it? I guess in .config file?

---

### Post by ddrichardson on 2007-08-20
No I mean when you were recompiling the kernel if you didn't include support for the filesystem in the kernel or compile a module to do so it would be unable to mount the root filesystem.

Of course it could be something really simple like the grub.lst wntry pointing at the wrong disk.

---

### Post by dscheste on 2007-08-20
Oh, I checked the /boot/grub/menu.lst, all dists are properly specified. Any other pointers?

---

### Post by ddrichardson on 2007-08-21
Did you do a make modules too?

Does the old kernel boot fine? If so then you probably just need to reconfigure and recompile the kernel - including all the filesystems.

---

### Post by dscheste on 2007-08-21
Ups, no, I haven't.

Here's what I have done to recompile the kernel:

```
cd /usr/src
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.16.46.tar.bz2
tar xjf linux-2.6.16.46.tar.bz2
ln -s linux-2.6.16.46 linux
cd linux
make menuconfig
# Configured everything, took .config from a working Ubuntu ysstem - did not help, then .config from a working SLED system - did not help.
make-kpkg clean
fakeroot make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers
dpkg -i linux-image-2.6.16.46-custom_2.6.16.46-custom-10.00.Custom_i386.deb
dpkg -i linux-headers-2.6.16.46-custom_2.6.16.46-custom-10.00.Custom_i386.deb 
nano /boot/grub/menu.lst


```

---

### Post by ddrichardson on 2007-08-21
As laborious as it sounds, going through the menuconfig and loading a config then selecting the missing filesystem support will solve the problem.

---

### Post by dscheste on 2007-08-21
Well, just went through all menuconfig, there was no mention of root file system options. Recompiling now...
Will keep you posted.

---

### Post by dscheste on 2007-08-28
After all the attempts, the system still does not booot. Same error. VFS - cannot mount the root filesystem.

Is there a way for more detailed debugging of this error? Is it a missing module or anything else?
I am kinda lost here right now.

Any help is appreciated.

---

### Post by ddrichardson on 2007-08-28
Post your grub.lst

---

