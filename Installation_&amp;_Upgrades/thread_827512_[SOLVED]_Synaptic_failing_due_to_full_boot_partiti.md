---
title: "[SOLVED] Synaptic failing due to full boot partition"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by dbisdorf0 on 2008-06-12
I've seen other folks with a similar problem to mine on the forums, but their solutions don't seem to be working for me.  Synaptic is (apparently) trying to upgrade my kernel image, but is failing with this message:

```

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic

```

A quick look at my file system shows me that /boot is 100% full.  It's clearly time to remove some of my old kernel images.  However, everyone seems to suggest that the safe way to remove an old kernel image is through the package manager.  If I try to run the package manager, I get:

```

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

```

And if I run dkpg --configure -a, the package manager tries to install the kernel upgrade again:

```

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-18-generic

```

So in order to get my package manager going, I need to clear space in /boot; but I can't clear space in /boot until I get my package manager going.  I seem to be trapped here ... is there any safe way out?

---

### Post by meierfra. on 2008-06-12
Just deleted some of the older kernels. Click on drs305 in my signature for instructions (and all about kernel updates)

---

### Post by meierfra. on 2008-06-12
> ut I can't clear space in /boot until I get my package manager going. 

I missed that point. Just use "sudo rm /boot/*-16-*" to deleted everything related to the 24-16 kernel. (But you still should have a look at "drs305")

---

### Post by dbisdorf0 on 2008-06-12
I was afraid of that.  Fortunately it seems to have worked okay.  I deleted one of my oldest kernel files (specifically "initrd.img-2.6.20-16-generic" ... yes, I've been keeping a lot of old kernels), which cleared enough space to start synaptic and fix it with dpkg --configure -a.  Then I deleted all of the files for the 2.6.20-16 kernel with the package manager, and now all is well again.

Thanks for the rapid reply and the assist!

---

