---
title: "Dual Booting WinXP/Mandrake 10.0, want to replace Mandrake with Ubuntu"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by DerGeist on 2005-12-03
Hi everyone!

I have a bit of a newbie question, but you all seem so friendly and helpful I thought it was safe to ask here. ;) 

I currently dual boot WinXP and Mandrake 10.0 Community. I tried the Ubuntu LiveCD and going back to 'drake doesn't even compare. Now I know I **need** Ubuntu!

I have the following partitions on my hard drive:

WinXP (NTFS)
'/' (VFAT - mandrake root)
'/home' (VFAT - mandrake home data)
swap (VFAT - mandrake swapfile)

I am running lilo to dual boot. I need to keep Windows XP for work and school and it's very important I don't bork my Windows install as it has many files which (although I've backed them up, don't worry :D) would be difficult to properly replace (complex projects integrated with existing programs, etc).

I am wondering if I can overwrite my Mandrake 10.0 Community install with Ubuntu without causing my PC to burst into flames, and wondering how to accomplish this if it's possible. Keeping my /home with all my custom settings would be a bonus, but isn't necessary. Any help would be *greatly* appreciated.

Thanks guys!

-DerGeist

---

### Post by aysiu on 2005-12-03
Hm. A few things:

1. Mandrake works on a FAT partition? I wouldn't put Ubuntu on FAT. Ext3 or Reiserfs are better choices.

2. You can install right over Mandrake. During the Ubuntu installation, select "Manually edit partition table" and make sure you select the former / to be /, the former /home to be /home, and the former swap to be swap.

3. Install Grub to the MBR, and Windows will be added to the boot menu.

4. You can preserve Mandrake's settings, but I think you're better off in the long run using a fresh /home (a separate /home is good for reinstalls of the same distro or a fresh install of a newer version of the same OS).

---

### Post by Qrk on 2005-12-03
Its easy to install Ubuntu over mandrake. Use the installer like normal, and select the manual partitioning option when pressed. Just choose the partition you currently have Mandrake on to install the new ubuntu. Be sure to set swap as well. 

If your /home is on a separate partition, you can have ubuntu use it. I would not recommend this, however. Using the same home directory in between distrobutions can be buggy. 

While the Ubuntu installer isn't as pretty as Mandrakes, its very intuitive and almost as easy.

---

