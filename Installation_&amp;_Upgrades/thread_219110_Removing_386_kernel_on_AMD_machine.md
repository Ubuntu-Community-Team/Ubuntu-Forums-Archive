---
title: "Removing 386 kernel on AMD machine?"
date: 2006-07-19
forum: Installation &amp; Upgrades
---

### Post by dwasifar on 2006-07-19
This machine was originally installed with Breezy using the install disc's 386 kernel.  I have since used Synaptic to change it to K7 kernel, and upgraded to Dapper.  Current kernel is 2.6.15-26-k7 (i686).  But now every time Ubuntu offers me an upgrade, it wants to upgrade both kernels. 

Is there a reason I should continue to maintain the 386 kernel on this system, or can I safely purge it out and just keep the K7 images?  What's the safest way to go about that?

Thanks in advance.

---

### Post by chadk on 2006-07-19
I believe you just open Synaptic and search for "Linux image" and then remove the references to the kernel(s) you no longer want.

---

### Post by dwasifar on 2006-07-19
That's all there is to it?  I'm worried about damaging some sort of dependency.

---

### Post by dwasifar on 2006-07-19
Well, it seems to have worked.  I was a little nervous about deleting kernels but everything looks fine and the 386 entries are gone from my GRUB menu.

Thanks.

---

