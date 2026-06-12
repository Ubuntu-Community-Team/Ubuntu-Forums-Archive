---
title: "Upgrade to 14.04.1 failed, RAID-1 mdadm, Boot Repair"
date: 2014-08-24
forum: Installation &amp; Upgrades
---

### Post by atp2 on 2014-08-24
I tried to upgrade a desktop to Ubuntu 14.04.1 by running "sudo update-manager -d".  I think this machine was previously running 12.04.3, but I'm not entirely sure now; it might have been 13.something.

During the upgrade, the "Distribution Upgrade" window froze during its "Installing the upgrades" step, while saying, "Preparing gnome-icon-theme-full".  I waited nearly an hour and it never made any more progress.

At that point, X-Windows still seemed to be working, and I *could* ssh into the machine, but various other things were very broken (shared library errors), including sudo.  Trying to do sudo anything immediately concluded that all my password attempts were wrong, without ever giving me a chance to actually type a password!  Like this:

```

[atp@kou ~]$ grep DESCRIP /etc/lsb-release
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"
[atp@kou ~]$ ps
ps: error while loading shared libraries: libprocps.so.3: cannot open shared object file: No such file or directory

[atp@kou ~]$ sudo ls
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts

```

sudo has a -S option to tell it to read the password from stdin like so, but that still failed with the exact same "3 incorrect password attempts" message:

```
echo mypassword | sudo -S ls
```

So at that point I restarted the machine, and discovered that it would *not* boot at all.  No grub boot prompts at all, nothing.

So I used the Ubuntu 14.04.1 Server AMD64 disk (which seems similar to the old "Alternate Install" disks) to try to re-install *without* re-formatting my partitions or deleting data.  I also tried the [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") disk.  After several rounds of both of those, things look slightly better, but I still can't boot the machine.

I strongly suspect that the problem is related to RAID and grub2.  This machine uses Linux software RAID-1 (*not* fakeraid) with 3 disks; the third disk is a hot spare.  All three disks are partitioned exactly the same way:

```

sda1, 150 GB, ext4, / (root partition)
sda5,   8 GB, swap
sda6, 842 GB, xfs, /data

```

So there are three md RAID volumes, one for each of the three partitions.

Currently the machine halfway boots and then gets stuck in some sort of mdadm loop.  First I see the [error: diskfile writes are not supported]("http://askubuntu.com/questions/468466/why-this-occurs-error-diskfilter-writes-are-not-supported") message due to [bug 1274320]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1274320").  But AFAICT, that isn't actually the cause of my boot problems, as after a few seconds the boot proceeds, and I see kernel dmesg output scroll by.

But then the boot gets stuck saying this over and over again, seemingly forever:

```

Incrementally starting RAID arrays...
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
Incrementally started RAID arrays.

```

I used the Boot Repair disk to record info about my system, it is here:  [http://paste.ubuntu.com/8135727/](http://paste.ubuntu.com/8135727/)

Some of that doesn't seem right to me but I have zero previous experience messing around with grub2 and mdadm, so I don't know what it's really *supposed* to look like.

Help?  (Thanks in advance...)

---

### Post by sduensin on 2014-10-05
Did you ever find a solution to your RAID boot getting stuck?  I just upgraded from 12.04 to 14.04 as well.  Same thing.  I've been arguing with it for two days.  :-(

---

### Post by atp2 on 2014-10-06
> **sduensin said:**
> Did you ever find a solution to your RAID boot getting stuck?  I just upgraded from 12.04 to 14.04 as well.  Same thing.  I've been arguing with it for two days.  :-(
No, not exactly.  I ended up doing another re-install, but this time formatting the partitions, and that worked.  So it seems that the re-format wiped out some sort of bad state or settings, and that fixed things.  But why, I don't know.

---

### Post by sduensin on 2014-10-06
Thanks for answering.  I tried the reinstall here.  Same results.  

However, I did manage to fix it.  Now here's the weird part...   Nothing was wrong with the mdadm array!  My system has two SSDs in software RAID1 to boot from.  After that, it brings up a 10-drive ZFS array.  One of the drives in the ZFS array was fried.  (Actually fried - like scorch marks on the board and everything!)  During startup, the kernel reported a gazillion errors about that bad drive.  No problem.  I was just ignoring it until I could get booted and tell ZFS to remove it.  Except I never got that far.  In frustration (and because I needed to start the RMA), I yanked out the bad drive.  Box fired right up.

WTF?  Sometimes I _love_ computers.  :-P

---

