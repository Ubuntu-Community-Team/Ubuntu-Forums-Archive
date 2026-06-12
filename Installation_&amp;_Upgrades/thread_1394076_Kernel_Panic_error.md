---
title: "Kernel Panic error"
date: 2010-01-30
forum: Installation &amp; Upgrades
---

### Post by bimboyin on 2010-01-30
Hi!

Yesterday I upgraded my ubuntu 9.10 from software center and then I turned off my computer. Today can't run the SO. The error when I choose the 2.6.31-17-generic kernel is the following:

[ 1.097071 ] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)

now I have to use another version of kernel (2.6.31.-14-) and it works, but not the sound.... The ubuntu upgrades always give me problems. The last time I did I had to reinstall ubuntu.

While my ubuntu doesn't work I have to use Windows...and I hate it =(

Thanks!

---

### Post by error420 on 2010-01-30
> **bimboyin said:**
> Hi!

Yesterday I upgraded my ubuntu 9.10 from software center and then I turned off my computer. Today can't run the SO. The error when I choose the 2.6.31-17-generic kernel is the following:

[ 1.097071 ] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)

now I have to use another version of kernel (2.6.31.-14-) and it works, but not the sound.... The ubuntu upgrades always give me problems. The last time I did I had to reinstall ubuntu.

While my ubuntu doesn't work I have to use Windows...and I hate it =(

Thanks!


I also received the same type of kernel panic error after updating my ubuntu server yesterday. I can't tell you how to solve it but for now I recommend you grab whatever data you need from the broken install. Boot off the live CD and choose "try ubuntu" then browse for your HDD and copy your work/files to a safe place.

---

### Post by garvinrick4 on 2010-01-30
> **bimboyin said:**
> Hi!

Yesterday I upgraded my ubuntu 9.10 from software center and then I turned off my computer. Today can't run the SO. The error when I choose the 2.6.31-17-generic kernel is the following:

[ 1.097071 ] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,2)

now I have to use another version of kernel (2.6.31.-14-) and it works, but not the sound.... The ubuntu upgrades always give me problems. The last time I did I had to reinstall ubuntu.

While my ubuntu doesn't work I have to use Windows...and I hate it =(

Thanks!
Can you run it in recovery mode of -17.

---

### Post by bimboyin on 2010-01-30
No I can't. Some friends of mine happened the same with the updating of yesterday...and more people in the forum as well.

---

### Post by shahani.w on 2010-01-30
I had the same problem when I rebooted after the updates yesterday (29/1/10).

Followed the instructions in [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210)

Worked fine with only step A.

---

### Post by bimboyin on 2010-01-31
It works!! Thanks!
I fixed it.

---

### Post by thinhhanh on 2010-02-01
Beautiful, it worked for me too.  It's just very annoying that we get into grub boot issues with Wubi every time there's a new kernel upgrade (3-4 times already).  Wubi is such a nice solution, the developers may want to make it more robust to encourage Windows users to switch over.

Anyways, thank you guys for saving me a new re-install.

---

