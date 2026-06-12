---
title: "Lucid 10.04 failed to mount"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by LinuXGo on 2010-04-30
Hi, I've recently upgrade ubuntu 9.10 to 10.04 LTS using my system update and after it had completed installing the packages. I shut down the computer.Then after I get home, I open my computer I have found out that the system is unable to mount my filesystem. I went to manual recovery, typing in fsck -y /dev/sda1  then after it runs, it said the system is clean. So then I type control d to reboot but then it said that the system I not ready or present and I continue to wait. It seemed that there's a major issue mounting partition in my computer, I'm not sure if NTFS has any involvement. What should I do next to resolve this issue?

---

### Post by LinuXGo on 2010-05-01
Bump

---

### Post by LinuXGo on 2010-05-01
It gave me the following message:

 Filesystem check or mount failed
The maintanence shell are starting

I've found only a few with this error message but they always implied that it can be resolved by the fsck command. The solution doesn't seem to work for me though, I've also had to touch forcefsck in order for it to boot, checking the hard drive for any errors. After it had finished, longer than I expected, the purple splash screen still reveals that there's any error occur while /mnt. This major issue had cause me headaches and it had never happen before, previously when I upgrade my Jaunty to Karmic it had successfully installed wonderfully. 

I also tried steps to crumble this matter, moving to a new mount point, e2fsck on the next reboot. I have absolutely no clue of the origin in this case, improbably the system had failed to recognize the mount location or that the partition is corrupted. 

I'm still waiting for an answer and if anyone had experience this situation before, please post some advice. Thanks for reading this thread

---

### Post by nhasian on 2010-05-02
please make sure to boot from the ubuntu liveCD to check your partitions while they are NOT mounted.  you can check the filesystem by going to System-> Administration-> Disk Utility or Gparted

---

### Post by madjr on 2010-05-02
i would check if the live-cd has the same problem

also check similar bug reports on launchpad

---

### Post by LinuXGo on 2010-05-02
Well the issue is that my computer had issued from booting live CD, even pressing some keys won't let the computer boot at all. So. I decided to break mount the kernel where I can spawn a shell before the partition mounts.

---

### Post by frantid on 2010-05-02
check you /etc/fstab  there have been others with comment lines not marked correctly or usb entries causing problems.

---

### Post by LinuXGo on 2010-05-02
> **frantid said:**
> check you /etc/fstab  there have been others with comment lines not marked correctly or usb entries causing problems.

well the only difference that I found was the uuid doesn't match with my disk's. I'll post the copy;

Proc /proc proc defaults 0 0
/dev/sda5 none swap sw 0 0
UUID=ac99ff4b-becc-4ad1-bceb-2437705e69ba / ext3 defaults 0 1
/dev/sr0 /mnt udf ,iso9660 defaults 0 0

---

### Post by frantid on 2010-05-03
> **LinuXGo said:**
> well the only difference that I found was the uuid doesn't match with my disk's. I'll post the copy;

Proc /proc proc defaults 0 0
/dev/sda5 none swap sw 0 0
UUID=ac99ff4b-becc-4ad1-bceb-2437705e69ba / ext3 defaults 0 1
/dev/sr0 /mnt udf ,iso9660 defaults 0 0

It definitely needs to match the right UUID, the one you posted is the root mapping.

---

### Post by LinuXGo on 2010-05-03
Alright so the UUID must match both the fstab file and the disk but I don't any comments or entries that need to be removed. Also I might the source of issue on this link: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604)

---

