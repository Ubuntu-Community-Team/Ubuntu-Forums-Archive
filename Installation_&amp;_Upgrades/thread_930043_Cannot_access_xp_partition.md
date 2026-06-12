---
title: "Cannot access xp partition"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by gavmoulds on 2008-09-25
ok, this is my last try.

I have ubuntu and xp installed in dual boot configuration.

I cannot boot the xp part it simply hangs with the following displayed.

Starting...

and a flashing cursor.

I can see the partition in the list and I can slect it.

It is also present in the 'computer' menu from the ubuntu desktop.

I really would like to get rid of this rubbish and go back to my xp installation

---

### Post by Crafty Kisses on 2008-09-25
First I'd like to see the results of this command:
```
sudo fdisk -l
```
Have you tried mounting your XP partition? Try creating the mount point, if you haven't done so already, the mount point may exist in **/media/hda1**.

---

### Post by gavmoulds on 2008-09-25
> **Codename said:**
> First I'd like to see the results of this command:
```
sudo fdisk -l
```
Have you tried mounting your XP partition? Try creating the mount point, if you haven't done so already, the mount point may exist in **/media/hda1**.

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12645   101567383    7  HPFS/NTFS
/dev/sda2           12646       30394   142568842+   5  Extended
/dev/sda5           12646       30043   139749403+  83  Linux
/dev/sda6           30044       30394     2819376   82  Linux swap / Solaris
gavin@gavin1:~$

---

