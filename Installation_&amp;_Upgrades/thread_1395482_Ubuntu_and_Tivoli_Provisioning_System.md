---
title: "Ubuntu and Tivoli Provisioning System"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by m.milway on 2010-01-31
I am having some issues deploying Linux systems via Tivoli Provisioning system for Operating System Deployment. Indeed, I believe this applies to most flavours of Linux running GRUB or GRUB2, not just Ubuntu.

I am building dual boot Window XP/Ubuntu 9.10 systems on Dell Optiplex 780s with the disks running in legacy mode.

It appears that Tivoli is overwriting part of the MBR whenever its toolkit is invoked. This is breaking GRUB You don't even have to take any specific action for this to happen, merely starting the toolkit is enough. I have used the dd command to compare the MBR at different times.


Two questions:

1) When Ubuntu 9.10 is installed it automatically loads GRUB2 onto the MBR. Is there a way of installing it on the root partition instead and then making that partition the active partition?

2) How do I restore the original MBR?

If need be I could then add an option to the Windows boot loader for Linux.

Regards,
Michael Milway
University of Wollongong

---

