---
title: "Problems after compiling kernel"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by 64mgb on 2007-01-31
I've recompiled my kernel (2.6.19.2) a couple of times.  Each time, when the compile is done and I do the "depkg -i xxx" on the image file, I get a warning that since I'm compiling the same kernel as what is already there, I should move /lib/modules/2.6.19.2/kernel out of the way, so I did this from /lib/modules/2.6.19.2:

sudo mv kernel kernel.old

Now, after rebooting, when I try to load a modified version of IVTV (with extra module parameters that the original version doesn't know about) with sudo modprobe ivtv, it tries to load the version from the "old" kernel:

/lib/modules/2.6.19.2/kernel.old/drivers/media/video/ivtv

Since the old version does not have the new parameters it fails.  Why is it trying to load from the "old" tree instead of the new one?  And how do I change it?

Thanks,
Rich

---

### Post by p!=f on 2007-01-31
Do you also make modules for your new kernel? Do you use kernel-package (make-kpkg) to create your new kernel? If so be sure to add modules_image as a parameter for make-kpkg.
```

sudo make-kpkg --initrd ... kernel_headers kernel_image modules_image

```
Also try to run
```

sudo depmod

```

---

### Post by 64mgb on 2007-01-31
Thanks for the input, p!=f.  I am at work right now, so can't try this right now but will look at it tonight.  I follow the instructions in the Master Kernel Thread to the letter:

[http://ubuntuforums.org/showthread.php?t=311158&highlight=master](http://ubuntuforums.org/showthread.php?t=311158&highlight=master)

Rich

---

### Post by glennric on 2007-02-12
Another thing you might try is when compiling the kernel type the following:

```
make-kpkg -initrd --revision=custom1 --append-to-version=-custom1 kernel_image kernel_image modules_image
```

custom1 can be pretty much whatever you want, but I believe it has to be all lower case and contain a number for the append-to-version option.
The append-to-version option will add -custom1 (or whatever you use) to the end of the version reported by uname -r, as well as to the director in /lib/modules.  The revision option will add custom1 to the version number to distinguish it from your previous version known by apt (or synaptic).

---

