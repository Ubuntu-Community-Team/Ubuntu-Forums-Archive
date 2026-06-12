---
title: "Windows install screwed up my LVM"
date: 2011-08-23
forum: Installation &amp; Upgrades
---

### Post by jant90 on 2011-08-23
I have 2x 2TB drives for data storage in my system. I placed both drives in a volume group and made 1 big 4TB partition on it. I made it ext4 and mounted it in my Ubuntu Server environment and used it for a while without any problems.

Just now I wanted to work a little with Windows 7 and I installed it on a separate hard drive (a 500GB one). This went fine but the (f***ing!) Windows 7 installer automatically made a 100MB system reserved partition on one of the 2TB drives (because the freaking MS OS saw them as unallocated space). That basically scewed up the volume group.

Running [FONT="Courier New"]**[COLOR="Red"]vgchange -ay[/COLOR]**[/FONT] gives an error that device with UUID (..) couln't be found. Running [FONT="Courier New"]**[COLOR="Red"]vgchange -ay --partial[/COLOR]**[/FONT] works and activates my volume group as read only.

When I try to mount my logical volume inside that volume group mount gives the error that I need to specify the file system. When I do so with [FONT="Courier New"]**[COLOR="Red"]mount -t ext4[/COLOR]**[/FONT] it returns the error that it's the wrong file system.

**Is there a way for me to fully restore my volume group? Or a way to mount what's left of it so that I can backup as much data as possible?**

---

### Post by jant90 on 2011-08-23
I found a data restore guide over here:
[http://www.novell.com/coolsolutions/appnote/19386.html#CorruptedLVMMetaData](http://www.novell.com/coolsolutions/appnote/19386.html#CorruptedLVMMetaData)

And I think that solution 2 might be it for me. The only problem is that windows created the 100MB partition and I can't decide whether or not to delete it before proceeding. And if I should delete it what tool I best use for it, because I can imagine one tool just deleting the partition and another tool to completely delete everything that's left on that drive in the 'unallocated space' (in which the remains of my VG are).

What do you guys think?

---

