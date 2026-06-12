---
title: "Clean Install: Disk layout for Btrfs (partially with LUKS)"
date: 2019-02-25
forum: Installation &amp; Upgrades
---

### Post by cptkaos on 2019-02-25
Hello!

I am setting up a new system. I would like to use Btrfs partially for learning, partially because it seems to be 'the future' and i intend to use this system for quite some time.

I have a 256 GB SSD and a 2 TB HDD. (On the SSD, i will also install Win 10, so this will be a dual boot.) I would like to encrypt my data, but keep root unencrypted, mainly for performance reasons, also because i think it is not nescessary for my security needs.

I am totally new to Btrfs. (I have used LUKS before, though.) My main question: Would the following work?

- Setting up the system on a Btrfs on the SSD
- Setting up home on a Btrfs on LUKS on the HDD

Can i integrate these two Btrfsses as one "volume" even though one is on LUKS and one is not? And: Can i still make sure that all user-data (except for temporary data) stays on the encrypted disks?

As far as i understand, this should not be a problem. Would you expect problems/drawbacks? The alternative would be full encryption, i guess. For that, i do find instructions on the net, but not for my particular layout, so i'd be grateful for comments, advise, warnings and so on.

If helpful, i can detail my current state of planning for the whole disk layout so far. I haven't worked out the fine details yet, though, because i am not sure if i am missing something that would make this approach a bad idea.

Any comments appreciated.

---

### Post by TheFu on 2019-02-25
I don't have any direct experience with btrfs, but use lots of file systems on lots of different platforms (10+).  At some point the bits have to be written to disk.

As to merging a single brtfs volume between encrypted and unencrypted storage ... what happens when the encrypted storage isn't mounted at the same time?  What if parts of the OS are inside the unmounted/encrypted part of the storage?  

Just seems like a really bad idea to me, but please try it and see what happens, then post back here. I would expect data and OS file loss.

If you make it over a few days and it works, I'd be certain to have excellent backups. Excellent backups are mandatory whenever encryption is involved. SOP.

---

### Post by cptkaos on 2019-02-28
Thank You!

I'll just not do it. You're right.

---

