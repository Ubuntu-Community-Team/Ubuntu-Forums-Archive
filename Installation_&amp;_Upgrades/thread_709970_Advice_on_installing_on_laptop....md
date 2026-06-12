---
title: "Advice on installing on laptop..."
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by Zalbor on 2008-02-27
I just bout an Acer 5920G, which comes with Vista, and I want to install Ubuntu as well.
Currently, the hard drive has 4 partitions:
-A small one for recovery
-A big one where Vista is installed
-Another big one which is empty
-A small one that contains a "special" version of XP, which the computer boots if I turn it on with a special button. It has DVD and TV capabilities.

What I want to do is delete the second big partition, and use that space to install Ubuntu in. I don't plan on resizing or deleting any other partition.

Now, reading things on here it seems there might be some problems, and I'd like someone to give me a definite answer about them...

1)I read that GRUB won't be able to boot Vista. Is that right?
2)I read that if I alter the MBR in any way, not only will the special partitions (recovery and XP) not work, but that I also won't be able to restore Vista with the 2 DVDs I burned. Is that right?

If someone has the same model and is dual-booting Ubuntu and Vista, I'd like to hear their experiences with doing so. But any advice is welcome.

---

### Post by Biggus on 2008-02-28
Hi dude.

I don't have any experience of doing this, but I've had a look at this page here :[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first) which looks quite similar to what you're trying to achieve.

According to that, you qill get a GRUB loader, but it probably will overwrite the windows MBR (if I'm following that correctly) and replace it with the grub loader.

You may be best to wait for someone who's actually done this though to come along with a more definitive answer before you go partitioning drives.

---

