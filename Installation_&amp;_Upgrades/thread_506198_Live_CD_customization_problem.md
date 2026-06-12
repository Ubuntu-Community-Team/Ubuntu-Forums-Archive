---
title: "Live CD customization problem"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by phenest on 2007-07-21
Not a new subject, but a problem that I have no idea how to fix. I have followed the guide on this page: [https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization") and have managed to extract the CD contents. The problem is when I have to put the CD together. I cannot chroot to the edit folder:
```
steve@computer:~/live$ sudo chroot edit
chroot: cannot run command `/bin/bash': Permission denied

```
If I can't chroot, then I can't use mkinitramfs. Or can I? Or do I need to?

My reason for the customization is to rename 2 driver modules as the drivers crash the system. This prevents me from using the LiveCD at all. I have renamed the modules, built the iso (without using chroot or mkinitramfs) and I can boot from it fine using qemu. But if I boot the computer using the LiveCD, it still crashes.

---

### Post by phenest on 2007-07-21
Update:

I have 2 computers, a Philips X56 laptop and an HP Pavilion 8750. Both running Feisty. Both fresh installs. The X56 will not accept the command chroot (but will from the Live CD), but the Pavilion will with no problems.

I need ideas, please?

---

### Post by phenest on 2007-07-21
Well, what can I say? I thought of a difference between these 2 computers and voila!

The difference? The Pavilion has 2 partitions: 1st root, 2nd swap. The laptop has 3: the 3rd is home. Yep! I was running this script from home on both machines. I moved the script to the /tmp directory in root, and chroot worked.

Now why is that? Doesn't my home directory have sufficient permissions when on a separate partition?

---

