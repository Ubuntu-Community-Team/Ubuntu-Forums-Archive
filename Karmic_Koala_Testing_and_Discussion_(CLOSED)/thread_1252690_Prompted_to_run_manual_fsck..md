---
title: "Prompted to run manual fsck."
date: 2009-08-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-08-29
Several times in about the past 24 hours I've been prompted to run manual fsck at reboot. Doing so shows no errors and sometimes repeated reboots will get-r-done.

Rebooting in recovery mode always works (of course after complete just selecting to boot).

Anyway, I thought my old Maxtor 30GB I use for testing was crapping a gut so I dug out a brand new 80GB WD and installed on it. Same thing!

Also same thing whether I'm using grub-2 or legacy grub. I've also checked partitions with gparted and it shows no problems.

So, right now I'm back on the old 30GB and I installed Jaunty in place of Karmic (same exact partitions) just formatted / and reused the same /home.

A dozen reboots in Jaunty and no problems:confused:

Anyhow, I thought I'd toss this out here and see if anyone else is having the same issue.

EDIT: Thought I should add that I've used ext4 filesystems in both Jaunty and Karmic so it shouldn't be an ext4 thing.

---

### Post by rajeev1204 on 2009-08-29
> **kansasnoob said:**
> Several times in about the past 24 hours I've been prompted to run manual fsck at reboot. Doing so shows no errors and sometimes repeated reboots will get-r-done.

Rebooting in recovery mode always works (of course after complete just selecting to boot).

Anyway, I thought my old Maxtor 30GB I use for testing was crapping a gut so I dug out a brand new 80GB WD and installed on it. Same thing!

Also same thing whether I'm using grub-2 or legacy grub. I've also checked partitions with gparted and it shows no problems.

So, right now I'm back on the old 30GB and I installed Jaunty in place of Karmic (same exact partitions) just formatted / and reused the same /home.

A dozen reboots in Jaunty and no problems:confused:

Anyhow, I thought I'd toss this out here and see if anyone else is having the same issue.

This was happening with the rc7 kernel due to it not shutting down and forcing a fsck.I had it every time on reboot,now upgraded to latest kernel and it doesnt happen now.

In fact i was getting dropped to a root shell with no keys running ,had to cold restart to do anything.

Now its solved.

---

### Post by NCLI on 2009-08-29
Confirmed with a brand new Velociraptor 300GB HDD.

---

### Post by pulpo69 on 2009-08-29
confirmed with one year old seagate hd.

---

### Post by rajeev1204 on 2009-08-29
Ya happening to me too. seagate sata 80 gb.

---

### Post by kansasnoob on 2009-08-29
Oh, I should also add that this wasn't happening with the -7 kernel but rather began after the -8 kernel update.

I don't think I can blame the kernel though. After two fresh installs that updated directly from -5 to -8 I think it also failed to boot -5 unless I first ran thru recovery mode.

I had noticed that the nautilus crashes had become more frequent. Maybe I should try an install w/thunar or maybe just try Xubuntu:confused:

I had tried removing palimpsest and that made no difference.

A bug report may be in order but I wouldn't know what to say in this scenario. Must thimk!

---

### Post by JohnJackson on 2009-08-29
I only experienced this with the -7 kernel

---

### Post by psyke83 on 2009-08-29
I think this is happening due to problems with the UTC clock on some machines. After some recent updates, fsck is considering the superblock last write time in the future as being a fatal error.

For example:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/405828](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/405828)
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/268808](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/268808)

I thought that I was subscribed to a different (and more complete) bug on this issue, but I can't find it.

---

### Post by kansasnoob on 2009-08-30
> **psyke83 said:**
> I think this is happening due to problems with the UTC clock on some machines. After some recent updates, fsck is considering the superblock last write time in the future as being a fatal error.

For example:
[https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/405828](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/405828)
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/268808](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/268808)

I thought that I was subscribed to a different (and more complete) bug on this issue, but I can't find it.

I'd hoped to have a response with more info but I've tried installing alpha 4 on two different drives, and all seems well until I update.

Now updates take me to a totally unbootable state.

Even if I do as before and remove or revert grub-2 to legacy grub I can't boot Karmic.

The one thing I was doing differently was installing karmics / on a non-first partition.

---

### Post by psyke83 on 2009-08-30
> **kansasnoob said:**
> I'd hoped to have a response with more info but I've tried installing alpha 4 on two different drives, and all seems well until I update.

Now updates take me to a totally unbootable state.

Even if I do as before and remove or revert grub-2 to legacy grub I can't boot Karmic.

The one thing I was doing differently was installing karmics / on a non-first partition.

It's not completely unbootable. When you're dumped to the command prompt, remount root and continue booting manually.

In other words:
```
$ sudo mount -o remount /
$ init 5
```

---

### Post by kansasnoob on 2009-08-30
Just getting back to this.

Thanks, that worked!

---

### Post by xeddog on 2009-09-06
Just thought I'd add my $.02 worth.  I am having this problem too with both the -8 and -9 kernels.  When this happens while doing a restart, there is an error message that says the last mount time was about 3 hrs 45 min ahead of the current time.  I just do the fsck, let it repair, and then reboot.

xeddog

---

