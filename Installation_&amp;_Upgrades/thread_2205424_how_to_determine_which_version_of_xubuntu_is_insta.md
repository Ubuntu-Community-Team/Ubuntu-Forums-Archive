---
title: "how to determine which version of xubuntu is installed (32 or 64 bit)"
date: 2014-02-13
forum: Installation &amp; Upgrades
---

### Post by sam_baker2 on 2014-02-13
Is there a way to determine which version of xubuntu is installed 
on my laptop?

I have an Intel laptop and on the xubuntu webpage there are two 
different types of xubuntu one can install:

(from the xubuntu website )
```

[PC (Intel x86) desktop CD]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.04/release/xubuntu-12.04.3-desktop-i386.iso")  
For almost all PCs. This includes most machines with  Intel/AMD/etc type processors and
 almost all computers that run Microsoft Windows, as well as newer Apple Macintosh systems
 based on  Intel processors.  Choose this if you are at all unsure.

[64-bit PC (AMD64) desktop CD]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/12.04/release/xubuntu-12.04.3-desktop-amd64.iso")  Choose this to take full advantage of computers based
 on the AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core  2).
If you have a non-64-bit processor made by AMD, or if you need full
 support for 32-bit code, use the Intel x86 images instead.

```

  Will both versions work on either an Intel or AMD machine?

---

### Post by plucky on 2014-02-13
> Is there a way to determine which version of xubuntu is installed
on my laptop?

Open a terminal and type ```
uname -a
``` and it will say > x86_64 x86_64 x86_64 GNU/Linux if 64 bit or > x86 GNU/Linux  if 32 bit.

> Will both versions work on either an Intel or AMD machine? 


x86_64 will only work on 64 bit processors. (Intel and AMD)

x86 will work on both 32 bit and 64 bit processors.(Intel and AMD)

---

### Post by sam_baker2 on 2014-02-13
I have a laptop with an Intel core i3 chip.
uname -a gives me this:
```
 x86_64 x86_64 x86_64 GNU/Linux   
```
so I suppose it is a 64 bit capable chip.


I want to set up an external HD with xubuntu on it
that I can interchangebly swap from the laptop ( Intel i3 chip )
to a desktop that has a AMD 64 chip in it.
I would like the external HD to have the AMD version
on it, but will that run on the laptop ( Intel i3 )?

---

### Post by fantab on 2014-02-13
AMD was the first to make 64bit processors AFAIK, which was later followed by other manufacturers like Intel. So 64bit is written as 'amdx86_64', which does NOT mean that it is AMD related only and neither does 'x86' mean Intel only.

Now, when you install xubuntu on an ext-hdd, say from AMD powered computer, xubuntu will install configuring hardware native to AMD computer.
The most important Hardware to note here is the Graphics Driver. If you have different Graphics on Intel machine then you will have problems. I am not sure, but you will have to install both Graphic Drivers.
If you run into 'black screen' issue then boot with '[NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997")' kernel parameter and later installl the required Graphics driver.

Remember you must install GRUB (Bootloader) to the Ext-HDD only. USB boot must be enabled in BIOS/UEFI and USB devices must boot first.

EDIT: You may also face issues if one PC boots in UEFI and other in BIOS... as the boot files will be different and placed in different locations...

---

### Post by sudodus on 2014-02-14
> **sam_baker2 said:**
> 
I want to set up an external HD with xubuntu on it
that I can interchangebly swap from the laptop ( Intel i3 chip )
to a desktop that has a AMD 64 chip in it.
I would like the external HD to have the AMD version
on it, but will that run on the laptop ( Intel i3 )?

As long as you don't install any proprietary drivers, Ubuntu is portable between computers.

And if you need a proprietary driver for the graphics chip or wifi chip, it can be installed and removed when necessary, while the rest of the system can remain. Often, but not always, the built-in free drivers work. An installed system is as portable as an Ubuntu desktop install CD/DVD/USB drive.

-o-

There are limits though (within Intel/AMD systems, which were called IBM compatlble PCs during the previous milennium).

1. 64-bit operating systems need 64-bit computers, while 32-bit operating systems work with both 32-bit and 64-bit computers.

2. UEFI works only with 64-bit operating systems and the GUID partition table (GPT).

-o-

And of course, other architectures (for example PowerPC or arm) need other code (completely other code, compiled for that particular architecture).

---

