---
title: "Install over previous ubuntu installation"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by ansiktsburk on 2009-12-21
Hello.
I have a messed-up  (but semi-working) ubuntu   on /dev/sda1  and I wish to install 9.10 to that partition.

What will happen if I install without formating the partition? (is it possible to skip the creation of a new filesystem?) Will it work? Will it keep my old files, that is, the files I created, documents, email, etc?

(please, no lectures on how to partition  the hdd :popcorn: I know I've done something wrong)

---

### Post by lloyd_b on 2009-12-22
> **ansiktsburk said:**
> Hello.
I have a messed-up  (but semi-working) ubuntu   on /dev/sda1  and I wish to install 9.10 to that partition.

What will happen if I install without formating the partition? (is it possible to skip the creation of a new filesystem?) Will it work? Will it keep my old files, that is, the files I created, documents, email, etc?

(please, no lectures on how to partition  the hdd :popcorn: I know I've done something wrong)

Quick answer - It's possible, you *can*, but probably *shouldn't*.

Long answer - If you install over an existing filesystem without formatting it, it is *possible* that you'll wind up with "leftovers" from the previous install that interfere with the new install.  Exactly what effect this would have is pretty much unpredictable - it depends on precisely what the leftovers are.

It might work, or it might not.

Is there any way you can backup the contents of the "/home" directory?  Since all your personal documents/settings/whatever should be stored in there, that would preserve the things you care about.

Assuming you have the free disk space, you may be able to shrink the existing partition, create a new partition, and then copy the entire contents of "/home" to the new partition.  Then when you go to reinstall, you can mount *that* partition as "/home" (without formatting), and have all your critical files *and* a clean system install.

(Sorry for throwing the partitioning advice at you, but, well, it *is* a good idea to have a separate /home :))

Lloyd B.

---

