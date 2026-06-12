---
title: "System won't start after an upgrade"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by skamarla on 2011-03-27
Hi,

I talked a friend into trying Ubuntu, and installed it via wubi. So far, he likes it a lot, but today I checked his computer out, and saw that he had a lot of updates pending. There was a kernel update, openoffice, grub, the whole lot. So, I started the update, and, when it finished, the system froze.

I restarted the PC, but now Ubuntu says that the root partition is not ready. When I open a diagnostic shell, it says "Root filesystem check failed". However, an fsck works just fine, and I can see all the files in both Ubuntu and Windows.

There's only one real disk, as far as I can see, /dev/sda1, and it's the Windows disk. The Linux root is a /dev/loop5 which points to a file under Windows. I suppose it's the wubi way, although I'm not familiar with that.

There's a possibility that the Windows disk had errors while I was running Ubuntu; in fact, Ubuntu said something to the effect while booting the first time it failed.

What can I do to boot normally?

---

### Post by Rubi1200 on 2011-03-27
Hi,
at this point can you please say what boots and what does not?

Is Windows booting normally?

If there was a GRUB update, then it is the likely cause of the symptoms you are seeing.

For Wubi issues and solutions, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

problem #2. solution #1 usually works best.

Don't forget to apply the Permanent Fix back in Ubuntu, including locking the grub-* packages to prevent this happening again.

If at all unsure, post the results of the boot info script and I will take a look.

---

### Post by skamarla on 2011-03-27
Yes, Windows boots normally.

I have tried the solution you mention, removing the first part of grub.cfg, but it didn't work. My main problem is that the root directory is mounted read-only. The rest looks OK, all the files are there and they seem to be intact. 

I have tried to run the boot info script, but it just hangs and generates nothing. I have even tried running it from a USB stick so it would have something writable to leave the results, but it didn't work.

Here is the backup copy of grub.conf before all the modifications.

---

### Post by Rubi1200 on 2011-03-28
I would start by first running a chkdsk in Windows:
[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)

Then, if it reports no errors, try running the boot script again.

If there are errors, keep running it until there are none.

---

### Post by skamarla on 2011-03-28
Chkdsk shows no errors.

The boot info script fails. I have done some debugging, and the first problem was that it was trying to create a directory in /tmp/, and this, like the whole filesystem, is in read-only mode, so it got stuck in an endless loop.

After changing the script to leave the results in the Windows disk, the script completes, but it still doesn't create the RESULTS.txt file. I think the boot info script designers didn't think of that problem. Can't blame them.

Anyway, the problem is definitely the fact that /dev/loop0 is mounted read-only. The mount options are errors=remount-ro. I suppose something goes wrong when mounting, and then it gets mounted as read-only. I have searched everywhere in /var/log, though, and I can't see any disk errors. Where else can I look?

On the other hand, I'm surprised that the system failed while doing a kernel upgrade, but grub still shows only the earlier kernel. I guess there are some processes that still need to be performed, and perhaps this is what prevents the /dev/loop0 from coming up properly.

Any ideas on these leads?

---

### Post by bcbc on 2011-03-29
So you have booted a live CD/USB and fsck'ed the root.disk? When you loop mount the root.disk it doesn't give you any errors, but it mounts it read only when you boot from it?

When you mount it, how much space does it say there is remaining? (after mounting use df and check /dev/loop*n*)

Did you try booting a previous kernel, or booting in recovery mode? Any difference?

---

### Post by skamarla on 2011-03-29
I'm not home right now so I can't test it, but yes, I have booted with System Rescue CD, and I can mount and fsck the loop0 filesystem. There is plenty of free space, too.

There are no previous kernels. I installed it a couple weeks ago, and this was the first update. Recovery mode doesn't make any difference.

---

### Post by Rubi1200 on 2011-03-29
If you can mount the file-system from a LiveCD, then surely you can run the boot info script?

---

### Post by skamarla on 2011-03-29
I guess you can run the boot info script even if you haven't booted with that disk.

OK, I'll try that this evening and will get back to you.

Thanks,

---

### Post by bcbc on 2011-03-29
> **skamarla said:**
> I'm not home right now so I can't test it, but yes, I have booted with System Rescue CD, and I can mount and fsck the loop0 filesystem. There is plenty of free space, too.

There are no previous kernels. I installed it a couple weeks ago, and this was the first update. Recovery mode doesn't make any difference.
When you say System Rescue CD, what exactly is that?
When you say fsck the loop0 filesystem, do you mean you fsck'ed the /<mountpoint>/ubuntu/disks/root.disk file, or the /dev/loop0 file system. You need to fsck the file (without mounting it.)

---

### Post by skamarla on 2011-03-29
[System Rescue CD]("http://www.sysresccd.org/") is a Live CD full of tools for system recovery. It's quite useful.

So I booted from that, mounted the windows disk, and tried

```
prompt# fsck /mnt/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.18
e2fsck 1.41.12 (17-May-2010)
/mnt/win/ubuntu/disks/root.disk: clean, 139977/1073152 files, 1046993/4286464 blocks
```

Then I mounted the loop filesystem, by doing
```
prompt# mkdir /mnt/loop
mount -o loop /mnt/win/ubuntu/disks/root.disk /mnt/loop
```

The filesystem looked healthy. I even went to the home directory, created, read, and deleted a file.

Boot Info Script tries to debug whatever is running at the moment, so it tried to debug the Live CD. No chance there.

I feel it must be something really trivial here, which prevents the loop filesystem from going read/write under Ubuntu, but I'm at a loss. Perhaps some housekeeping pending from the botched kernel upgrade?

Thanks for your time, BTW

---

### Post by bcbc on 2011-03-29
I suppose you could chroot into the wubi install and try to repair it - depending on where the system froze. The question is also why it froze, and whether a reinstall would be simpler.

```
mkdir /mnt/loop
mount -o loop /mnt/win/ubuntu/disks/root.disk /mnt/loop
for i in dev proc sys dev/pts; do mount --bind /$i /mnt/loop/$i; done
chroot /mnt/loop
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
```

Try some fixes... e.g. 
update-initramfs -u
apt-get update
apt-get upgrade
dpkg-reconfigure ...
etc...

Exit chroot:
```
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys; do umount /mnt/loop/$i; done
```

---

### Post by skamarla on 2011-03-30
That was it! :D :D :D :D

I followed your instructions (I only had a slight problem with chroot, because System Rescue CD expected zsh, so I had to do a # SHELL=/bin/bash chroot ...)

It took a while (basically, it repeated the upgrade that had been interrupted), but the loop partition became usable.

Then I found the grub.cfg problem reported in problem #2 solution #1 of the Wubi [megathread]("http://ubuntuforums.org/showthread.php?t=1639198#post10207564"). I followed the instructions (included locking future grub upgrades), and that's it!

Thank you all for your patience!

---

### Post by bcbc on 2011-03-31
> **skamarla said:**
> That was it! :D :D :D :D

I followed your instructions (I only had a slight problem with chroot, because System Rescue CD expected zsh, so I had to do a # SHELL=/bin/bash chroot ...)

It took a while (basically, it repeated the upgrade that had been interrupted), but the loop partition became usable.

Then I found the grub.cfg problem reported in problem #2 solution #1 of the Wubi [megathread]("http://ubuntuforums.org/showthread.php?t=1639198#post10207564"). I followed the instructions (included locking future grub upgrades), and that's it!

Thank you all for your patience!
Excellent! It seemed a bit like a long shot, but I'm happy to hear it worked out.

---

### Post by Rubi1200 on 2011-03-31
Nice one! Enjoy :)

---

### Post by skamarla on 2011-03-31
By the way, a reinstall would have been simpler indeed, since user data were totally accessible.

But this was a lot more fun! :)

---

