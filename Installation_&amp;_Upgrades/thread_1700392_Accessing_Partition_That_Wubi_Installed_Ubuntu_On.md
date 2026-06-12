---
title: "Accessing Partition That Wubi Installed Ubuntu On"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Dice62 on 2011-03-04
Hello,

So far, everything is running great, but I do have one question:

I installed Ubuntu through Wubi on my E partition. I set the install size to be 30gb, and it has worked without any problems, however, when I go to "Places" in the top Panel in GNOME, I see my other partitions in windows, but not the partition that Ubuntu was installed on.

I thought it may be now called "File System" but the size of it is only the 30gb i set, and not the 250gb of the partition.

The reason I ask is because that partition contains all the movies, tv shows, etc that I would like to watch through Ubuntu, so is there a way I can access it?

Lastly, are there dangers to mounting a windows partition in Ubuntu? Could that partition become corrupt? For example, I mount my D: drive which has my music on it, will that somehow make it inaccessible via Windows 7?

Thanks again for your time,
Mirwan.

---

### Post by mikewhatever on 2011-03-05
Wubi doesn't install on partitions, but instead, installs Ubuntu into a file. That file may be located on E or D, it makes no difference. I think the partition where the file resides is accessible through /media/host or something similar.

Mounting the Windows partition can be dangerous, because with the full read/write access, you can accidentally delete important system files, other then that, it should be safe. Regardless, backing up your music is never a bad idea.

---

### Post by Dice62 on 2011-03-05
I found the rest of my E drive under Host.

Thank you for the help, and for your time.

---

