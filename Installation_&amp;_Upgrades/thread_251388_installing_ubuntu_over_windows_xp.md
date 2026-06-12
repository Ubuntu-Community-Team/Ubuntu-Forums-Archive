---
title: "installing ubuntu over windows xp"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by ryan_h on 2006-09-05
okay, i'm a noob so please be easy on me.

I'm currently running windows xp with two hard drives both NTFS file system.  My C drive has all my windows and program files.  my D drive has all my music, movies, files....all of which I do not have an easy way to back up, because i don't  have a dvd burner or external hard drive.

essentially, Windows has been making me very frustrated.  Its slow, awkward, not secure, etc, etc and I want to make a complete jump to ubuntu....no dual booting.  I've used linux before a couple years ago and I was pretty good with it so I'm not worried about the learning curve, i'm willing to figure it out.

So here's what I want to do.  Install ubunto on my C Drive, completely format it.  However, I would like for my D drive to stay intact so i can access my music and movies with ubuntu.  Is this possible?  If I convert the partition to FAT32 will it work?  Are there other alternatives?

Thanks for your help!

---

### Post by meng on 2006-09-05
If you choose to replace Windows with Linux on your first partition (C: ), and keep your second partition (D: ) as-is, Ubuntu should be able to read the NTFS (although it may not be able to write to it).
[https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29](https://help.ubuntu.com/community/MountingWindowsPartitions?highlight=%28mount%29)

---

