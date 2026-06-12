---
title: "are partitions preferred in 12.04"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by henry cow on 2012-05-09
I have tried several unsuccessful installations of 12.04 on various computers that were running 10.x without problems.

When I attempt to install 12.04, either Ubuntu or Xubuntu, the installation seems to be steering me towards erasing existing partitions and using the entire disk.

One one of the computers, I allowed it to do this, assuming that it might help. It didn't.

As I move down this trail, I want some opinions. In the past, I have created about 3 partitions: 1 for the OS, 1 for data, and a swap file (a couple of the boxes do not have as much RAM as I might like).

Is there any compelling reason to have partitions, or should I just let it have its way?

Thanks, Harry

---

### Post by Sef on 2012-05-09
> Is there any compelling reason to have partitions, or should I just let it have its way?


You need at least 2 partitions: swap and root. Many people have a third one for data.

---

### Post by darkod on 2012-05-09
I haven't noticed 12.04 steering you towards erasing partitions. Note that if you have errors or irregularities in the partition table on the disk, the installer would usually offer only the "erase and use whole disk" option because it can't detect the partitions correctly.

But that is a specific situation.

One new option I noticed is the "replace ubuntu" option, but that is not erasing all partitions.

Of course, you can always use the manual method (Something Else) which is recommended anyway since it gives you best control. In this case you decide what partition is used for what and the installer can't "make you" do anything you don't want.

If you give a specific case (or more of them), someone might have an idea why are you getting "weird" options during install.

---

