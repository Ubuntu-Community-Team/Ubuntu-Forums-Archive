---
title: "Installing ubuntu on HP Compaq 615; using Win XP bootmanager to choose OS"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by anonymissimus on 2010-04-09
Hi!

First, I need to note that almost always when doing the disk integrity check when installing any of the k/x/ubuntu systems there are 1 or more errors found in files, although md5sum checks were okay! (also on my desktop PC) This did never happen with any of the Debian install images (which I wrote to CD in the same way).
Strange to say, I also got different results with the exact same hardware. Sometimes the ubuntu live CD boots on the mentioned notebook, but mostly it does not. (black screen after the initial menu). Using acpi=off and radeon.modeset=0 options it boots mostly (not quite sure, could also be always, then.)
Debian testing installation was working with the above mentioned options, although it seemed to have severe problems with the soundcard. (driver issues ?!)
I'd prefer ubuntu due to its user-friendlyness.

Okay, now to the actual question. To boot into Debian, I'm installing Grub to the Debian root partition. After the installation, I'm using the dd command (e.g. from the Debian install CD's rescue mode) to write the Debian root partition's boot sector into a file, copy that file onto a partition noticed by Win XP and manually reference the file in Win XP's boot.ini on the hard drive's first partition. From Win XP's boot loader menu I get to Grub's menu and can boot into Debian, then. This works with Debian stable, testing and an old Knoppix version, but not with ubuntu. What I DO NOT want to do is installing Grub to the MBR. There's the commonly known "can't boot into Linux after windows reinstall" problem which I want to work around this way, and I do not or not yet want to make windows dependant on Linux.
Is there a way to install ubuntu in a way so that this works ?

thanks for reading
cheers

EDIT
It seems that using Grub legacy enables the method to boot described above. Installing Debian with Grub 2 disables it for Debian too, but it works with Grub legacy, and it even lets me boot into ubuntu after a reinstalling Debian...
So it comes down to how do I install ubuntu with Grub legacy.

---

