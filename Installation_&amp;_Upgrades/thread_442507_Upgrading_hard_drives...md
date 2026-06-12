---
title: "Upgrading hard drives.."
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by rnichols430 on 2007-05-13
I am trying to upgrade my system to a RAID1 set, I have two 80GB hdd's and I want to put the Ubuntu 7.04 on those, but how do I get the data from the old hdd?  What I am thinking of doing is using the old hard drive as a 3rd drive that is outside of the raid set.  All I really want off this other drive is the data files from the email(thunderbird), the ktorrent data, personal files.  I wanted to do a fresh install of the OS onto this raid set.  Any ideas of the best way to achive this?

Thanks,
Ryan Nichols

---

### Post by kidders on 2007-05-14
Hi there,

What to do depends very much on what you want to achieve. For instance, if (as you mentioned) you would like to reinstall Ubuntu and empty the old hard disk onto your array, then it's a case of lots and lots of copying.

On the other hand, I kinda get the impression that what you might *really *be interested in doing is storing your personal stuff on the array (in which case you could avoid reinstalling Ubuntu altogether).

Personally, I would normally prefer to avoid running (or at the very least booting) my OS off a RAID array. If you'd prefer to do that though, transferring your personal files & settings onto your new install would be a simple matter of duplicating your home directory. The important thing to note though is that you need an *exact* duplicate (ie you should be careful to preserve all ownerships & permissions), to avoid odd behaviour in the future.

[COLOR=Silver][[SIZE=1]*[UAResolved]*[/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")[/COLOR]

---

### Post by rnichols430 on 2007-05-16
How complex would it be to just install a 2nd drive the same size, keep the os and data intact and create a RAID set?

---

### Post by kidders on 2007-05-16
If you erased the contents of at least one of your existing hard drives, you could do that very easily. All you would really need is two *partitions* of the same size though ... depending on what kinds of disks you've got, that can be an important distinction.

---

