---
title: "changing kernel back to generic version"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by Niall Flinn on 2006-12-29
Hi folks,

I'm running edgy on an AMD64 system and I've just attempted to install the nvidia-glx package. One of the things that happened when I did that was that it installed linux-2.6.17-10-386 to replace linux-2.6.17-10-generic. I can now no longer boot my edgy installation from grub (error 15 - file not found), but I have access to the edgy filesystem from an older installation. What files do I need to remove or replace to get my system to boot again?

Thanks,

Niall

---

### Post by Rodneyck on 2007-01-15
Bump!

---

### Post by Enverex on 2007-01-15
The "linux-generic" package and it's "linux-*" dependencies. I'm guessing things are still there and Grub has tab complete, so when it comes up with the list of kernels on boot, select the one you want, press 'e' and then select the line with "kernel" on it then press 'e' again and go to the part of the line where it has the location (like /boot/vmlinux-2.6.17-generic) and hit tab and it should show you what's available, if it doesn't show anything start deleting parts of the kernel name until it does and play about with this.

---

### Post by Rodneyck on 2007-01-15
> **Enverex said:**
> The "linux-generic" package and it's "linux-*" dependencies. I'm guessing things are still there and Grub has tab complete, so when it comes up with the list of kernels on boot, select the one you want, press 'e' and then select the line with "kernel" on it then press 'e' again and go to the part of the line where it has the location (like /boot/vmlinux-2.6.17-generic) and hit tab and it should show you what's available, if it doesn't show anything start deleting parts of the kernel name until it does and play about with this.

You are basically editing menu.lst it sounds, which I have done this, changing everything from 386 (or whatever the original poster was using) to generic and it still shows the 386 kernel when you type "uname -r" in a terminal.  So that does not work. I need to uninstall the 386 driver and revert back to the generic, but can't.

---

### Post by smartbei on 2007-01-15
See my post here:
[http://www.ubuntuforums.org/showthread.php?t=337851#post2008615](http://www.ubuntuforums.org/showthread.php?t=337851#post2008615)

---

### Post by Enverex on 2007-01-15
No, you're not, read what I wrote. This is IN GRUB directly after post, before you boot Linux.

---

