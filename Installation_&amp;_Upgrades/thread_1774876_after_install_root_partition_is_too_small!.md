---
title: "after install root partition is too small!"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by griztown on 2011-06-03
Hi all,

I made a significant mistake.  When I installed Ubuntu and partitioned my hard disks, I made the root partition rather small.  Well, I should say it is either my root partition or my boot partition that is too small.  Boot is around 400 MB and root is around 500 MB.  Now I can't run any updates since it runs out of disk space, primarily with kernel updates.  The root partition is on a logical volume so I'm hoping I can resize it.  Could anyone offer any advice on how to do this?

Thanks in advance!

---

### Post by garvinrick4 on 2011-06-03
Take a screenshot of "gparted" and post it here. Use the little paperclip to upload
the screenshot. If do not have gparted installed:
```
sudo apt-get install gparted
```

---

### Post by griztown on 2011-06-03
Thanks for your help!

---

### Post by griztown on 2011-06-03
Sorry posted that too soon.  As you can see, there may be something else going on.

---

### Post by garvinrick4 on 2011-06-03
Sorry I do not use Raid maybe someone else will be along that does.

---

### Post by griztown on 2011-06-04
Thanks Rick.  If anyone has experience resizing logical volumes on a RAID partition, I'd be much obliged.

---

### Post by griztown on 2011-06-08
Hoping someone has some experience with resizing LVM partitions in a RAID configurations

---

### Post by fixitdude on 2011-06-08
Don't know about raid, but when you use gparted you have to select "swap off", then delete the swap partition stuff, and make room for some empty space, then you can expand the root partition and then put swap back, leave room for it of course, or make it bigger just for fun. Write everything down on how it WAS configured of course.

Depending on your raid configuration, isn't one of the drives just a copy of the other? So couldn't you do this to one drive and then copy it to the other one and then turn raid back on? Is one drive the "master" ?

---

### Post by stracky on 2011-06-08
With the little knowledge i have about partitions, I'll put my 2 cents in


You should just be able to boot a Live CD and use [FONT=Arial Narrow][SIZE=1]gparted[/SIZE][/FONT] to resize/move the *other* partitions over to create free space, then expand the small partition into the new free space

Just to be safe, I would restart after each change, to make un-doing easier


I know nothing of RAID, so this my not work

Can you post what **type** of RAID it is? [ [http://en.wikipedia.org/wiki/RAID#Standard_levels ]("http://en.wikipedia.org/wiki/RAID#Standard_levels")]

---

