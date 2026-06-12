---
title: "Merging Partitions?"
date: 2008-10-20
forum: Installation &amp; Upgrades
---

### Post by Thorney13 on 2008-10-20
What I'm trying to do.
1.Add the empty hda7 to hda6
2.Move around 4GB of data from hda1 to hda6
3.Format hda1 and add the free space to hda6

[ATTACH]89069[/ATTACH]

Im using Gparted on my Ubuntu 7.04 Live cd
hda 6 has a fresh install of 7.04 and hda1 has an unstable install of ubuntu 8

---

### Post by Partyboi2 on 2008-10-20
> 1.Add the empty hda7 to hda6Unmount hda6 and hda7 (right click and unmount), right click on swap and turn off, then delete hda7 and then use the resize tool to increase hda6
>  2.Move around 4GB of data from hda1 to hda6 Cut and paste or copy and paste from hda1 to hda6 after adding more space to hda6
>  3.Format hda1 and add the free space to hda6 Delete the partition and use the resize tool to add it to sda6
Remember to back up important stuff before working on partitions.

---

### Post by Thorney13 on 2008-10-20
> **Partyboi2 said:**
> Unmount hda6 and hda7 (right click and unmount), right click on swap and turn off, then delete hda7 and then use the resize tool to increase hda6

This is where the problems start when I've deleted hda7 and attempt to resize hda6 I can't grow it to the left

[ATTACH]89071[/ATTACH]

---

### Post by Thorney13 on 2008-10-21
Someone has to be able to help me? Is there any possible way?:confused:

---

### Post by Thorney13 on 2008-10-22
*Bump*

---

