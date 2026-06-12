---
title: "Can anyone help this poor newbie unable to install dual-boot setup to SATAII HDD"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by Gizmonty on 2006-12-25
I have spent the last 2 days trying to get Ubuntu 6.10 to install on my system with no luck. I have a 320G SATAII HDD with a 160G partition that boots Windows XP and the rest unassigned. The HDD is hooked up via a PCI express RAID controller card as a single drive Concatenation and boots XP very well (but I think this card is the source of my woe). My system is an Athlon 64 3200 with 1G of RAM (but I'm installing the 32 bit version). I have tried many different ways of installing Ubuntu and probably can't list (or remember) everything I've done here but here's a brief summary.

Performed an install using the desktop install CD. Partitioned the unassigned portion of the HDD as 158G ext3 primary partition and 2G Swap partition. Let it run and it seemed happy. When I restarted though it went straight into XP. Grub did not appear.

After a bit of research I decided that maybe I needed to use the alternate install CD because it gives more control over what can be done with Grub. When I used this though, it did not even acknowledge the existence of my HDD! I couldn't get as far as partitioning because there was nothing to partition!

My suspicion is that using this RAID controller card to connect my HDD is causing the problem. I have no other way of connecting this HDD to my motherboard though.

Is my problem the same FakeRAID thing that others complain about. This seems odd to me if it is as I don't actually have a RAID set up. I have thought about getting a new Mobo with built in SATAII connections as this would (I think) eliminate the whole RAID issue but I would rather save my money if I can. Can anyone help?

---

### Post by bulldog on 2006-12-25
You have IDE connectors on your motherboard I presume?
Just find an old hdd which uses IDE and install Ubuntu on it,and leave windows on the other disk.
20GB or more should be sufficient.

---

### Post by Irony on 2006-12-25
> When I restarted though it went straight into XP. Grub did not appear.

Do you mean that it started up with the usual windows bootloader, did you install GRUB to the MBR.

---

### Post by Gizmonty on 2006-12-25
Thanks for the replies.

At present I don't have any old IDE HDDs lying around. I would prefer to have everything on the single drive anyway (for aesthetics as much as anything).

As for installing GRUB to the MBR, when I installed from the desktop version it seemed to be installing GRUB but then the usual Windows bootloader was all that I had afterward. This is why I tried the alternate install CD but it completely failed to recognise the HDD at all when the partition manager loaded! It's hard to install a program on a drive that your computer doesn't believe exists.

---

### Post by bulldog on 2006-12-25
I think you have a driver installed in windows to recognize the PCI card.
It's fairly possible this is the reason it's not 'seen' by ubuntu.

Maybe it's an option to buy a new IDE drive?
They are cheap now a days and you don't need a huge amount of GB.
Think about it,you can't mess your windows if things go wrong.

---

### Post by psusi on 2006-12-27
When you installed from the livecd, what was the name of the device that you installed to?  Was it /dev/sda?

You can try manually installing grub to make sure takes.  Please post additional system information.  Start by posting the output of fdisk -l on each disk.

---

