---
title: "USB booting - kernel compilcation"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by IdealVithVodka on 2007-08-21
Hi,


I have installed a debian system on a USB stick. It boots fine using the distribution kernel.
I have recompiled the kernel for my mashine and this time it doesn't like to boot from my USB stick anymore. I get a kernel panic that he can;t mount the root filesystem (ext3 support compiled into kernel)

I have added the usb support, the usb storage and some ide drivers (all build in to the kernel).

Does anyone have a list of the things that must be built into the kernel so it will boot properly ?

On my distribution kernel it boots from root=/dev/sda1

I'm using kernel : 2.6.22.3  for the compilcation


With Kind Regards
Matt

---

### Post by 1/0 on 2007-08-21
I don't have a list for you, since that depends on what components are in your computer. I suggest you compare the kernels to e/o. As you know they are usually located in /usr/src/linux-version/.config.

Also when you booted with the kernel that works, try to see what modules are loaded and what's needed.
```
lsmod
lspci
```

That will give you a hunch of what's needed. It could also have to do with the root label (root=LABEL=/dev/sd..) or that GRUB doesn't point at the correct kernel in /boot/. Is ext3 compiled in the kernel or as module?

---

### Post by IdealVithVodka on 2007-08-21
> **1/0 said:**
> I don't have a list for you, since that depends on what components are in your computer. I suggest you compare the kernels to e/o. As you know they are usually located in /usr/src/linux-version/.config.

I know it depends on my components. But I just need to boot from the USB as the rest of the hardware I know. You think that a default compilation with no changes will work proper for me ?



> **1/0 said:**
> Also when you booted with the kernel that works, try to see what modules are loaded and what's needed.
```
lsmod
lspci
```


I tried the lsmod - it did give me some results. But still I cant check if I have compiled it properly cause the system hangs (the compiled kernel). I'll try to compile with the default .config and tell you whats up.

> **1/0 said:**
> 
That will give you a hunch of what's needed. It could also have to do with the root label (root=LABEL=/dev/sd..) or that GRUB doesn't point at the correct kernel in /boot/. Is ext3 compiled in the kernel or as module?

The ext3 is compiled into the kernel(not a module). Grub points to the correct image (double checked that) and the root label is the same as in the original distribution kernel.


Ahhh.. and one more question : When you have the distribution kernel - is it compiled using the /arch/i386/.config file ?  U can use the make defconfig to use the default config file that is provided with the source code.



Matt

---

### Post by 1/0 on 2007-08-21
When you say it boots fine from the distribution kernel, do you mean from USB or HDD? I thought you booted from USB in both cases. The default kernel is usually compiled with extensive support. It might be worth trying to boot from that other one and then start to take unnecessary modules away. 

But if it hasn't worked at all with the USB then it might be something else. 

I don't know if you'll find anything useful in /arch/i386. Maybe the make defconfig is a good idea. The config is usually compiled to: /usr/src/linuxversion/.config

---

### Post by MQMike on 2007-08-21
External HD, booting from:
[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
Case:  [http://ubuntuforums.org/showthread.php?t=506179](http://ubuntuforums.org/showthread.php?t=506179)
[http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub](http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grub)

He's got some list.

---

### Post by IdealVithVodka on 2007-08-21
> **1/0 said:**
> When you say it boots fine from the distribution kernel, do you mean from USB or HDD? I thought you booted from USB in both cases. The default kernel is usually compiled with extensive support. It might be worth trying to boot from that other one and then start to take unnecessary modules away. 

I have installed the system on a USB stick. I have no HDD attached to the mobo.
The kernel provided with the distro works fine. I have the list of modules it loads but still... no success...

> **1/0 said:**
> 
I don't know if you'll find anything useful in /arch/i386. Maybe the make defconfig is a good idea. The config is usually compiled to: /usr/src/linuxversion/.config

Well, I have tried the /arch/386 - nothing special there as it compiles most things to the kernel (no modules or I haven't noticed any...). It detected the stick but no further success.

I'm trying to compile a 2.6.22.4 kernel with the /usr/src/2.6.22.4/.config  file. Probably it will be the same as usual but I'll give it a try.


Matt

---

### Post by MQMike on 2007-08-21
[http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grubFirefoxHTML\Shell\Open\Command](http://ubuntuforums.org/showthread.php?t=80811&highlight=Success+breezy+booted+from+USB+grubFirefoxHTML\Shell\Open\Command)

This looks good, too.

---

### Post by IdealVithVodka on 2007-08-22
Will give that a try... Thanks

---

