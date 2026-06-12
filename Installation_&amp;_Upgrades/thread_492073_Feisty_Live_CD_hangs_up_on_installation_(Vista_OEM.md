---
title: "Feisty Live CD hangs up on installation (Vista OEM)"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by Amadomon on 2007-07-04
Hi,

I am trying to dual-boot my latest machine, which came with Vista Home Ultimate as the OEM OS.  I have followed all the various instructions including on the wiki:  I have successfully shrunk the volume of my hard drive, using Vista's native partition tool.  I now see 53.1 GB of unallocated space on my hard drive.  However, when I try to install Feisty using the Live CD I downloaded and burned, things start off normally at first--I select "start or install Ubuntu", and the kernel loads--but then the install quickly hangs up with the following error message:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) built-in shell (ash)
/bin/sh: can't access tty; job control turned off
(initramfs)_

I have configured several XP/Ubuntu machines in the past, and all docs say that Ubuntu will simply install in the unallocated space on my hard drive, but I can't get there.  I realize that after the installation I may have to chainload--I am prepared for that--but I can't complete the installation.  Please help-- I want Ubuntu back!  FWIW, this is a Core 2 Duo machine--actually a Sony Vaio, and the machine was shipped with a "hidden" partition that is an archive of the OEM installed apps and OS.

---

### Post by Amadomon on 2007-07-05
Well, FWIW, I did get my machine to dual-boot.  In a nutshell, for future installers with a native copy of Vista, here is what I recommend:

[LIST=1]
[*]Do let Vista shrink the volume.  Leave the new partition unallocated.
[*]Use the alternate install CD.  I never got the regular install disk to work, and others have had problems too.
[*]Make sure to install Ubuntu into the largest unused partition.  In all my previous installs and including this one, I have never (seriously) screwed up my Windoze OS, so although Backups ARE recommended, I have never done so...{blush}
GRUB seems to work fine loading Vista (and of course, Ubuntu).  I did install Easy BCD, and that could work too, but since GRUB is doing the job, I don't want one more step in booting up.
[/LIST]

Now if I could only get Ubuntu to accept screen resolutions higher than 800 x 600...any ideas, people?  I have certainly run higher resolutions before...8 x 6 is the only option available on my pulldown menu under System>Preferences>Screen Resolution...also there is the usual annoyance regarding lack of support for my integrated wireless card...as of right now, Ubuntu doesn't even see it...

---

