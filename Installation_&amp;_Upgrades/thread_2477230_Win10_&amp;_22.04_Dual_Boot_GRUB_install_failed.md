---
title: "Win10 &amp; 22.04 Dual Boot GRUB install failed"
date: 2022-07-18
forum: Installation &amp; Upgrades
---

### Post by libertyspike138 on 2022-07-18
I have a Win10 system in EFI mode so the partition map is EFI / System Reserved / Windows on a 1TB. I used GParted to resize Windows to 750GB and created the Ext4 partition with the remaining space to install 22.04. The installer gets to the end and then says GRUB install failed. I have been using Ubuntu since version 6 and have other systems that boot multiple systems such as 20.04, Win10, & MacOS. I initially tried installing GRUB to EFI partition sda1 like in other systems and then tried again using the default of just sda to see if anything changes. I can see GRUB files in the EFI folder but something obviously went wrong because it still only boots Windows. I'm not sure what has changed in 22.04 or what I need to do to get it working. I would appreciate any insight into this, thanks!

---

### Post by libertyspike138 on 2022-07-19
Update: I have always created my partition maps before installing anything so for example if I want Windows to show a 750 GB disk I previously planned for it by selecting 768006 MiB in GParted. Because of this and multiple operating systems I always choose something else on the installer because choosing alongside Windows the last time I had ever used it, it didn't really give you much control and would just estimate and split up a current partition. Anyway I tried the installer again after deleting the Ext4 partition and leaving unused space and this time selected alongside Windows instead of something else and it installed OK on the free space without changing any other partitions. I don't think this is a viable option with many partitions and operating systems. I'm not sure what was different, did it install GRUB on sda4 Ext4 / instead of in sda1 EFI or what? I would like to know what was different so that I may be able to manually execute it in more complex scenarios with more partitions / disks and operating systems.

Now I'm on my next problem which is the fact that I cannot figure out how to set a custom resolution in Wayland as the xrandr stuff I'm used to is not working and under audio I only see digital optical out and no analog.

At this point I may just stick with 20.04 until the bugs are worked out...

---

### Post by oldfred on 2022-07-19
Did you install in UEFI boot mode?

Always better to use Windows to shrink NTFS partitions. Sometimes after use with gparted, users complain it broke Windows. Often issue was originally Windows had issues and using Windows tools would have resolved issue or told user there was an issue. And NTFS always needs a chkdsk after resize to update PBR or boot sector with correct size.

---

### Post by libertyspike138 on 2022-07-19
Yes they are both installed in UEFI mode. I have always used GParted to resize partitions and then just run a disk check after booting into Windows so I can set a partition to the desired size in explorer such as 100GB instead of explorer showing 99.7 GB or something and it has always worked fine. I also resolved the video & sound issues so I will be keeping 22.04 on this machine. But as I previously stated, I would like to know why GRUB install fails when I choose something else instead of alongside Windows as seen on the starting point of this video. [https://youtu.be/GXxTxBPKecQ?t=540](https://youtu.be/GXxTxBPKecQ?t=540)
The machine I'm on atm and previous other installs, I have always selected something else and told it to use the Ext4 partition as / and to use the EFI partition to install GRUB so what was different in choosing alongside Windows?

---

### Post by oldfred on 2022-07-19
If Windows has fast startup on, that can set hibernation flag on all Windows partitions.
Some new UEFI have settings to lock drive from installing. Review UEFI settings. Often have to check manual for details. 
Did installer see your drive as first drive?

Most do not have issues.
What brand/model system?

---

