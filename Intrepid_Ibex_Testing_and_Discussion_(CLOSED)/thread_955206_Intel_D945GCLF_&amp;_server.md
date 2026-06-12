---
title: "Intel D945GCLF &amp; server"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by prosonik on 2008-10-22
Hi Everybody,

I'm trying to get D45GCLF up with Intrepid SERVER, and I'm having some problems. i have it fully tested under a upgrade-from-hardy desktop install.

1)I want to create run it off a usb driver. Is there any easy method? I used virtual box, and installed it a live persistant USB. It seemed to work, but I'm running into the realtek driver issue. There is no driver connectivity, with the default kernel.

2) I was hoping that the kernel had the REALtek driver fixed, so I tried to upgrade to the latest kernel, but it blew up (sorry, I don't have the dump, but it's on boot). I booted the flash dive under qemu, and upgraded the kernel using qemu. Returning the drive to the D45GCLF, the system barfed on boot, just after grub. (I think) When i selected the original kernel it worked, but again, no network connectivity.

So i guess my question is two fold.

1. Is there a quick way to create intrepid server persistent live-usb
2. Does anybody have the D45GCLF up and running intrepid server? How did you install the realtek driver issue.

thanks
pro

---

