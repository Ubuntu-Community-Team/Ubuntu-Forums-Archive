---
title: "Installation Guide: How to install without formatting"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by Excessive on 2007-10-30
Suppose you already have a Linux partition which has an Ubuntu or other Linux distribution. By default, Ubuntu forces you to format your target partition. There is a way to override it.

Here's the required steps:

1. Boot with your Ubuntu live cd.
2. Mount your Linux partition, and cd to it.
3. Copy your every valuable data under /backup.
4. Delete the rest of files and folders, thus, only /backup folder will exist on your root partition.
5. Unmount the partition.
6. While on live cd, give the command:
```
sudo rm /lib/partman/check.d/12system_partitions_formatted
```
7. Start the installation.
8. When partition editor launches, select Manual from options, and click Next.
9. Double click your Linux partition and set mount point to /
10. Click Next. 

And there you go. Ubuntu doesn't ask you to format your partition before installing system.

Hope it helps.

---

### Post by ofb on 2007-10-30
Neat. Which LiveCD did you test that on?

I just checked the files in 7.10 and that's a match.

---

### Post by Excessive on 2007-10-30
I just installed Ubuntu 7.04 without formatting with this workaround. I didn't try it on 7.10 yet, as I don't have it burned on a cd. But this should work if same file does exist on 7.10.

---

