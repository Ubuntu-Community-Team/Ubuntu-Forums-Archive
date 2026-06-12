---
title: "Windows Not in GRUB Bootloader?"
date: 2010-01-20
forum: Installation &amp; Upgrades
---

### Post by justinram22 on 2010-01-20
Hello, my friend is having a mini lan/computer party this weekend so i figured that it would be easier just to dual boot windows this weekend than trying to get all the games to work in ubuntu.  So i install windows fine and it of course wipes out grub, so i reinstall grub by using the following commands off a live CD.

> 
# Boot from the CD/USB flash drive from which you installed Ubuntu
# Open terminal (It is there under Accessories)
# type in sudo fdisk -l
# then type sudo mount /dev/sdAB /mnt , where A is your drive and B is your linux partition. In my case, I typed in sudo mount /dev/sda7 /mnt
# install GRUB again by typing this sudo grub-install --root-directory=/mnt /dev/sdA , where A is your drive. In my case, I typed sda
# Now type sudo umount /mn


But now it seems that windows is not in the bootloader.... Any help w/ how to get windows into the bootloader would be greatly appreciated.

Running ubuntu 9.10

Thanks!

---

### Post by darkod on 2010-01-20
Because windows was just recently added run also:
sudo update-grub

You just reinstalled grub which uses the same grub.cfg file as before windows install. And it won't "see" windows without update-grub.

---

### Post by presence1960 on 2010-01-20
what version of Ubuntu are you running and what version of GRUb are you using? If you do not know for sure (100%) then do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Leppie on 2010-01-20
> **darkod said:**
> Because windows was just recently added run also:
sudo update-grub
+1, just boot into ubuntu and run the command, it should add windows automagically

---

