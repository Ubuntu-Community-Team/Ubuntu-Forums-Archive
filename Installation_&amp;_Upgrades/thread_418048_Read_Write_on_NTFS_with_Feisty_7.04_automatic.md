---
title: "Read Write on NTFS with Feisty 7.04 automatic?"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by linuxguiri on 2007-04-22
This wiki article sounds like you can automatically read/write to ntfs partitions in Feisty:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

Is that true? Or do you have to install and run ntfs-config?

---

### Post by kratzz on 2007-04-22
Yes, it is true, you actually don't have to do anything at all, Feisty mounts all partitions from the start (including NTFS) and you can edit them as easily as you can in Windows... pretty neat, huh ? ;)

---

### Post by weedwacker on 2007-04-22
Not necessarily true.

I upgraded to Feisty from Edgy and although my windows drives were mounted and I could read/copy from them, I could not write/paste to them.

I solved this by having Synaptic Package Manager (which is under System>Administration) install the package [COLOR="Red"]NTFS-CONFIG[/COLOR].

This installs the NTFS Configuration Tool which will set up the fstab correctly.

---

### Post by linuxguiri on 2007-04-22
> **kratzz said:**
> Yes, it is true, you actually don't have to do anything at all, Feisty mounts all partitions from the start (including NTFS) and you can edit them as easily as you can in Windows... pretty neat, huh ? ;)

That would be neat, but after a clean install of feisty on a dual boot system, my ntfs partitions were mounted automatically but they are still read-only.

What's going on? I've tried changing the fstab options to "user, rw, exec, umask=000" but they're still read-only. I've also tried changing permissions as root, but I get an error that the disk is read-only.

Is installing ntfs-config, the only way to fix this? The wiki article I quoted makes it sound like that is less reliable then whatever it is 7.04 supposed to do.

---

