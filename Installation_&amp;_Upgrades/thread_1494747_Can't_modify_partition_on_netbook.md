---
title: "Can't modify partition on netbook"
date: 2010-05-27
forum: Installation &amp; Upgrades
---

### Post by ChildOfLore on 2010-05-27
I'm trying to install Ubuntu Netbook Remix (which is amazing btw) on my brother's new netbook. The problem is that when I try to install it, there is no option to partition the hard drive (which is currently saturated with Windows XP), I couldn't do it via GParted either, the option to modify the size of the Windows Partition is just greyed out/not there. I don't expect him to be using Windows XP much but I want to keep it on there just in case, does anyone know why I can't edit the partition?

Thanks,
Marlon

---

### Post by dino99 on 2010-05-27
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-05-27
> **ChildOfLore said:**
> I'm trying to install Ubuntu Netbook Remix (which is amazing btw) on my brother's new netbook. The problem is that when I try to install it, there is no option to partition the hard drive (which is currently saturated with Windows XP), I couldn't do it via GParted either, the option to modify the size of the Windows Partition is just greyed out/not there. I don't expect him to be using Windows XP much but I want to keep it on there just in case, does anyone know why I can't edit the partition?

Thanks,
Marlon

In Gparted, does it have like a yellow triangle mark next to the XP partition? That usually means some type of problem (which might be something really irrelevant) and because of that Gparted doesn't want to try to resize it.

You can right-click it and select Check, see what it says.

After that, you can also run the famous chkdsk from XP to check its partition.

---

### Post by ChildOfLore on 2010-05-28
Got it! Thanks darkod. I right-clicked the yellow exclamation mark and clicked check, the error console informed me to boot into windows and run "chkdsk /f" which fixed it. When I rebooted into Ubuntu, it was all cool and the netbook is running on a proper dual-boot!

Ubuntu Forums are awesome! :)

---

