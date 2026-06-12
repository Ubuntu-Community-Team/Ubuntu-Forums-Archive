---
title: "Suppress installation of bootloader during install"
date: 2007-03-02
forum: Installation &amp; Upgrades
---

### Post by Lilley_peter on 2007-03-02
Hi,

I've installed Windows on my PC and now want to install Ubuntu 6.10.  The complication for me is that I already have a bootloader installed that I want to keep using (bootITNG).

The instructions (from the bootITNG people) for installing Ubuntu over this software are to use the Ubuntu "Expert" install mode and suppress the installation of Grub as it will wipe the MBR.  However, the instructions relate to an earlier version of Ubuntu and I don't think they are applicable any more.

My question is, is there a way to install Ubuntu 6.10 and suppressing the installation of Grub.  I should preface this by saying that I'm not a Linux expert, so any dumbed down advice would be appreciated.

Thanks in advance.

---

### Post by yabbadabbadont on 2007-03-02
I don't know about the desktop install cd, but the alternate install cd for edgy has expert mode available.  I believe you just hit F6, then hit it again (for some weird reason) and choose the expert option.  Then you can either skip the grub installation or choose to install it to the root partition instead of the mbr.  You will probably want to install grub to the root partition.  Then you can launch grub from your other bootloader.

---

### Post by Lilley_peter on 2007-03-02
Thanks Yabba...,

I've just read up on the Alternate install and that looks like the one, am downloading now....

---

