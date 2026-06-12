---
title: "Dual boot, now want single boot."
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by georgy.k.zhukov on 2008-01-25
Hi I wasn't really sure where to post or what to call the subject.  So if it's in the wrong place, please feel free to move and accept my apologies.
Here goes.
I installed ubuntu dual booting with windows on a 100gb drive, with ubuntu having 60gb and windows 40 gb on a Dell laptop.  I now have ubuntu configured exactly how I want it (took some time and pain) and have now realised I have no need for windows. 

What I would like to do is somehow "remove" windows and allocate the 40gb to ubuntu, so ubuntu has use of the whole drive.

My question is, is this possible?  And if so how do I do it?

Many thanks

---

### Post by Tux.Ice on 2008-01-25
i think you may be able to do this with gparted. i cannot remember how though. Try googling it.

---

### Post by v1cho on 2008-01-25
> **georgy.k.zhukov said:**
> Hi I wasn't really sure where to post or what to call the subject.  So if it's in the wrong place, please feel free to move and accept my apologies.
Here goes.
I installed ubuntu dual booting with windows on a 100gb drive, with ubuntu having 60gb and windows 40 gb on a Dell laptop.  I now have ubuntu configured exactly how I want it (took some time and pain) and have now realised I have no need for windows. 

What I would like to do is somehow "remove" windows and allocate the 40gb to ubuntu, so ubuntu has use of the whole drive.

My question is, is this possible?  And if so how do I do it?

Many thanks

Resizing the root partition is not a good idea, at least it is not an easy task. You can just format the windows volume and use as a second volume. To get a GUI partition editor install **gparted** through Synaptic. :)

---

### Post by kpkeerthi on 2008-01-25
Grab [gparted live cd]("http://gparted-livecd.tuxfamily.org/") and boot with it. 

Launch gparted. Select the windows partition and click delete. This will produce 'unallocated' space. 
Now select ubuntu partition and click resize. In the dialog that pops up, just drag the ubuntu partition to cover up the unallocated space.
Click Apply.

Windows is gone for good now.

If GRUB has trouble booting Ubuntu, restore it using [super grub disk]("http://supergrub.forjamari.linex.org/")

---

### Post by georgy.k.zhukov on 2008-01-25
Hi Tux.Ice thanks for the quick response.  I should have said what I've tried already.
I have tried gparted & g4l and was able to create an image of my ubuntu install.  I did a test re-image but it left the extra 40gb as an LVM partition and using ubuntu's partition manager I couldn't get it to utilise the extra space.

---

### Post by georgy.k.zhukov on 2008-01-25
> **kpkeerthi said:**
> Grab [gparted live cd]("http://gparted-livecd.tuxfamily.org/") and boot with it. 

Launch gparted. Select the windows partition and click delete. This will produce 'unallocated' space. 
Now select ubuntu partition and click resize. In the dialog that pops up, just drag the ubuntu partition to cover up the unallocated space.
Click Apply.

Windows is gone for good now.

If GRUB has trouble booting Ubuntu, restore it using [super grub disk]("http://supergrub.forjamari.linex.org/")

Thanks for the reply.
How likely is it that I could destroy my ubuntu install as well?

---

### Post by kpkeerthi on 2008-01-25
gparted worked perfectly for me everytime I used it - once to nuke win XP and then when I made space for vista and again to nuke vista.
And yes, backup your data when you are playing with your partitions.

---

### Post by georgy.k.zhukov on 2008-01-25
Cool. I shall give that a try this weekend.

Many thanks

---

