---
title: "How to clone Ubuntu installation to another partition?"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by P3P on 2008-04-25
Hello,

I have an Ubuntu 8.04 working on my system, but I want to move that installation to another partition.

It is possible to copy all the contents of / to the new partition with **cp -r** command?
Is any other option needed for the cp command?

After copy the root partition contents I will change the **grub configuration** and the **fstab** file. Are any other changes needed?


Do you think that this method will work well? Any alternative ideas?


Now I will explain you why I need this trick. My current partition is on a FakeRaid RAID0 volume and my target partition is on a FakeRaid RAID5 volume. Standard Kernels do not support RAID5, so I need recompile kernel with RAID5 support. But I do not known how to use the Ubuntu installation CD with a custom kernel (capable of install on a RAID5), so I install Ubuntu in the RAID0 using the installation CD and dmraid. Once Ubuntu installed I recompile a custom kernel with RAID5 support, boot with this custom kernel and copy everything to target RAID5 partition.
**Will it work?**

Thanks in advance.
Regards.

---

### Post by Pumalite on 2008-04-25
I don't know anything about Raids, but there is something called Clonezilla:
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by P3P on 2008-04-25
Thanks for your reply.

> **Pumalite said:**
> I don't know anything about Raids I think that RAID do not interferes in the copy process, so you can ignore the exitence of a RAID and assume that is a copy to one mount point to another. I explained the raid configuration only for better understanding of the problem.

[QUOTE=Pumalite]but there is something called Clonezilla:
[http://www.clonezilla.org/](http://www.clonezilla.org/)[/QUOTE]This tool may be a better solution than **cp -r** command. Thanks.

But the main question is:
**If I copy root partition, change fstab and reinstall grub, will it work or is any more required?**

The alternative question:
**Is there any way to use Ubuntu CD installer with a custom kernel?**

Regards.

---

### Post by Pumalite on 2008-04-25
The first is correct.

---

### Post by chrisj26 on 2008-09-15
anyone ever done this? I'm currently dual-booting vista/ubuntu and want to clone my current ubuntu setup to my new HDD. is it possible to use clonezilla to do this and then reformat the old linux partition for vista use?

---

### Post by Pumalite on 2008-09-15
Read the information on the site.

---

### Post by P3P on 2008-09-15
Finally I didn't make the clone, but I think that is possible as we said in this post.

You can read [How to copy linux to a different partition]("http://it.toolbox.com/blogs/locutus/how-to-copy-linux-to-a-different-partition-12865") article or search for [clone root partition]("http://www.google.com/search?q=clone+root+partition") on google.

If you want to reinstall you can use [debootstrap](http://www.debian-administration.org/articles/426) to make the new root system from your current linux installation.

---

