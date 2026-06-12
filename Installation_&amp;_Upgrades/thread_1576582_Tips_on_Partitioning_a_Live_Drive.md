---
title: "Tips on Partitioning a Live Drive"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by albienoche on 2010-09-17
*
[quote=quadproc][quote=albienoche]any advice on partitioning a live drive? I hate to lose any data.[/quote]
i understand your feeling as i feel the same way. Here are the things that i do when i am going to modify partitions:
 
Get a printout on paper of where things are now. The boot info script is a great tool for this. If i have to do any troubleshooting or repair or recovery, this information might save me a lot of trouble.
 
Make sure that my system is backed up to at least the most recent place that i can live with. This usually means do a backup right then, unless i am wanting to back out of some updates. Make sure that the backup succeeded.
 
Boot from a copy of the live cd, either on cdrom or on a usb stick, with the same ubuntu version that i normally run. The usb stick runs faster so i usually prefer that. Use gparted to modify the partitioning. When i am satisfied with the new disk arrangement then i quit gparted. If i changed anything that affects booting then i run grub-update.
 
At this point, reboot. This is always a tense time.
 
A related thought: If i am going to change kernel versions then i uninstall fglrx, the proprietary ati graphics driver for my graphics cards, before i boot from the live cd. I will eventually reinstall the driver after the new system is up and running, but leaving the driver installed during a kernel change can cause problems ranging from "low graphics mode" to a dead, black screen.
 
One other comment: If you lose system power during some parts of this process, you may end up with a real mess on your disk. The fsck program can sometimes fix these messes, and sometimes it can partially fix these messes, but you won't really know until you are faced with the situation. Therefore, i have a ups which powers my computer, monitor, and printer and which can keep everything running for about 20 minutes. This improves my chances but is still not a guarantee because some partitioning moves can take a very long time (> 20 minutes), depending on how big the partition is and on how fast my disk and its interface is. I have never had to try to abort a partition move so i haven't experienced that problem. I guess that you could say that i have been lucky, but i would probably say "prudent" because i don't try to do risky operations if the weather may cause power problems.
 
I hope that this helps.
 
Quadproc[/quote]

---

