---
title: "swap for 1.5GB RAM and where?"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by eeried on 2006-10-11
Hello,

I installed Ubutu on someone's computer. It has 1.5GO Ram. I was stupid enough not to post this message before the install and then it was too late. As the HD is big (160GB) and I didn't really know what to do I set 2GB for the swap partition. I now think this was a stupid choice but can a too big swap partition damage performance?

My other question is : on a dual-boot (Windows-Ubuntu) where should the swap partition be (there's none on the Windows side on that computer)? I see some people put the swap partition after the Ubuntu partitions (/ and /home).

I put the swap partition just after the Windows one and before the Ubuntu / partition.

Many thanks in advance!

---

### Post by TheMono on 2006-10-11
It will be just fine as is. Don't worry about it. The location will be fine, and there's no such thing as a harmfully big swap.

---

### Post by mozetti on 2006-10-11
Like TheMono said, you're fine. For future reference, the best place for a swap partition (Windows or Linux) is the first partition on a 2nd separate physical hard drive (separate meaning a different HDD than the one the OS is installed on). This is because swap, well,  "swaps" files from RAM to the swap space as needed. If the swap partition is on the first partition of a separate hard drive, then the arm that swings over the disk doesn't have to move very far to access the swap, and it can do it's thing while the HDD for the OS is cranking away.

---

### Post by eeried on 2006-10-12
Many thanks for your messages! :-)

---

