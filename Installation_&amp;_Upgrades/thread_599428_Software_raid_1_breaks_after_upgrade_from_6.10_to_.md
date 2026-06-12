---
title: "Software raid 1 breaks after upgrade from 6.10 to 7.04 - will 7.04-7.10 do the same?"
date: 2007-11-01
forum: Installation &amp; Upgrades
---

### Post by ryanthemadone on 2007-11-01
Hello,

I call upon the wisdom of this board.  I used a 6.10 alternate CD to install Ubuntu on a software raid 1 array (not fake raid).  This worked fine, although curiously I noticed didn't work if I tried to make a raid 0 array (don't ask why I even tried).  I noticed LILO was installed instead of Grub, which I put down to Grub being incapable of being able to boot off of a software raid device - I might be wrong, maybe someone can enlighten me?

When it came to the appropriate time to upgrade from 6.10 to 7.04 the upgrade installed successfully, however when I rebooted, the system wouldn't boot, I don't remember the exact error, but LILO I think was in some way broken, I googled for a solution and searched these boards, but had no success.

To solve the problem quickly I used a 7.04 alternate CD to reinstall the system - probably not the best choice, but I was working to a pretty serious time restraint (house mates not able to access Facebook type crisis).

I'm now at a point where I'd like to upgrade from 7.04 to 7.10 and I'm seriously worried I'm going to get the same problem.  Is there anyone on this thar board who might be able to advise on whether I'll have the same problem or not?  Is there something I can do to prevent it happening?  Is there a tried and tested way to fix it if it does happen?

All guidance would be much appreciated,

Ryan.

---

### Post by digitalbenji on 2007-11-01
My experience with software RAID is that no installer ever properly installs the bootloaders, at least not on RAID 1.  

Download the Super Grub Disk, and after you install the OS, go back and (assuming this is raid 1) install a bootloader onto each physical disc in the array.

---

### Post by ryanthemadone on 2007-11-01
Hi DB,

This sounds cool, I've never heard of this Super Grub Disk - what is it and how will I use it to set up a bootloader on each disk?  I'm not entirely sure I fully understand how the software raid on my system works.  I know it uses two disks sda and sdb, and that it gives me a raid device md0.  Do I have to pretty savvy to make it install or will be all neat and nice and auto-detect my configuration?

Thanks dude,

Ryan.

---

### Post by digitalbenji on 2007-11-09
Hi,
  Sorry I didn't get back to you sooner, I need to track my threads better.  When you boot a computer is first reads something called a bootloader off of the hard disks, and these are usually found in the first sector (0,0) of a hard disk, known as the master boot record (MBR).  When you install a RAID 1 software configuration it takes two physical devices (/dev/sda and /dev/sdb say) and combines them into a single RAID device called /dev/md0 .  The thing is, the computer can't boot off this new device because its a "virtual" device.  So the bootloader still needs to be installed manually, but, since this is a mirrored setup, we should install the bootloader onto both /dev/sda and /dev/sdb.  

Super Grub Disk is a bootable CD image that does just this mostly automatically, with lots of easy prompts to follow.  You can download it and find info here: 
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Just download the .iso, burn it to a CD, boot, and use the help messages and follow the prompts for Linux and Grub.  Grub is the Grand Unified Boot Loader.  Use the Super Grub disk to install Grub on both your hard drives, and I'm positive your system will start.

Thanks,

---

