---
title: "Kernel sources?"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by mbobak on 2006-06-06
How do I install kernel sources?  I tried a package called 'kernel-devel', but that didn't seem to do it.  At least, they're not anywhere I looked....which was all over /usr.

Can someone offer me a clue?

-Mark

---

### Post by risings0n on 2006-06-06
i think linux-source

---

### Post by FredB on 2006-06-06
Synaptic / Adept is your friend here.

---

### Post by mbobak on 2006-06-06
Using Synaptic, I searched for linux source, but, if I recall correctly, it only showed 2.4.x kernels.  I tried kernel-devel, but that seemed to only install tools, like gcc and git.

I need the kernel sources for my currently running kernel, 2.6.15-23-386, I think it is....I'm at work, laptop is at home, so I can't verify the version, but it's whatever is standard w/ Dapper Drake.

I say again, can anyone offer me a clue?

Oh yeah, also, I know about synaptic, but what's Adept?

-Mark

---

### Post by mannheim on 2006-06-06
risings0n is correct. Using Synaptic (or apt or whatever), install **linux-source**. I think your confusion comes from the fact that you saw **kernel-source** which is **not** the package you want. (kernel-source will give you legacy source for the 2.4 driver. The linux-source package gives you the latest source for the ubuntu kernel.)

---

### Post by az on 2006-06-06
To build a kernel module, you need the linux-headers package for your kernel.

On the alternate cd, it is right there and part of your sources after you install.  You can install it along with build-essential.

If you installed using the Desktop cd, you have to add the little repository that is on the cd to your list.  Boot into your ubuntu box and then insert the cd.  You will be prompted to ask if you want the packages to be adde to your list of repos.  Say yes and then install linux-headers-386 and build-essential.

That avoids the catch-22 of having to go online to get the packages you need to build kernelmodules for your networking device so that you can go online.

---

### Post by mbobak on 2006-06-06
Thanks for the help, guys!  I'll give it a shot as soon as I get home this evening.

---

