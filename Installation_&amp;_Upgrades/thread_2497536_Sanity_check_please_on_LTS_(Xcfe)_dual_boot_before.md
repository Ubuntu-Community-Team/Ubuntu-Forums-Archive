---
title: "Sanity check please on LTS (Xcfe) dual boot before deleting previous OS (Fedora 40)"
date: 2024-05-09
forum: Installation &amp; Upgrades
---

### Post by rupertreynolds on 2024-05-09
I've never done this before. Please be kind :-)

As far as I can see, I need to resize the Btrfs partition to make room, add another partition for /boot after the 1.1GB EXT4, boot LTS from USB and install into the new free partition. At that stage, LTS should be booting by default and I should be able to use update-grub to be able to choose Fedora until I delete it. 

But that assumes grub will be installed when I add Ubuntu LTS. Can I assume that?

Is there a rule of thumb on how much space may be wasted in the big Btrfs partition by files left over from Fedora? Also is it likely that anything left there will cause problems for Ubuntu LTS? I already have Gnome, Cinnamon and Xfce desktops with Fedora, but I only want Xfce in future.

Current: Framework 13 on Crucial P3 Plus 4TB SSD with Fedora 40, updated from a fresh install of Fedora 38, via 39

/dev/nvme0n1p1 629MB FAT32 /boot/efi
/dev/nvme0n1p2 1.1GB  EXT4  /boot
/dev/nvme0n1p3 4TB      Btrfs    /

---

