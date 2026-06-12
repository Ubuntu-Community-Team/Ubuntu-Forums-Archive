---
title: "Ubuntu 18.04  install on old notebook?"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by PDA1 on 2018-04-23
Will 18.04 be compatible with my Dell Inspirion E1505 which has the following hardware?

[SIZE=2]E1505 Inspirion  Memory- 2.5 Gb  [/SIZE] 

 [SIZE=2]Processor- Intel CPU T2050    1.6 GHz x 2              *Centrino Duo*[/SIZE]

 [SIZE=2]Graphics- Intel 945 GM x86/MMX/SSE2[/SIZE]

 [SIZE=2]OS type- 32- bit

SSD- 240 Gb



Thank you,

PDA1


[/SIZE]

---

### Post by PaulW2U on 2018-04-23
> **PDA1 said:**
> OS type- 32- bit
Ubuntu ISO images are now only 64-bit.

Ubuntu MATE, Xubuntu and Lubuntu still produce 32-bit images and would work fine IMO.

---

### Post by Autodave on 2018-04-23
Xubuntu would be much better on there: uses less memory and is faster. All programs available for Ubuntu are also available for Xubuntu.

---

### Post by PDA1 on 2018-04-23
Just found these notes.  Maybe it'll work?

[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

[64-bit PC (AMD64) desktop image]("http://releases.ubuntu.com/18.04/ubuntu-18.04-beta2-desktop-amd64.iso")  Choose this to take full advantage of computers based on the  AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core  2).**  If you have a non-64-bit processor made by AMD, or if you need full  support for 32-bit code, use the i386 images instead.  Choose this if  you are at all unsure.**

---

### Post by PaulW2U on 2018-04-23
> **PDA1 said:**
> Just found these notes.  Maybe it'll work?

[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

[64-bit PC (AMD64) desktop image]("http://releases.ubuntu.com/18.04/ubuntu-18.04-beta2-desktop-amd64.iso")  Choose this to take full advantage of computers based on the  AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core  2).**  If you have a non-64-bit processor made by AMD, or if you need full  support for 32-bit code, use the i386 images instead.  Choose this if  you are at all unsure.**
PDA1, in your first post you **implied** that your hardware was 32-bit and I and Autodave responded appropriately.

Are you now saying that your Dell E1505 is a 64-bit machine? Confused......:confused:

---

### Post by cruzer001 on 2018-04-23
32bit
[https://ark.intel.com/products/27231/Intel-Core-Duo-Processor-T2050-2M-Cache-1_60-GHz-533-MHz-FSB](https://ark.intel.com/products/27231/Intel-Core-Duo-Processor-T2050-2M-Cache-1_60-GHz-533-MHz-FSB)

---

### Post by PaulW2U on 2018-04-23
> **cruzer001 said:**
> 32bit
Thanks cruzer001.
> **PDA1 said:**
> Just found these notes.  Maybe it'll work?

[http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)

[64-bit PC (AMD64) desktop image]("http://releases.ubuntu.com/18.04/ubuntu-18.04-beta2-desktop-amd64.iso")  Choose this to take full advantage of computers based on the  AMD64 or EM64T architecture (e.g., Athlon64, Opteron, EM64T Xeon, Core  2).**  If you have a non-64-bit processor made by AMD, or if you need full  support for 32-bit code, use the i386 images instead.  Choose this if  you are at all unsure.**
No, the images on that webpage are all 64-bit. The text that you quoted should have been removed or amended as Ubuntu no longer issues 32-bit images.

Only the Ubuntu [flavours]("https://wiki.ubuntu.com/UbuntuFlavors") will be issuing 32-bit images for the 18.04 release.

---

### Post by mörgæs on 2018-04-24
If you want a 32 bit Ubuntu 18.04 install it's still possible. You just have to begin with the minimal ISO without the option to do a live boot.

---

