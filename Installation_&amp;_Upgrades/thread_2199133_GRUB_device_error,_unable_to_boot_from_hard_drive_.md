---
title: "GRUB device error, unable to boot from hard drive or live cd"
date: 2014-01-12
forum: Installation &amp; Upgrades
---

### Post by grubfix on 2014-01-12
Hey,

I am fairly new to working with ubuntu and linux in general. I've been trying to install Ubuntu from live cd over Debian but I encountered a problem with the bootloader. My problem is similar to this:
[http://ubuntuforums.org/showthread.php?t=2179338](http://ubuntuforums.org/showthread.php?t=2179338)

Upon trying to boot from either DVD or USB (I've tried different USB slots) I get the following error:
error: no such device: <device>
grub rescue>

I read that reinstalling grub might help things so I tried it out but it ended up making matters less ideal by making debian unbootable as well. (I reinstalled grub2 from the official debian repository with apt-get).

The reason the link I gave does not address my problem specifically is because I am unable to boot from live cd or hard drive. The only command line available to me right now is the grub rescue, which I am not at all familiar with and which I get upon failed boot up.

I don't have anything of value on my hard drive and have no problem formatting everything if it proves to be the easiest way to fix the problem.

Is there any known fix to this?

---

### Post by oldfred on 2014-01-12
It may just be USB is corrupted?
And sometimes BIOS gets confused. A full cold boot may work where warm reboots do not. If laptop remove battery & hold power switch for a few seconds to drain any extra power in system.

 Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
May be better to run the git/beta version of boot script as it has some fixes.

   [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

You can try manual boot.
      
 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

#if that does not work try these with (hd0,5) and sda5 replaced with correct partition.
set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

 Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

