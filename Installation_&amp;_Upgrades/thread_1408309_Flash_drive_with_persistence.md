---
title: "Flash drive with persistence"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by flyver on 2010-02-16
I tried xubuntu with a persistence-enabled live flash drive.

If you keep using a distribution this way, then want to install it on your system, will it keep your files and settings?

Also, I installed xubuntu on a computer with Windows 7 on it. Unlike what I had done earlier, I let xubuntu take care of the partitions, I only selected the size for Windows and the size for xubuntu. I previously had selected the size for swap and other stuff manually, thinking that would be better (is it?).

When xubuntu 10.04 arrives, will I be able to upgrade and keep all files and settings? I think this depends on the "home partition" or something?

Thank you.

---

### Post by darkod on 2010-02-16
If you UPGRADE you will keep all personal files and settings. But often upgrade can create some issues and clean install is recommended.
But clean install will delete your personal data unless you have separate /home partition.
Actually, I see separate /home partition as main advantage for manual partitioning as opposed to the automatic guided methods. Another small advantage is that you can control the size of the partitions. With the guided method you can only control how much total space ubuntu takes, but not how big are / and swap in that space.
Separate /home partition allows you to do clean installs formatting the / partition while you just use the same /home WITHOUT formatting it and all your data and settings are there.

---

