---
title: "Not enough sda1 space to upgrade"
date: 2012-06-27
forum: Installation &amp; Upgrades
---

### Post by rkashby on 2012-06-27
I an running Ubuntu 11.04. I tried to upgrade to a new version but did not have enough space on /dev/sda1.

Here is what a df shows for sda1:

/dev/sda1 9851308  7795832  1555056  84% /

Someone suggested I try BleachBit, which had very little effect--although I did not have every item in the left panel checked. Some gave dire warnings that sounded too risky to delete.

QUESTIONS:

How do I know what is on /dev/sda1?
How can I decide whether something on /dev/sda1 is safe to delete?

Thanks very much.

---

### Post by darkod on 2012-06-27
Unless you have a separate partition mounted as /home (look again with df it would show), everything is in /dev/sda1. That's your main root partition (mount point /) and everything is there.

Any big files, documents, photos, videos you delete from your Home folder (or move to an external disk for example) should free space on sda1. Of course, this is under the assumption you do not have a separate /home partition.

---

### Post by rkashby on 2012-06-27
> **darkod said:**
> Unless you have a separate partition mounted as /home (look again with df it would show), everything is in /dev/sda1. That's your main root partition (mount point /) and everything is there.

Any big files, documents, photos, videos you delete from your Home folder (or move to an external disk for example) should free space on sda1. Of course, this is under the assumption you do not have a separate /home partition.
Thanks. I do also have sda3 with /home, which has plenty of space:

ilesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1              9851308   7795832   1555056  84% /
none                   1019396       692   1018704   1% /dev
none                   1026024      2904   1023120   1% /dev/shm
none                   1026024       268   1025756   1% /var/run
none                   1026024         0   1026024   0% /var/lock
/dev/sda3            180298120  30768124 140371340  18% /home

---

### Post by darkod on 2012-06-27
OK, so it's not your data in Home that is taking too much space.

There are graphical tools to tell you what takes most size on /, I just haven't used one in a long time.

Not sure if such tool comes included or you need to install. There was one called baobab for example, if my memory serves me right.

You can also google for "ubuntu tools to show disk usage" or similar. Then install what ever looks good to you.

---

### Post by ajgreeny on 2012-06-27
Open up Disk-usage-analyser, click on "Scan filesystem" icon in toolbar and it will show you what is using all that space.  YOu can ignore the 100% use on filesystem, as it always shows the root of its scan at 100%, but the pie chart and the listed system folders will show you which is using up your space.  Your /home will also show as part of the filesystem even though it is a separate partition
My screenshot shows what the chart will look like.

---

### Post by rkashby on 2012-06-27
Thanks for your help, darkod and ajgreeny.

I do seem to have a lot of stuff in /usr/lib, including the over 600MB file /usr/lib/debug/usr/lib/libwebkitgtk-1.0.so.0.6.0.

I now just have to decide what I can safely get rid of, or alternatively how to safely increase my sda1 partition size.

---

