---
title: "Double installation"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by jburkhart on 2009-12-17
I installed Ubuntu 9.04 twice on my Dell laptop without realizing it. I am running Ubuntu on a partitioned HD so have the choice of using WinXP while I become used to Ubuntu.  How do I remove one of the two Ubuntu installs?  Thanks for any help.

---

### Post by raymondh on 2009-12-17
> **jburkhart said:**
> I installed Ubuntu 9.04 twice on my Dell laptop without realizing it. I am running Ubuntu on a partitioned HD so have the choice of using WinXP while I become used to Ubuntu.  How do I remove one of the two Ubuntu installs?  Thanks for any help.


Just to double-check .... you mean 2 ubuntu root (system) installs or,  2 kernels?

You can use the liveCD and in live session access gparted (system > admin > partition editor) to remove the unwanted  root install.

Here's the [documentation on gparted.]("http://gparted.sourceforge.net/larry/resize/resizing.htm")

---

### Post by jburkhart on 2009-12-17
I'm really new at this, so bear with me... It appears to be two kernels, although when I get the boot screen for a choice of which OS to boot, I have Ubuntu, then WinXP, then Ubuntu again and the two different Ubuntu choices are different as I had different desktop displays on the two different Ubuntu choices. Root or Kernel?

---

### Post by dhavalbbhatt on 2009-12-17
> **jburkhart said:**
> I'm really new at this, so bear with me... It appears to be two kernels, although when I get the boot screen for a choice of which OS to boot, I have Ubuntu, then WinXP, then Ubuntu again and the two different Ubuntu choices are different as I had different desktop displays on the two different Ubuntu choices. Root or Kernel?

Can you do a screen print of your GRUB menu? If you can't do that, do type up the two Ubuntu versions that you see during GRUB boot up.

---

### Post by raymondh on 2009-12-17
> **dhavalbbhatt said:**
> Can you do a screen print of your GRUB menu? If you can't do that, do type up the two Ubuntu versions that you see during GRUB boot up.

either a print screen or ... in ubuntu, access a terminal (applications > accessories) and type

```
sudo fdisk -l
```

small L.  Copy and paste back the results in your next post.

---

