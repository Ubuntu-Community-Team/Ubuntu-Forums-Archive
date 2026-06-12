---
title: "Update 2.6.24-19 Gives Grub Error 18"
date: 2008-08-28
forum: Installation &amp; Upgrades
---

### Post by eiffel on 2008-08-28
Last night I auto-updated my laptop to kernel 2.6.24-19

Now when I bootup I get the Grub error:

Error 18: selected cylinder exceeds maximum supported by BIOS

I've tried booting older and safe mode kernels and changing the boot order of my devices etc with no joy.  It always takes me back to that error and I simply can't boot.

Nothing else has changed apart from doing the update, so I'm stumped.

Any help much appreciated.

---

### Post by eiffel on 2008-08-29
Any ideas - I'm stuck.

The laptop was working fine - I do an update and now it's a brick.

I've googled around a whole bunch of threads but I can't find anywhere to get started on this. :(

---

### Post by Pumalite on 2008-08-29
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)
The solution; depending on your harware and BIOS, might be to make a small /boot partition at the beginning.

---

### Post by eiffel on 2008-08-30
Thanks for your post.  It looks like in my attempts to sort this out I've managed to wipe that drive - at least gparted is showing the whole drive as 'unallocated' - so a fresh install it is :(

I still don't understand what's going on.  It's a fairly new laptop with a new harddrive - why would doing a simple update make it unusable?

O well, I have a fairly recent backup :)

---

