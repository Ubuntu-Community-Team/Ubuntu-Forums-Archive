---
title: "Grub: No Such Device after Clean Install"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by strange_cathect on 2011-11-20
I've just completed a clean install of 11.10 rather than upgrade from 10.10. I completely wiped the hard drive and then created a swap and root partition, requesting that grub be installed to dev/sdb (where the two partitions live).

I get the grub rescue prompt: "no such device . . ." and a UUID. I reinstalled with the same error.

I then used the boot-repair program to reinstall Grub2. But upon rebooting, I have the same error.

Can someone help me?

---

### Post by darkod on 2011-11-20
Are you sure you are booting from /dev/sdb? You may have grub that you are not even aware of on /dev/sda which is now broken with the partitions deleted. And you might be booting that.

If you have any doubt you can run the boot info script to see what is where.

---

### Post by Rubi1200 on 2011-11-20
You should also check which drive is set as first boot priority in BIOS.

The boot info script mentioned by darkod will really help us diagnose this issue.

(Instructions in the link at the bottom of my post).

---

### Post by strange_cathect on 2011-11-20
Fixed.

I had elected to put Grub on /dev/sdb and my /dev/sda drive comes first in the boot order. I installed Grub on /dev/sda and it worked.

Now if I can only get my nvidia driver to work!

---

### Post by Rubi1200 on 2011-11-20
Great news :)

Please mark this Solved using the Thread Tools near the top of the page.

---

