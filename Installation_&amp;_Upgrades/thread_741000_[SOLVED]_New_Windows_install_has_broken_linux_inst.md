---
title: "[SOLVED] New Windows install has broken linux install."
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by mayfairman on 2008-03-31
Hi, I had previously had Gutsy working fine on a dual boot with XP, I have now upgraded to Vista however and the dual boot has gone, which I expected. I have tried to recover Grub using several methods outlined on some posts here, but to no avail. 

I am almost certain that the issue is that I tinkered with the partition table when I installed Vista and merged my previous 3 XP partitions into 1 partition for Vista, So I am assuming that when I try to recover my Grub setup, it is pointing to the old, incorrect sda, hence it is hanging, I have tried recovering manually and using the grub super CD, but no joy.

Will I need to re-install Gutsy or is this recoverable, I know my way round basically but I don't have the depth of knowledge to work my way out of this one just yet. Any help to get me started would be excellent.

Many Thanks

Peter
:)

---

### Post by dannyboy79 on 2008-03-31
is there a grub error or does just windows vista appear without any grub boot menu? most likely vista overwrote your MBR (master boot record) so it's using it's own boot loader and not seeing Ubuntu at all. if that's the case, you merely need to reinstall grub onto the MBR and tell grub where your grub files are by using the root command within grub interactive shell.

---

### Post by mayfairman on 2008-03-31
Thanks Dannyboy, I have tried rcovering grub through the super CD and through the terminal and did reinstall it, it sees my old grub config and lists my gutsy install there, but when I select that one now it just hangs when it trys to init it, so Im guessing it is still looking for the old partition it was sinstalled on (sda4 or something, I cant remember) but now because I have merged sda1, 2 and 3, its getting confused I think, as well as me!! lol.

Thanks again!

---

### Post by forestpixie on 2008-03-31
Can you get to the menu list through the livecd - obviously when you boot the cd the filesystem will be that of the cd. The real menu.lst will be accessible through the partition which will be in /media.

Check that against the partitions.

---

### Post by dannyboy79 on 2008-03-31
> **mayfairman said:**
> Thanks Dannyboy, I have tried rcovering grub through the super CD and through the terminal and did reinstall it, it sees my old grub config and lists my gutsy install there, but when I select that one now it just hangs when it trys to init it, so Im guessing it is still looking for the old partition it was sinstalled on (sda4 or something, I cant remember) but now because I have merged sda1, 2 and 3, its getting confused I think, as well as me!! lol.

Thanks again!

it sounds like you just need to determine your root device and using the livecd edit your /boot/grub/menu.lst file so that it's calling out the correct locations. Once in the livecd, you may have to manually mount your linux partition to /media/ or /mnt/, then edit the menu.lst file.

---

### Post by mayfairman on 2008-03-31
Many Thanks both, Grub now re-installed and working fine after some tweaking with the partitions in the menu.lst file. Thank you very much :)

---

### Post by dannyboy79 on 2008-03-31
glad you got it sorted.

---

