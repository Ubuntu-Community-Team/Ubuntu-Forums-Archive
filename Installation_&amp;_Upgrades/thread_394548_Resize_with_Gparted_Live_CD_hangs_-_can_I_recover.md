---
title: "Resize with Gparted Live CD hangs - can I recover?"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by Yob on 2007-03-27
When I first installed Ubuntu I made 3 partitions:
root 5 GiB
swap 1 GiB
home - rest of hard disk.

Now i've run into trouble upgrading since the root partition is all but full.
So i downloaded the gparted live cd, freed an additional 15GiB from my home partition and added those to my root. 
This was to take 4 hours so i went to bed. This morning when i got up it seems the process has hung.
It claims to have moved 38GiB, but there seems to be no activity going on.

Any ideas what do to? I guess rebooting the machine will mean destroying data etc? Can i restart the process somehow?

---

### Post by Yob on 2007-03-27
I hit cancel and started over - will update thread when i know the result..

---

### Post by Yob on 2007-03-27
So, i'm stuck and need help.
I've managed to reboot my machine so no data loss so far.
However when i run Gparted Live CD it shows that my /home partition has been resized. That's good, however, when I run e check on it, it says that:
The level of the node (0) is not correct, (1) expected the problem in the internal node occured (52245384), whole subtree is skipped block 50200581: The level of the node... etc
The on-disk and the correct bitmaps differs. Will be fixed later.

It's a reiserfs filesystem btw.

I've tried searching the Gparted forum - no luck, Googled - just made me more confused..

Any help will be greatly appreciated ;)

---

