---
title: "Install from USB, to USB"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by pokepal101 on 2013-05-08
So here's what I want to achieve: a bootable Ubuntu USB. Hard-drive style. No live-USB shenanigans.
The 'problem' is I only have the one USB to spare, and I *really* don't want to have to burn a CD/DVD (I'm just that cheap).

So my problem is this: Is there a way I can _install_ (_not_ live-USB-ify) Ubuntu to my USB, without
[LIST]
[*]access to another USB
[*]access to an existing Ubuntu installation
[*]installing Ubuntu to my computer
[*]burning a CD/DVD
[/LIST]

I was thinking something along the lines of:
[LIST]
[*]create two partitions on the USB
[*]turn the first partition into a live-USB
[*]install Ubuntu to the second partition (by booting off of the live-USB partition)
[*]delete the first partition and resize the second (now only) partition
[/LIST]
but I'm open to other methods as well.

---

### Post by Irihapeti on 2013-05-08
In theory, your proposed method could get you as far as deleting the first partition on your USB.

Then, though, you'll need to move the beginning of your non-live partition to use the space left by the first partion. I've tried that a few times - occasionally it works, but more often than not it gets hopelessly messed up. Even if it works, it takes ages to do, and that means it's more vulnerable to the power going off or something like that. In any case, you'd need to boot off something other than your USB so as to be able to resize the partition - someone else's Ubuntu install, for example.

It's going to be much easier to just install directly from a liveCD. You may find that you can use a rewritable DVD or CD for your live system, which means that you can re-use your disk afterwards. I've had no trouble with them, though I'm not speaking for everybody.

---

