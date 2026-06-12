---
title: "Multiple Distros, Pt. 2"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-28
Hi,

If I'm trying to install a 2nd distro (just to try it out and whatnot)...do I need to create a whole separate partition for it or can it use the same partition as Ubuntu, but just boot from a different kernel? I'm kinda a newbie, so I don't want to do any throwing-out of entire systems and/or reinstalls if possible, but would like to experiment/learn

Thanks!

---

### Post by matthew on 2005-10-28
You will need a different partition.

You can share a /home partition among several OS's, each having its / on its own partiton.

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-29
How do I access said /home partition from within one of the others? I've got it set up but don't see it anywhere in breezy...

---

### Post by matthew on 2005-10-29
[quote=SuperDiscoMachine V.5.7-3]How do I access said /home partition from within one of the others? I've got it set up but don't see it anywhere in breezy...[/quote]
You can do it temporarily (until you reboot or unmount) using the command "mount" but then you would have to do it every time you boot.

You probably need to edit your fstab file which tells the operating system which partitions to use and how to use them. 

Find the file /etc/fstab in each OS and post the current contents here and I can tell you what to add in the breezy one.

---

### Post by SilentCacophony on 2005-10-29
Hi. As mentioned, you should have separate partitions for different distros' / mount point. While you *can* have more than one distro share one single /home partition, it can be problematic having different distros trying to share the config files there, so I personally wouldn't do it.

> How do I access said /home partition from within one of the others? I've got it set up but don't see it anywhere in breezy...

I'm not at all clear what your setup is, but if you've created a new /home partition for the other distro, you'll have to mount it manually in Breezy. Breezy will mount what partitions it sees when it installs, but after that, you're on your own.

If you just want to access it, you can go to *Administration -> Disks* and look for it there. Then give it a name and mount point (usually a subfolder of /media,) and 'enable' it. You may do the same by adding it to */etc/fstab* with an editor and issuing a **sudo mount -a** afterward.

If you want to try to have Breezy use it as /home for itself, I'm not quite sure, but I'd imagine that you'd do as in the above paragraph, but mount it as */home* instead of */media/whatever*.

If that's not clear to you, then it would probably help if you posted the outputs of:

**sudo fdisk -l**

and

**df -h**

... and identify the partition(s) in question, and what you want to do with it. Then someone can probably show in detail what to do.

---

### Post by SuperDiscoMachine V.5.7-3 on 2005-10-29
thank you very much...it seems to be working now, at least for now. So that's good. Thanks a lot!

---

