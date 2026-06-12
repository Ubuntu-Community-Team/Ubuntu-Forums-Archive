---
title: "best partitioning setup??? (RAID/LVM/multiboot/SATA...)"
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by kerinin on 2005-11-30
i'm in the process of setting up a new system, and i'm a little overwhelmed trying to work out how to set up the partitions.  here's the relevant hardware:

250Gb SATA hd
Motherboard with on-board RAID 0,1,JBOD
amd64 processor

i would like to accomplish the following:
1) seperate my base folders (boot, var, home) from root so i can install other distros and keep some of my settings
2) dual-boot windows for gaming
3) add additional hard-drives later without spending days moving data back and fourth

what's the best solution here?  should i use my motherboard's RAID to create a JBOD volume or does this incur substantial performance losses?  should i use software RAID or will this cause problems with the dual-boot.  does LVM work with windows?

thanks for any suggestions...

---

### Post by luopio on 2005-12-15
[QUOTE=kerinin]
250Gb SATA hd
Motherboard with on-board RAID 0,1,JBOD
amd64 processor

i would like to accomplish the following:
1) seperate my base folders (boot, var, home) from root so i can install other distros and keep some of my settings[/QUOTE]
Well I'd suggest putting:
 /boot on a separate partition (32 - 256 MB in size)
 /home on a separate partition (depending on how much you want.. probably 2BG->100GB?)
/swap - you'll only need one for all the partitions and modern kernels don't actually use it that much, so I'd create one with the size of ~700MB
/ naturally on it's own partition (size would be something like 5-15GB). 

I'm not sure what you gain by separating /var or /etc, since each distro uses these in it's own way(?). I would probably keep them in /.

[QUOTE=kerinin]2) dual-boot windows for gaming[/QUOTE]
Ok. Just make sure you don't delete your win-partitions and that you configure your bootloader to start windows.
[QUOTE=kerinin]3) add additional hard-drives later without spending days moving data back and fourth[/QUOTE]
This is where I would recommend LVM to be used in partitioning. With LVM you can easily add new harddrives, change partition sizes (add new space, take space from /home to /, etc). I actually haven't used it myself yet, but I'm currently in the process of learning and I'm installing it right now on an old computer. For info I'd suggest seeing here: [http://www.tldp.org/HOWTO/LVM-HOWTO](http://www.tldp.org/HOWTO/LVM-HOWTO)

[QUOTE=kerinin]what's the best solution here?  should i use my motherboard's RAID to create a JBOD volume or does this incur substantial performance losses?  should i use software RAID or will this cause problems with the dual-boot.  does LVM work with windows?

thanks for any suggestions...[/QUOTE]

I have no idea wheter windows can read LVM... but then again windows won't read ReiserFS, or any other linux-fs. If you mean that is it possible to use LVM for linux and still dual boot, then I think that is possible. You can use (and have to use) "normal, old-school" partitions for /boot and possibly / (depending on the distro) and the windows partitions aren't touched by the LVM setup. LVM lives in the space you give it (and LVM partitions live inside that LVM space).

---

