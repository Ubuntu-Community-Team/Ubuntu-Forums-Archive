---
title: "Is there a way to install Ubuntu into serveral computers at once?"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by asaren on 2008-11-05
Hi,

Is there a way to install Ubuntu into serveral computers at once?

Thank you

---

### Post by yota on 2008-11-05
Hi,

you can just install on one and clone on many, taking care of reconfiguring only what is subject to be different from pc to pc.
You can clone with the tool you like more: all the disk with dd (or even ghost), only the filesystem with cp or tar for instance.
Most of the times the image can be restored on the target using a live-cd or by removal-write on another machine-restore of the hard drive.

But if you want an army of clones with the least effort probably you should look at a terminal server solution [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

What are you exactly trying to accomplish?

---

### Post by asaren on 2008-11-05
> **yota said:**
> Hi,

you can just install on one and clone on many, taking care of reconfiguring only what is subject to be different from pc to pc.
You can clone with the tool you like more: all the disk with dd (or even ghost), only the filesystem with cp or tar for instance.
Most of the times the image can be restored on the target using a live-cd or by removal-write on another machine-restore of the hard drive.

But if you want an army of clones with the least effort probably you should look at a terminal server solution [https://help.ubuntu.com/community/UbuntuLTSP](https://help.ubuntu.com/community/UbuntuLTSP)

What are you exactly trying to accomplish?

Thank you a lot Yota
I just want to find a way to save the time for installing Ubuntu on every computers in my office. That's all.

---

