---
title: "Ubuntu with XFS"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by rayfun on 2008-10-21
Hi,

I'd like to install Ubuntu with XFS filesystem.

Now when I partioned the system the installer gave me a warning that there might be problem with Grub booting from XFS. In addition Grub failed when installing.

Two questions:
1. How would have to go forth to install Grub now with my XFS root filesystem? I'm still now in the live session...

2. Would lilo work better?

Thanks,
ray

---

### Post by armageddon08 on 2008-10-21
> **rayfun said:**
> Hi,

I'd like to install Ubuntu with XFS filesystem.

Now when I partioned the system the installer gave me a warning that there might be problem with Grub booting from XFS. In addition Grub failed when installing.

Two questions:
1. How would have to go forth to install Grub now with my XFS root filesystem? I'm still now in the live session...

2. Would lilo work better?

Thanks,
ray

Make a separate /boot partition with ext3 filesystem and install grub on it (you can do this from the "Advanced" option during installation).

BTW, is it possible to access XFS drive from Windows ?

---

