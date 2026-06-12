---
title: "re partition"
date: 2016-12-19
forum: Installation &amp; Upgrades
---

### Post by pete1977x on 2016-12-19
I have a dual boot windows 10 and 14.04. I gave Windows 50 gigs and Ubuntu 75 gigs. Everything works ok. If I decide later to increase Windows to 60 gigs can I do it easily??

---

### Post by oldfred on 2016-12-19
Attach screen shot with gparted, using paper clip icon in advanced Forum editor.
And/or this:
sudo parted -l

---

### Post by Keith_Helms on 2016-12-19
It depends on whether there is any free space after the windows partition.  If there is 10 gb free following the windows partition, you can just boot ubuntu and increase the size of the windows partition using gparted, after unmounting it if you happen to have it mounted on ubuntu.

If there's no unused space left on the drive and windows is in the first slot and ubuntu in the second slot, you have to go through the following:

1. Boot from a live disc.
2. Shrink the ubuntu partition which will free up space past the end of it.
3. Move the ubuntu partition up into that free space, which will then make free space in front of ubuntu and after windows.
4. Expand the windows partition.

If ubuntu is first on the drive:

1. Boot from a live disc.
2. Shrink the ubuntu partition.
3. Move the windows partition forward into the newly freed space
4. Expand the windows partition.

As you can see, this is kind of a pain and involves some risk.  You have to cross your fingers that all the partition moving and resizing works 100% correctly.

---

### Post by ajgreeny on 2016-12-19
> **Keith_Helms said:**
> It depends on whether there is any free space after the windows partition. [COLOR="#FF0000"] If there is 10 gb free following the windows partition, you can just boot ubuntu and increase the size of the windows partition using gparted, after unmounting it if you happen to have it mounted on ubuntu.[/COLOR]

If there's no unused space left on the drive and windows is in the first slot and ubuntu in the second slot, you have to go through the following:

1. Boot from a live disc.
2. Shrink the ubuntu partition which will free up space past the end of it.
3. Move the ubuntu partition up into that free space, which will then make free space in front of ubuntu and after windows.
4. Expand the windows partition.

If ubuntu is first on the drive:

1. Boot from a live disc.
2. Shrink the ubuntu partition.
[COLOR="#FF0000"]3. Move the windows partition forward into the newly freed space[/COLOR]
4. Expand the windows partition.

As you can see, this is kind of a pain and involves some risk.  You have to cross your fingers that all the partition moving and resizing works 100% correctly.
I would recommend you **never** shrink or enlarge a Windows partition with gparted. Use the Windows Disk-management utility instead as Windows can be very fussy about partition management carried out in any other way and may refuse to boot after carrying out such an activity.

Definitely do not ever move the start of a Windows partition; that is even worse than shrinking or enlarging it, and I believe will almost guarantee that it won't boot again.

A very good general mantra is "Windows apps for Windows, Linux apps for Linux" in any such activities.

---

