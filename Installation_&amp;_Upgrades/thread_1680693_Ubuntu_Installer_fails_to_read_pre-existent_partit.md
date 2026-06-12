---
title: "Ubuntu Installer fails to read pre-existent partition table"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by stkrzysiak on 2011-02-02
Hi everyone, 
So I decided to reinstall my 10.10 to undo the 'encrypted home folder feature.'  I know are other ways to undo the encryption, but for various reasons I'd rather just do a quick reinstall and start fresh.  Currently, I dual boot linux and windows, each with their respective partitions.  There is also a storage partition that is fat32 to swap files between the two OSes.  So the partitions are: 
Linux:
swap
/
/home

then the windows partition and the storage partition.

So when I fire up the installer, it doesn't recognize a valid partition table.  It tells me to either install on the entire disk or partition myself.  I choose the latter and see a completely empty disk!  No partitions.  So my ultimate question is this:  Does the home encryption make the partition table behave differently somehow?  

Also, this may be worth noting.  When I do boot into my linux install, I do not see the fat32 storage partition but I do see the windows partition and can access it.  I found this odd immediately upon my intitial install as it should be there, and is the whole point of its existence.

I haven't had a chance to inspect the partition table with other tools.
[B]
tl;dr[/B] Does the ubuntu home encryption option make the partition  table unreadable?

Much thanks for any insight, and I'll update accordingly if I figure it out.

-Steve

---

### Post by sikander3786 on 2011-02-02
Can you please post the output of this command from your Applications > Accessories > Terminal.

```
sudo fdisk -lu
```

The fix most likely seems to lie in this link.

[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)

But better let us see the output first.

---

### Post by stkrzysiak on 2011-02-06
Being from Chicago, I didn't think anything could cheer me up today, but this did, thank you so much.  Looks like you're spot on.  :p
[HTML]ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd9042418

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   565134569   282463861    7  HPFS/NTFS
/dev/sda3       565127166   976768064   205820449+   5  Extended
/dev/sda5       565127168   580749311     7811072   82  Linux swap / Solaris
/dev/sda6       580751360   639342591    29295616   83  Linux
/dev/sda7       639344640   836147199    98401280   83  Linux
/dev/sda8       836149248   976771071    70310912    b  W95 FAT32
[/HTML]

---

### Post by dino99 on 2011-02-06
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.

bad formatting, fix it (chkdsk or so). 

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by stkrzysiak on 2011-02-06
Actually, I may have jumped the gun, doesn't seem like I am exceeding boundaries, but it definitely appears that something is amiss...

---

### Post by srs5694 on 2011-02-06
> **dino99 said:**
> /dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.

bad formatting, fix it (chkdsk or so).

There's nothing wrong with the partition you've quoted. I wish the fdisk developers would just remove those "does not end on cylinder boundary" messages; today there's no reason to align partitions that way (unless you're running some *very* old versions of DOS), and the messages just make people think there's something wrong with their disks when there isn't.

That said, there *is* something wrong with the disk:

[quote=stkrzysiak]```
stkrzysiak

/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   [COLOR=Red]565134569[/COLOR]   282463861    7  HPFS/NTFS
/dev/sda3       [COLOR=Red]565127166[/COLOR]   [COLOR=DarkOrchid]976768064[/COLOR]   205820449+   5  Extended
/dev/sda5       [COLOR=Red]565127168[/COLOR]   580749311     7811072   82  Linux swap / Solaris
/dev/sda6       580751360   639342591    29295616   83  Linux
/dev/sda7       639344640   836147199    98401280   83  Linux
/dev/sda8       836149248   [COLOR=DarkOrchid]976771071[/COLOR]    70310912    b  W95 FAT32
```[/quote]

I've highlighted the problems in your partition table. Go over it yourself, though; it's easy to miss problems. No partitions should overlap, with the exception of the extended partition, which must be large enough to contain all the logical partitions (those numbered 5 and above). The extended partition must not overlap any other primary partitions (numbered 1-4). Your /dev/sda2 overlaps both the extended partition and the first logical partition it contains. Also, your extended partition is not big enough to cover all your logical partitions.

The first problem is potentially very dangerous; an unlucky write to /dev/sda2 could end up wiping out all your logical partitions. Thus, I *strongly* recommend you don't boot Windows and don't mount that partition in Linux until you resolve this problem.

I recommend you read [this Web page of mine,](http://www.rodsbooks.com/missing-parts/index.html) which describes a simpler variant of the problem you've got, along with some solutions. There are several ways to deal with this problem. I recommend you begin by backing up all your important data, since every solution is at least a little risky. With that done, try to use fdisk to delete /dev/sda5 (your swap partition). That will eliminate one problem, and swap space is easily re-created. I'm not sure that fdisk will permit you to save the partition table at that point, because of the remaining problems. If not, you could try sorting the partitions (using the "f" option on fdisk's experts' menu). If you're very lucky, those actions alone might fix the problem, although you'll then need to create a new swap partition. If you can save the partition table but the overlap remains, then using sfdisk (as described on my Web page) to change the start point and length of the extended partition may be the best solution; or you can use gdisk to convert to GPT and back to MBR, which will lose and re-create the extended partition. This back-and-forth conversion will require you to reset the Linux partitions' type codes, and you may have to re-install GRUB (but if you're re-installing Linux, that's not a big deal; the installer will do it).

Additional background information: [Partitioning with fdisk](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html) and [the gdisk instructions](http://www.rodsbooks.com/gdisk/) (see in particular the page on [url=http://www.rodsbooks.com/gdisk/mbr2gpt.html] converting between partition table formats).

Anyhow, please check the pages to which I've linked and post back if you have further questions. I realize this is a scary and confusing situation. There are a lot of very bad partitioning tools out there that create these problems, and not much in the way of good recovery tools (at least, not that I'm aware of).

---

