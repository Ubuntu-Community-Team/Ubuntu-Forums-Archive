---
title: "Hang during boot after &quot;skipping profile ... &quot;"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jmmL on 2009-09-28
I've just rebooted after the recent grub updates and I get a hang during boot after the "skipping profile .. " line. This can only be solved with a hard reboot. I get this issue on kernels -11, -10 and -9 (the only ones I have), as well as on the recovery kernels.

Grub still loads windows fine, so I'm in that at the moment. Can anyone else confirm?

---

### Post by philinux on 2009-09-28
If you cant get in at all I reckon you'll have to use the live cd and chroot in to be able to perform an apt update etc.

---

### Post by DougieFresh4U on 2009-09-28
This won't help at the moment, but I have gotten into the habit of running **sudo update-grub2** after every grub and/or kernel update before rebooting. I find it saves me a lot of drama.

---

### Post by jmmL on 2009-09-28
I chrooted in and run the available updates - that didn't seem to help. The hang happened about 3.7 seconds into the boot - before xsplash. There aren't any obvious errors when booted into recovery mode. Messages from the kernel are still displayed on the screen after the boot process seems to stop (I still get notifications if I plug in a set of USB speakers, for example).

I'll chroot in again and try updating grub.

---

### Post by jmmL on 2009-09-29
Chrooted in and updated grub - seemed to fix the problem.
Thanks, and I think I'll be more careful with those grub updates in future.

Side note: trying out the new humanity icons - very nice!

---

### Post by philinux on 2009-09-29
> **jmmL said:**
> Chrooted in and updated grub - seemed to fix the problem.
Thanks, and I think I'll be more careful with those grub updates in future.

Side note: trying out the new humanity icons - very nice!

Think we still at grub2 version 1.97 (Beta 1) / 2009-08-30 according to the wiki.

Still could be buggy now and then.

---

