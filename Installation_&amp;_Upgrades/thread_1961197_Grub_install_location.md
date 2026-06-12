---
title: "Grub install location"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by briansvgs on 2012-04-18
Guys,

I recently installed Ubuntu 12.04 as a dual boot on my laptop. I am using it with the chameleon bootloader picking up grub when Ubuntu is selected. To get this to work I had to install grub to the local ubuntu partition after I installed the operating system and then reinstall chameleon. Unfortunately, the system updates are reinstalling grub over my mbr and getting rid of chameleon. I think that this is caused by updates to grub after kernel upgrades. Anyways, is it possible to change the location that grub updates itself at? I would like to change it from the mbr to my local partition (/dev/sda4).

Thanks,
Brian

---

### Post by lisanels47 on 2012-04-18
I'm running the same thing, but why not just use grub as your bootloader?  Why chameleon?

---

### Post by briansvgs on 2012-04-18
I have a couple of reasons for running chameleon. First of all, I have another operating system that I am trying out for which it was suggested that I use chameleon. The second reason that I have is that chameleon actually seems to automatically adapt to new hardware/operating systems. For instance if I plug in a bootable thumb drive it will automatically detect it and add it to the menu.

---

### Post by oldfred on 2012-04-18
Grub remembers where to reinstall on major updates. So if you installed to the MBR the first time, some grub updates may reinstall it.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

Normally you do not select a partition. You may want to or deselect everything so it does not install. May want to let it update occasionally or it may have issues??

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by bpedman on 2012-06-06
> **oldfred said:**
> 
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Thank you! This worked great for me, though I actually did want to choose partitions and not the whole disk (mbr).

---

