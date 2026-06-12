---
title: "grub loader is becoming overrun with different ubuntu options"
date: 2010-07-25
forum: Installation &amp; Upgrades
---

### Post by jredkai on 2010-07-25
so, everytime I upgrade Lucid Lynx a new version of Ubuntu shows up in the grub loader and it's getting kinda carried away, how do I get rid of the previous versions of Ubuntu without messing up the most recent updated version? Thx ahead of time.

---

### Post by ThomasHC on 2010-07-25
I believe [Startup Manager]("apt://startupmanager") can help you hide them, but be careful not to hide too many if you run into problems.

---

### Post by iponeverything on 2010-07-25
Removing previous version of the kernel with synaptic will remove them from the grub menu.

---

### Post by PaulReaver on 2010-07-25
+1 for the synaptic solution.

just make sure your current kernel works well with all your hardware first.

---

### Post by jredkai on 2010-07-25
alright so I'm in the synaptic manager right now and I'm not totally sure how to go about removing the old versions, and also I tried looking for the startup manager and I dont see anything called startup manager....thx so far though for the tips

---

### Post by ThomasHC on 2010-07-25
> **jredkai said:**
> alright so I'm in the synaptic manager right now and I'm not totally sure how to go about removing the old versions, and also I tried looking for the startup manager and I dont see anything called startup manager....thx so far though for the tips

The package is called "startupmanager", the link should install it for you, otherwise install with synaptic or Software Center.

---

### Post by jredkai on 2010-07-25
ok so now I have the startup manager, but I don't see any way to get rid of lucid versions 2.6.32-21, 2.6.32-22, 2.6.32-23 and their safe modes.

---

### Post by PaulReaver on 2010-07-25
> **jredkai said:**
> ok so now I have the startup manager, but I don't see any way to get rid of lucid versions 2.6.32-21, 2.6.32-22, 2.6.32-23 and their safe modes.

why don't you just use synaptic to remove kernels 2.6.32-21, 2.6.32-22 and 2.6.32-23.
grub's menu will be updated and the extra unwanted entries will be removed.

---

### Post by jredkai on 2010-07-25
should I remove the headers for kernels as well, and after removing the kernels will the boot loader be removed too, or will everything still be alright? should I go ahead and re-install grub loader as well just in case?

---

### Post by PaulReaver on 2010-07-25
> **jredkai said:**
> should I remove the headers for kernels as well, and after removing the kernels will the boot loader be removed too, or will everything still be alright? should I go ahead and re-install grub loader as well just in case?


grub won't be removed unless you tell synaptic to remove it. (which would be bad).  grub's config will be updated automatically when you remove the old kernels.:p

you can remove any unused kernels and kernel headers,
keep the latest kernel and matching headers and you should be fine.:D


just be careful when removing the kernels, remove too many and your system is hosed. :-?

hope it helps

---

### Post by oldfred on 2010-07-26
Uninstall extra kernels:-------------------------
In synaptic search for linux-image to choose to delete old ones
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

