---
title: "[SOLVED] Resizing into Unallocated Space with GParted"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by raashell on 2007-09-05
I haven't been able to find a post that addresses my issue, or google an answer.  My situation is this:  I have a dual boot on my computer and resized the windows portion as small as I could, while allowing it to remain (in customizing ubuntu, it has proven handy whenever I do something destructive).
  I want to use GParted to resize Ubuntu to take advantage of the unallocated space.  I now have, in this order:


..................................................Size         Used        Unused
/dev/hda2     fat32   /media/disk           3.99GiB   1.27GiB  2,72GiB
/dev/hda1     ntfs    /media/disk-1         34.18GiB  18.75GiB  15.43GiB (This is Windows XP)
unallocated                                        61.54GiB
/dev/hda3     ext3   /media/disk-2          47.91GiB  35.59 GiB  12.32GiB (This is Ubuntu)
/dev/hda4     extended                         1.43
   /dev/hda5  linux-swap                       1.43

  When I attempt to resize Ubuntu, it won't let me make it any bigger then it already is.  Some bits written in other posts seemed to indicate that possibly the Ubuntu area needed to be before? the unallocated space, but I see no option to move it when I hit "Resize/Move."  I made a half hearted attempt to copy the Ubuntu partition onto the unallocated space (although this approach seems like it could be riddled with problems) however, five partitions is the limit.
  Re-installing Ubuntu is currently out of the question as I've spent around 96 solid hours getting my printer, my Nvidia graphics card, a virtual box, and my precious World of Warcraft to work on Fiesty, all through Google and cut and paste (now you see why the dual boot comes in handy ;)  ).  Any help would be greatly appreciated,

Thanks,

John

---

### Post by mxg01 on 2007-09-05
I've not been able to expand my / partition into unallocated space below it. I don't think you can do it with  ext3 type partitions. Neither gparted or partition magic allowed me to do it. 

What you could do is move your /home into the spare partition. The problem would be that you are up to the 5 partitions max.

So errr..... hopefully someone else will post something useful.

---

### Post by wonk-o-matic on 2007-09-05
Try deleting the unused partition.  Then try resizing its neighbor.

---

### Post by raashell on 2007-09-05
Unfortunately,  when I click on the unallocated space the only option on the tool bar, is "New."  Is there some way to do it outside of GParted?

---

### Post by merlinus on 2007-09-05
IIRC, you will need to format the unallocated space before attempting to add it to an existing parttion.

And, are you you using gparted live cd?

-merlin

---

### Post by raashell on 2007-09-05
I am loading GParted from the Ubuntu Live CD.  I will see if I can figure out how to format in Ubuntu and try to expand one more time.  Thanks for the help.

John

---

### Post by merlinus on 2007-09-05
Use gparted live cd.  Small download and many more features and capabilities.  

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by ajgreeny on 2007-09-05
I agree with merlinus, get the live gparted CD; it's much more up-to-date than that on ubuntu live CD.  I did exactly what you want to do on my machine with the gparted live CD, by chosing to first move the ubuntu partition backwards on the disk, not possible with the ubuntu version, and then increased the size of the moved partition.  I did it in two steps, but could have done it in one , but it was my first try with the live gparted CD and I was a bit uncertain of safety.  All was well, however, so give it a try.

---

### Post by raashell on 2007-09-05
Not getting the information you need is always aggravating so I appreciate your guys help.  I burned the GParted Live Cd and it *was* able to expand backwards, with no problems.  I'm the happy new owner of 68.5 GiB.  :)

Thanks again,

John

---

