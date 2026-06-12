---
title: "Problem installing ubuntu Gutsy 7.10 from live CD"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by jolato on 2008-04-11
**Short story: **Install Gutsy 7.10 from liveCD worked initially, but after 1-2 days, I can only boot into Busybox. Re-installed again but same story.  Hope someone can help and that this is the correct group to post this problem ? :(. See details of my system below.

I have to admit I physically disconnected disk 1 before starting, because I do not trust Ubuntu grub install not to touch my disk 1 where my main XP is installed ! Disk 2 contains also second XP. Both XP boot fine.

So I installed from live CD, Gutsy 7.10. The Ubuntu partitioning tool refused to format my hdb5 to FAT32 for some reason, so I skipped. I ended up with grub booting generic kernel 2.6.22-14. Did an update of all packages, changed fstab not to fsck some filesystems, rebooted and all is ok. Changed video driver to NVidia using tool (don't know when exactly I did that). Suddenly next day boot into busybox. Can't do much. Typing reboot boots again into BB. :confused:

Searching on the net suggests that I upgrade my generic kernel but to what version ? I doubt this would help much. I'd rather customise my kernel for Athlon CPU, but don't know how, if at all that would help.

Rgds,
JO

------------------------------------------------------------------------------------
System is AMD AThlon 2100+ with 1,5 Gb memory and ASUS mobo, nVidia 6800 XT Geforce,  2 IDE hard disks hda and hdb, both have XP installed already on first partition and work fine. Partitioning was done with Acronis Disk Director. Gparted during iinstalling Ubuntu.

---

### Post by em3raldxiii on 2008-04-11
Very interesting problem.  Okay, so you have a couple of things going on here.  First off, pulling your HD1 before installing Ubuntu, then re-plugging it after is definitely not the happiest way to go about installing ubuntu.  If GRUB installs itself on your HD1 boot sector, it's not going to affect your Windows install, other than changing the boot loader.  However, I doubt that this is affecting your startup.

Formatting your hdb5 to FAT32.  Is this a Logical partition within another partition?  If so, that might be your issue.  If you rearrange the partitions a wee bit so that your FAT32 is on it's own primary partition, (you'd probably have to put one of your other EXT3s on a logical), you might have more success ... this is only a bit of a guess, but, might be worth a try.

Finally, it appears, according to your timeline, that your video driver is the culprit.  Which tool did you use to install it?  Was it Envy, or was it something evil like automatix or something?  You could try editing your xorg.conf file to swing your driver back to the nv one Ubuntu is packaged with.

I doubt changing your kernel is going to drastically affect your overall experience, particularly on an athlon 2100+ which would be perfectly happy with the generic kernel (afaik).

Keep us apprised of how stuff goes ... I'd like to see what you finally do to fix the issue :D

---

### Post by jolato on 2008-04-11
Thanks, yes I agree about grub, but I don't trust Windows!

I think my partitions were ok, hdb1 is XP, hdb2 ext3, hdb6 swap and the rest I'll have to check ...

I also think it has to do with the Nvidia driver. I installed it first from some icon that popped form the screen after booting for the first time. Second time from the menu System-admin-some tool I found over there, didn't check the name. 

So I'll edit xorg.conf using live CD and mounting the root fs. **Any idea where this file lives ? And what lines to change ?**

---

### Post by Sef on 2008-04-11
> I think my partitions were ok, hdb1 is XP, hdb2 ext3, hdb6 swap and the rest I'll have to check ...

To check your partitions, use the live cd then Applications > Accessories > Terminal

then type the following command:

```
sudo fdisk -l
``` Small L

---

