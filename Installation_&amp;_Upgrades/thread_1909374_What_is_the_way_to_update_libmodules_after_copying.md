---
title: "What is the way to update /lib/modules after copying VM disk to a different system?"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by vfclists on 2012-01-15
I have transferred the disk of a a Hardyvirtual machine to another virtual machine with a different kernel but there is no equivalent of /lib/modules// on disk. How can the /lib/modules of the new kernel be added to the image to let it boot without error messages?

Is there apt-get command to download the kernel modules of the new kernel from the repository?

/vfclistsGUY

---

### Post by dino99 on 2012-01-15
you should have  it at /lib/modules/

---

