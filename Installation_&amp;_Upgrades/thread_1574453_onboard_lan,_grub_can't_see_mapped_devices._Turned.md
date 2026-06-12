---
title: "onboard lan, grub can't see mapped devices. Turned off, windows can't see hard drive"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by skelooth on 2010-09-14
Hi, this is a frustrating, and I guess complicated, problem. I have not been able to find this exact situation posted anywhere in my google searches.

I have a prefab'd gateway fx computer. The price was right at the time but it has a bunch of "features" that are really in the way. 

The motherboard (nvidia brand) has an INTEGRATED raid controller that feeds off of the sata ports. I've inspected the inside of the computer, and there is no hard way to remove the fake raid.

Anyway, here's the story:

When the raid card is enabled (it has two 512gb disks as one, i forget the number), windows sees this fine, and linux *installer* sees this fine. However, grub can not see it, and gpart can not see it. fdisk can see it only if i -l the /dev/mapper/funnydevname

With the raid card disabled in bios:
nothing can see the hard drives properly!

With the raid functionality (but raid still technically "on") nothing can see the hard drives properly!

So what I've ended up with, is that I can install windows fine however I want. I can even install linux, but I have no way to boot into linux because grub will NOT install !!!!!

I even tried using windows 7 boot loader using easy bcdedit, but when i choose linux i get a grub error 15 that it can't find menu.lst (because it can't see the mapped devices again!)

Any help? I'm so frustrated. I'm really sick of using virtual machines in windows. I really want and need a native ubuntu boot. 

Thank you so much for any help or ideas to try.

---

### Post by sikander3786 on 2010-09-14
Have you tried this?

[http://ubuntuforums.org/showpost.php?p=9237139&postcount=18](http://ubuntuforums.org/showpost.php?p=9237139&postcount=18)

---

### Post by skelooth on 2010-09-14
Nope I haven't seen that one. Thank you so much I'll try that later this evening.

---

