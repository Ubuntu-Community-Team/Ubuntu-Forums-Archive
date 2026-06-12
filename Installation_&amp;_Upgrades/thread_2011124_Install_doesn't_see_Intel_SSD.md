---
title: "Install doesn't see Intel SSD"
date: 2012-06-26
forum: Installation &amp; Upgrades
---

### Post by deeppow on 2012-06-26
OK, gave up on 12.04 so tried 10.04.3 which does get past the problems 12.04 has.  However, in the installation process it doesn't find my Intel 510 SSD that has Windows 7 on it.  I want to install side by side to dual boot so this is necessary.

Suggestion?

---

### Post by darkod on 2012-06-26
It doesn't find the disk at all or it doesn't detect the win7 on it?

Can you boot into live mode with the cd and post the output of:
```
sudo fdisk -l
sudo parted /dev/sda print
```

---

### Post by deeppow on 2012-06-26
Good suggestion darkod!  With the "sudo fdisk -l" in the live-mode, it sees all the drives.  I'm on another machine so can't copy the output.

---

### Post by deeppow on 2012-06-26
If I try to install once in the live-mode, it still doesn't see Windows.  I've not done the specify partitions before so am weir of that.

---

### Post by darkod on 2012-06-26
People tend to play with SSDs in raid. If the disk has been used in raid the ubuntu installer might ignore it. You will need to open terminal in live mode and remove the raid meta data remains with:
sudo dmraid -E -r /dev/sda

NOTE: DO NOT do this if you are running raid, but you would have mentioned it if you are.

EDIT: I see in your signature that you also have raid5 array. Be careful on which disk you run that command. Run it on the SSD only.

---

