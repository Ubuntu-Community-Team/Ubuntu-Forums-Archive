---
title: "Cannot set mount points in installer"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by x-shaney-x on 2011-05-01
I have tried installing the latest Natty final and as normal I do custom partitioning as I have other distros and a windows partition.

Well when I edit a partition, the box to set the mount point only gives me options and I cannot edit anything.

For example, for my windows partition I click mount point box and nothing happens so I click the bit at the side and it brings up the options "/dos" and "/windows"
Likewise, when trying to set the mountpoint of another partition which already has linux on, it only lets me select options like "/usr/share", "/" etc.

Why has this option been removed?
Last install I did was either beta 1 or 2 (I forget) and I WAS able to edit the mount points then.

---

### Post by tacman2k on 2011-05-01
I just noticed the same thing when I attempted to install Ubuntu 11.04 over my existing installation.

I have several Hard Drives that I would like to have custom mount points for so I don't have to mount them every time.

---

### Post by marcus0263 on 2011-05-23
Major Bug, work around is to manually create the disk slices before install.  Then after install while still in the Live CD edit /etc/fstab then copy the dir's over to the slices.

This should not be out in the wild, 11.04 sure isn't "stable" LTS quality with all the bugs that infect it.

---

### Post by smgendler on 2011-05-30
Does anyone know if the alternate installer has the same mount point bug?

---

### Post by smgendler on 2011-05-30
From another thread: [http://ubuntuforums.org/showpost.php?p=10847933&postcount=3](http://ubuntuforums.org/showpost.php?p=10847933&postcount=3)

> **bdoe said:**
> As a workaround, you can open a text editor, type your custom mount point into that, then copy/paste it into the mount point field in the installer. This is assuming you are installing from the LiveCD environment.

I was going to try the alternate installer, but this workaround did work.

---

