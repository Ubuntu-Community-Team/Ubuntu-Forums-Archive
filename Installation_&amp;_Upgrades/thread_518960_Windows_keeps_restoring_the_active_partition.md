---
title: "Windows keeps restoring the active partition"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by Muqker on 2007-08-06
Hi.
I have a dual boot: Ubuntu and Windows XP SP2. I have grub set on the Linux ext3 partition. Whenever I boot in Windows, it restores the partition table and sets the active partition to it's own partition and the ext3 partition to not-active. Why is this and how can I stop this from happening?
Thanks.

---

### Post by JudasReanimated on 2007-08-06
Does it give you a warning, or does it just change when you restart?

More details please.

---

### Post by psusi on 2007-08-06
You manually installed grub to the ext3 partition instead of the mbr?  Because it goes to the mbr by default, so the active partition doesn't matter.  

Check your grub config, it is probably set to make the windows partition active when chain loading it.

---

