---
title: "Kernel Configuration"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by andy101 on 2005-11-29
I am trying to check and possibly change the size of stacks used in the kernel.
How do I find out the current size of stacks used by the kernel? I installed from the Ubuntu 5.10 CD using default settings.
I am having problems with ndiswrapper and one of the posssible solutions is to increase the stack size to 8k or 12k. I have been told it involves something to do with changing 'CONFIG_4KSTACKS', where/how do I changew this and does it mean i have to recompile the kernel? If so how do I do that and will it involve losing everything from my Ubuntu install (I have a dual boot atm).

I also would like to be able to check wether SMP is set and possibly disable that aswell, I assume the procedure for this is very much similar to the above change.

Thanks

---

### Post by g-a-c on 2005-11-29
To find out what the current kernel you're running has, this command should work:

```
grep 4KSTACKS /boot/config-`uname --kernel-release`
```

To check for SMP support:

```
grep SMP /boot/config-`uname --kernel-release`
```

Not sure how much experience you have of kernels etc but there's a wiki article on recompiling the kernel [here](https://wiki.ubuntu.com//KernelHowto), or another [here]() which will enable you to change both stack size, and SMP ability.

---

