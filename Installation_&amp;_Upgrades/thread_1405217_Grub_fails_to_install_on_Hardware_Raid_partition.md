---
title: "Grub fails to install on Hardware Raid partition"
date: 2010-02-12
forum: Installation &amp; Upgrades
---

### Post by shaiss on 2010-02-12
No matter which ubuntu version at 95% through the install it will complain that grub failed to install.

I'm installing this on an HP XW6600 with hardware raid striped.

I can use the supergrub rescue CD to boot to ubutu after, but whatever I do doesn't seem to get grub installed.  

Any ideas on how to proceed?  I'm guessing I need to install grub from scratch.

---

### Post by darkod on 2010-02-12
Do you have an actual hardware raid or motherboard BIOS raid, so called fakeraid?
Maybe this will give you some idea:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Also, for raid you need to use the Alternate Install CD image, not the standard Desktop CD. That might be the problem.

---

### Post by shaiss on 2010-02-12
Unfourtunatly it is fakeraid.  The thing that gets me is why the supergrub disk can boot and why grub can't even install on the raid array.  BTW, under the Ubuntu Live disk, it shows filesystem 308GB, which is the combined amount of both drives.

But, under gparted you see two unpartitioned 150gb drives.  

I'm going to try the install of the alternate disk and report back.

---

### Post by darkod on 2010-02-12
> **shaiss said:**
> Unfourtunatly it is fakeraid.  The thing that gets me is why the supergrub disk can boot and why grub can't even install on the raid array.  BTW, under the Ubuntu Live disk, it shows filesystem 308GB, which is the combined amount of both drives.

But, under gparted you see two unpartitioned 150gb drives.  

I'm going to try the install of the alternate disk and report back.

I don't think Gparted would be able to recognize them as raid because it's fakeraid. I'm not experienced too much in raid, but I think you only need to reinstall/reconfigure grub2. In that article I linked just focus on the section of installing/configuring grub2. You already have karmic installed and the alternate cd would do the same. The difference is, it seems to install grub better on raid than the desktop cd.

---

