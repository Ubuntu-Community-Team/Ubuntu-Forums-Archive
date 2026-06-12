---
title: "Installation from iso using grub"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by zoharj on 2006-12-05
I have a toshiba r100 which can not boot from usb, and does not have a floppy or cd-drive. I can access the computer from booting knoppix via the network.

I would like to install ubuntu 6.10, but am having a hard time doing it.

my hard drive is setup as follows

hda1 = ext3fs with vmlinuz and initrd.gz copied from iso/chaser?(or something)

hda2 = dd if=/mnt/usb/ubuntu.iso 

hda4 = dd if=/mnt/usb/slax.iso


my computer will boot into grub just fine, but i dont know how to get the ubuntu install to run.

I have been working off this [https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies)

minus the floppy part

maybe i copied the wrong files to hda1? 

I can move files around and format drives using knoppix via network boot.


any help would be VERY much appreciated

---

### Post by Sebastral on 2006-12-11
This should make you :) ; [HOWTO: Install Edgy 6.10 from an .iso file](http://www.ubuntuforums.org/showthread.php?t=316093)

---

