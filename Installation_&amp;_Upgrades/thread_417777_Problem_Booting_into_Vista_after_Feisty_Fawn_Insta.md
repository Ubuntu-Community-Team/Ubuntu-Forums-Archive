---
title: "Problem Booting into Vista after Feisty Fawn Install"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Derr on 2007-04-21
Hello,

This is my first post here. Forgive me if I'm asking a FAQ, but after reading the forums for a while, I didn't see a post that described the same problem I'm having.

I recently adopted a machine on which I installed Windows Vista. I had set up the hard drive (the only HD on the system) to give most of the space to Vista, and left some space nallocated for a later Ubuntu install. I burned the Feisty Fawn installer CD a few days ago, and installed Ubuntu on the hard drive, manually creating partitions on the unallocated part of the hard drive for / and /swap.

The install itself went smoothly, and Ubuntu itself seems fine. However, I cannot seem to boot into Vista anymore. Grub gives Vista as a boot option, but when I select it, the machine just reboots, and then I'm back to Grub. I can verify that the Vista partition and all its data are fine (the Vista partition appears as /dev/sda1 in Ubuntu); I just can't startup under Vista. I don't see any error messages, so I'm guessing that there's a problem with Vista's boot loader, or whatever it's called, and not with Grub.

Any clues as to how to proceed? Additional details available upon request. Thanks much!

---

### Post by eyelessfade on 2007-04-21
Could you post the relevant part of /boot/grub/menu.lst

The 1-4 lines under #Windows..

---

### Post by Derr on 2007-04-21
Here is the relevant entry:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

This is what the installer provided, without any changes on my part. To the best of my knowledge, Vista is on partition 0 of the drive, so the reference should be correct.(?)

---

### Post by walden2 on 2007-04-22
I've got the same problem, but with XP instead of Vista. Any ideas?

---

