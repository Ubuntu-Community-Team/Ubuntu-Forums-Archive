---
title: "Ubuntu installed twice??"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Synyster06Gates on 2010-07-02
When I first started to install Ubuntu to my system, I got an error that told me Ubuntu was not successfully installed, so I restarted my computer and tried again. That time it works, and I'm thoroughly enjoying the OS. I noticed that when I start up my computer and I have the OS boot list, Ubuntu and Ubuntu safe mode are listed twice. How do I remove the 2nd one, and is it still installed on my other partition even though it said failed?

---

### Post by dino99 on 2010-07-02
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Synyster06Gates on 2010-07-02
Hmm that doesn't really tell me how to remove the failed OS, though

---

### Post by darkod on 2010-07-02
Look more carefully at the boot menu. Linux works with kernels and you can have more than one with a single install.
If the menu entries are like:
2.6.32-22 normal and recovery mode
2.6.32-21 normal and recovery mode

then you have only one install. Keeping at least one older kernel is recommended in case the newest one starts giving you problems. You can just boot a previous one and the system will work.

For removing older kernels, open Synaptic and search for linux-image. Remove the ones you want to remove. Be careful not to remove all, there will be nothing to boot.

After that you might or might not need to run:
sudo update-grub

to recreate a new boot menu.

---

### Post by dino99 on 2010-07-02
> **Synyster06Gates said:**
> Hmm that doesn't really tell me how to remove the failed OS, though

maybe you have not paid attention at formatting tool (gparted or partedmagic) which are able to load the partitions and show you what the reality is. So if installation have been made twice, remove the unwanted partition(s) with this tool, but take care to do that on a non active partition of course: so follow my previous link, is that is making more sense ?

---

