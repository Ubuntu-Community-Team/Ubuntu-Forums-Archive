---
title: "Quick question about unwanted free space in new installation."
date: 2015-09-30
forum: Installation &amp; Upgrades
---

### Post by hey2 on 2015-09-30
Hi.

Just a quick question:

I'm trying to make a fresh install with just 2 partitions and a swap.

No matter what i do, after everything is installed, on Disks i see a small unallocated space.

I've tried installing Ubuntu on a Laptop and on Disks it shows only the partitions that i made.

What could be happening on my desktop?

Thanks.

---

### Post by v3.xx on 2015-09-30
Are you seeing a bit of free space like this?

[ATTACH=CONFIG]264753[/ATTACH]

Because of..

[ATTACH=CONFIG]264754[/ATTACH]

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by hey2 on 2015-09-30
Hi.

Thank you very much for your reply. 

I don't know if i understand what you're saying.

In mine i see Swap, two ext4 (/ and one without mounting point) and a free space of 1.1mb.

My problem is that i didn't do anything to have that free space.

Once again, thanks.

---

### Post by yancek on 2015-09-30
Are you using GPT partitioning?  If so, the article below would shed some light on the subject.

[http://linuxbsdos.com/2014/02/05/gpt-disk-partitioning-guide-for-ubuntu-13-10-on-a-pc-with-uefi-firmware/](http://linuxbsdos.com/2014/02/05/gpt-disk-partitioning-guide-for-ubuntu-13-10-on-a-pc-with-uefi-firmware/)

---

### Post by oldfred on 2015-09-30
It also could just be rounding.
With the old MBR(msdos) the rounding was smaller and did not appear on partitioning tools. First sector was 63.
But with new 4K drives & SSDs, first sector is 2048 and now partition tools may show that as unallocated space. But rounding is important for drive to function well.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by hey2 on 2015-09-30
Hi.

I'm not using Gparted.

I installed Ubuntu with the live USB.

After i installed, i ran the live usb to use gparted so that i can resize the drives.

The weird thing is that Gparted only let me use that extra 1.1mb to one of the drives (the one without any mount point).

Is this the normal behaviour?

> **oldfred said:**
> It also could just be rounding.
With the old MBR(msdos) the rounding was smaller and did not appear on partitioning tools. First sector was 63.
But with new 4K drives & SSDs, first sector is 2048 and now partition tools may show that as unallocated space. But rounding is important for drive to function well.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

Thank you very much for your time and detailed post.

That makes sense, but i tried the the same not so long ago on a laptop and it used all the space.

I just tried allocate that space with gparted and it worked. The weird thing is that it doesn't let me allocate that space to the / partition.

Do you see this extra 1.1mb on yours?

---

### Post by oldfred on 2015-09-30
I am using gpt & new drives, both a small SSD & larger HDD. I do not have any of the small unallocated.

But if I remember with my older BIOS system with MBR, it did have some of those. I think one somehow was even shown as NTFS even though I do not think I ever set it as NTFS. But since so small with the sizes of new drives I have not worried about a few MB here & there.

---

