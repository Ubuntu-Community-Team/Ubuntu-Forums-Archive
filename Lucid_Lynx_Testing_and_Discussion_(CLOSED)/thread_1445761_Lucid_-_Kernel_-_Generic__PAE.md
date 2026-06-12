---
title: "Lucid - Kernel - Generic / PAE"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by churfsan on 2010-04-03
Hello,

I installed Lucid Beta 1 at my home, and in the boot-up grub screen it says "Linux Kernel ..... - pae". I installed the same in my office computer, and there it says "Linux Kernel ...... - generic".

I did not make any specific selection during installation, and both were installed with the same disk. 

My home computer is having ATI chipset, while office computer is having Intel chipset.

What is the difference - pae and generic, and why the different installations?

Thanks
Chufsan

---

### Post by tommcd on 2010-04-03
Does the home computer with the ATI chipset have more than 3.6GB of memory? If so, then Lucid will automagically install the PAE kernel, see this:
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)
> ... Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages is not present on the CD.

Here is a thread discussing the PAE kernel in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1381288](http://ubuntuforums.org/showthread.php?t=1381288)
For all the tech details about PAE, see this:
[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
I asume you installed the 32bit version of Ubuntu. Is that correct?
The 64bit version is capable of addressing much more memory, so PAE is not needed there. It also (theoretically) maximizes performance for 64bit CPUs.
I have (so far) always used 32bit Ubuntu for what it's worth. I am using 64bit Slackware on my desktop though.
Hope this helps. I learned a thing or two looking this up!

---

