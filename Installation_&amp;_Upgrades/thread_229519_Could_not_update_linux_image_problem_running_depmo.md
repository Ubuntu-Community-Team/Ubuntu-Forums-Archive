---
title: "Could not update linux image: problem running depmod"
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by john_d_mchenry on 2006-08-04
Hi,

Synaptic urged me to update today. I had to abort because of the error below (threatening to prevent successful reboot if I did not abort). Any ideas what's wrong?

Thanks,

Jack.

Preparing to replace ubuntu-desktop 0.119 (using .../ubuntu-desktop_0.120_i386.deb) ...
Unpacking replacement ubuntu-desktop ...
Setting up linux-image-2.6.15-26-386 (2.6.15-26.46) ...
There was a problem running depmod. This may be benign,
(You may have versioned symbol names, for instance).
Or this could be an error.
depmod exited with return value 0
depmod got a signal 11
Since this image uses initrd, I am not deleting the file
/lib/modules/2.6.15-26-386/modules.dep. However, there is no
guarantee that the file is valid. I would strongly advice
you to either abort and fix the errors in depmod, or
regenerate the initrd image with a known good modules.dep
file. I repeat, an initrd kernel image with a bad modules.dep
shall fail to boot.
Would you like to abort now? [No]

---

### Post by GadgetsGuy on 2006-08-05
I too had this exact same problem, so would like to know how to fix it? :confused:

---

