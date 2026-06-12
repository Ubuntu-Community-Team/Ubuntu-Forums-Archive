---
title: "Partitioning a WinXP/Ubuntu 9.10 dual-boot"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Wintermut3 on 2010-01-27
Hi :) Welcome to the n00b an' all that.

I've finally given up in exasperation with XP, and, having tried the Ubuntu Live CD I'm convinced enough to give it a go for real.

However, some of my Win programs don't have Linux counterparts and won't, as I understand, run too well under WINE (sound apps like Reason / Ableton etc), plus I don't really want to jump in with both feet just yet, so I figure a dual-boot is the way.

The target machine is a 5-6 year old compaq laptop with a 50GB hard drive. Currently the XP install - which I've cut down as much as possible - is taking up 20GB of this, on a single partition.

My plan is to put Ubuntu on a new 20GB partition, leaving XP 30GB to play with. However, I've read that XP needs about 20% free space to function effectively, so my first question in the Ubuntu forum, to users of Ubuntu, is: will my partitioning adversely affect Windows?

Secondly, the [official docs]("https://help.ubuntu.com/9.10/switching/installing-partitioning.html") seem to breeze through the whole resize-repartition-install process. Just stick the disk in, tell it how big you want your new partition to be, and breathe out. However, I've stumbled upon [this entry in the community docs]("https://help.ubuntu.com/community/HowtoResizeWindowsPartitions") that seems to contradict it:
> After shrinking the Windows partition, you should  reboot once (or twice) into Windows prior to installing Ubuntu (or using  GParted). This allows the Windows system to automatically rescan the  newly-resized partition (using chkdsk in earlier versions or a similar  utility in later versions) and write changes to its own bootloader  configuration files. 
If you start  mucking around with other partitions before Windows has a chance to  reset itself, the Windows bootloader will not be able to read the  partition table properly (and will therefore refuse to boot entirely).  If this happens, you may later have to repair the Windows partition  bootup files manually using the Windows Recovery Console. That seems to be saying... resize manually first, and reboot windows when you're done, otherwise you could corrupt your Win installation.

Any advice? What's recommended?

Thanks :)

---

### Post by darkod on 2010-01-27
Yeah, for XP definitely resize first, do everything else later. :)
Since XP doesn't have tool for resizing in disk management, I would backup first. Then boot with ubuntu cd, Try Ubuntu option, open Gparted in System-Administration, and resize XP to 30GB as you said. That will leave unallocated space. DO NOT ceate any partitions into it at this stage.
Reboot without the cd and boot XP few times, to swallow the resize.
After XP is happy, boot again with ubuntu cd, Install Ubuntu option, and in step 4 just tell it to Use Largest Available Free space. It will make default installation into the unallocated space you left.
That should be it.

PS. When using Gparted initially it only schedules your tasks (you can see them at the bottom). That gives you the chance to just exit Gparted with no changes to the disk if you change your mind. If you want to execute your commands you need to hit the big green tick mark button in Gparted toolbar.

---

### Post by bluesscream on 2010-01-27
I just resized an xp to get free space for an experimental lucid installation. This is my way i did it several times: After backing up important stuff first I also resize window's ntfs partition with a live cd and reboot  windows once. Then in ubuntu's install process I choose the manual way, define size for swap, /, home, then format and install. No warranty, but I never lost data.

---

