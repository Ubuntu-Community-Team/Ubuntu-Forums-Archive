---
title: "Ubuntu has overwritten Vista"
date: 2007-07-03
forum: Installation &amp; Upgrades
---

### Post by glendavee on 2007-07-03
I've just installed 7.04 on a new laptop which had Vista already pre-istallled, intending to have a dual-boot system. I used an installation CD which I burned from the current download site. Ubuntu installed ok, but when I reboot, I don't get the option to open Vista - It's gone. Have I screwed up, and destroyed the partition where Vista was? How can I check and/of fix things?

---

### Post by xfile087 on 2007-07-03
> **glendavee said:**
> I've just installed 7.04 on a new laptop which had Vista already pre-istallled, intending to have a dual-boot system. I used an installation CD which I burned from the current download site. Ubuntu installed ok, but when I reboot, I don't get the option to open Vista - It's gone. Have I screwed up, and destroyed the partition where Vista was? How can I check and/of fix things?

Did you partition manually? If you didn't then you've most likely lost Vista... I hope it wasn't one of those laptops with a hidden recovery partition instead of a CD - like mine.

You could try opening GNOME Partition Editor and see if Vista is still there if it is you should just be able to change your grub settings to get it working.

---

### Post by glendavee on 2007-07-03
I didn't use the manual partition option. When I look in disk usage analyser, looks like Ubuntu has taken the entire hard drive. I've checked and discovered that the laptop came with a hidden recovery paritiion, so I assume there's nothing I can do. I do have a genuine copy of XP, so can I repartition and install that?

---

### Post by xfile087 on 2007-07-03
> **glendavee said:**
> I didn't use the manual partition option. When I look in disk usage analyser, looks like Ubuntu has taken the entire hard drive. I've checked and discovered that the laptop came with a hidden recovery paritiion, so I assume there's nothing I can do. I do have a genuine copy of XP, so can I repartition and install that?

In that case it's most likely wiped your drive and installed Ubuntu. If you want Vista back - depending on your laptop you might be able to order a set of recovery disks instead - I know HP send you them if you ask. The thing about installing XP is that the laptop came with Vista so there might not be any XP drivers available for it? That's not to say you can't give it a try! If you get it sorted and want to put ubuntu on again then make sure you choose manual partitioning so you wont lose everything.

Oh and if you do "sudo fdisk -l" in the terminal it will show you your partitions so you will definitely know if Vista is still there because you will see an NTFS partition.

---

### Post by glendavee on 2007-07-03
Thanks for the help. fdisk -l merely confirms my worst fears. If I can get the wireless drivers configured, I might just forget Microsoft altogether......

---

### Post by xfile087 on 2007-07-03
> **glendavee said:**
> Thanks for the help. fdisk -l merely confirms my worst fears. If I can get the wireless drivers configured, I might just forget Microsoft altogether......

Which laptop do you have? I might be able to help you with that one depending on which laptop it is.

---

