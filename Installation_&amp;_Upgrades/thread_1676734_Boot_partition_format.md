---
title: "Boot partition format"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by new-num-order on 2011-01-27
What should I format my boot partition as?
I can't find any info on this, seems like ext4 is alright, but I'm not sure.

Thanks in advance!

---

### Post by new-num-order on 2011-01-27
Did some more research for each partition format and found out that ext4 is actually not officially supported by GRUB, so ext3 or ext2 is a better choice.

---

### Post by kansasnoob on 2011-01-27
I don't know where you're looking but a separate "/boot" partition is seldom needed unless you have very old hardware. But, if needed, using ext4 should work fine.

It would be best if you explained exactly what you're trying to do, or maybe look here:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by coffeecat on 2011-01-27
> **new-num-order said:**
> Did some more research for each partition format and found out that ext4 is actually not officially supported by GRUB, so ext3 or ext2 is a better choice.

The information you found is very out-of-date. Grub has supported ext4 for quite some time now. And I agree with kansasnoob - a separate boot partition is only needed for special cases.

---

### Post by new-num-order on 2011-01-27
I'll explain the whole thing, since some issues appeared...

I have macbook pro 2,1 (late 2006) and I want to triple boot OS X, Win and Ubuntu. I want rEFIt (boot menu for macs) to boot directly into Win if I select Win, instead of loading GRUB. I won't be the only one using the computer and I don't want GRUB to confuse others. I've read this is possible (the boot thing not the confusion), but not how to do it.

I've successfully installed Win7 (without Boot Camp) and Boot Camp drivers afterwards. I've reserved another partition for Ubuntu, which I then split with Ubuntu's partitioning tool into 3 parts:

Swap => 2048 MB swap
/boot => 200 MB ext3
/ => ~40 GB ext4

I've then selected the /boot partition for boot loader in advanced options before installing. After installation I've booted into Win7 first to check if everything's fine and it was. Then I've tried to boot into Ubuntu, but Win7 started loading and computer restarted few seconds after. I noticed a BSOD but I forgot to turn off immediate restart for BSODs in WIn.
After that I've tried to boot again into Win7 to see if it did anything to it and the same thing happened.

1.) Can I fix Win7? Clean install is not a problem, but I'd rather fix it than go through the whole thing again.
2.) How can I make GRUB load only for Ubuntu? Clean install is not a problem.

---

