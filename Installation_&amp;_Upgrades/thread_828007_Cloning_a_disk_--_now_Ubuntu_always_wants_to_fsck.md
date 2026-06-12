---
title: "Cloning a disk -- now Ubuntu always wants to fsck?"
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by randysparks on 2008-06-13
I've cloned my hard disk to a new disk using ddrescue. It went OK and the new disk boots beautifully. All the partitions were copied across. 

The trouble is that, each time Ubuntu starts, it runs fsck. This isn't an issue but it drops the splash screen and throws out a lot of output. And it doesn't even look like fsck runs a full test, but just a quick one. 

Does anybody know what's going on? I've got a feeling that the check count (tune2fs) has got screwed, and I've yet to try resetting it. 

Incidentally, I've run fsck.ext3 manually using a boot CD, and the Ubuntu file system checked out fine. I thought this might reset some kind of check flag, but the check request still happens on each boot.

---

### Post by vanadium on 2008-06-13
tune2fs is the command with which you can list and change the parameters of an ext2/3 volume.

By the way, it is normal that a quick file check is done during every boot. Perhaps there is another reason why you are dropped to the console boot screen: inspect the messages that appear. Moreover, since Hardy, the output of a lengthy file check is drawn on the graphical splash screen.

---

### Post by randysparks on 2008-06-13
> **vanadium said:**
> tune2fs is the command with which you can list and change the parameters of an ext2/3 volume.

Yes, I know. What I'm saying is that fsck only steps in after a certain count number has been passed, and my theory was that that cloning the disk had somehow bumped up this number. Hence the use of tune2fs to reset it. 

But I don't think that's right because, like you say, every boot involves an fsck. And I'm not seeing any error messages at all during boot. 

I've been looking at the dmesg output and I think the cause might be that the new disk is SATA and it's replacing an old IDE disk. I think that Ubuntu is viewing the new SATA disk as hot-swappable, rather than as an immovable boot volume, and that's what's causing the splash to drop and log messages to appear. But, as I said, everything works fine. Just a curiosity.

---

