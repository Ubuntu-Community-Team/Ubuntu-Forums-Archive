---
title: "Installing Grub to each bootable drive?"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2010-02-11
I read on a thread or How to: recently (can no longer find it),the suggestion that Grub be installed on each bootable drive in a multiboot system.
What are the pros and cons (if any) of doing this.

---

### Post by darkod on 2010-02-11
Absolutely unnecessary. The most important is: Have the correct bootloader on the disk you are booting from.
Everything else is just for cosmetics. :) For example, if dual booting with 2 disks with windows and ubuntu on each, you might choose to have windows bootloader on the windows disk, and ubuntu on the ubuntu disk. If grub gets messed up, just boot from the windows disk and you can use windows at least.

But even that is unnecessary in a way, because repairing grub in most situations is quick and easy.

So it is really your choice how you want things.

---

### Post by jenaniston on 2010-02-11
> **darkod said:**
> . . . If grub gets messed up, just boot from the windows disk and you can use windows at least.

. . .  repairing grub in most situations is quick and easy.


But if grub gets messed up when using linux for a mission of rescuing files off a corrupted Windows partition . . .
then repairing grub is gonna be the *only *way . . . and may or may ***not ***be all *that* obvious or easy.

---

### Post by darkod on 2010-02-11
If we start with various IFs, we won't get very far... Lets deal with actual problems, all right?

---

### Post by kansasnoob on 2010-02-11
> **Paulgirardin said:**
> I read on a thread or How to: recently (can no longer find it),the suggestion that Grub be installed on each bootable drive in a multiboot system.
What are the pros and cons (if any) of doing this.

Particularly with grub2 I've found that sometimes that's an easy solution to "mapping". Actually "mapping" may be the wrong term.

I've found that sometimes, even if the BIOS is set properly, and everything looks like it should work I can't get grub2 to boot a Win OS on a drive with a Win mbr.

Actually legacy grub could be even more difficult but regardless I've sometimes found that simply installing grub2 to the mbr of each drive gets things working.

What's important is knowing how to restore various boot loaders to the mbr of any given drive.

---

