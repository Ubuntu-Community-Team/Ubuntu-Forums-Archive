---
title: "Ubuntu 11.10 cannot login after resize with gparted"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by davideps on 2011-12-19
UPDATE: If I push "esc" under grub and enter recovery mode, I can login as myself and see all my data. So, my home directory is getting mounted (at least in recovery mode). But, when I try to boot normally I cannot login. The screen blinks, some writing comes up quickly, and then I return to the purple login screen. I created both a normal and a system user account in recovery mode using adduser to see if I could login as another user. It works fine in recovery mode but the same problem occurs when I boot normally. I can only login as guest and cannot get root access to get any trouble shooting done. As an added note, I cannot shutdown from the purple screen either. Nothing seems to happen. Since I resized my home partition and not my boot partition, I simply don't understand this behavior.

ORIGINAL POST: I'm running Ubuntu 11.10 on a laptop. I recently used Gparted to shrink an extended partition with a linux-swap and an ext3 (home) partition on it and created a 45gb ntsf partition. The laptop boots but I can only login as guest. I'm guessing it lost access to my home partition and possibly swap also. Maybe a UUID problem? Something with fstab? I'm not sure how to proceed. Gparted currently shows:
 
/dev/sda1. Ext3.  20.43gb used. 10.28gb unused. Boot flag.
/dev/sda2. Extended 267.65gb size
  /dev/sda5 linux-swap 3.99gb size
  /dev/sda6 ext3 214.98gb used. 4.38gb unused.
  /dev/sda7 ntfs. 65.83mb used. 44.23gb unused.
unallocated 2.49mb

I hope someone can provide guidance.

-david

---

### Post by davideps on 2011-12-20
After exploring this problem for the last few hours I saw a post that described this behavior as signaling not enough room on the resized home partition. Gparted and du give very different results. To be safe, I erased some files--and was finally able to login. Problem solved.

-david

---

