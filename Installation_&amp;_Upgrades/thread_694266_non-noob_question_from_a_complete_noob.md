---
title: "non-noob question from a complete noob"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by otheracco on 2008-02-11
Hello, I love Ubuntu, it is totally awesome especially with compiz.  Windows can go bye-bye and take Bill with it.

Anyway, I've got UbuntuStudio running, and very smoothly at that.  But what I would like to do is use 2 kernels on this one install.  Obviously I want to use 2.6.22-14-rt when doing music production, but I'd like to also have a non-realtime kernel for general usage and to be able to switch between the 2 through GRUB.

Is there a way to do this?  Is it safe?  Will I have to install all my prgrams and libraries all over again on the other (new) kernel or will they all just work?

THANKS!
:guitar:

---

### Post by linuxmagick on 2008-02-11
You should be able to add more than one kernel to your grub boot options.  You just have to choose which kernel you want at boot time.  Some programs may have to be reinstalled if they are dependent on a certain kernel version.  I use ndiswrapper for wireless and I have to reinstall it after any kernel upgrades/changes.  That's just one example.  Most stuff should work though without reinstalling.

---

### Post by otheracco on 2008-02-12
How would I go about installing the kernel?  Is it only one file?  It couldn't possibly be THAT simple.  I already know how to link it to the route in GRUB, but I just don't know everything I have to do to make a different kernel available.

Thank you!

---

### Post by zvacet on 2008-02-12
Synaptic>search box type linux-image>select one you want and install it.it will show in grub and you will be able to choose it when you want to.

---

### Post by otheracco on 2008-02-12
OK, got it.  But now when I try to start ubuntu with that kernel, my X doesn't start.  It starts fine under the other kernel.

Does each kernel keep it own libraries, bins, and everything else?  
If it does, is there a directory I can look at them in?

What happens to a kernel when I install something thorugh synaptic.  Does it get compiled or change or somehting?

---

