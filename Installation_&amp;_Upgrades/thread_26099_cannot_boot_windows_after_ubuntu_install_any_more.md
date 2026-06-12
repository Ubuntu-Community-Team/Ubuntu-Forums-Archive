---
title: "cannot boot windows after ubuntu install any more"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by martinko on 2005-04-11
After installing Ubuntu I cannot boot a previously existing windows install any more. Installed Grub into MBR, and Ubuntu into 3rd partition of HDD (Partition 1+2 are Windows). Now when I try to boot Windows I get UNMOUNTABLE_BOOT_VOLUME. Please help.

---

### Post by taygan on 2005-04-11
I assume you have a /boot/grub/menu.lst that has a windows entry similar to this one:

```

title         Windows XP
root          (hd0,0)
makeactive
chainloader   +1
savedefault
boot

```

see if the BIOS has changed the disk geometry so grub can't see the windows partitions.  see this desktoplinux thread:

[http://www.desktoplinux.com/cgi-bin/board/UltraBoard.pl?Action=ShowPost&Board=migration&Post=365&Idle=0&Sort=0&Order=Descend&Page=1&Session=](http://www.desktoplinux.com/cgi-bin/board/UltraBoard.pl?Action=ShowPost&Board=migration&Post=365&Idle=0&Sort=0&Order=Descend&Page=1&Session=)

here's what microsoft has to say about it:

[http://support.microsoft.com/?kbid=297185](http://support.microsoft.com/?kbid=297185)

and some folks on fedora have some opinions:

[http://lwn.net/Articles/86835/](http://lwn.net/Articles/86835/)

Try LILO instead of GRUB for a workaround?

---

### Post by numb3r5ev3n on 2007-09-13
I am having a similar problem...I had Ubuntu 7.04 dual-booting with Windows Server 2003 Standard Edition on a 40GB secondary drive (Ubuntu was running on the 80GB Primary) and aside from a few errors now and then that made me think that perhaps the Windows installation was starting to get corrupted (it had weird conflicts where it occassionally wouldn't recognize my ipod, only to be fine again after a reboot) it was doing ok. Then I installed Kubuntu Fiesty  in order to try it out, and I suddenly couldn't boot to Windows anymore. 

I reinstalled Ubuntu last night, and though I can see and access the files on the Windows partition (and backed everything up!) I still can't boot to Windows. It's there in the grub list, but when I boot to it, it just hangs on a blank, black screen.

I'm wondering if this is something I can fix with Knoppix, or if I should just reformat over the Windows partition, use it as backup space, and see if I can get away with just using Wine?

---

