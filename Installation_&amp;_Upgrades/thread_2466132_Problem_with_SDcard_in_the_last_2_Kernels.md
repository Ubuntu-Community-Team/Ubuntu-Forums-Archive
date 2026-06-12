---
title: "Problem with SDcard in the last 2 Kernels"
date: 2021-08-20
forum: Installation &amp; Upgrades
---

### Post by hk42 on 2021-08-20
On my mini PC (Z8350 IIRC) my home directory is mounted from an ext4 partition on 
the SDcard.
mmcblk2p1 is NTFS used by W10
mmcblk2p2 is mounted  as /home
Since the last 2 updates I was stuck at boot with a message saying that a mount job was
waiting for mmcblk2 and a 1.30 minutes timer.
By chance I also have the low latency kernel witch is not yet affected.
I found a solution :
During boot but before the message remove the SDcard and reinsert it.
It can even be useful to protect from unauthorised access :-)

bilou@bt3-pro:~$ uname -a
Linux bt3-pro 5.11.0-27-generic #29~20.04.1-Ubuntu SMP Wed Aug 11 15:58:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
HTH

---

### Post by MAFoElffen on 2021-08-21
And did you verify that the filesystems on that SDcard are okay?

---

### Post by hk42 on 2021-08-21
I forgot to tell that I have the same problem on 2 completely different set up.
To me it looks as if the driver/module for the SD-card reader was not loaded at boot
if there is an SD-card in it.
I have the same error for the Windows partition on the same card.
Both work  after the trick I explained.

---

### Post by hk42 on 2021-09-14
I found  a more permanent solution it is to use only UUID in fstab.
In fact since the beginning internal EMMC was called mmcblk0 and the SD-card mmcblk2
With no mmcblk1
The last kernels seemed to mix all that with random results.

---

### Post by MAFoElffen on 2021-09-14
Yes. Always a good idea of using the UUID's as the pointer to in fstab.

So this is "Solved"? If so, please use the 'Thread Tools' link in the upper right of the page to mark as 'Solved' so others may find answers to their similar problems.

---

### Post by hk42 on 2021-11-15
In fact I found a better solution:
Instead of the rather obscure UUID this is what I now use in my /etc/fstab file:
LABEL=LINUXhome       /home ext4 errors=remount-ro 0  1
# UUID=93d606c2-4141-4ac6-92e4-8bad316dbffc /home ext4 errors=remount-ro  0   1
It seems it even works for swap provided you give a name to your swap partition.

---

