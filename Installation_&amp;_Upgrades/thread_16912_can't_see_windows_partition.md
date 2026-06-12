---
title: "can't see windows partition"
date: 2005-02-24
forum: Installation &amp; Upgrades
---

### Post by zack18 on 2005-02-24
hi all,

this is my first time trying to install linux on an amd64 with a partitioned harddrive.  installing fedora on an intel pc was rather painless.

we worked through the video card issue (ati)... but now, i can't seem to be able to dual boot it.  ubuntu (amd64-general) device manager shows 4 volume devices (windows xp - installed first; another partition that both windows & linux can see; my linux partition and then the other 8MB partition).  however, all the vendors for the devices are unknown, with Block bus types & unknown capabiities.

how do i get it so that i can dual boot.  hopefully this ubuntu installation didn't ruin all my hardwork on the windows side.

thanks!

---

### Post by alastair on 2005-02-24
You have 1 hard drive? What are the devices e.g.

sudo fdisk -l /dev/hda

(assuming primary IDE disk)

What is in your grub config file :

/boot/grub/menu.lst

At boot, grub should allow you to press "ESC" and see a choice of OS's to boot.

---

### Post by zack18 on 2005-02-24
yes, 1 hardrive:
windows previously formatted
data partition (for windows & linux) was unformatted
linux partition was unformatted prior to installing ubuntu.

sudo fdisk command doesn't bring anything up... just gives me another prompt.

/boot/menu.lst
what am i looking for?  i noticed that timeout 3 (corresponds to 3sec) to decide which OS to enter into...  

can't edit the menu.lst, but haven't tried to reboot.

if i reboot, when do i type 'grub'


when i  'more /boot/device.map' it says "(hd0) /dev/sda"
when i 'fdisk -l /dev/sda' it tells me "Cannot open /dev/sda"
not sure if this helps.

i have a SATA drive.

i can access the menu in grub, but grub doesn't detect the windows option.

---

### Post by zack18 on 2005-02-24
edited the /boot/menu to add windows & both windows & ubuntu can now see the one partition they both have in common... thanks!

---

