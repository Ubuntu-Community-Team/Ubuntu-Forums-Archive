---
title: "Ubuntu Installation Problems (HD not recognized)"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by actionj317 on 2008-03-14
I have the WD1600JB 160GB ATA100 hard drive and for the past week I have been trying to install Ubuntu 7.10.  The Live CD and the alternative CD both work fine until they get to the drive partitions.  No partitions are listed at all.  After a little research, I think I have found the solution.  Linux doesnt recognize my hd.  The alternative CD gives me a list of drivers to try but as I am a noob I do not know which one is compatible with my drive.  Is there a way i can just download my driver off the internet and put it on a floppy?  I appreciate any help and I just want to get my computer running this great Linux I keep hearing about.  Thanks.  Let me know if you need anymore info.

-Josh

---

### Post by taurus on 2008-03-14
Let's see if the LiveCD really can't access your harddrive.  Open a terminal and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by actionj317 on 2008-03-14
Thanks for the reply. However, since uninstalling win 98, the live cd will not boot. when i get home from work i will reinstall and give it a try.  stupid windows.

---

### Post by actionj317 on 2008-03-14
Alright so this gets a little wierd. i decided not to reinstall 98 cuz thats not the problem.  I erased the CD-RW that had live cd on it to use the alternate installer. since then, I installed the live cd twice on the cd-rw and also on a cd-r. it has stopped recognizing the cd-rw and the cd-r stops when "adding live cd", then says "[67.499424] PCI: failed to allocate mem resource #6: 10000 f1000000 for 0000:01:00.0". I followed all the steps, burned at the slowest speed, and checked the isos for errors.

---

