---
title: "How to upgrade the kernel"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by LinuxIsAmazing on 2010-10-22
My question is how do I upgrade the kernel in Ubuntu 10.04 to the latest 2.6.26 from Kernel.org?  I am a newbie but very computer literate.  I can follow technical advice.  Thank you all in advance for all of your responses and advice.  :-)

---

### Post by tommcd on 2010-10-22
> **LinuxIsAmazing said:**
> My question is how do I upgrade the kernel in Ubuntu 10.04 to the latest 2.6.26 from Kernel.org? 
Is that a typo? The latest kernel as of this writing is 2.6.36: [http://kernel.org/](http://kernel.org/). Ubuntu 10.04 uses kernel 2.6.32:
[http://packages.ubuntu.com/lucid/linux-image](http://packages.ubuntu.com/lucid/linux-image)
What is your output of: ```
uname -a
```
Anyway, an upgrade (or better yet, a clean install, which is what I prefer) of Ubuntu 10.10 will get you kernel 2.6.35.
If you really want to stay with 10.04 and want a newer kernel, you can get Ubuntu kernels as .deb packages here: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
You can also use **kernelcheck** to get the latest and (hopefully) greatest kernel. See this from Ubuntu-Geek:
[http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html](http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html)
Hope this helps.

And welcome to the Ubuntu forums!

---

### Post by sgosnell on 2010-10-22
As noted, 2.6.26 is a very old kernel.  You can get the newest Ubuntu kernels [here](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  Get the appropriate image kernel for your CPU, and install it with gdebi.  If it causes problems, boot into your previous kernel and delete it.  There is no need to install the headers if you don't intend to do any customization of the kernel, but you can if you wish.

---

### Post by LinuxIsAmazing on 2010-10-22
Yes, I am wrong and embarrassed.  I totally meant to say the Linux kernel 2.6.36.  Either way thank you both very much for all of the helpful information.  I will try out your advice.  Thank you guys again!  :-)

---

