---
title: "Upgrading to 18.04, Determining Free Space on BTRFS"
date: 2018-05-11
forum: Installation &amp; Upgrades
---

### Post by mryumyum on 2018-05-11
Hi! I'm currently running Ubuntu 17.10 on a Dell XPS 13 laptop and I am trying to upgrade to 18.04. I did not receive a prompt to upgrade (I installed some KDE/Kubuntu stuff on top of an Ubuntu install, so not everything works together quite right, unfortunately), so to cause the upgrade I used `sudo update-manager`. This seems to work, but it tells me I need 10.4GB of free space on / (that seems like a lot!), and I need to free up ~7GB because I only have ~3GB free.

For context, I have separate / and /home partitions. Both are btrfs.

This is where things get odd due to the nature of btrfs. (I seem to have btrfs related headaches every few months...) Gparted seems to agree with the installer, as it lists my 28GB / partition as 25GB used and 3GB free. However, QDirStat lists the / directory as using only 11GB. The `df` command agrees with Gparted and the installer, showing 25 GB used and 3GB free. Doing `sudo btrfs fi show /dev/sda6` gives

Label: none  uuid: cd095eb5-81e9-4919-8a6c-5156cc4acb73
        Total devices 1 FS bytes used 24.35GiB
        devid    1 size 27.94GiB used 27.94GiB path /dev/sda6

and `btrfs fi df /` gives,

Data, single: total=26.68GiB, used=23.31GiB
System, single: total=4.00MiB, used=16.00KiB
Metadata, single: total=1.26GiB, used=1.04GiB
GlobalReserve, single: total=73.34MiB, used=0.00B

Looking up suggestions, I tried `sudo btrfs balance start -dlimit=3 /` which gave back,

ERROR: error during balancing '/': No space left on device

So I'm somewhat stuck because I apparently need to free up 7GB of space (I don't remember needing so much space for previous upgrades), but I'm not sure where to begin because QDirStat isn't making a lot of sense to me.

Can anyone provide insight as to how I can understand and manage my space with btrfs? I'm temped to nuke the whole thing and not use btrfs since it seems that 11GB of files are taking up all 28GB of the partition, but I'd like to avoid such a situation if possible. Thanks!

---

### Post by stefan-hundhammer on 2018-05-12
Please check if you have a number of snapshots that use up all that disk space.

Quite some time ago, I added Btrfs subvolume support to QDirStat which means that it doesn't stop scanning directories when a subvolume boundary is reached (unlike with other mount points). Maybe there are pathological cases where this does not work 100% reliably. Since all subcommands of the "btrfs" command require root privileges, I had to find a workaround that would not require you to enter your password; see also

    [https://github.com/shundhammer/qdirstat/issues/39](https://github.com/shundhammer/qdirstat/issues/39)

But this relies on /proc/mounts, i.e. only when all those subvolumes are actually mounted. If you have a subvolume that is currently not mounted, QDirStat will not show the disk space it consumes. Similar with snapshots since it is the normal case that they are not mounted.

If you use "snapper", use "snapper ls" to show the snapshots that were made; you may find that quite a number have accumulated in the meantime. Deleting unneeded ones should free a lot of disk space. But you might want to create another snapshot just prior to the upgrade so you can go back in case things go horribly wrong.

Disk usage on Btrfs is a nightmare IMHO: It does not provide correct information to the "statfs()" syscall which is what "df" and related tools use, and the "btrfs" command does not volunteer very much useful information, either.

Maybe this helps:

[https://ownyourbits.com/2017/12/06/check-disk-space-of-your-btrfs-snapshots-with-btrfs-du/](https://ownyourbits.com/2017/12/06/check-disk-space-of-your-btrfs-snapshots-with-btrfs-du/)

Kind regards

-- 
Stefan Hundhammer (HuHa)
Author of QDirStat and KDirStat

---

### Post by stefan-hundhammer on 2018-05-12
I just found out something else that might have hit you: By default, QDirStat has an exclude rule for directory ".snapshots" because some backup tools use that. This might also prevent any Btrfs snapshots from showing up. So, if you don't use that kind of backup tool, you can safely remove that exclude rule. Not sure if that makes any difference, but it is worth a try.


[COLOR=#000000]Kind regards[/COLOR]
[COLOR=#000000]-- [/COLOR]
[COLOR=#000000]Stefan Hundhammer (HuHa)[/COLOR]
[COLOR=#000000]Author of QDirStat and KDirStat[/COLOR]

---

### Post by mryumyum on 2018-05-14
Thanks for the suggestions! I managed to clear out a really big snapshot. I obviously can't roll back to it now, but it cleared over 12GB of space! Enough to upgrade (with crossed fingers...).

I first installed the `btrfs-du` tool which was useful to see the volumes, but ultimately I installed the `apt-btrfs-snapshot` tool which allowed me to list and delete snapshots. I did use `snapper` when I had openSUSE installed, but it seems to not be installed by default on Ubuntu, and when I installed it, it was completely unaware of the snapshot config on my machine. The `apt-btrfs-snapshot` tool worked out of the box.

I did happen to notice the ".snapshot" filter in qdirstat and I got rid of it, but it didn't show the snapshots since they probably aren't mounted anywhere, as you mentioned.

Anyway, the update is currently downloading, so I think everything is working as it should! Thanks!

---

