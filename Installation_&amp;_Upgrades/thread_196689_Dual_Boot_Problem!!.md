---
title: "Dual Boot Problem!!"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by jelly5150 on 2006-06-14
I have installed Ubuntu 6.06 on a 15GB drive setup as a master on ide channel1.(i disconnected my primary winxp drive to do this) assuming i could just hook the drive up as a slave when the install was done and then choose which drive to boot up. NOT!!! heh heh heh!!
Anyways is there a quick fix....it looks like Ubuntu tries to start then it crashes saying it can;t mount the volume. It's lookin for hda1 which is actually hda2 now.

---

### Post by Sutekh on 2006-06-14
An exact error message would be very helpful here.  

So you are getting to the GRUB menu?  If so you will need to edit the menu at this time, so you can boot Ubuntu.

Press 'e' to edit the entry for Ubuntu, and 'e' again to edit the **root** line.

If you have changed the hard disc, then it should be looking for /dev/hdb1 instead of /dev/hda1 (not /dev/hda2 - thats the second partition on the first disc, we want the first partition on the second disc).

It probably originally had
```
root        (hd0,0)
``` You will need to edit this to
```
root        (hd**1**,0)
``` Next you will need to edit the **kernel **line, originally it might have been
```
kernel     /boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
``` You will need to edit this to
```
kernel     /boot/vmlinuz-2.6.15-23-386 root=/dev/hd**b**1 ro quiet splash
``` Then try to boot this entry with 'b'. If this doesn't work, please make a careful note of the error you get. It will help alot in working out exactly what to do.

If this works you should make the changes permanent once Ubuntu boots up, by editing the GRUB menu.
```
sudo cp /boot/grub/menu.st /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```And don't swap the physical order of your discs, it can get tricky. :p

---

