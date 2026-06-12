---
title: "installing ubuntu to an external usb drive"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by shoggoth on 2006-07-26
so i followed the direction from [http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)
and im now at step four. everything before this step has worked correctly and ive made a reply in that thread for help but i just now noticed its in a previous releases forum so i thought i would post and ask for help here where more people are prolly at. my orignal post is on the last page of that thread but please reply here. :)

I do not know what i should be booting from on step four. Im using dapper drake alternative install cd and booting from it does give me the option of rescuing an install on other drives. booting directly from the external drive doesnt seem to work.

thanks for any help.

---

### Post by shoggoth on 2006-07-26
bump

---

### Post by avtolle on 2006-07-26
From step 4: ( STEP 4 ) BE 100% SURE to leave the CD in the drive (and close the drive door) before rebooting. When the PC reboots, type in rescue (to load UBUNTU in rescue mode) ( Review REQUIREMENTS at the beginning of this guide! )

Why do we startup in rescue mode you might ask? It's because we have to edit a few files to get USB support loaded before UBUNTU actually gets going. And, we also need to change a setting in the GRUB menu file to make it work correctly.

So, it would appear one reboots from the CD in rescue mode. HTH.

---

### Post by b.treu on 2006-10-14
You don't need to go through all of this.[-X  You can do the install SIMPLY and completely through the GUI. You just need to disable the automatic mounting of drives. I found the following exactly as you see it on the [Ubuntu Switch]("http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/") website. You only need to do the following:

To install Ubuntu on the external USB hard drive, I simply ran the install from the live CD just as if I were going to install normally. Before running the install, I plugged the USB hard drive in and Ubuntu detected it. Not only did Ubuntu detect it, but in mounted the drive. ](*,) This became a problem later when trying to partition the drive and create a file system because the drive was mounted.

To fix the problem System > Preferences > Removable Drives and Media and deselect the following options

    * Mount removable drives when hot-plugged
    * Mount Removable Media When Inserted
    * Browse Removable Media When Inserted

I then proceeded to install Ubuntu on the USB Hard Drive by clicking through the defaults in the installer. I chose to wipe my external hard drive and do a fresh install. If you have data on the disk you want to keep, choose to partition the disk appropriately. Be sure you are dealing with the right disk. The installer lists your main internal hard drive as /hda1/ more than likely and your external hard drive will be listed as /sda1/ or something similar.

The last step after actually installing Ubuntu on the external USB Hard Drive was to get my laptop to boot from the USB. This was nothing more than pressing F2 at a normal boot to change the boot order to load my USB before my internal hard drive.\\:D/ 

Best to all!

---

