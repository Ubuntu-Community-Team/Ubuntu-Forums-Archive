---
title: "Tips for making a LiveUSB faster"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by blazemore on 2010-01-12
Hi all,
I'm due to try out the new Mint 8 KDE over the next couple of days, and I want to know if there's a way I can make my LiveUSB perform to the best of its abilities.
I'm thinking in terms of filesystem to use, should I use unetbootin to make it, or dd?
If dd, what's the best blocksize?

Things like that.
Any hints?

Thanks!

---

### Post by kerry_s on 2010-01-12
use the ubuntu usb-creator, it was made for just that.

---

### Post by blazemore on 2010-01-12
Yes, unetbootin, ubuntu usb creator, whatever.
I mean what filesystem should I format my flash drive? should I make a partition (apparently smaller partitions are faster than larger - check me)

---

### Post by kerry_s on 2010-01-12
just the normal fat32, when you use the usb-creator there is a slide bar to pick how much space you want to use for persistent storage, this allows you to save changes even update if theres enough space, you can install stuff, remove stuff, etc...

unetbootin only creates a live installer. there is no option to save changes.

---

### Post by blazemore on 2010-01-12
Okay I've been researching and it seems any changes are negligible, as the bottleneck is the controller on the stick, rather than the speed of access to the flash itsself.

---

### Post by kerry_s on 2010-01-12
with the persistent setup, you can tweak it like a normal install, use lighter alternatives, even say a fast window manager, you can make it feel faster, if not be faster. play with it, you'll see.

---

### Post by C.S.Cameron on 2010-01-12
In my experience doing a full install, (using the install option from the Live CD or Live USB), results in a faster system than using an image install, (produced with unebootin or usb-creator).
Boot and shutdown times however may be a bit slower.
I understand formatting in ext4 may also have some speed advantages.

---

