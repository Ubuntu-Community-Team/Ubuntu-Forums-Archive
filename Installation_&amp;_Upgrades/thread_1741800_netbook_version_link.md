---
title: "netbook version link"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by ycwkpp898 on 2011-04-28
I cant get the netbook version to start to download. i can download any of the other ones.

---

### Post by swindler on 2011-04-28
> **ycwkpp898 said:**
> I cant get the netbook version to start to download. i can download any of the other ones.
 
Ditto. Also when you drop into the text-based alternate installer, you can see ISOs and torrent links present for just about everything except the netbook images. 
 
Were the netbook images supposed to be released today as well?

---

### Post by ycwkpp898 on 2011-04-28
I would of thought so. as when i installed the 10.10 version of netbook it comes up with the update for 11.4. which when i try to install errors with connection problem. so thought i would get the iso and install it that way

---

### Post by An Sanct on 2011-04-28
In Natty (11.04) the netbook and desktop versions are merged, so download the ISO, that is suitable for you (32/64 bit) for desktop and it will work on your netbook.

[Additional info here]("http://www.ubuntu.com/testing/natty/alpha2#Ubuntu%20Netbook%20Edition"). (search for "netbook edition")

> Ubuntu Netbook Edition

In  Natty the dedicated Ubuntu Netbook edition is  only used on the  preinstalled OMAP3 and OMAP4 armel images. **On all  other architectures  the Ubuntu Netbook Edition has been merged with the  Ubuntu Desktop  Edition**.  The ARM version is still using the EFL  launcher that we  started the cycle with, we are still integrating the  Unity 2D launcher,  but don't expect it to be the default launcher until  A3.  We are still  using a 2.6.35 kernel as a 2.6.38 kernel is not yet  available for OMAP  4.   



PS. update through 'software update' will fail ... there is a known bug.

---

### Post by ycwkpp898 on 2011-04-28
ty for the info. downloading now

---

### Post by rahulagarwal622 on 2011-05-30
Hi,
 
 This is Rahul Agarwal. I am working on OMAP4430 processor based pandaboard. I have successfully booted pandaboard with **Ubuntu 11.04 netbook**  image. Now I have to enable DMA on both ARM and DSP. I heard from  someone that the DMA code is part of the kernel and should come in the  directories 
arch/arm/mach-omap2/dma.c  
 or
 arch/arm/plat-omap/dma.c
I have checked the directories but couldn't find such file. The  directory has only a Include folder, Kconfig and a Makefile file. Please  help where I can find these files. Is there any update or package which  will install the dma.c and the necessary header files.

Thanks & regards,
Rahul Agarwal

---

