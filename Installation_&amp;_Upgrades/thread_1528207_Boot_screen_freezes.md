---
title: "Boot screen freezes"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by mohanradhakrishnan on 2010-07-10
Hi,
I am trying to boot ubuntu but the initial screen just freezes. It does not process after that. It could be caused by frequent power loss when the PC is on.
 
How do I run fsck by booting in safe mode ? When this happens even the automatic fsck does not run.
 
Thanks,
Mohan

---

### Post by tommcd on 2010-07-10
> **mohanradhakrishnan said:**
> 
I am trying to boot ubuntu but the initial screen just freezes. It does not process after that. It could be caused by frequent power loss when the PC is on.
Well, there is no computer operating system known to man that will continue to run when the power goes out! So either get a UPS, a backup generator, or try using Ubuntu when the power is more reliable. Also, if the voltage supplied to the computer is not stable, this could cause problems as well.

How did you burn the Ubuntu CD? If you are burning the Ubuntu CD from Windows, try using Iso Recorder or Infra Recorder, and be sure to burn the Ubuntu CD at the *slowest possible speed*.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Then, when you boot the Ubuntu CD, first choose the option: *check CD for defects* and let that run. If it reports no errors, then the CD is good.
 > **mohanradhakrishnan said:**
> 
How do I run fsck by booting in safe mode ? When this happens even the automatic fsck does not run.

There is no "automatic fsck" on the Ubuntu live or alternate CD. Both CDs walk you though installing Ubuntu. They both include a section for partitioning your hard drive that offers you several options.
If you wish to run fsck from safe mode then just run:
```
sudo fsck /dev/sd**X**
```
Or if you prefer cfdisk:
sudo cfdisk /dev/sd**X**
Where **X** is the hard drive that you want to partition.
Better yet, go grab a Parted Magic live CD and use it for all your partitioning needs:
[http://partedmagic.com/](http://partedmagic.com/)
Hope this helps!

---

### Post by mohanradhakrishnan on 2010-07-10
I am not using a live CD. Sometimes when the boot screen appears I see a file repair utility running. I thought that this is like the Disk check utility in Windows.
 
I see some more boot options in grub like the one for memtest. Can't I boot into one of those and run fsck or something like that to check why the screen freezes ?

---

### Post by tommcd on 2010-07-10
> **mohanradhakrishnan said:**
> I am not using a live CD. Sometimes when the boot screen appears I see a file repair utility running. I thought that this is like the Disk check utility in Windows.
Yes, you are right. The fsck utility is similar to the disk check utility in Windows.
If you have a *reliable* Ubuntu live or alternate CD (or almost any linux live CD) you can boot from that and choose to run
"*sudo fsck /dev/sdXY* on any partition you want. I suggest a live CD because you should not run fsck on a partition that is mounted.
  > **mohanradhakrishnan said:**
> 
I see some more boot options in grub like the one for memtest. Can't I boot into one of those and run fsck or something like that to check why the screen freezes ?
You could boot into recovery mode and run fsck on any partition *except* your root partition. To run fsck on the root partition you will need to boot from another distro (if you have more than one linux installed) or a live CD, since the partition that is being fsck'ed should not be mounted at the time.

---

