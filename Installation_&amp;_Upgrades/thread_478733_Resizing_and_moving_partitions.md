---
title: "Resizing and moving partitions"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by neko18 on 2007-06-19
Does anyone know how to repartition my harddrive from this:


[IMG]http://img353.imageshack.us/img353/39/isil5.png[/IMG] (screenshot)


to this:


[IMG]http://img353.imageshack.us/img353/9816/wantho3.png[/IMG] (mockup)


I resized /dev/hda1 down to the correct size, but then got stuck because it's not possible to move /dev/hda2 and /dev/hda3 in front of the newly created unallocated space.

---

### Post by merlinus on 2007-06-19
You might try deleting your swap partition, adding the freed-up and unallocated space to hda3, and then recreating /swap.

You may need to boot from the gparted live cd to do it, or unmount /swap if using gparted from ubuntu.

-merlin

---

### Post by neko18 on 2007-06-19
What would I do with the unallocated space between /dev/hda1 and /dev/hda2 then?

---

### Post by merlinus on 2007-06-19
> **neko18 said:**
> What would I do with the unallocated space between /dev/hda1 and /dev/hda2 then?

I don't see any unaollocated space between these in your screenshots....

Anyway, you would be very ill-advised to shrink your windows partition any more than you already have.

Also, you may have to temporarily delete your extended partition in order to add the swap and unallocated space to hda3, and then recreate it as well as swap.

I do not think you can add space in a logical partition (swap and unallocated) to a primary without deleting the extended partition.

BTW, the white areas are not unallocated, they are unused.  The grey area is unallocated.

-merlin

---

### Post by neko18 on 2007-06-19
After I shrink my /dev/hda1 partition, about 8 GB of unallocated space appears between /dev/hda1 and /dev/hda2. Basically what I want to do is add that 8 GB of unallocated space to /dev/hda3.

I don't use Windows anymore, so I don't really care how small its partition is. I just don't want to delete the partition since it's the only copy of Windows I have.

Edit: I think you have been misunderstanding my screenshots. The first one is how my computer currently is. The second one is a mockup of how I would like it to be.

---

### Post by bodhi.zazen on 2007-06-19
I advise you use a more up to date version of gparted, should do the trick ...

Try the gparted live CD (it is a small download)

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

(The version in the Ubuntu repos does not have the newest latest features

The problem is you can not move the start point of a partition with older versions)

---

### Post by neko18 on 2007-06-19
Thanks. I'll report back in about 10-15 minutes.

---

### Post by neko18 on 2007-06-19
That was a pretty terrible time estimate, but oh well. I resized /dev/hda1, but it couldn't read one of the blocks (cylinders? I don't remember) in /dev/hda2 when it was doing the simulation read, so it couldn't finish the moving process. I give up.

---

### Post by bodhi.zazen on 2007-06-19
Ouch

---

