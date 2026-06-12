---
title: "Ubuntu on a secondary ATA drive without GRUB in a XP/Vista system"
date: 2008-03-08
forum: Installation &amp; Upgrades
---

### Post by viking23 on 2008-03-08
Hi all,
I would like to install Ubuntu on my Vista/XP dual boot system. So right now Vista is controlling the boot process.
Vista/XP reside on the main hard drive which is a serial primary drive.
I also have a 200gig parallel ATA drive connected as the primary with my DVD drive as secondary.

As I only have 15gigs for each vista and xp left on my main drive, I would like to install Ubuntu on the secondary drive. Obviously there is going to be performance issues right? are there any ways to mitigate them??

second, last time I had ubuntu but decided to get rid of it and I took the brute force method and simply formatted using XP, the logical disk in the primary drive where Ubuntu was. Bad Idea, it immediately crashed the system and I had to use the restore XP disks to fix the MBR.

So basically I dont want GRUB to manage the booting process and I would like to simply format the logical drive if I dont want Ubuntu for some reason.

I can find step-by-step instructions for each of my above needs, but is there something missing when I try to do all of the above: Ubuntu on a secondary disk with no grub + Vista as the boot manager?
So could somebody help me give me advice/instructions on how I may go about doing these?

thanks,
V.

---

### Post by mikewhatever on 2008-03-08
There shouldn't be any performance issues, unless something is wrong with the secondary HDD you want Ubuntu on. During the installation, you can specify where to install GRUB by hitting Advanced button in the bottom right corner, or use an Alternate CD and skip GRUB all together ([Alt CD in action]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location")). In the latter case, I hope you do know another way of booting Ubuntu. Here is Ubuntu un-install page just in case [http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm).

---

### Post by lha on 2008-03-09
You can't boot Linux directly from WIndows' boot loader, you'll need grub (or some other real boot loader). I recommend you to remove your sata drive, then install Ubuntu to your pata drive. After installing, set bios to boot pata drive, and add Windows to grub menu. With this method, you can remove the pata drive and still have a working Windows.

Alternatively, you might be able to add Ubuntu to Vista's boot loader. However, I'm not familiar with Vista, and I do not know how its boot loader work. (With XP, this would be simple; [BootPart]("http://www.winimage.com/bootpart.htm") can do it automatically.)

---

