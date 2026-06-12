---
title: "Dual boot Ubuntu 11.04 w/ 10.10"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by GRAYgoose12 on 2011-04-02
Well, I upgraded my main system to test 11.04, it's a bit too glitchy for me, but I don't want to lose my private data. I figured I would just dual boot with 10.10 until a stable release was distributed, but I can't seem to get 10.10 to boot up, I can't even get grub open(:/, I could before). I've been troubleshooting for the past 2 hours, but I'm pretty tired and I'm about to format my drive.

---

### Post by beew on 2011-04-02
I don't know exactly what your problem is, your description is kind of vague.

See if these may help.

[http://ubuntuforums.org/showthread.php?t=1698582]("http://ubuntuforums.org/showthread.php?t=1698582")
[URL="http://ubuntuforums.org/showthread.php?t=1699552"]
http://ubuntuforums.org/showthread.php?t=1699552[/URL]

---

### Post by GRAYgoose12 on 2011-04-02
Basically, for some reason, I can't open grub, and I have one partition with 11.04, which boots, but I have another with 10.10. Obviously, which doesn't. I want to use 10.10 until there is a stable release though. Sorry for my vagueness, I'm having trouble keeping my eyes open.

---

### Post by beew on 2011-04-02
What do you mean by can't open grub? Do you mean you don't find 10.10 in the boot menu?

If that is the case, boot into 11.10 and run ```
sudo update-grub
``` and reboot and see if you can see 10.10.

---

### Post by Hedgehog1 on 2011-04-02
**Before you reformat!**

Boot your system holding down the "Shift" key.  This forces the GRUB menu to come up.

The new grub menu for 11.04 (and that is the grub you are running) has an option in the 3rd position to see 'older kernels'.  Your Ubuntu 10.10 is in there.

***The Hedge***

:KS

---

