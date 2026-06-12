---
title: "Partitioning Question - A Limit of 4"
date: 2008-07-21
forum: Installation &amp; Upgrades
---

### Post by capatt on 2008-07-21
Hello
      I'm up against the 4 primary partition limit on a SATA drive and I don't know how to resolve this.  
      I have a dual boot system:  XP, Ubuntu.  I've used EasyBCD to create the boot menu.  This is my layout:

C:\
--Primary Partition 1:  XP
--Primary Partition 2:  Ubuntu root
--Primary Partition 3:  Ubuntu swap
--Primary Partition 4:  Ubuntu home

 I'd like to install another distro to the C:\ drive, but I already have 4 primary partitions, which is the limit.  I have plenty of unallocated space on C: which I originally reserved for another installation, but now I realize that I'm up against this partition limit.  

I want to preserve the Ubuntu installation.  How can I do that, given my layout?  Do I convert one of these primary partitions to an extended partition into which I can add more logical partitions?  How?  Is there a simpler alternative?  Partitions 2 - 4 were originally created with gparted during the Ubuntu installation.  Windows sees the drive with 4 primary partitions and unallocated space.  Windows will not allow me to create any more partitions.  If I attempt to do that it wants to convert the C: drive to a dynamic disk and that's not what I need, of course.

Any hints would be appreciated.  Oh, and I'm a newbie, as if one couldn't tell.

Thank you

---

### Post by vanadium on 2008-07-21
You will need to delete one or more primary partitions in order to create an extended partition covering all free space on your disk. It is not possible to "convert" a primary partition to a logical one while leaving the data in place.

Additionally, any repartitioning will require you to update /etc/fstab so that the new partitions are correctly mounted.

I would probably just reinstall the current Ubuntu. This would involve 1) backing up your user data 2) delete the swap and home partition 3) create an extended partition covering all free disk space 4) create a logical partition for /home and swap 5) reinstall Ubuntu, having it use the new logical home and swap partitions.

If you want to keep your current Ubuntu installation, you will need to 1) mirror your current /home to a backup disk 2) delete the swap and home partition 3) create an extended partition covering all free disk space 4) create a logical partition for /home and swap 5) Restore the backup of /home 6) Update /etc/fstab

---

### Post by capatt on 2008-07-21
Thank you.  What about simply moving /home to the second primary partition, so the entire Ubuntu installation is simply in one partition?  Not ideal, but perhaps simpler?  That would free a partition to combine with free space and make an extended?
But why would I have to touch swap, at all?

---

### Post by vanadium on 2008-07-21
If you have the room on your ubuntu root, that is a perfect option. Indeed, there is no need to touch your current swap. That was just me, having a preference to move the swap more to the end of the disk.

You probably know that another distro can use the same swap space just fine. You can leave it as it is and make other distros use it as well.

Moving a /home is not trivial. You have to copy the existing home correctly. The psychocats site [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) suggests a command such as:

```

find . -depth -print0 | sudo cpio --null --sparse -pvd /new/

```

I would use this command (adapted, of course) to move the /home to the root partition, and afterwards, move it back to the new logical partition destined for your /home. You will also need to update /etc/fstab such that the correct partition is mounted to /home.

---

### Post by capatt on 2008-07-21
What exactly is the output of that command and what would I have to customize for my current configuration?

What about this method:  
Create /home-bak in root, 
copy the contents of /home to that, 
unmount the partition /home was in, 
then copy everything back to /home, 
remove the /etc/fstab entry, 
reboot?

---

### Post by vanadium on 2008-07-21
If you want your /home to remain on your root partition, this will work: indeed, then you just can remove the entry for /home in /etc/fstab.

You should be aware that you must do all this from a live CD.

1. Boot a live CD session
2. Mount both the partitions "ubuntu root" and "Ubuntu home" (that is your terminology)
3. Create /home in "ubuntu root"
4. Copy home from "ubuntu home" to "ubuntu root"
5. remove the /etc/fstab entry
6. Reboot

You can do the repartitioning (deleting your "ubuntu home", create an extended partition and logical partitions within that) later from within your regular Ubuntu session (that way, you can´t accidentally harm your root partition).

---

### Post by Vivaldi Gloria on 2008-07-21
EDIT: vanadium corrected me below. This method will not work unless your non-allocated space and the swap are adjacent.

If the new OS you want to install works in a logical partition then you can do as follows.  Start partition editor (or gparted) using the ubuntu 8.04 live cd or 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

This is how it looks now:

```
Primary Partition: XP
Primary Partition: Ubuntu root
Primary Partition: Ubuntu swap
Primary Partition: Ubuntu home
unallocated space
```

Remove swap so that you get

```
Primary Partition: XP
Primary Partition: Ubuntu root
Primary Partition: Ubuntu home
unallocated space
```

Create an extended disk in unallocated space

```
Primary Partition: XP
Primary Partition: Ubuntu root
Primary Partition: Ubuntu home
Extended partition
```

Create the swap and the other partitions you want in the extended partition as logical partitions:

```
Primary Partition: XP
Primary Partition: Ubuntu root
Primary Partition: Ubuntu home
Extended partition - (Logical Partition 1: swap) + (Logical Partition 2: New OS) + ...
```

You need to edit fstab to reflect the change of the swap partition.

I guess grub is in the primary ubuntu root partition. I expect that any sensible new OS will add itself to it. (Not windows - but there are guides around for installing windows in a logical partition. A google search gives [http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition](http://www.sousuke.org/wiki/Installing_Windows_on_a_logical_partition) among others.)

---

### Post by vanadium on 2008-07-21
I am afraid that is a bit too easy to be true. It would work if swap was at the end of the used space, but there is no info that indicates this is the case.

---

### Post by Vivaldi Gloria on 2008-07-21
> **vanadium said:**
> I am afraid that is a bit too easy to be true. It would work if swap was at the end of the used space, but there is no info that indicates this is the case.

Yes you are completely right. Don't know what I was thinking.

---

### Post by capatt on 2008-07-21
I'll leave swap as it is, and just move /home.  I think that answers the problem for me and I thank everyone for the interesting discussion.

---

### Post by Potatoj316 on 2008-07-21
Using gparted you could delete the swap but I dont know if you can slide your partitions around, probably not.  I dont know about your swap but mine was in an extened partition by default.

---

### Post by capatt on 2008-07-21
I'm aware of just one application that can slide partitions:

[http://www.terabyteunlimited.com/image-for-linux.htm](http://www.terabyteunlimited.com/image-for-linux.htm)

I'm not about to spend the $$, though.

---

### Post by vanadium on 2008-07-22
You can "slide" (= move) partitions with gparted. Where and how you can move depends on your current partitioning scheme.

While creating, deleting and resizing partitions are fast processes, moving a partition can be very time consuming and does not not always proceeds successfully.

---

### Post by capatt on 2008-07-22
If one slides a partition (say sda4) to take the space of one that was deleted (say sda3), would the designated of the partition that was moved drop to sda3 in order to keep the numbering of partitions sequential?  If the partition moved was /home, would the fstabs need to be edited to reflect this change?
What happens if Ubuntu is booted up but there is no swap partition?  I have 4 GB RAM.....

Thanks

---

### Post by vanadium on 2008-07-22
Not sure whether sda4 would become sda3: I guess not. fstab would not need updating if you are using UUID. If using device names, the answer depends on that of the previous question. Ubuntu can start without a swap.

---

