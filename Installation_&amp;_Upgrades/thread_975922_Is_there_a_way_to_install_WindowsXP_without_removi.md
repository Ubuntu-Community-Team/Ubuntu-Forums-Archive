---
title: "Is there a way to install WindowsXP without removing Linux"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Bochenekgsx on 2008-11-08
My main reason for this is to play world of warcraft. I have been playing in Ubuntu under wine for about 6 months now. I love it. Problem is, with the release of patch 3.0 for WoW, it is virtually unplayable with the severe framerate drop. A friend of mine has a computer with windows and ubuntu set up to dual boot, but windows was there first, and the gui installer for ubuntu made it easy to setup the dual-loader.

Is there a way to do the reverse? I have a lot of files on ubuntu that will take a long time to back up. I want to partition part of my hard drive for a fresh windows xp install?

---

### Post by anystupidname on 2008-11-08
There are multiple ways to do it, but just installing XP won't wipe your Ubuntu install unless tell the XP installer to reformat. Your master boot record will be overwritten and the NTLDR implemented but you can re-install GRUB. Before anything else, you'll probably want to repartition your drive in preparation. You can use this:

[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=240127)

(choose the EXE version obviously, and then reboot to it)
Create a 15+GB parition for XP

Then install XP and use this:
[http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261880](http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=261880)
(exe version again)

or boot from an Ubuntu liveCD and:
[http://ubuntuforums.org/showthread.php?t=965672&highlight=repair+grub+xp+install](http://ubuntuforums.org/showthread.php?t=965672&highlight=repair+grub+xp+install)

P.S. If you'd rather just use the NTLDR:
[http://ubuntuforums.org/showthread.php?t=208951](http://ubuntuforums.org/showthread.php?t=208951)

---

### Post by LinuxRocks713 on 2009-01-23
Or if you have enough disc space, just install VirtualBox **or** VMWare and run WindowsXP there. DirectX is supported.

---

