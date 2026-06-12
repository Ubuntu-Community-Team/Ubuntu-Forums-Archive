---
title: "LVM and manual partition"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by johnarild on 2009-11-19
Hi, I want to install a fresh copy of Ubuntu9.10amd64 but I want my whole filesystem encrypted. This was easy with the alternative CD using the Guided encrypted LVM option, but I find the manual partitioning to be unusable. Is there a way to do the graphical installation with LVM and encryption support or a way to do partitioning easier on the text based install?

---

### Post by geurt on 2009-11-19
First of all:
It is not possible to encrypt the whole filesystem. The kernel needs to be loaded before things like the encryption of a filesystem work.

I don't know how the graphical ubuntu installer looks like. I allways use the alternative installation discs to install the ubuntu operating system.

To use LVM, please look at:
[http://www.howtoforge.com/encrypted-root-lvm]("http://www.howtoforge.com/encrypted-root-lvm")

Good Luck.

---

### Post by johnarild on 2009-11-20
> **geurt said:**
> First of all:
It is not possible to encrypt the whole filesystem. The kernel needs to be loaded before things like the encryption of a filesystem work.

I don't know how the graphical ubuntu installer looks like. I allways use the alternative installation discs to install the ubuntu operating system.

To use LVM, please look at:
[http://www.howtoforge.com/encrypted-root-lvm]("http://www.howtoforge.com/encrypted-root-lvm")

Good Luck.

Obviously I leave a /boot partition outside the encrypted LVM and that works quite good when using the alternative installer. I have now managed to do what I want by using expert mode, but I still have a problem, but I think that might be a kernel configuration problem and I hope to get that fixed too and then I'm in goal. I just cant understand why you cant select separate /home partition when not in expert mode, thats just stupid IMHO.

The graphical install got an easier to use partitioner tool, but other than that I don't see the point of using it.

Edit: Got it fixed. All is is fine now.

---

