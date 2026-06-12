---
title: "Uninstalling ubuntu"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by Itqan on 2010-06-23
hi i am running into some some sort of problem with ubuntu 10.4 32 bit.its hangs badly after 5 mins of starting my computer. i have installed it with XP and i chose the option install side by side with windows and now i dont know where it is installed. so how do i remove it without getting my XP corrupt?:confused:

thanks in advanced

---

### Post by dino99 on 2010-06-23
have you checked your driver activation ?
(system admin hardware driver)

into a terminal:

fdisk -l

then remove it with the path given above

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by darkod on 2010-06-23
Use your XP cd to revert to windows boot process first. If you need instructions:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After that is done the computer will start booting XP directly. You can't see the linux partitions in My Computer if that's what you expect.

Once XP is working fine with its own bootloader, just open Disk Management and delete the ubuntu partitions. Then create new ntfs partition from that space to use it for windows data.

Deleting the ubuntu partitions will delete all data on it, so copy all data you need from it before starting all this.

---

### Post by gdonwallace on 2010-06-23
You should also check the add/remove programs in control panel.

It has been a while since I used the wubi install to "install" ubuntu within windows, but I think there should be an option to remove it.

---

### Post by darkod on 2010-06-23
> **Itqan said:**
> i chose the option install side by side with windows 

That's a full install, not wubi. There shouldn't be anything regarding ubuntu in Add/Remove Programs.

---

### Post by hip on 2010-06-23
> **Itqan said:**
> hi i am running into some some sort of problem with ubuntu 10.4 32 bit.its hangs badly after 5 mins of starting my computer. i have installed it with XP and i chose the option install side by side with windows and now i dont know where it is installed. so how do i remove it without getting my XP corrupt?:confused:

thanks in advanced

remember if you are going to dual boot xp and ubuntu you have to scan disk and disk defrag before installing linux.  that should fix it if not . check back to the forums.:guitar:

---

### Post by Itqan on 2010-07-06
thanxx guys will try that out tommorow any suggestions for installing any previous stable versions?

---

### Post by Itqan on 2010-07-10
oh my god i tried the same but it deleted 4 more partitions with it automatically. how can i get them back????

i mean data on them?

can i get it back somehow?

---

