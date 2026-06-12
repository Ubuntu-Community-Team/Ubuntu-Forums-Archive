---
title: "Moving home without dedicating a whole partition"
date: 2007-01-16
forum: Installation &amp; Upgrades
---

### Post by coady on 2007-01-16
I have a number of related questions:

(1) I have a multiboot system with WinXP, Ubuntu Edgy (6.10), Debian Etch, and one another distro. At present I have a separate "/home" partition for some of these, but I have read in this forum about a more elegant solution which I would like to implement. I want to mount a separate partition (formatted as ext3) to where I can move the contents of the "/home" directory, and rename the "/home" directory for each of the linux distros. This would result in a partition with, for e.g.: "/homeUbuntu", "/homeDebian", "/homeLinuxOS1", "/homeLinuxOS2", After this the idea would be to remove the "/home" directory from each of the OS's and then use a 'symlink' ("ln -s"), naming it "home", to replace the "/home" on each system "/", and which would point to the "/user_name" folder with all the config files on the separate ("home data") partition.

Has anyone tried this? Does anyone have any advice?

It seems to me to be a nice solution to having many partitions (i.e. dedicated to a "/home" partition) as well as allowing for easy adjustment of partitions (adding, removing, changing) as well as installing upgrades and/or new distro's (given that the Ubuntu cycles is 6 months, for e.g.). Ubuntu is my main OS, but my experience has been with other Debian distro's and like to keep them running, or try new releases from time to time, without having to lose all those config files!

(2) Where would be the best place to mount such a partition (as described above)?
E.g.:
"/data" (i.e. a custom mount point in the file system), OR
"/mnt/data", OR
"/media/data"

Does it matter?

(3) Related to messing around with reinstalling Ubuntu, how can I reinstall grub efficiently? I know of two ways: (i) use the LiveCD installation, (ii) boot from LiveCD and use the console to run: "grub" > "root" > "setup".

I cannot do either of these with the Ubuntu LiveCD, however. The installation will not allow to reinstall grub without a full install, and the LiveCD does not mount any disk partitions which means that issuing "grub" at the console does not work.

I want to be able to restore a full image backup of the Ubuntu "/" partition (or other OS) and then reinstall grub so that it automatically lists the other bootable systems. Should that be possible, or do I have to edit the "menu.lst" anyway? [Note, I have grub installed to the MBR with on (hd0) with WinXP on (hd0,0) and Ubuntu on (hd0,7)]

Sorry for the long post, but the issues are related. Thanks to anyone who can give me any ideas... :)

coady

---

