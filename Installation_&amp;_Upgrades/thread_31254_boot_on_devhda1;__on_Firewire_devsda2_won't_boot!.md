---
title: "/boot on /dev/hda1; / on Firewire /dev/sda2: won't boot!"
date: 2005-05-02
forum: Installation &amp; Upgrades
---

### Post by jem on 2005-05-02
I'm trying to get Linux up and running native (not remotely booted) on an HP
Compaq 5700 Thin Client (1 GHz Transmeta Crusoe processor, 256 MB RAM), supplemented by an IDE disk connected via Firewire through an Adaptec USB/1394 combo card.  Yeah, yeah; very odd.  The big plus, though, is that if I can get it to work, I'll have a very compact and virtually silent Linux workstation.

I've tried lots of distributions.  I have gotten one 2.6 kernel and system
to run on this hardware: a very laborious and error-prone Gentoo
installation.  However, I'd prefer something less complex, like Ubuntu,
which I am working on currently.

The problem is getting the installed system to finish booting.  There is a
256MB ATA Flash "virtual disk" built into the thin client, and I can get the
partitioner to "see" that as /dev/hda.  I put /boot on that and stick GRUB
into the MBR.  Swap and a nice big root partition go onto the Firewire disk.

Everything seems to install correctly.  I have tried both 2.4 and 2.6
kernels (via expert mode in Ubuntu).  Upon powering up, it finds the kernel
and initrd, but during boot, I get this:

Starting Ubuntu...
pivot_root: No such file or directory
/sbin/init: 428: cannot open /dev/console: No such file
Kernel panic - not syncing: Attempted to kill inint!

At which point, the system hangs.

Because the big HD is in an enclosure that also allows USB 2.0 connection, I tried that as well; no joy.

What to I need to do to get this puppy to boot?


Jim McCauley

---

