---
title: "ReInstalling Ubuntu"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by crokett on 2011-08-21
I want to redo the partitions on a machine I have Ubuntu on.  Right now Ubuntu is in an extended partition and I want to delete that and put Ubuntu on a primary. I also want to get rid of Windows. Could I just reformat the Windows partition and copy the Ubuntu install there, then fix Grub?  As I recall I can't copy /dev so how can I get it onto the new partition?  I am trying to do this without running through a reinstall.

---

### Post by YesWeCan on 2011-08-21
Hi there. I like to make all my linux partitions logical. That way I can have as many as I like and I have primaries free for future use.

One method to do what you hav described is to boot live CD/USB and run GParted.
Delete your Windows partitions
Copy and paste your Ubuntu partition to the unallocated space vacated by Windows. Then make a swap partition next to it in the remaining unallocated space.
Note the new partition name. I'll assume it is sda1 for these instructions, change to suit your actual:

**Very important** - you must give sda1 its own unique UUID:
[COLOR="Navy"]sudo tune2fs -U random /dev/sda1[/COLOR]

Then you must edit the copied fstab to use this new UUID for / and to use the UUID of your new swap partition rather than the old one:
[COLOR="navy"]sudo blkid[/COLOR]
to see the new UUID for sda1 and new swap
[COLOR="navy"]sudo mount /dev/sda1 /mnt
sudo gedit /mnt/etc/fstab[/COLOR]

Then reboot as before to your original Ubuntu.
[COLOR="navy"]sudo update-grub[/COLOR]
to add the new Ubuntu to the boot menu
reboot and select the new Ubuntu and check / and swap are mounted at the correct partitions
[COLOR="navy"]mount[/COLOR]
then reinstall Grub to /dev/sda
[COLOR="navy"]sudo dpkg-reconfigure grub-pc[/COLOR]
change the wallpaper so you can be sure you are in the right Ubuntu when you reboot.

Reboot, again to the new Ubuntu and new wallpaper
Use GParted to delete your old / and swap and delete the extended partition.

---

### Post by crokett on 2011-08-21
I've always thought if you need more than the 4 primary partitions, you are doing it wrong.  :)  I see your point on the logical partitions though and mayhap when I move stuff around I might put /home on its own.  

Thanks for the writeup, that is a lot simpler than I had planned. For the copy, can I copy /dev?  I have a vague recollection that you can't copy it and don't really need to anyway.  Am I recalling correctly?

---

### Post by YesWeCan on 2011-08-22
The /dev problem you may be thinking about is when you are copying a runnng OS; you don't want to end up copying the contents of a device, or you could copy your whole disk to a disk partition! With a command line copy you'd use cp -x to only copy the local file system.

Here you use GParted to copy and past a whole partition that isn't running so this problem doesn't arise.

---

