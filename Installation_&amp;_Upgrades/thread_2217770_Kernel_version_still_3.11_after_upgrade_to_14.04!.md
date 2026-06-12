---
title: "Kernel version still 3.11 after upgrade to 14.04!"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by jay_kay2 on 2014-04-18
Hi everybody,

I just upgraded today a laptop from 13.10 to Trusty Tahr but I was first puzzled after first boot that Grub offered only Ubuntu Linux 3.11 or 3.8
Then I checked again using ***uname -mrs*** which gave the result:
[COLOR=#000080]**Linux 3.11.0-19-generic x86_64**[/COLOR]

This doesn't seem right, I thought 14.04 comes with Kernel 3.13!?

I even looked into /boot where I only see this:
[COLOR=#000080]**abi-3.11.0-19-generic         lost+found**[/COLOR]
[COLOR=#000080]**abi-3.8.0-33-generic          memtest86+.bin**[/COLOR]
[COLOR=#000080]**config-3.11.0-19-generic      memtest86+.elf**[/COLOR]
[COLOR=#000080]**config-3.8.0-33-generic       memtest86+_multiboot.bin**[/COLOR]
[COLOR=#000080]**efi                           System.map-3.11.0-19-generic**[/COLOR]
[COLOR=#000080]**extlinux                      System.map-3.8.0-33-generic**[/COLOR]
[COLOR=#000080]**grub                          vmlinuz-3.11.0-19-generic**[/COLOR]
[COLOR=#000080][B]initrd.img-3.11.0-19-generic  vmlinuz-3.8.0-33-generic

[/B][/COLOR]Any ideas?

Thanks a lot!

ps. The rest is runnig very fine btw...

---

### Post by Ubi_one_2014 on 2014-04-18
go to:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14.1-trusty/)

install desired packages regarding yours kernel.
you need the Linux headers.deb linux-headers-generic.deb enad the linux image.deb

reboot
enjoy

---

### Post by jay_kay2 on 2014-04-18
Thanks this is what I did, I installed 3.13.9 which is the 14.04 LTS supposed to be based on.
However I'm not sure if now the regular updates for the kernel will still continue as usual?

---

### Post by su:bhatta on 2014-04-18
If Linux Headers Generic is installed you will get regular updates of Kernel, no problems.
But the release version of Trusty has 3.13.0.24-28 as default Kernel if I am not mistaken.

---

### Post by Ubi_one_2014 on 2014-04-19
> **jay_kay2 said:**
> Thanks this is what I did, I installed 3.13.9 which is the 14.04 LTS supposed to be based on.
However I'm not sure if now the regular updates for the kernel will still continue as usual?

for me, i removed all kernel-3.13 related debian files, in order to avoid kernel updates of older versions

3.14 is running smooth for me, and i am not waiting for kernels that i never use

i am upgrading my kernels manually. Version 3.15 wilol bre relaesed soon

---

### Post by jay_kay2 on 2014-04-19
My problem is, this is my wife's laptop and she wanted a "stable" long term supported version, so I guess with the 3.19 kernel she'll be on the safe side, because if I got this right, this version will be the one Ubuntu will support for a couple of years.
But I'm willing to learn if I was wrong here :-)

---

### Post by Ubi_one_2014 on 2014-04-19
if you want a long term support kernel, pls install 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.17-trusty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.12.17-trusty/)

---

### Post by pfeiffep on 2014-04-19
> **jay_kay2 said:**
> My problem is, this is my wife's laptop and she wanted a "stable" long term supported version, so I guess with the 3.19 kernel she'll be on the safe side, because if I got this right, this version will be the one Ubuntu will support for a couple of years.
But I'm willing to learn if I was wrong here :-)

I respectfully suggest that you examine this [release schedule]("https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule") and stick with whatever kernel is associated according to dates.

My newly installed Trusty on Dell Laptop (specs in signature) > pfeiffep@pete-dell:~$ uname -mrs
Linux 3.13.0-24-generic i686




---

### Post by Ubi_one_2014 on 2014-04-19
for me:

```
kubuntu:~$ uname -mrs
Linux 3.14.0-031400-generic x86_64
```

---

### Post by Chad_Wagner on 2014-04-19
I would check if you have the linux-image-generic metapackage installed, this package is usually the one that points to the latest kernel for your distribution.

---

