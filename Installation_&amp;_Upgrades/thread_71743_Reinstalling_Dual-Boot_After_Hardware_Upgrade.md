---
title: "Reinstalling Dual-Boot After Hardware Upgrade"
date: 2005-10-04
forum: Installation &amp; Upgrades
---

### Post by ScoobyDan on 2005-10-04
Hi All,

I currently have a dual-boot WinXP/Ubuntu system, with 4 partitions - WinXp (NTFS), "/", "/home", and "swap".

I will be doing a major hardware upgrade in the next week or two (new motherboard/processor/sound/graphics - basically a new PC, just using the same HDD). Given previous (Windows) experience of hardware upgrades, I will need to re-install WinXP, and probably Ubuntu.

Now my questions:

1) Is it safe to re-install WinXP to the NTFS partition, or will it try to wipe the whole drive?

2) When I re-install Ubuntu, is it easy to tell the Ubuntu installer to leave my "home" partition alone (assuming the WinXP installer in step 1 hasn't borked my whole drive)

3) I am currently using Hoary. Would it be worthwhile waiting for Breezy before doing this upgrade, or installing the latest preview now? Or should I just stick with Hoary, then load Breezy when it comes out?

Many thanks for the help. I have only been using Ubunt (and Linux in general) for about a month, so I still have losts of questions!

Daniel

---

### Post by SilentCacophony on 2005-10-04
Hello. 

1) Re-installing Windows XP should be fine, as long as you're careful. See [this]("http://www.winsupersite.com/showcase/windowsxp_sg_clean.asp") site for a look at how the install process works.

2) When you get to the *Partition disks* part, you'd want to choose the *Manually edit partitions* option, and select the root partition to be mounted as /, choose what filesytem to use, and optionally format it. As for the /home partition, make sure that is set up for the same filesytem type that it was, tell the partitioner to mount it as /home, and make sure the option to format it is not set. Generally, the installer will recognise and choose the existing swap partition automatically.

3) I'm using the Breezy Preview release, and it has a few bugs on my setup, though nothing serious. Generally, I've seen that waiting for the official release would probably be less potentially problematic.

---

