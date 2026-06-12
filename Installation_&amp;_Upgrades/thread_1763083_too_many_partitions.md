---
title: "too many partitions"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2011-05-20
I would like to install 11.04/64 bit on a new HP Pavilion dm3, but the free space I created is listed as "unusable," and I can't figure out how tp use gparted to format it, either.  

I think I have too many primary partitions.  Please see the attached screenshot which I took while in the Live environment.

Perhaps I could delete one of these partitions - perhaps the sda1 boot partition - and then the space would become formattable/useable?

Thanks in advance,
Scott

---

### Post by linuxinstalledfromhdd on 2011-05-20
The simple way would be to let Ubuntu resize your paritions automatically for you during the live disc installation. That option always works.

---

### Post by sks24 on 2011-05-20
Thanks, but I don't see that option listed with this installation.

So too the "Install in largest continuous free space" option.  That one would be nice.

---

### Post by Rubi1200 on 2011-05-20
Hi sks24,

did you create the space for Ubuntu from within Windows using the built-in Disk Management tools?

I suggest you boot into Windows a couple of times, even run a chkdsk, just to make sure all is good.

So, to the problem; you have 4 primary partitions, which is why you cannot install Ubuntu right now.

Here are some options:

1. do NOT delete sda1; if you do Windows will be unbootable!

2. the safest is probably to delete sda4, the HP Tools partition. Make a backup of it first or see if the tools are available for separate download from their site.

3. Then, you can create an extended partition in the space you previously prepared and create as many logical partitions as you want to install Ubuntu or anything else.

4. more than anything else, please make backups before proceeding with changes to the structure of your system. Clone the drive if needs be with something like Clonezilla:[http://clonezilla.org/](http://clonezilla.org/)

5. it would also be a good idea to create a Windows recovery disk as well:
[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

Let us know if you have any other questions.

---

### Post by sks24 on 2011-05-20
Thanks Rubi2000:

I have redo and easeus images, and discs.  I will delete the HP Tools and proceed.

Thanks again,
Scott

---

### Post by sks24 on 2011-05-20
Oh: yes, I did create the space using easeus partition manager, and I will run chkdsk before proceeding . . .

---

### Post by srs5694 on 2011-05-20
Your "recovery" partition is your computer manufacturer's way of saving a buck or two on recovery DVDs that they should have provided you but didn't. There should be a Windows utility that will create DVDs from that partition's contents. Create two sets (that'll probably take about 12 DVDs) and, while you're playing human disc changer for the program, write a letter to HP (with a cc: to Microsoft) telling them how cheap you think they are for not including the DVDs and how annoying it is that they used up all four primary partitions. Tell them you'll buy from somebody else, or even build a computer yourself and load a retail version of Windows, in the future because of this. The manufacturers will keep pulling this sort of garbage as long as people don't complain about it.

Anyhow, after you're finished making your DVDs, it will be fairly safe to delete the recovery partition. (There's always the risk that you'll lose the discs or that they'll become unreadable, of course.) You can then resize /dev/sda2 (if necessary; it looks like you've already done this), create a new extended partition in the free space, and install Linux using as many logical partitions as you like. (Unlike Windows, Linux does not need a primary partition.)

A caution: Don't use the Windows partitioning tools for any of this, except possibly resizing /dev/sda2; it has a tendency to convert from standard partitions to "dynamic disks," which is Windows' version of logical volume manager (LVM). Installing Linux to a Windows dynamic disk configuration is tricky at best, and converting back can be difficult, too, so that's a bit of a trap. This conversion seems to happen when you exceed four partitions, but I really wouldn't trust the Windows partitioner at all.

---

### Post by sks24 on 2011-06-11
Thanks srs5694: Given how fragile DVDs are, I simply imaged his drive using both easeus and redo on an old naked 3.5 inch drive and sealed it in a box.  If he runs into problems, I'll simply restore from that.

---

