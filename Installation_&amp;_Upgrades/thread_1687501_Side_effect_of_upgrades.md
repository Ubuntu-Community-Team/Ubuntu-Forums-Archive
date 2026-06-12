---
title: "Side effect of upgrades?"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by elkingrey on 2011-02-14
Hello,

I suspect that the problem I am about to explain is a result of upgrades, possibly from disk image upgrades.

You know how when you boot your computer, you come to a screen that allows you to choose which operating system you want to boot, Windows, Linux, etc? Well, the Linux option repeats 4 times. That can't be right. Is there any way to fix that so that it only shows once? 

I suspect it's also causing my computer to work harder. Here's why.

When I used to use Windows, my computer's fan was constantly revving up and working overtime. When I first switched to Linux, the fan was as quiet as a mouse. Over time, it's gotten to now it's revving up a lot all of the time. What's going on here? 

Any help would be much appreciated.

---

### Post by zvacet on 2011-02-14
For entries for linux in grub is normal.You have two kernels installed and each of them have recovery mode.It is good to have two kernels in case something don´t work properly with new kernel.If you tested and you are sure that new kernel work as it should you can remove old kernel from synaptic.In synaptic search box type** linux-image** and you will see all installed kernels.Remove one with lower number.

---

### Post by An Sanct on 2011-02-14
I assume, that the four repeated Linux options are something like this:
```
ubuntu 8.04, kernel 2.6.24-17-generic
ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
ubuntu 8.04, kernel 2.6.22-14-generic
ubuntu 8.04, kernel 2.6.22-14-generic (recovery mode)
```

This is fine, it just means, that the kernel you use has been updated, but for security sake, the old kernels have been left, so you can choose from them if you aren't pleased with the new one.

There is a [HOWTO]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/") here, but I personally would leave at least one older kernel.

This is not making the computer work harder at all, its just an option you can choose from.

---

