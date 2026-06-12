---
title: "How to resize partition 465GB, need free space for Blacktrack?"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by Buksetyv on 2012-11-19
Hello,

I have some issues, cant resize partition so i can get some free  space for my Blacktrack.

[IMG]http://i45.tinypic.com/286vpc2.jpg[/IMG]

Like in image, i hope somebody could help me with my issue:)

Best regards Jonas:)

---

### Post by darkod on 2012-11-19
Do you plan to install Backtrack as LVM too or not?

If you do, you can only shrink the LV (provided it has free space). Or maybe the LV doesn't take the whole VG as it is right now. As long as you have free space in the VG you can simply install Backtrack on the LVM, if it can work on LVM.

Otherwise, I'm not sure that you can shrink a partition that is a physical device for LVM. First try to do some googling if it's supported and possible at all.

---

### Post by Buksetyv on 2012-11-19
> **darkod said:**
> Do you plan to install Backtrack as LVM too or not?

If you do, you can only shrink the LV (provided it has free space). Or maybe the LV doesn't take the whole VG as it is right now. As long as you have free space in the VG you can simply install Backtrack on the LVM, if it can work on LVM.

Otherwise, I'm not sure that you can shrink a partition that is a physical device for LVM. First try to do some googling if it's supported and possible at all.

I am sure it doesnt, it is a fresh install of ubuntu. Problem is when, i try to install it...

---

