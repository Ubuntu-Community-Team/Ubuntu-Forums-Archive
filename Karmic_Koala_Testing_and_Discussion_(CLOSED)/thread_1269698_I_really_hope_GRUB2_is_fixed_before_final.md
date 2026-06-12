---
title: "I really hope GRUB2 is fixed before final"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SunnyRabbiera on 2009-09-18
Testing out karmic in virtualbox, and well GHRUB2 is a big issue it seems, making the user do a manual fsck is not good for newcomers.
GRUB2 really messed up for me, luckily I can use EXT3

---

### Post by Vanishing on 2009-09-18
> **SunnyRabbiera said:**
> Testing out karmic in virtualbox, and well GHRUB2 is a big issue it seems, making the user do a manual fsck is not good for newcomers.
GRUB2 really messed up for me, luckily I can use EXT3

what does fsck have to do with grub2?o.o
i dont really understand.:confused:
edit:
oh..and i think fsck problem is fixed now.

---

### Post by kansasnoob on 2009-09-18
The fsck problem is not solved! I just experienced it again after a fresh install of Alpha 6 and updates through Update Manager!

I have no idea what the culprit is.

As far as grub goes I recently discovered that I couldn't boot Karmic after installing with no boot-loader regardless of what options I tried to add to my existing multi-boot grub legacy.

So there is a level of frustration that should be expected with so many changes. What changes?

#1: hal deprecation

#2: Upstart

#3: Grub2 and Ext4 as default.

So, things break as a part of the development process.

Remember the integration to pulse audio?

It's waaaaaaaaaaay too soon to say any part of this sucks!

I am however looking at a proper way to downgrade from grub 2 to legacy grub.

---

### Post by SunnyRabbiera on 2009-09-18
> **Vanishing said:**
> what does fsck have to do with grub2?o.o
i dont really understand.:confused:
edit:
oh..and i think fsck problem is fixed now.

well I suspect grub, as grub2 is beta

---

### Post by Longinus00 on 2009-09-19
> **SunnyRabbiera said:**
> well I suspect grub, as grub2 is beta

This bug has been reported already. [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/427822](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/427822)

As you can see the problem is not with grub2.

---

### Post by jocko on 2009-09-19
> **kansasnoob said:**
> As far as grub goes I recently discovered that I couldn't boot Karmic after installing with no boot-loader regardless of what options I tried to add to my existing multi-boot grub legacy.
That's not a problem with grub2, as you're not using it. It's of course a problem with grub legacy. Grub legacy did not have ext4 support, unless it's the patched grub version from jaunty.
I don't see why you complain about grub2. You're not using it, so you can't say it's broken for you.
Your problems are probably easily solved by replacing your grub legacy with grub2 in the mbr of your first hard drive (but remember that karmic is still in alpha, so grub2 may still break in a future update).

---

### Post by jocko on 2009-09-19
> **SunnyRabbiera said:**
> well I suspect grub, as grub2 is **beta**
I suspect something else (perhaps something that actually affects/is affected by the filesystem, such as e2fsprogs), since karmic is **alpha**...

---

### Post by LKjell on 2009-09-19
Assume this case: You have installed 8.04 and upgrade to 9.04 your grub is not compatible with ext4 but your want to try it out so you manually convert to ext4. THEN you need to upgrade grub first then convert.

---

### Post by Funnnny on 2009-09-19
It' not that grub2 isn't compatible with ext4. I think it's maybe the problem with the timezone :-s

---

### Post by jocko on 2009-09-19
> **Funnnny said:**
> It' not that grub2 isn't compatible with ext4. I think it's maybe the problem with the timezone :-s
Yep. If you don't have the same time in the os setting as in the bios, the kernel sometimes think it has travelled through time and have a seizure...
So this has nothing to do with grub2. According to the bug report (see Longinus00's post#5) it was fixed in the last kernel update.

---

