---
title: "Retrieve existing distro files?"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by Lateralus@desktop on 2007-05-16
I'm running Kubuntu Feisty (after upgrading) and several things broke. So I downloaded and burnt the Kubuntu Feisty CD, expecting to be able to just go in, and be able to quickly copy files over to my external hard drive.

But I cant find a way to read any of the partitions. They are there if I go to the Disk & Filesystems in the 'control panel', but I cant access any of them.

---

### Post by taurus on 2007-05-16
You probably need to mount them before you can access them.  Post the output of this command from a terminal and state which partition(s) you want to mount to backup your important stuff.

```
sudo fdisk -l
```

---

