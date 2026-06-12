---
title: "Yet another new kernel - do I need those?"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by Skara Brae on 2011-12-19
Hello to everyone,

Tonight, the Update Manager of my Ubuntu 10.04 LTS install showed a new available kernel: 2.6.32-35-generic.
There are two older kernels in my GRUB list (-21 and -27), which I keep just in case I ever mess things up (I am not at all an expert in Ubuntu/Linux). So far, I have always let the Update Manager install a new kernel.

But I am wondering if I always "need" a new kernel. With this particular computer of mine here, I don't see any difference - on the contrary: I seem to sense that Ubuntu is just this itsy bitsy teeny weenie slower with a new kernel (as compared to the first and/or older kernel(s) ).

So, do I need to install every new kernel?

---

### Post by hhh on 2011-12-19
No, you don't need to upgrade with every new kernel, especially if the kernel you are using has no security holes in it and all your drivers function well. Those are the main 2 reasons to upgrade a kernel, along with newer kernels sometimes offering increased speed and/or stability.

A couple of kernel links...
[http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/stable/linux-stable.git;a=summary)
[http://www.kernel.org/](http://www.kernel.org/)

BTW, as long as you haven't deleted them, you should be able to boot into older kernel versions from your Grub (boot) menu.

---

