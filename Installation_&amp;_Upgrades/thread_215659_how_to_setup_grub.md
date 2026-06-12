---
title: "how to setup grub"
date: 2006-07-14
forum: Installation &amp; Upgrades
---

### Post by 88djy on 2006-07-14
my grub..is not to setup .

"grub loading please wait..."
the computer is stop in here?why?

then my use liveCD to steup grub.
sudo  grub
root (hd0,0)
setup (hd0)

then reboot.
but is not Success ~it't the samll
"grub loading please wait..."

then me ..go on use liveCD
sudo grub-install /dev/hda
"probing devices to guess bios drires ,the may take a long time
 /dev/mapper/casper-snapskot dos not have any corresponding bioss drive "
  why?..anyone help me...
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
this is .my computer
k6-2 300 SD196 ST 20G rain128 Main Board chips :mvp3
one hard in ide1 max...one-rom in ide2 max 
only system :ubuntu 

sudo fdisk -l

/dev/hda1 *                          linux
/dev/hda2                           exteded
/dev/hda5                        linux/solaris

---

### Post by 88djy on 2006-07-14
only system :ubuntu server

---

