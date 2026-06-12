---
title: "Readahead and DKMS"
date: 2008-09-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phelin4 on 2008-09-16
Hi,

this might be an issue with Hardy or Gutsy also, but I jumped straight from Feisty to Intrepid with my HTPC when I bought a new Intel G35 based motherboard and for me this is an issue with Intrepid :) 

Anyways, I use lirc in order to use remote control with the HTPC. Lirc modules are now inserted by DKMS. I don't really know how DKMS works, but it results in working lirc setup. So that's ok. But what strikes as strange to me is the fact that after I profiled my boot sequence I see that file /etc/readahead/boot contains all the Linux headers and all lirc source files. Does that mean that the lirc modules are built anew on every boot? It looks like not, since I can see that for example module /lib/modules/2.6.27-3-generic/kernel/ubuntu/lirc/lirc_imon/lirc_imon.ko is the several days old, so it has not been replaced. But why are those files in the readahead list then?

And I would also appreciate if someone could give me a short description on how the DKMS actually works in real life.

---

### Post by plun on 2008-09-16
Perhaps something to start with..

[http://linux.dell.com/projects.shtml#dkms](http://linux.dell.com/projects.shtml#dkms)

We are trying to figure this out for nVidia drivers so
everything is new... :)

Perhaps someone knows more about Lirc ?

---

### Post by TheMono on 2008-09-16
That is odd. DKMS does check on every boot that all is well... but you are right that it certainly doesn't recompile every boot!
I agree with the other poster, that you are likely to get a better answer from the dev mailing list at Dell or something.

---

### Post by phelin4 on 2008-09-17
It reallly looks like DKMS will check for the need to build a module on every boot, just like you said, and because of that profiling to boot sequence added all linux header and lirc source files to readahead list. I tried removing DKMS (which removed the lirc sources too) and it left me the already built modules. After that I reprofiled and now the boot is a second or two faster.

---

