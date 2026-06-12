---
title: "kernel compilation"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by eckmann on 2006-07-05
according to this page (which I a m trying to follow even though I have ubuntu breezy and this page is for gentoo)
[http://gentoo-wiki.com/HARDWARE_go7007](http://gentoo-wiki.com/HARDWARE_go7007)

it says to compile the kernel one should do:

make install modules_install

and the guides posted in the forums here say to do the following:

sudo make-kpkg clean
sudo make-kpkg --initrd --append-to-version=-custom kernel_image kernel_headers modules_image

Can someone tell me what the difference is between these two forms of kernel compilation and which is preferred and why?  Thanks.

I have tried both and still can't get the kernel to boot.

Mike

---

