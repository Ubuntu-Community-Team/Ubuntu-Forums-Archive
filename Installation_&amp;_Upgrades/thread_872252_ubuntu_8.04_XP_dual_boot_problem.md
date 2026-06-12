---
title: "ubuntu 8.04 XP dual boot problem"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by outerspacerace on 2008-07-27
Hi all,

I'm having some difficulty trying to install ubuntu 8.04.

I have Windows XP home installed on my 80GB IDE drive (C:\ under XP) and would like to set up a dual boot system.

I also have a 320GB IDE (D:\ under XP) and a 500GB SATA drive (E:\ under XP).

The integrity of the live CD has been checked and contains no errors. In addition to that I've defragged all drives from within XP.

Problem is once reaching the partitioner step, it wants to do the Guided-Resize install option on my 320GB drive, not the drive containing Windows XP obviously.

It does detect the 80GB drive, I can see it greyed out under the Guided-use entire disk option.

I tried unplugging both the 320GB/500GB drives in order to force it to use the 80GB drive although that simply made the installer freeze when at the scanning disks stage.

I've noticed something that could well be the problem but am unsure of how to fix it.

In the example below, the install drive is labeled SCSI2 (0,0,0)

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm?page=3)

However, on my system the install drive shows up as SCSI2 (0,1,0) from memory.

Any ideas folks?

Would love to get this sorted out as I think I'm going to quite like ubuntu from the live CD trial!

Thanks in advance.

---

### Post by outerspacerace on 2008-07-28
I now realise there is a small 8MB partition on my C:\ drive that I was attempting to install onto - apparently (from a quick google) ubuntu won't do the Guided-Resize option on drives with multiple partitions.

In XP's Computer Management> Disk Management the 8MB partition doesn't show up at all.

I'm not sure how that partition got there, maybe it was left over from a Windows install, either way I need to rectify the problem ASAP.

What should I do, try to delete the partition (I think not as it shows up as free space from within the ubuntu partitioner) or reformat it to be NTFS somehow?

So if possible I need a quick how to on that one... otherwise I'm guessing I'd have to manually create a partition on the drive for ubuntu to install on?

I'm not confident with doing that just yet so help is much appreciated.

---

### Post by outerspacerace on 2008-07-28
P.S. I don't have my XP installation CD handy right now either... figured that would give me further access to these annoying 8MB's.

---

### Post by cdtech on 2008-07-28
From the Window's Support:

> Some space at the end of the disk is reserved by Setup in case you later want to upgrade the disk to a dynamic disk. Dynamic disk information is saved at the end of the disk. The amount that is reserved is a minimum of one cylinder, or 1MB, whichever is greater. One cylinder can be up to 8MB, depending on drive geometry and translation.

Some just remove the additional partition.

**P.S.**
You will have to create a partition for your Ubunut install.......

---

### Post by outerspacerace on 2008-07-28
Wow, thanks for such an informative reply!

I didn't appear to be able to remove the additional partition from GParted or the Ubuntu installer though.

I will go back and try again, as well as that I'm downloading Acronis software to help in doing so.

How annoying that Microsoft do that! Also, why the hell doesn't that show up from within the XP Disk Management section... very frustrating.

Oh well, I'll report back & thanks again.

---

### Post by outerspacerace on 2008-07-29
After a couple of attempts I still haven't been able to manually partition the c:\ drive for a ubuntu install yet.

I probably aren't doing it right, it aborts (forget the exact error message - am at work now) into the process yet luckily my XP install is still fine.

Can somebody please give me a guide on how to manually resize my XP partition so that I have 20GB free for ubuntu?

As I posted earlier, I can't use the installer or GParted's graphical interface to do so.

On previous PC's ubuntu has installed perfectly as a dual boot along with XP but this one is proving tough.

I'd rather not have to buy something like Acronis Disk Director unless I really have to :(

---

### Post by xen-uno on 2008-07-29
There's nothing in stock Windows that will let you resize C:. I use Paragon Hard Disk Manager for such disk related tasks, and I don't think even it would allow me to shrink the boot partition, if I recall correctly. Short of a basic re-install (and application of your Windows backup), I think Acronis is your only solution.

---

### Post by outerspacerace on 2008-07-29
Acronis will let me re-size (shrink) the boot, the demo just won't apply the changes, looks like a good program though.

Yeah, I knew I couldn't do it with stock XP tools... are you also telling me I can't shrink it manually from the live CD installer - or just that it's hard to explain here?

I'd like to do it for free it at all possible...

---

### Post by xen-uno on 2008-07-29
It's real hard for me to explain cuz I haven't done it :). Have you done a forum search yet? I'm pretty sure that resizing via Acronis would be the safest, most fault tolerant way.

---

### Post by outerspacerace on 2008-07-30
Well I'm happy to say I got it working perfectly manually so I saved myself some dollars as well as learning a few things about partitioning and other things in the meantime.

Thanks to all who helped here.

If I was better able to explain what I'd done I'd write a guide... I'd be very surprised if more first time users weren't running into the problem of the Guided Resize not working due to multiple partitions - even small 8MB ones created by Microsoft.

---

