---
title: "Hard disk reformat problems"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ramshaw on 2007-05-15
I am wanting to go Ubuntu as my porimary and only OS on my desktop from Windows XP. The previous XP installation was installed under RAID 0 on 2 disks. I have loaded Ubuntu from the Live CD and used GNOME Partition Manager to try and delete the partitions on the disk the disks have been reformatted a couple times and I have tried to install Ubuntu on to one of the disks. The hard drives seem no to be reformatting correctly and have the RAID controller from before interrupting the Ubuntu boot. How can I completely reformat the disks and prevent this RAID controller appearing. So Ubuntu can boot correctly? I'm new to Linux and Ubuntu so any help would be greatly appreciated. :)

---

### Post by starcraft.man on 2007-05-15
> **ramshaw said:**
> I am wanting to go Ubuntu as my porimary and only OS on my desktop from Windows XP. The previous XP installation was installed under RAID 0 on 2 disks. I have loaded Ubuntu from the Live CD and used GNOME Partition Manager to try and delete the partitions on the disk the disks have been reformatted a couple times and I have tried to install Ubuntu on to one of the disks. The hard drives seem no to be reformatting correctly and have the RAID controller from before interrupting the Ubuntu boot. How can I completely reformat the disks and prevent this RAID controller appearing. So Ubuntu can boot correctly? I'm new to Linux and Ubuntu so any help would be greatly appreciated. :)

Well, I know absolutely nothing about RAID... never really thought I wanted it. I just buy extra hard drives when I need more. The best way I can think of to format those drives and get you going is [DBAN,]("http://dban.sourceforge.net/") make sure you back up whatever you want to keep first, once you Boot and nuke, it's gone forever...

---

### Post by hartz on 2007-05-16
I suspect that you have (pseudo hardware) raid configured in your BIOS/RAID card setup on the motherboard.

If so, you should put the drives back into JBOD / standalone mode.

If this is NOT your problem, try booting form the LiveCD and from there use Gparted, the Gnome Partition Editor, to get rid of any traces of raid and/or array configs.

---

### Post by ramshaw on 2007-05-16
Ok thanks for the help everyone. The problem was the motherboard was still trying to boot as a RAID I turned this off and wiped the drives using killdisk then installed Ubuntu, worked a treat. Now I have something else to sort out, ATi drivers :(  I'll try and sort that out myself and if I need any help I'll post an other thread. 

Thanks.

---

