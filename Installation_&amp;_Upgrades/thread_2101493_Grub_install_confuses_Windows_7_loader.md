---
title: "Grub install confuses Windows 7 loader"
date: 2013-01-04
forum: Installation &amp; Upgrades
---

### Post by Skiro'n on 2013-01-04
Dear all,

My problem is solved, I post here just to keep a trace about what happened to me, and to explain why it happened that way.

The problem started on Windows 7 (I have a dual-boot with Linux) where I couldn't install Windows Update (SP1). This problem concerns only Windows (and its solution is explained [here]("http://www.sevenforums.com/windows-updates-activation/272259-solved-problem-install-sp1-bcdedit-problem.html")), but it occured because of Grub.

When I installed Windows (on my disk B), a NTFS partition was active on my other disk A, (I write disk instead of partition because the point is precisely that there were 2 disks). Then Windows installed its boot manager on disk A (first in list) rather than on disk B where the base system was located.
The installation of Grub made the choice of Windows linked to disk B, but once launched, Windows was considering the boot manager in the disk A and was offering 2 options "Windows 7" (not in Grub, but in the Windows boot sequence).

To correct that, I had to suppress the active flag from the NTFS partition in disk A, to move the folder "Boot" and the file "bootmgr" from the root of disk A to the root of B (this can only be done in Linux), update grub and finally update the boot manager in Windows to suppress the extra "Windows 7" option, as explained [here]("http://www.sevenforums.com/windows-updates-activation/272259-solved-problem-install-sp1-bcdedit-problem.html").

As it is written everywhere in Internet, when installing Windows, you should unplug any disk in your computer that is not used for the installation... what a pity. I think it's better to understand that Windows is installing its boot manager on the first active partition, whether or not it holds the base system.

---

