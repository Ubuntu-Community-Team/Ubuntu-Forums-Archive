---
title: "How do you Delete Windows?"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by Zachzee on 2011-11-02
I have Dual boot system one side with Ubuntu the other with windows xp i was wondering if there was any way to delete the partition with windows (and give me back the space for Ubuntu.) on it without messing up the boot loader? 
other specs  1 Tera-byte hard-drive about 750gb Ubuntu and about 250 windows.

---

### Post by gordintoronto on 2011-11-03
You could use Gparted to reformat the Windows partition. Assuming Windows was installed first, I don't think you can expand the Linux partition to include that space. However, in the file manager it will show up as something like "230 GB Filesystem" in the top-left of the window. Click on it and you're there; you can create folders, paste files, etc.

---

### Post by darkod on 2011-11-03
Yes, the process would go something like:

1. In Ubuntu with Gparted delete the XP partition.
2. Run sudo update-grub which will delete the XP entry from the boot menu since it can't find the partition any more.
3. You can either format the newly created unallocated space as another ext4 partition and use it in ubuntu, or expand the ubuntu partition onto the unallocated space.

If ubuntu is installed inside extanded partition (as default) that means you will leave your disk with no primary, only one extended partition. It can work like that, although personally I find it weird.

---

### Post by rng on 2011-11-03
If you have 1 Terabyte disk, why don't you just shrink windows partition to about 50gb (or even less) and you will get 200gb of free space to put another partition or to expand ubuntu partition. You never know when you may need that OS. But one should defragment windows partition before shrinking it. This way the bootloader will also not be affected.

---

