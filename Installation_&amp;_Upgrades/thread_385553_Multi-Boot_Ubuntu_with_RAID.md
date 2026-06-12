---
title: "Multi-Boot Ubuntu with RAID"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by DJMatty on 2007-03-15
Hello everyone

I am just starting out in the linux world and have been trying to install ubuntu as a 3rd O/S on my machine, but my setup is a little unusual and I am having trouble getting GRUB to install and give me any options.

My machine is:

ASUS Striker Extreme (nForce680i)
nVidia 8800 GTX
2GB RAM
2x150GB SATA RAID drives
1x300GB SATA drive

I have already got win XP installed, and vista, on 2 partitions in the raided drives, the 300GB drive is just for data.

I have got as far as partitioning 3 more partitions on the raided drive for ubuntu, and have been following instructions to get them installed, along with setting options for forcedeth to get the onboard network cards to work, and also used dmraid to get the raid controllers going.

The boot partition for my windows installs is the 300gb drive (this appears as a * in the boot column in fdisk if I run 'fdisk -lu /dev/sda', if I fdisk the raid drives none of the partitions are bootable.

I decided to use the feisty distro as I had been reading about the nvidia chipset and gfx card problems, and have been following the instructions here (Except for the bits about fetching dmraid from somewhere, i just used the one that was available via apt-get): 

[http://www.howtoforge.com/ubuntu_dapper_raid_system](http://www.howtoforge.com/ubuntu_dapper_raid_system)

The grub setup seemed to work ok, however on reboot it just booted into the windows boot manager, not grub. I am guessing that this is because it needs to do something to the other drive... I have also read that my vista install may not work if I do this as it relies on stuff on the boot partition, is this the case? (It's not a big deal anyway, if it goes wrong I can always re-install, I also read somewhere that changing the active partition before installing vista can make a difference)

One other thing that didn't work in these steps, was the 'apt-get install ubuntu-base' command. How do I find out where the ubuntu-base package is, as it says it can't find it...?

Can someone help point me in the right direction for getting GRUB going with my drive/os setup?

Thanks!

Matt

---

### Post by Felix-the-Cat on 2008-03-15
try booting into the "rescue and broken system" go through all the menus until you get to one that says something about mounting a recovery partition and then press "esc" then go down to execute a shell and mount the ubuntu partition. chroot into the ubuntu partition and then run grub-install /dev/hdx(sdx) for each of the drives in the array. that might work unless you have a more complicated raid arrangement

---

