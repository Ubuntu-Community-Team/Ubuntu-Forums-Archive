---
title: "GParted - unable to use free space"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by mardybear on 2006-11-12
Greetings....

I'm a linux newbie.

I  installed Ubuntu on a 10GB drive - 3GB fat32 (Win98), 6 GB Ext 3 (main Linux directory), 1 GB Linux swap. 

My 6GB Ext 3 was quickly getting full and my 1GB Linux swap was too big, so i reduced/resized the swap down to ~500MB. I now have ~500 MB 'unallocated' free space but GParted will only allow me to add another new directory and won't allow me to simply slide/resize my current Ext 3 directory.

Current setup:
Win98XXX, Ext3XXXXXX, unallocatedX, SwapX

What I want:
Win98XXX, Ext3XXXXXXX, SwapX

Thanks in advance,

Marty

---

### Post by emdeem on 2006-11-12
gparted will not edit a partition that is mounted.

---

### Post by bulldog on 2006-11-12
Use the live cd or download the gparted live cd.

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by mardybear on 2006-11-13
Thanks for the replies....

I have an install CD....me thinks it's the live CD.

To confirm, i boot using the live CD, run GParted from this CD boot, first 'unmount' my primary Ubuntu drive (/dev/hda), confirm changes and then resize/increase this primary partition.

Will i be able to re-mount this primary drive (/dev/hda) without/before rebooting?

If a reboot is required, do i reboot to the main system or the live CD?

I'm probably just overthinking this...i suppose i can always boot to the live CD and pretty much repair any issues. I just don't want to lose the ability to log back into Ubuntu as i'll be making changes to my primary/root partition. 

Also....doesn't 6GB seem rather large for a recent Ubuntu installation with a few relatively minor package installs and all of the recent Linux/Ubuntu updates? I've run apt-get clean and autoclean...anything else to get rid of some of this bulge? I've heard about installing/running deborphan. Is this a possible solution or something better to try?

Thanks again,

Marty

---

### Post by mardybear on 2006-11-17
Thanks for your help.

Booting from the LiveCD to run GParted worked like a charm....

Marty

---

