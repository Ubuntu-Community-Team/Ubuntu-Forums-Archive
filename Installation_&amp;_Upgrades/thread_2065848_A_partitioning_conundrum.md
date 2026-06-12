---
title: "A partitioning conundrum"
date: 2012-10-03
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-10-03
I've just gotten myself a Lenovo laptop, which came with Windows 7 preinstalled (no surprise there).  I've installed Kubuntu on quite a few systems before, but this one poses a new problem for me.

The hard drive comes with four primary partitions, as revealed by Gnu Parted (running off a flash drive).  If one of them was an extended partition there would be no problem -- I could just create a new Linux secondary partition and move things around as needed.  I'd rather not clobber any of the existing partitions, though of course I can move them around or even resize them.  Is there any way to create a partition for Linux without losing the contents of one of the existing partitions?

---

### Post by darkod on 2012-10-03
If you already have 4 primary, there is no way to create new partitions.

Usually the suggestion is to delete the recovery partition, that way you can also utilize the space it holds. Boot windows and look for the recovery/backup software that comes with the machine. It should offer possibility to create a set of DVDs from the recovery partition. That way you can still do a factory recovery even with the partition deleted, simply use the DVDs.

If you can't find the option, look in the manual or contact their support.

Once you delete the partition, it seems you know what to do. :) Just a reminder that if shrinking another partition (to create more unallocated space than the recovery partition has to offer) it's best to do it from within windows with Disk Management.

---

### Post by prshah on 2012-10-03
> **pwabrahams said:**
>  Is there any way to create a partition for Linux without losing the contents of one of the existing partitions?

No, you cannot create a partition with 4 primary partitions already created.

However, if your usage of Ubuntu is going to be occasional, you might want to look at a Wubi (within Windows) install.

---

### Post by coffeecat on 2012-10-03
> **pwabrahams said:**
> Is there any way to create a partition for Linux without losing the contents of one of the existing partitions?

If the drive has an mbr partition table, then no. You would have to remove one of the primary partitions before you could create an extended partition for your logical partitions. The same problem has been plaguing HP owners for some time. Two of your current partitions would be the Windows 7 system (boot) and C: partitions which, obviously, are essential. A third is likely to be a restore partition. With HP machines some people delete that one after they have made a set of restore DVDs. Before making any decision, you need to establish what the fourth is. Post a screenshot of the Windows 7 Disk Management window, and from a Kubuntu live CD or USB session post the output of these two commands:

```
sudo blkid
sudo fdisk -lu
```

blkid to get the partition labels and fdisk to see the exact partition layout and whether the drive has an mbr partition table. Which leads to the next point....

It is possible that the drive has a GUID partition table (GPT) with UEFI firmware and an EFI partition. If so, **do not** delete the EFI partition. If the drive is GPT, then there is no 4 partition limit. You don't have extended/logical partitions as the partition number limit with GPT is 128 (if I remember correctly). However, with GPT there are some issues that you need to know about in order to get Windows and *buntu dual-booting.

If you do have UEFI/GPT, then the above information should tell us this and we can take it from there.

---

### Post by SeijiSensei on 2012-10-03
I posted the steps I followed to deal with this problem on an HP laptop here: [http://ubuntuforums.org/showthread.php?p=11299287#post11299287](http://ubuntuforums.org/showthread.php?p=11299287#post11299287)

You have to wonder why OEMs ship machines with all the primary partitions in use.  My conspiratorial mind thinks they are conniving with Microsoft to make it difficult to create a dual-boot machine.  Certainly there is no technical reason why they couldn't use an extended partition.

---

### Post by pwabrahams on 2012-10-03
I've attached the requested images.  As you can see, there's a small partition at the beginning (which I assigned the E: drive letter -- it didn't come that way), two ordinary partitions, and an oddball one at the end.  I could easily shrink the C: partition since there's plenty of space.  I suppose #1 and #4 handle boot and recovery; #4 is an oddball.
But which is which?

What I thought of doing was copying the contents of #1 (200 MB)into #2 and then deleting #1 -- if that doesn't kill the bootup.  Once I have a partition loose, I'm home free.  I can restore partition #1 a little later, provided that it's only its contents that matter.

I was hoping that by some magic I could use gparted to convert one of the primaries to a secondary within an extended partition, but I guess that's not possible.

In any event, I see no reason to disturb #4.

An afterthought: a vital question is whether deleting and recreating either #1 or #4 paralyzes the machine.  In other words, do these partitions have any essential invisible properties beyond their location and contents?

---

### Post by coffeecat on 2012-10-03
> **pwabrahams said:**
> What I thought of doing was copying the contents of #1 (200 MB)into #2 and then deleting #1 -- if that doesn't kill the bootup.

Yes it will. Partition 1 is your Windows 7 boot partition - it usually has the partition label "system", but yours doesn't for some reason. It's theoretically possible to write the boot files to the partition boot sector of sda2 if you have a proper Microsoft Installation DVD or Windows 7 repair CD prepared from within Windows, but if that was my machine I would investigate exactly what sda3 and sda4 are doing, and leave sda1 well alone. My guess is that sda3 is your Lenovo recovery partition, but I have no idea what your Compaq Diagnostics partition is and why it needs to be 19.5GB. I also wonder what a partition labelled Compaq Diagnostics is doing on a Lenovo machine. I thought Compaq was part of HP. You'll see that the Compaq partition is not formatted NTFS, so it would be interesting to know what it is meant to do.

---

### Post by 1clue on 2012-10-03
Do yourself a favor and create a recovery CD/set of CDs/DVD before you go trashing recovery partitions.  If you ever sell this thing, you'll probably want it in its original state, and if you don't have the original OS on there (or the recovery media) then you or the new buyer will need to buy a full non-oem license.

---

### Post by darkod on 2012-10-03
You shouldn't force a drive letter to sda1, it's supposed to be hidden and not seen in Computer.

I think sda4 is the recovery partition since blkid says the name is LENOVO_PART. The fdisk results just interpret the partition code (12) as Compaq Diagnostics.

sda3 might be a separate partition they did just so it's separate from C:. That would explain the D: letter assigned, unless you did that too yourself. In contrast, sda4 doesn't have a letter assigned and should be hidden too.

As I already mentioned, my bet would be to first create the set of recovery DVDs, and once you have that delete sda4.

With this layout, you might as well move any data from D: (sda3) and delete that too. That would give you approx 45GB joined unallocated space for ubuntu. If you want more, you will have to shrink C: for as much as you want.

I wouldn't play around with sda1 and the boot process, no need and too risky. And I would undo the letter assignment.

---

### Post by 1clue on 2012-10-03
Actually, better yet do what I did with my fiancee's laptop:

Go buy another drive, swap them out and you will have everything exactly as it was if you decide to switch back at some point.  "undo" then becomes a 5 minute project.

---

### Post by Mark Phelps on 2012-10-03
If you download and install EasyBCD from NeoSmart technologies, it had an option that will allow you to "migrate" the boot loader folder and files into your "OS" partition. Once installed, click the BCD Backup/Repair button, then click the Change boot drive radio button and select the OS partition.

After this, your boot files will be in the Win7 OS partition and you can then remove the original boot partition.

But, BEFORE you do this, do yourself a favor and use the Win7 Backup Feature to create and burn a Win7 Repair CD.  That way, if anything goes wrong later, you can use that CD to rewrite your boot loader files.

However, that said, you are far from "home free" after you remove this one TINY partition.  You will need to shrink the Win7 OS partition to make some room.  Use only the Win7 Disk Management tool to do this; do NOT attempt to do this using the Ubuntu installer and its slider.  Doing it that way risks corrupting the Win7 filesystem and rendering it unbootable.

---

### Post by pwabrahams on 2012-10-03
A couple of things I didn't make clear.  I thought all along that with 4 primary partitions, there was no way I could create an extended partition unless I deleted one of them.  But I was hoping I was wrong and had overlooked something, which was the whole point of the post.  Unfortunately it seems that I was right.

When I assigned the drive letter E to sda1, I didn't actually create anything.  I did that through Windows Disk Management.  So after that I still had 4 partitions: sda1 (E:), sda2 (C:) sda3 (D:), and that fourth unreadable recovery partition.  E: seems to be the boot partition.

I've taken the suggestion and, as we speak, I'm creating a set of recovery DVDs.  It takes 4 of them, and a lot of time.

I think I've gotten around the problem, though.  What I did was to copy the entire contents of D: into a folder in C: and then delete the D: partition.  There was a weird recovery folder within D: that didn't seem to make it across, but I may never miss it.  Once D: was gone, I used gparted to create an extended partition in its place, starting with an NTFS logical partition.  In passing I also created root, home, and swap partitions for Kubuntu.  When I rebooted back into Windows I was able to assign D: to that new logical partition and copy the contents of the old D: into it.

Now that I've gotten the flexibility of that extended partition, I can change things again if it proves necessary in the future.

By the way, one annoying oddity of the Lenovo Z580: it doesn't seem to have a disk activity light.  None of the reviews I've seen mentioned that.  Maybe it's lurking somewhere where I couldn't find it.

---

