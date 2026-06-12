---
title: "&quot;windows can't start beacuse x.dll is damaged or missing&quot; - WTF?"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by iAlta on 2007-05-09
I just installed Ubuntu over an xp install I had.

When I reboot my computer it says it can't boot windows because some .dll is missing, but I don't want to f***ing boot windows!! I just installed Ubuntu!!

It is very annoying! I just wanna get Ubuntu working, I even installed it twice, but windows just won't get of the harddrive.

---

### Post by stchman on 2007-05-09
> **iAlta said:**
> I just installed Ubuntu over an xp install I had.

When I reboot my computer it says it can't boot windows because some .dll is missing, but I don't want to f***ing boot windows!! I just installed Ubuntu!!

It is very annoying! I just wanna get Ubuntu working, I even installed it twice, but windows just won't get of the harddrive.

How did you install Ubuntu?  Did you select erase entire hard drive?  Did you so the free up space on a partition?  If you did the install Ubuntu on a partition then the GRUB menu should come up.  If you erased the entire hdd Windows should be gone.  More information please.

---

### Post by iAlta on 2007-05-10
The first time I installed it on the hardrive, I chose the automatic "use the entire drive".

The second time I installed ot on the harddrive, I chose the manual, and deleted all the partitions and created 3 partions, '/', '/home' and 'swap'.

And now I'm gonna install it for the third time...

EDIT: I've installed it for the third time now, and the forth, and I have messed around with Arch Linux for two days without success. That filth is still on my harddrive craving that damned hal.dll...

EDIT2: I feel like an idiot, I feel like an idiot, I feel like an idiot, and the problem is solved. Ubuntu was installed on hd0, boot sequence floppy, cdrom, hd1..

---

