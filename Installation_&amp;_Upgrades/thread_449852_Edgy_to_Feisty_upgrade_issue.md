---
title: "Edgy to Feisty upgrade issue"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by ebike on 2007-05-20
Hi All,

Am trying to upgrade my Mythtv box from Edgy to Feisty using the gui upgrade method.

When I try the upgrade, it complains that it does not have enough room on /usr to do the upgrade
(states it needs 200Mb) however, I have 900Mb available on the partition that /usr resides, so
cannot understand why I am getting this problem.

Anyone know why this could happen? What can I do as a workaround? df shows the following:

> df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             4.6G  3.4G  979M  79% /
varrun                236M  188K  236M   1% /var/run
varlock               236M     0  236M   0% /var/lock
procbususb             10M  176K  9.9M   2% /proc/bus/usb
udev                   10M  176K  9.9M   2% /dev
devshm                236M     0  236M   0% /dev/shm
lrm                   236M   18M  219M   8% /lib/modules/2.6.17-11-generic/volatile
/dev/hdb1             187G  166G   21G  90% /media/hdc1
/dev/hda3              69G  214M   69G   1% /var/lib


---

### Post by pbw on 2007-05-20
clean your apt cache to free up some room on your root partition. You also might want to shrink that gigantic /var/lib partition and migrate /usr there (i would for sure).

As for why there's not enough space, perhaps it's stating you will need 200mb of additional space after unpacking (which isnt including the dl'ing of packages).

-- pbw

---

### Post by ebike on 2007-05-21
Thanks for the advice.

Is there a non-destructive partitioner?

Rather than re-partitioning. Can I move /usr over to the other partition by moving everything under /usr
to a directory of that name on the /var partition and symbol link to it from the  root directory?

Is there any problem doing it that way?

---

### Post by superm1 on 2007-05-21
As an alternative, clean out old logs in /var/log.  I've seen these add up really quickly (especially mysql logs if you have any level of verbose logging turned on).

Remove any old kernel images that you don't need.  (You can free 100-200 megs on a single kernel image with all restricted-modules). 

Clean out apt-cache by removing all debs from /var/cache/apt/archives and /var/cache/apt/archives/partial.

Remove any apps that you won't be needing for this box.  Eg if this is a mythtv only box, you probably won't need openoffice or evolution.

---

### Post by pbw on 2007-05-21
> **ebike said:**
> Thanks for the advice.

Is there a non-destructive partitioner?

Rather than re-partitioning. Can I move /usr over to the other partition by moving everything under /usr
to a directory of that name on the /var partition and symbol link to it from the  root directory?

Is there any problem doing it that way?

Well, that's basically all you'd have to do to use to use it correctly. Then just add an entry to /etc/fstab to mount /usr on the new partition (instead of symlinking).

BTW, all of superm1's suggestions are good and will help. It's just that (imo) it's an extremely big waste of disk space to give /var/lib that large of a partition, and if distributed a bit better, you have way more than enough space for anything you might want to do..

What i would suggest in your situation ebike, would be to move everything in /var/lib onto your root partition, kill it's fstab entry. Reboot, then split hda3 into 2-3 paritions. One for /home (it'll be good down the road if a reinstall is needed, so user settings and files aren't lost), one for /usr and also one for /var if you still wanted it seperate. That way everything is setup nice and neat and you're optimizing the diskspace you have.

Lemme know if you have any questions on that, i don't mind walking you through it.

-- pbw

---

### Post by superm1 on 2007-05-21
The reason that his /var/lib/ is so large is because mythtv recordings are being stored there.  MythTV records by default to /var/lib/mythtv/recordings.  As most users know, the more space, the better off they are.

---

### Post by ebike on 2007-05-21
That's right. I followed the Ubuntu Mythtv "Frontend Backend" guide which suggested only a small root partition and a large /var/lib partition for recordings.

I do have a seperate drive for my TV recordings, but have all my photos and music on /var/lib, so want to keep that as free as possible.

I will take on some of the suggestions to prune back some disk space, then see how I get on with the upgrade.

Thanks.

---

### Post by pbw on 2007-05-21
ah, lol sorry guys. I totally overlooked that it was a mythtv box in your opening post. I kept wondering why you'd choose that partition setup. :p

---

