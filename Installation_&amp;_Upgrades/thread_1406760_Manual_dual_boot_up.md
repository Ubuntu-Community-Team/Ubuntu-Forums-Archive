---
title: "Manual dual boot up"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by bjdd4 on 2010-02-14
I am trying to install Ubuntu 9.1 on an existing xp op. It is prompting to replace xp. Can somebody help how to install manually the dual boot with out replacing xp. Thanks

---

### Post by darkod on 2010-02-14
If you have no unallocated unpartitioned space on the hdd (not belonging to any partition), you will be offered only two options:
Install side-by-side, which shrinks XP to make space for ubuntu, there is a slider that you can move to control how much you shrink.
Erase and use whole disk, which will erase the whole hdd and use it only for ubuntu, which obviously you don't want.

For XP is it highly recommended to shrink it like this: boot with the ubuntu cd, Try Ubuntu option, open Gparted in System-Administration, and use it to shrink the XP partition (or any other, depending on your hdd layout and what you plan to do) for as much as you want. Boot XP few times because it will need to do some disk checks. That is a very IMPORTANT step.
After that again boot with ubuntu cd, Install Ubuntu option, and this time because there will be unallocated space after the XP shrink, you will have another option, Use Largest Available Free space. Just use that and ubuntu will get installed into the unallocated space.

---

