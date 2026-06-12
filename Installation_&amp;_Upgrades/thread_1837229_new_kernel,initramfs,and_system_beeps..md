---
title: "new kernel,initramfs,and system beeps."
date: 2011-09-01
forum: Installation &amp; Upgrades
---

### Post by johnalexrob on 2011-09-01
I decided to compile my own kernel again (as if I didn't take the hint from my last failure at this) and moved it to the /boot directory. On boot, I got a magic number error, so I tried to access my grub so I could select the old kernel. Unfortunately, I had edited the wrong setting for timeout setting so I couldn't reach my menu. I booted from my Gentoo external drive to edit my settings. I booted, mounted my internal drive and bind mounted dev, and chrooted to run update-grub. After segfaulting 3 times, it said it couldn't read my partition list. I rebooted to see if it would work anyway. I made it to grub and manually loaded my old kernel and initrd through its command line and continued booting. Eventually I made it to an initramfs prompt. I don't remember the exact error message. After doing the same thing I did through Gentoo, except this time also bind mounting proc, update-grub did not segfault but gave me the same error about not being able to read my partition list. When I rebooted, I could not reach my grub menu and when I tried holding the escape key, I would get a system beep and have to unplug my battery. 
 
What is the magic number error, and how badly did I screw up my computer?

---

### Post by johnalexrob on 2011-09-01
So I rebooted and without touching any keys it booted just fine to the grub menu. I was able to boot into my old kernel and log in. But I still wonder, though, what happened? What is that magic number error? I had this same error a while back trying to boot into a new kernel I had just compiled. Why did it beep when I tried to access grub? I know that sometimes system beeps happen when you hold a key down for too long while trying to boot. Why did it work so well this time? Will I ever be able to get anything right? I want to become a programmer and contribute to the kernel in the future, but things like this make me think I should give up.

---

### Post by johnalexrob on 2011-09-04
After a while of working, something went wrong and now I boot to initramfs. I keep getting disk read errors on my HDD and other distros give me the same error. I think my drive is damaged somehow.

---

