---
title: "kernel 2.6.20-16"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by joelotz on 2007-10-15
OK, this is going to sound really stupid, and it is. During a 30hour thesis crunch I deleted the vmlinuz-2.6.20-16-generic file in my /boot/ folder. I know I'm going to get crap and I deserve it.

Now (of course) my box won't boot and I need to turn in my thesis. My question is what do I do? If I find that file can I just put it back in the directory a viola? I've tried googling and even downloaded the kernel from kernel.org but I can't find that file.

Help:(

thanks!

---

### Post by codejunkie on 2007-10-15
> **joelotz said:**
> OK, this is going to sound really stupid, and it is. During a 30hour thesis crunch I deleted the vmlinuz-2.6.20-16-generic file in my /boot/ folder. I know I'm going to get crap and I deserve it.

Now (of course) my box won't boot and I need to turn in my thesis. My question is what do I do? If I find that file can I just put it back in the directory a viola? I've tried googling and even downloaded the kernel from kernel.org but I can't find that file.

Help:(

thanks!

boot using the ubuntu desktop cd, mount your ubuntu partitions, and chroot into them. then use apt-get to reinstall the kernel if you need any help doing that let me know and i'll walk you through it.

---

### Post by joelotz on 2007-10-15
OK, I've made it pretty far but i'm stuck on the "apt-get to reinstall the kernel". I've upgrade all my packages but not the kernel.

I've used "sudo apt-get update && sudo apt-get upgrade-dist"

Am I on the wrong path?

thanks

---

### Post by codejunkie on 2007-10-16
> **joelotz said:**
> OK, I've made it pretty far but i'm stuck on the "apt-get to reinstall the kernel". I've upgrade all my packages but not the kernel.

I've used "sudo apt-get update && sudo apt-get upgrade-dist"

Am I on the wrong path?

thanks

once you have chrooted into the ubuntu partition you need to remove the old kernel first so try running ```
sudo apt-get remove --purge linux-image-generic*
``` when it finishes this should have completly removed the kernel and all kernel packages related to that kernel image so you will get a clean install.

now reinstall the kernel ```
sudo apt-get install linux-image-generic
```

---

