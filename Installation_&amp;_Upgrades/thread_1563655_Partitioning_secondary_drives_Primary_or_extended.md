---
title: "Partitioning secondary drives: Primary or extended?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by jcd29 on 2010-08-29
I have my main hard drive with Ubuntu and XP, and I want to format my secondary drive purely for data in two partitions, one being ext4 and the other NTFS. Should I choose primary or extended for these partitions, or does it not matter at all?

---

### Post by cj.surrusco on 2010-08-29
It doesn't really matter. The only things that needs a primary partitions are the root filesystems for some OS's like Windows, for example. If it is just for data, there won't be any difference.

---

### Post by jcd29 on 2010-08-29
Thanks! So I'll just format both partitions in my secondary drive as extended, then.

---

### Post by jcd29 on 2010-08-29
Hmm, for some reason GParted won't let me format both partitions as Extended. Apparently one of them has to be primary?

Edit: Nevermind, just saw my mistake. I had to make both primary, since extended wouldn't let me choose the filesystem.

---

### Post by srs5694 on 2010-08-29
There are *three* (not two) partition types in the Master Boot Record (MBR) scheme:


[list]
[*]**primary** -- There can be a maximum of four primary partitions on an MBR disk. They're defined in the first sector of the hard disk. As others have said, some OSes, such as Windows, insist on booting from primary partitions.
[*]**extended** -- This is a special type of primary partition that serves as a placeholder for the next type. Extended partitions don't hold filesystems; you can't create "an ext3 extended partition." Rather, they hold an arbitrary number of logical partitions. Most tools impose a limit of one extended partition per disk.
[*]**logical** -- These partitions reside inside an extended partition. For all practical purposes, you can have as many logical partitions as you like; however, because they're all contained within a single extended partition, they must be contiguous -- you can't have two logicals, a primary, and then another logical partition. Like primaries, logicals contain filesystems (ext3fs, NTFS, etc.).
[/list]


It's certainly possible to create a disk with a single extended partition and logical partitions within it, with no primary partitions. Some disk utilities might refuse to do this, but there's nothing in the rules that says it can't be done, and some utilities (such as Linux fdisk) will certainly do it. I don't know offhand if GParted will create such a setup. Since it's meaningless to create an extended partition with a filesystem, though, GParted won't do it.

The distinction between extended and logical partitions seems to be what's caused your confusion, jcd29.

---

### Post by jcd29 on 2010-08-30
> **srs5694 said:**
> There are *three* (not two) partition types in the Master Boot Record (MBR) scheme:


[list]
[*]**primary** -- There can be a maximum of four primary partitions on an MBR disk. They're defined in the first sector of the hard disk. As others have said, some OSes, such as Windows, insist on booting from primary partitions.
[*]**extended** -- This is a special type of primary partition that serves as a placeholder for the next type. Extended partitions don't hold filesystems; you can't create "an ext3 extended partition." Rather, they hold an arbitrary number of logical partitions. Most tools impose a limit of one extended partition per disk.
[*]**logical** -- These partitions reside inside an extended partition. For all practical purposes, you can have as many logical partitions as you like; however, because they're all contained within a single extended partition, they must be contiguous -- you can't have two logicals, a primary, and then another logical partition. Like primaries, logicals contain filesystems (ext3fs, NTFS, etc.).
[/list]


It's certainly possible to create a disk with a single extended partition and logical partitions within it, with no primary partitions. Some disk utilities might refuse to do this, but there's nothing in the rules that says it can't be done, and some utilities (such as Linux fdisk) will certainly do it. I don't know offhand if GParted will create such a setup. Since it's meaningless to create an extended partition with a filesystem, though, GParted won't do it.

The distinction between extended and logical partitions seems to be what's caused your confusion, jcd29.

That seems to be it, yup! Thanks man.

I could've made an extended partition with two logical partitions then. But I left it as two primary partitions, which should be fine, right?

---

### Post by srs5694 on 2010-08-30
> **jcd29 said:**
> I could've made an extended partition with two logical partitions then. But I left it as two primary partitions, which should be fine, right?

Yes. The probability of this decision coming back to haunt you is very low -- probably under 1%. The only possible issues I can think of are these:


[list]
[*]Logical partitions use a linked-list data structure to define them, whereas primary partitions are defined in the main Master Boot Record (MBR) partition table. This actually makes primary partitions a little more robust against certain types of damage to their data structures. This factor works in favor of primary partitions; however, the risk of losing logical partitions is pretty small, so it's not a big advantage.
[*]If you need to add more partitions in the future (presumably after resizing one or both of the current partitions), you'll be limited to two primaries or one primary and as many logicals as you like. This could be an issue if you want to install more than one OS that requires a primary partition to boot.
[/list]


There may be other issues, but if so I can't think of what they might be just now.

---

### Post by cj.surrusco on 2010-08-30
> **jcd29 said:**
> That seems to be it, yup! Thanks man.

I could've made an extended partition with two logical partitions then. But I left it as two primary partitions, which should be fine, right?

Yeah, you wouldn't need to mess with an extended partition. You can make up to four primary partitions anyway, if you ever plan on adding a few more partitions.

---

