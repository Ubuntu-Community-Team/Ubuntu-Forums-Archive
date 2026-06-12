---
title: "New to ZFS root install"
date: 2020-05-10
forum: Installation &amp; Upgrades
---

### Post by darksidedude on 2020-05-10
Good day all. I hope this is the right sub forum for this question. 
I’m new to ZFS but so far it looks great with the snapshots. I did the default use all disk space install. Upon some minor google-fu I saw you can add multiple drives to a ZFS pool (looks kind of like old school WHS drive extender but much less janky) 

My question is,
I have 2 SSD’s both 480GB. Can i add the other one to the root pool to get a raid 0? Or would that Bork my install? 

Thanks for the help!!

---

### Post by DuckHook on 2020-05-10
It would not bork your install. I'm relatively new to ZFS myself, but so far, my experience reflects yours.

Please have a look at this: [https://docs.oracle.com/cd/E19253-01/819-5461/index.html](https://docs.oracle.com/cd/E19253-01/819-5461/index.html)

Oracle was the primary developer of ZFS so their docs are pretty good. However, be mindful that Unix handles things a bit differently than Linux, so commands/directories/standards will be slightly different.

You would need to set up RAID 0 (ZFS calls it Mirroring) after the fact.

---

### Post by darksidedude on 2020-05-10
so just an update, it just works thanks to [https://www.techrepublic.com/article/how-to-manage-zfs-pools-in-ubuntu-19-10/]("https://www.techrepublic.com/article/how-to-manage-zfs-pools-in-ubuntu-19-10/") I can format the extra drive as GPT and ZFS 

then 
```
sudo zpool add rpool /dev/sdX
```

---

### Post by DuckHook on 2020-05-10
When working with ZFS, it's best to use /dev/disk/by-id/&#8230;

Relative device paths can change, which will give you a very bad day.

---

### Post by DuckHook on 2020-05-10
Like a dummy, I wasn't paying proper attention.

Are you really setting up your rpool as a RAID 0? I hope you've thought this through because this is *very* brittle. Sufficient disk errors will bring your whole pool down. I had assumed that you were doing a RAID 1 mirror, but your command produces a simple striped set which is extremely fragile, especially for something as important as rpool, which (I assume) contains your whole base install and /home.

You may wish to reconsider this approach.

---

### Post by darksidedude on 2020-05-11
yes I was setting up rpool as a striped raid 0. I didn't really consider disk errors since they are both SSD's oh well live and learn I suppose... my truly important data is on a XFS formatted spinning drive. but now I see this setup is probably a bad idea.

---

