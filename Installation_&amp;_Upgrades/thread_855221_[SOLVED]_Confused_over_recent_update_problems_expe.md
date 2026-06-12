---
title: "[SOLVED] Confused over recent update problems experienced by users"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Tim Silver on 2008-07-10
Hi,

Over the last few days I've read much about people having problems (particularly regarding connectivity, although not all the same) since recent updates have been downloaded

I've just had to re-install Ubuntu 8.04 - kernel 2.6.24-16. I'm a noob but have finally sorted my wifi connection and notice that I have 218 updates available. Anything I should avoid?

---

### Post by PmDematagoda on 2008-07-10
If it's wireless you are worried about then you may want to update everything but the kernel since the kernel is usually what takes care of networking along with Network Manager.

---

### Post by Tim Silver on 2008-07-10
Thanks for info - but just to double check (I am a noob after all ;-) ) - I assume you mean me to un-check the updates named eg 'linux-whatever-2.6.24-19' etc. Are there any others I should look out for?

---

### Post by cpetercarter on 2008-07-10
Updating the kernel does not remove the old kernel. The new kernel will be added to the GRUB menu as the first (defaut) item, with the old kernel or kernels further down the list. This means that, if you find problems with a new kernel, you can always reboot using the old kernel - the one you know will work. You can then try to work out what has gone wrong with the new kernal, or simply use Synaptic to remove it.

---

### Post by Tim Silver on 2008-07-10
OK, thanks for that. I'll update all then and see what happens.

---

