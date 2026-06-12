---
title: "GParted Help"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-03-28
Hi,
I zeroed out my 250GB HD using Sea Tools and I now want to create some partitions using GParted (while using the Live Ubuntu CD) so the size information will already be established when I try to install Ubuntu Studio.

When I opened up GParted, here in Ubuntu, the first thing I noticed was that my zeroed out drive shows up as unallocated space (expected) with only 233 GB of space (unexpected).

 My main question is:

Of the following list:
msdos, aix, amiga, bsd, dvh, gpt, mac, pc98, sun, loop.
Which option do I select? 
to correctly partition the drive to install Linux on an intel machine.

I think I can assume that I don't want aix, amiga,mac, sun, or loop.

Why isn't linux on the list?  

Why would I want an msdos partition to install linux?

Anyone have a clue about that size difference?
Thanks,

---

### Post by jerrrys on 2010-03-28
i have found that gparted on the live cd will get you by.  but i find gparted live to be a better choice. reading 233 of space?  i also get odd readings.  after you finish partitioning and restart it should read good.  any help??

---

### Post by wizarddrummer on 2010-03-28
> **jerrrys said:**
> i have found that gparted on the live cd will get you by.  but i find gparted live to be a better choice. reading 233 of space?  i also get odd readings.  after you finish partitioning and restart it should read good.  any help??

Thanks very much for the reply,

Sorry, I'm a little bit more confused now. 

Not sure I understand the difference is or what you mean with  "gparted on the live cd" and "but i find gparted live to be a better choice" Are these two separate programs?

I'm sill unclear about the choices msdos, bsd, loop etc.

---

### Post by jerrrys on 2010-03-28
gparted live is just like your ubuntu live cd.  it runs without the use of your HDD.  .  and i do not remember those choices coming up.  what was the option in the previous screen?

---

### Post by wizarddrummer on 2010-03-28
> **jerrrys said:**
> gparted live is just like your ubuntu live cd.  it runs without the use of your HDD.  .  and i do not remember those choices coming up.  what was the option in the previous screen?

I read the manual **[here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm"),** but I didn't understand if the label was just a name or whether it means that the particular partition is created with different attributes.

[IMG]http://gparted.sourceforge.net/larry/generalities/big/1-main-4b.gif[/IMG]

---

### Post by jerrrys on 2010-03-28
ok, that is where i use default and not advance

EDIT...thats wrong..be back...firing up gparted

---

### Post by ajgreeny on 2010-03-28
I don't think I have ever seen that appear when using gparted either.  Perhaps that's because I have never yet used a brand spanking new, unused disk, as far as I can remember.

Either way, I think you need msdos, unless the disk is over 2TB, if I remember correctly.  The fact that it is an msdos disk label will not affect the partitions you put on it, they can staill be ext3, ext4, reiser, or anything else.

---

### Post by jerrrys on 2010-03-28
> **ajgreeny said:**
> Perhaps that's because I have never yet used a brand spanking new, unused disk, as far as I can remember.

i don't even remember what one looks like

---

### Post by srs5694 on 2010-03-28
First, the size difference: Disk manufacturers define "giggabyte (GB)" to be 10^9 (or 1,000,000,000) bytes, whereas most disk utilities define "gigabyte (GB)" to be 2^30 (or 1,073,741,1824) bytes. Thus, a "250GB" hard disk holds approximately 250,000,000,000 bytes of data, which works out to about 233x2^30 bytes ("233GB", by most utilities' measure). From a technical point of view, the disk manufacturers' definition is correct (or at least more defensible), but it flies in the face of the usual convention for using power-of-two units for most size measurements in computing. This difference has been causing confusion for decades, although in years past the units of measurement were megabytes or even kilobytes. FWIW, I recently noticed a Slashdot story suggesting that Ubuntu would be switching its partitioner to use power-of-10 units with version 10.10. Also FWIW, when I wrote [GPT fdisk,](http://www.rodsbooks.com/gdisk/) I used power-of-2 units but gave them the more technically correct abbreviations of KiB, MiB, GiB, TiB, etc., rather than KB, MB, GB, TB, etc.

As to the partition table format, there are several choices. The two most common today are the Master Boot Record (MBR) and the GUID Partition Table (GPT). GParted refers to MBR as "msdos", presumably because the format originated in the days of MS-DOS. As ajgreeny's response hints, MBR has a size limit of 2TB (really 2TiB; it's based on power-of-2 units), so it will soon be going the way of the dodo, at least for hard disks. Its replacement is GPT.

For a Linux-only system with a sub-2TB hard disk, either MBR or GPT will work fine. GPT has some minor advantages, though, such as data redundancy, error checking features, a lack of the confusing and limiting primary/extended/logical partition differences in MBR, and the ability to name each partition. Therefore, my own personal preference and recommendation on Linux-only systems is to use GPT.

GPT does have some drawbacks, though. The most important of these is that Windows won't boot from a GPT disk on a BIOS-based computer. There's a workaround known as a [hybrid MBR,](http://www.rodsbooks.com/gdisk/hybrid.html) but it's flaky and a bit dangerous. Another problem is that there are some rare BIOS bugs that can cause boot problems for Linux on BIOS-based computers. AFAIK, these can always be worked around; see [my Web page on the topic](http://www.rodsbooks.com/gdisk/bios.html) for details. Still, the Windows limitation means that if the computer is to dual-boot with Windows, it's almost always better to use MBR.

If you've already partitioned your disk with MBR for a Linux-only installation, that's fine. As I said, GPT's advantages are fairly minor.

---

### Post by wizarddrummer on 2010-03-28
> **jerrrys said:**
> i don't even remember what one looks like

Now that's funny. Ahem. No, this is not a new disk.

A tiny story: I've been trying to install studio for a few days. The process kept dying. Why because my machine is a little flaky and I can't diagnose it.

I figured that it might be my hard drive. I downloaded the Windows version of Sea Tools ran the Long DST and Long Generic tests. It failed on the Long Generic.

So I downloaded the DOS versions so I could see if it could test and repair anything.
The test Passed in the DOS version. So I told it to write all zero out the drive.

The drive is about 6 years old.

Thanks, msdos, the default it is.

---

### Post by wizarddrummer on 2010-03-28
> **srs5694 said:**
> First, the size difference: Disk manufacturers define "giggabyte (GB)" to be 10^9 (or 1,000,000,000) bytes, whereas most disk utilities define "gigabyte (GB)" to be 2^30 (or 1,073,741,1824) bytes. Thus, a "250GB" hard disk holds approximately 250,000,000,000 bytes of data, which works out to about 233x2^30 bytes ("233GB", by most utilities' measure). From a technical point of view, the disk manufacturers' definition is correct (or at least more defensible), but it flies in the face of the usual convention for using power-of-two units for most size measurements in computing. This difference has been causing confusion for decades, although in years past the units of measurement were megabytes or even kilobytes. FWIW, I recently noticed a Slashdot story suggesting that Ubuntu would be switching its partitioner to use power-of-10 units with version 10.10. Also FWIW, when I wrote [GPT fdisk,]("http://www.rodsbooks.com/gdisk/") I used power-of-2 units but gave them the more technically correct abbreviations of KiB, MiB, GiB, TiB, etc., rather than KB, MB, GB, TB, etc.

As to the partition table format, there are several choices. The two most common today are the Master Boot Record (MBR) and the GUID Partition Table (GPT). GParted refers to MBR as "msdos", presumably because the format originated in the days of MS-DOS. As ajgreeny's response hints, MBR has a size limit of 2TB (really 2TiB; it's based on power-of-2 units), so it will soon be going the way of the dodo, at least for hard disks. Its replacement is GPT.

For a Linux-only system with a sub-2TB hard disk, either MBR or GPT will work fine. GPT has some minor advantages, though, such as data redundancy, error checking features, a lack of the confusing and limiting primary/extended/logical partition differences in MBR, and the ability to name each partition. Therefore, my own personal preference and recommendation on Linux-only systems is to use GPT.

GPT does have some drawbacks, though. The most important of these is that Windows won't boot from a GPT disk on a BIOS-based computer. There's a workaround known as a [hybrid MBR,]("http://www.rodsbooks.com/gdisk/hybrid.html") but it's flaky and a bit dangerous. Another problem is that there are some rare BIOS bugs that can cause boot problems for Linux on BIOS-based computers. AFAIK, these can always be worked around; see [my Web page on the topic]("http://www.rodsbooks.com/gdisk/bios.html") for details. Still, the Windows limitation means that if the computer is to dual-boot with Windows, it's almost always better to use MBR.

If you've already partitioned your disk with MBR for a Linux-only installation, that's fine. As I said, GPT's advantages are fairly minor.

Thanks,

Now you bring up an interesting question for me.

I have two hard drives. One is total XP and this one that I want total Linux.

If i understand you correctly; Windows can't boot from a GPT that has both Linux and Windows on it. Yes?

Then, ... can I have GPT on the Linux only HD and MBR on the Windows Only and Grub being able to do it's thing when the machine boots. 

I think this would mean if I have the XP disk as the first boot disk XP will load and won't see the Linux Disk. 

If I have the Linux disk first then (I assume Grub2) I will have a choice? 

Or is this the place you referred to where Windows will not boot correctly from the Grub menu?

---

### Post by srs5694 on 2010-03-28
> **wizarddrummer said:**
> I have two hard drives. One is total XP and this one that I want total Linux.

If i understand you correctly; Windows can't boot from a GPT that has both Linux and Windows on it. Yes?

Correct, unless the disk has a hybrid MBR, which I don't recommend using unless you've got a very good reason.

> Then, ... can I have GPT on the Linux only HD and MBR on the Windows Only and Grub being able to do it's thing when the machine boots.

Yes.

> I think this would mean if I have the XP disk as the first boot disk XP will load and won't see the Linux Disk.

Almost. XP will see the GPT disk, but it will see it as a disk with a single partition of unknown type, so it'll ignore the disk. (That's part of GPT's design; it includes a "protective MBR" to keep GPT-unaware OSes and utilities from messing with the disk.) Of course, XP will also ignore Linux partitions on MBR disks, so this isn't really very different from using MBR for the Linux disk.

> If I have the Linux disk first then (I assume Grub2) I will have a choice? 

Or is this the place you referred to where Windows will not boot correctly from the Grub menu?

It should work. I don't believe I referred to GRUB in my earlier reply, but GRUB2 (used by Ubuntu 9.10 and later by default) understands both GPT and MBR. I recommend setting up a small (35KB to 1MB) [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) when installing GRUB on a GPT disk.

In theory, it shouldn't matter which disk is first, although in practice there can be weird boot-loader/OS/disk-order interactions that can cause problems for some configurations.

To hedge your bets, you could set aside a small (~200MB) partition on the MBR disk. If you have problems getting Linux to boot, you could re-install Linux and turn it into a Linux /boot partition.

---

