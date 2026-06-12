---
title: "Installing Ubuntu over Win 7 on SSD?"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by jasonshim on 2011-03-20
Hello,

I'm trying to figure out how to install Ubuntu on top of Windows 7 on my intel X-25 M G2 SSD.

I bought the SSD a while ago and installed Win 7 without partitioning it.

Soon, I got sick of worrying about the wear and tear, and chucked it into my drawer.

Instead, I installed Ubuntu on my HDD, and forgot about the SSD.

Now that I need to dual-boot because of some obscure VM-bashing ActiveX plugins,

I need to install Ubuntu on my SSD.

However, I'm overwhelmed and confused. I just have no idea how to do just that.

What steps should I take to install Ubuntu without messing up Win 7 on my SSD?

I need general pointers like align your drive, manually partition for ubuntu, and the like.

I think I can plough thorough howtos and find out necessary details.

I've been searching, but my effort was fruitless mainly because I didn't know 

what was involved.

Can anyone give me a broad overview or an outline of things I need to do?

Thanks!

---

### Post by Hedgehog1 on 2011-03-20
If the SSD is the same size or larger than the Hard Drive, you can dupe the hard driver to the SSD using:

* dd
* ddrescue (useful if you have any bad sectors on the HDD
* Clonezilla CD.

If your hard drive is larger then the SSD, reduce the size of the HDD partitions to fit onto the SSD, and use the Colonezilla CD

If you don't use 'dd' or 'ddrescue', you will likely need to reinstall grub on the SSD.  No big deal, just an extra set.
[B][I]
The Hedge[/I][/B]

:KS

---

### Post by LMHmedchem on 2011-03-20
You may want to plug in the ssd and boot into windows (unplug the ubuntu drive). Win7 creates properly aligned partitions for the ssd, so you could create the partitions in win7. I would probably unplug any other drives as well.

You need two partitions for ubuntu, one for root, and one for swap that is about 2x the size of your RAM. Make sure that the ubuntu partition is about 2x the size of the data you are going to put there. You don't need to format either partition.

After that, you can do a fresh install of ubuntu to the new partition using sda2 as root (/) and sda3 as swap. Install grub to the MBR of the ssd. If you only get the option to boot into ubuntu, you should be able to do grub-update to fix that.

If you want to keep your current ubuntu, as Hedgehog1 said, you need to shrink the ubuntu partition to the same size or smaller than the partition you create to install it on. Tools like[ easus free partition manager]("http://www.partition-tool.com/download.htm") work very well for that, plus it's a nice tool to have anyway. Once you have resized the partition, you can use [Clonezilla]("http://clonezilla.org/downloads.php") to either clone it to the ssd partition, or make an image of it, and then write the image to the ssd partition. An image is a very good thing to have around if you don't have one, but will require a drive partition to store it on. Clonezilla can be a bit confusing if you aren't super comfortable in linux, but is sounds like you should be fine with it.


**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by jasonshim on 2011-03-21
So, resizing is not a concern?

I thought data were distributed randomly across my SSD, because I didn't partition it.

That led me to guess I'd screw up everything if I resized or created partitions..

The inner workings of SSD are quite new to me, though I had it for a long time.

This seems like a piece of cake!

Anyway, thanks for useful pointers!

---

