---
title: "[SOLVED] Fedora 8 beside Ubuntu?"
date: 2008-03-06
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-03-06
I can't install Fedora 8 anywhere (of 4 hard disks).

I tried 3 unused, unpartitioned disks for the install sda, sdc, sdd, but even with option 'Remove all partitions and create default layout', the return is 'Could not allocate requested partitions', for all 3 disks.

So I tried the sdb disk, where Ubuntu is loaded, and went with option 'Use free space on selected drive, with default layout'.

Same return as for the other 3 drives.:confused:

Help?

---

### Post by empthollow on 2008-03-07
i used to use fedora but haven't messed with it since 5.  anyway, the first thing i would check is that the cd does not have a defect.  i've had alot of bad disc images when downloading with a web browser.  if there isn't a verify disc on the cd - last i used fedora there was such an option- then check the md5sums on the .iso file.  the reason i suspect this is because it happened with multiple hard drives.

---

### Post by buccaneere on 2008-03-07
> **empthollow said:**
> i used to use fedora but haven't messed with it since 5.  anyway, the first thing i would check is that the cd does not have a defect.  i've had alot of bad disc images when downloading with a web browser.  if there isn't a verify disc on the cd - last i used fedora there was such an option- then check the md5sums on the .iso file.  the reason i suspect this is because it happened with multiple hard drives.

Thanks there empt...

I'm sure that's possible - a bad burn, but the CD is a pro burn that came with '_Fedora 8 and Red Hat Enterprise Linux Bible_'. THey packed a DVD too, but I've just tried the CD Live disc before swappin' the optical drive with my other desktop.

I think I have a setting wrong somewhere, that's stoppin' the load...

:confused::confused::confused:

---

### Post by empthollow on 2008-03-07
yeah, if you have an official disc, the disc is most likely not the problem.  The next thing that comes to mind is needing to set the root and swap partitions but being that you've tried the "default layout" that doesn't seem to be the problem either.  I'll let you know if i think of anything else but i'm drawing a blank right now.

---

### Post by buccaneere on 2008-03-10
> **empthollow said:**
> yeah, if you have an official disc, the disc is most likely not the problem.  The next thing that comes to mind is needing to set the root and swap partitions but being that you've tried the "default layout" that doesn't seem to be the problem either.  I'll let you know if i think of anything else but i'm drawing a blank right now.

You're onto somethin' here - the root and swap partition assignments.

That's the message on two machines - 'assign root partitions'. I don't know why default doesn't work - I just know it doesn't.

Nor do I know how to assign root partitions. Is that done from the first boot log-in, or from the second-boot live boot???

---

### Post by empthollow on 2008-03-10
you have to assign the partitions when you partition the drive.  This is a utility on the install disc.  pick a partition for your filesystem and assign '/' to it.  this specifies root.  choose a partition that is roughly 2 times the size of the amount of ram you have e.g. you have 512mb ram, use 1gb partition for swap.  This is not a law and there are different schools of thought on how big you should make your swap partition.  this is just what i do.  So.... chose a partition and assign it swap.  If they haven't changed the installer too much there should be a continue button, it will ask you what programs you want to install and then the installation will begin.

---

### Post by buccaneere on 2008-05-11
The problem was caused by my KVM switch.

It is not a faulty switch, that I know of; it did switch function properly...

???

---

### Post by empthollow on 2008-05-11
Glad you solved the problem.  Weird that the kvm was a problem.  I know i used to use fedora w/ a kvm.  :guitar:

---

