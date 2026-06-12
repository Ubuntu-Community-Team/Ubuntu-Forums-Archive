---
title: "Trying to install on a Dell"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by chuyo on 2007-01-31
I just bought a Dell Inspiron 1501 with an AMD Mobile Sempron processor. I would like to install Ubuntu on it but the installer doesn't seem to be working. When I get to step 6 of the install I only get the option to manually edit partition table and nothing else. If I click on the forward button everything in the next step is grayed out. I am a newbie to Linux and ideally I would love to be able to dual boot the machine. The computer came with XP pre-installed but I am not a huge fan of windows and yet I am a bit hesitant to completely throw it out. Any advice would be greatly appreciated.

---

### Post by dcstar on 2007-02-01
> **chuyo said:**
> I just bought a Dell Inspiron 1501 with an AMD Mobile Sempron processor. I would like to install Ubuntu on it but the installer doesn't seem to be working. When I get to step 6 of the install I only get the option to manually edit partition table and nothing else. If I click on the forward button everything in the next step is grayed out. I am a newbie to Linux and ideally I would love to be able to dual boot the machine. The computer came with XP pre-installed but I am not a huge fan of windows and yet I am a bit hesitant to completely throw it out. Any advice would be greatly appreciated.

Possibly Ubuntu is not detecting your hard drive at all, do a forum search for your hardware and see if someone else has fixed any similar issues.

---

### Post by aberry5555 on 2007-02-01
This is probably because you have only one partition on your hard-drive, so you have to reformat or manually partition it, and I don't think there's really any easy way around that. If your dell has a backup partition or a reinstallation CD then you could reinstall after installing ubuntu (though you'd need to read up on dual booting properly) what might be a problem, too, is that, if your hard-drive is sata, it might not have the drivers. If you do end up repartitioning on your current drive, however, I would advise you to make use of extended partitions rather than master partitions as they cause less trouble :) .

---

### Post by Ronirvol on 2007-02-06
I too have a Dell 1501 with AMD sempron.  I tried to install 6.06 and had problems, but was successful with installing 6.10 and leaving my XP Windows intact.  (I am a novice, and did this only once, so my recall may be vague) During the load of the 6.10 live CD, I hit F6 and typed pci=nomsi per the blog instruction.  At the partition step of the install, there was no automatic option, so I exited the install.  Still at the Ubuntu desktop running the live CD, I loaded the gparted partioning tool in order to create the partitions prior to retrying the install.  The tool has a graphical display which highlights the partition being worked on with a colored rectangle.  First I resized the large middle partition to create about 10G of freespace.  I clicked on the freespace and converted it to an extended partition.  Inside the extended partition I created about 9.5G of ext3, leaving 500M of freespace which I then converted to swap. With all these setup steps complete I hit "apply" ? or something to do the actual partitioning.  I restarted the install process and selected the "manual" option of partitioning.  I was able to skip a step, having previously done the partitioning, and move to a step where the installer automatically selected the ext3 and swap partitions.  After completing the install, I checked the menu.lst file and saw that the pci=nomsi was already present and didn't need to be added.  I hope this helps.

---

