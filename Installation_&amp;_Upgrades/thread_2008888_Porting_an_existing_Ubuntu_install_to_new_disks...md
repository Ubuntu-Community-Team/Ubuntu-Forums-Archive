---
title: "Porting an existing Ubuntu install to new disks.."
date: 2012-06-23
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2012-06-23
I have Ubuntu installed on a SATA drive and I plan on getting an SSD. I want to move the / directory to the SSD but leave swap and home on the SATA drive.

How can I do this and still have a working system?

I'm thinking the quickest / hackiest way of doing it would be to dd the entire existing SATA image to the SSD, update grub to boot the SSD and then modify fstab on the SSD to use /home and swap on the other drive for subsequent boots.

How does that sound?

---

### Post by darkod on 2012-06-23
I don't like using dd since it copies empty space too. Plus you can really mess things up if you confuse if and of.

Do you have a separate /home partition right now or it's a folder on /?

---

### Post by David Andersson on 2012-06-23
> **jarlath said:**
> 
I'm thinking the quickest / hackiest way of doing it would be to dd the entire existing SATA image to the SSD, update grub to boot the SSD and then modify fstab on the SSD to use /home and swap on the other drive for subsequent boots.

How does that sound?

For dd the partitions should have exactly the same size. Is /home on a separate partition on the SATA drive now? If not, dd will copy home too.

I would use *cp* or *rsync* and make sure they excluded the /home directory from copying. There are different ways to exclude /home, depending on if it is a separate partition or not.

---

### Post by QwUo173Hy on 2012-06-25
Thanks for your replies darkod & David Andersson.

> **darkod said:**
> I don't like using dd since it copies empty space too. Plus you can really mess things up if you confuse if and of.

Do you have a separate /home partition right now or it's a folder on /?

It's all on the same partition as / at the moment so maybe cp -R would be the best way to go in that case.

> **David Andersson said:**
> For dd the partitions should have exactly the same size. Is /home on a separate partition on the SATA drive now? If not, dd will copy home too.

I would use *cp* or *rsync* and make sure they excluded the /home directory from copying. There are different ways to exclude /home, depending on if it is a separate partition or not.
As above DA, it's on the same partition. So maybe I should use cp or rsync to copy the whole lot across and then delete the /home foler and update stab to point to the old drive?

I don't really have time for a 'project' at the moment so I'd rather avoid any linux adventures this time :)

---

### Post by oldfred on 2012-06-26
We often find those who try to use dd or some major copy as the adventure. With DD you get duplicate UUIDs and then have to edit fstab & reinstall grub2.

But even just copying you have to edit fstab & reinstall grub2 as the new drive has different UUIDs.

And install to SSD also should have some different fstab settings anyway for trim. I find a new install easy and then you can copy /home over or keep using the /home if separate partition from the rotating drive.

Some settings:
With SSD or Flash drives, Use ext2 or ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives) - SSD
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

