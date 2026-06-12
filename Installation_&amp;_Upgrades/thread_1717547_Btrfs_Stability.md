---
title: "Btrfs Stability"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by linuxyogi on 2011-03-30
Hi,

While installing Ubuntu & some other distros I found btrfs but didn't use it because I didn't knew anything about it & therefore was worried about its stability. 

After a little googling, now I have an overall idea about btrfs. 

But I want to hear from people who are presently using it.

There are a couple of threads in this forum regarding this issue but they are almost a year old. So, I guess things must have progressed  since then.

Q1) Is btrfs stable enough for regular Desktop use  ?

Q2) How is its performance ?

Q3) I am presently using reiserfs as my /home (That's where all my data is). Is btrfs a better choice ? 
     

TIA.

---

### Post by srs5694 on 2011-03-30
Btrfs is still considered experimental. I'm using it on a couple of systems, but not in any critical capacity. So far, it seems stable to me; however, my use of it is limited, and I'm not using any of its advanced features. Also, the last I heard, there was no fsck utility for Btrfs, which means that if the filesystem becomes damaged, there's no way to repair it. Thus, I cannot recommend that anybody use it for storing important data.

In the future, Btrfs is likely to be an important filesystem. It's got a lot of very useful features and it benchmarks well (although this may change as it becomes more stable). It's just not yet at that point.

If you need Btrfs features now, many of them can be achieved in other ways. For instance, LVM supports snapshots with any filesystem, so if you need snapshots, you can use LVM and whatever other filesystem you like.

---

### Post by linuxyogi on 2011-03-31
> **srs5694 said:**
> Btrfs is still considered experimental. I'm using it on a couple of systems, but not in any critical capacity. So far, it seems stable to me; however, my use of it is limited, and I'm not using any of its advanced features. Also, the last I heard, there was no fsck utility for Btrfs, which means that if the filesystem becomes damaged, there's no way to repair it. Thus, I cannot recommend that anybody use it for storing important data.

In the future, Btrfs is likely to be an important filesystem. It's got a lot of very useful features and it benchmarks well (although this may change as it becomes more stable). It's just not yet at that point.

If you need Btrfs features now, many of them can be achieved in other ways. For instance, LVM supports snapshots with any filesystem, so if you need snapshots, you can use LVM and whatever other filesystem you like.

Okay/Thanks

---

