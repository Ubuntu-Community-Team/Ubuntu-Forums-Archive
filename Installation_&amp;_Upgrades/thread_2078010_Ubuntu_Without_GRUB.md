---
title: "Ubuntu Without GRUB?"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by bradjohns94 on 2012-10-29
Hey all,

So I recently reinstalled ubuntu on my laptop after playing around with a few different operating systems on it. Unfortunately with this fresh install I seem to be loading GRUB while ubuntu should be the only OS on the hard drive (the other OS that was on it appears along with standard options such as memtest, etc, however the previous OS does not actually boot). I'm nearly certain there is a way to get ubuntu to boot without loading grub because it worked that way with my last install of it. I have an SSD in my laptop so the boot time is something I'd really like to utilizes, so does anyone know how I can skip the GRUB loader and boot straight into ubuntu?

---

### Post by LemonLime on 2012-10-29
I was able to streamline and boot Ubuntu without a grub menu by completely formatting and repartitioning my hard drive into a single partition, then running the install from the Ubuntu disk and having it reorganize the hard drive on its own (the OS, swap, etc). It no longer had a boot menu and went directly from my motherboard image to the loading screen. 

If you still have things appearing, though, maybe you should check out this resource, which tells how to modify and make invisible the boot menu: [https://help.ubuntu.com/community/Grub2#Hidden](https://help.ubuntu.com/community/Grub2#Hidden)

---

### Post by offgridguy on 2012-10-29
> **LemonLime said:**
> I was able to streamline and boot Ubuntu without a grub menu by completely formatting and repartitioning my hard drive into a single partition, then running the install from the Ubuntu disk and having it reorganize the hard drive on its own (the OS, swap, etc). It no longer had a boot menu and went directly from my motherboard image to the loading screen. 

If you still have things appearing, though, maybe you should check out this resource, which tells how to modify and make invisible the boot menu: [https://help.ubuntu.com/community/Grub2#Hidden](https://help.ubuntu.com/community/Grub2#Hidden)

I used the same procedure, with the same results {hardly surprising}
Thanks for the link, LemonLime. :)

---

