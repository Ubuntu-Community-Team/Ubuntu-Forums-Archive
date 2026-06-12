---
title: "default timer tick"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by stoive on 2007-11-08
Hi all
I am running mythbuntu and I have a winfast dtv1000 tuner card which does come with a remote that doesn't work.

I got it working yesterday to receive IR inputs but because of the timer tick set as default being 250hz, the buttons end up being 'stuck down' so to speak.

i did recompile the latest kernel yesterday, 2.6.23, but upon reboot i lost support for my wireless network usb stick, and ubuntu wouldn't let me go to the restricted drivers manager until i have installed 2.6.23 restricted drivers package manager! which didn't seem to exist...

can someone tell me how i can preferable go about changing the cpu timer tick to 1000hz without recompiling the kernel

or

where did i go wrong, should I just recompile the kernel version that ubuntu is running with ? will that allow me to keep my old settings and drivers which were working fine ?  is there an ubuntu repository for the specific kernels that I should've done ?  i got the 2.6.23 kernel from [www.kernel.org](www.kernel.org)

---

### Post by BoneKracker on 2007-11-08
What you're doing isn't "wrong", but it will probably be much easier for your to use the ubuntu kernel sources, which are in the repository.

If you haven't read it, there is information about compiling your own kernel in these forums and in the other documentation sources (wiki, etc.).  I haven't looked at in a long time so I can't point you directly to it.  Maybe someone else will chime in, but you can probably find it easily by searching.

---

