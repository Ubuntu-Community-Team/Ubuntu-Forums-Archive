---
title: "partitioning on HP laptop"
date: 2011-10-01
forum: Installation &amp; Upgrades
---

### Post by teacherjeff on 2011-10-01
I've been using Ubuntu in a WUBI installation.  I like it, so I'm starting to plan to install it for real.  But I seem to have a problem.  I want to dual boot with Windows 7 (I need Windows for work, so getting rid of it is not an option).  But it seems I already have four partitions on the hard disk:

SYSTEM NTFS 209MB
(main Windows partition)   NTFS 476GB
RECOVERY NTFS 23GB
HP_TOOLS FAT 108MB

RECOVERY would appear to be an image of the installation files.  HP_TOOLS looks to have utilities for updating the BIOS.

So what is the most sensible, least disruptive way to free up a partition for Ubuntu?  I really don't want to mess up my Windows installation, and while I did make recovery DVDs, I would really rather not lose the RECOVERY partition on the disk.  But if that's what I have to do, I will.

Advice?

Thanks

---

### Post by Quackers on 2011-10-01
Well noticed! Some people don't and pay a price.

Other people in your position have deleted the HP TOOLS partition (as they are available to download, if required from the HP site).
This doesn't leave much space for Ubuntu so the next thing is to defragment (IMPORTANT!) the Windows C: drive, then shrink that C: drive using the Windows Disk Management utility by as much as you need.
You will then have some unallocated space for Ubuntu to install into.

---

### Post by Mark Phelps on 2011-10-01
Quackers gave you some excellent advice!

And pay particular attention to the use of the Win7 Disk Management tool to shrink the Win7 OS partition.  Don't take the lazy way out and let the Ubuntu installer do the resizing for you.  That runs the risk of corrupting the Win7 OS partition and rendering it unbootable.

And, to be safe, BEFORE you do anything else, use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will come in handy later, should you need to repair the Win7 boot or restore the original Win7 MBR.

And, AFTER you do the resizing, if you want a restorable version of Win7 (which eliminates the need for the Recovery partition), then download and install the FREE version of Macrium Reflect and use the option to create the Linux boot CD.  Once you image your Win7 install to an external drive, using the Linux boot CD, you now have a means of restoring it in just a few minutes.

---

### Post by teacherjeff on 2011-10-25
I just wanted to thank both of the posters above for their excellent and helpful advice.  I repartitioned, installed Oneiric, and it's up and running.;)

---

### Post by Quackers on 2011-10-25
Nice one! Glad to hear that :-)

---

### Post by bobthe on 2012-04-26
hello! i also have a HP laptop and was wondering the same. 

when Quackers said to defragment, how exactly do i do that? Windows 7 disk management tool doesn't have that option. and can't i just delete the partition with SYSTEM (199 MB, NTFS)?

Can someone please guide me? Thanks!

---

### Post by jadtech on 2012-04-27
> **bobthe said:**
> hello! i also have a HP laptop and was wondering the same. 

when Quackers said to defragment, how exactly do i do that? Windows 7 disk management tool doesn't have that option. and can't i just delete the partition with SYSTEM (199 MB, NTFS)?

Can someone please guide me? Thanks!

 from windows - start menu - accessories - system tools -defragment

---

### Post by bobthe on 2012-04-27
i'll try to do that ^

---

### Post by jadtech on 2012-04-27
> **bobthe said:**
> hello! i also have a HP laptop and was wondering the same. 

when Quackers said to defragment, how exactly do i do that? Windows 7 disk management tool doesn't have that option. and can't i just delete the partition with SYSTEM (199 MB, NTFS)?

Can someone please guide me? Thanks!

I don't reccomend deleting the partition with system (199mb, NTFS) it is the Master boot record  window will no longer boot for you when that is gone .

removing hp tools is a better solution not likly you wil need them how ever if you do you can go to HP website and down load  it again and install  your computer will run fine without it ..

---

### Post by SeijiSensei on 2012-04-27
If you want to preserve everything, I posted a [set of steps]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5") that I used to repartition an HP dv6t.  It's a bit complex, but one nice feature is that you end up with a much cleaner version of Windows without all the added cruft that HP ships.

If you're not comfortable using the command-line partitioner fdisk as I describe in the linked article, use gparted instead.

---

### Post by bobthe on 2012-04-28
@jadtech: so deleting hp tools should be okay?
@SeijiSensei: Thanks! I'll try it out

---

### Post by rplantz on 2012-04-28
My laptop is dual-boot (Windows 7 / Ubuntu) and desktop triple-boot (Windows 7 / Windows 8 / Ubuntu).

One thing to note here is that if you use grub, you will lose the ability to boot into the Windows repair options. At some point in the Ubuntu installation process there is the ability to install its boot loader only in the Ubuntu partition. This keeps the Windows 7 boot loader as the primary one. Then I used EasyBCD (under Windows 7) to add Ubuntu as a boot option.

BTW, when I installed Windows 8 Consumer Preview on my desktop machine, it preserved the Ubuntu entry in (presumably) the Windows 7 boot loader, thus easily giving me the triple boot capability.

---

### Post by jadtech on 2012-04-28
> **bobthe said:**
> @jadtech: so deleting hp tools should be okay?
@SeijiSensei: Thanks! I'll try it out

yes deleteing hp tool partition will be fine  , the you will be able to shrink win7 partition a some for free space to set up ubuntu ..

SeijiSensei's solution will make a way cleaner  setup  it does require some experience with the command prompt or Gparted  also requires reinstalling everything including windows with out the HP installed junk ...

---

