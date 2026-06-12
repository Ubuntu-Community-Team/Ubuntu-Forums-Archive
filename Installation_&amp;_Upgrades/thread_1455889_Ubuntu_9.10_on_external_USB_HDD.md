---
title: "Ubuntu 9.10 on external USB HDD"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by Josh_Dude83 on 2010-04-16
Hello,
This is my first post. Let me start off by saying i haven no real experience with ubuntu or linux. Trying out for the first time to prepare me for an upcoming class. I've been trolling the forums but can't find anything specifically related to what I'm doing that answers my question. I decided to install ubuntu on my external usb hdd. After following some tips ([http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)) i was able to edit the:
/etc/initramfs-tools/scipts/modules 
adding to end of file:
 
ehci-hcd
usb-storage
scsi_mod
sd_mod
 
 
and
/etc/initramfs-tools/scipts/initramfs.conf
adding to the top to allow for usb drivers to load
WAIT=12 
 
Now on step 10. I'm inside alt+F2 terminal. I run that command and it closes. Can't tell if it runs or not. Is there some type of confirmation? What file do i look to see if its been updated? Because the image modify date doesn't change after running and th other one is the same size so i woudl assume it hasn't changed either. I'm also not doing this in recovery mode. Just standard mode using gksudo and sude appended to the front of the command and still nothing. Any help from here woudl be apprecaited. 
 
So i guess inevitably i'm askign how to i compile the new image. I dont have internet access right now so i can download any additional packages other than preloaded.

---

### Post by Josh_Dude83 on 2010-04-16
To be more specific what ive been doing in that step is running command:
gksudo mkinitramfs -o /boot/initrd.img-2.6.31-14-generic /lib/modules/2.6.31-14-generic
 
or
tried initramfs and initramfs-tools vs mkinitramfs because of previous step showing a directory of mkinitramfs whereas my install only has a initramfs-tools directory
 
gksudo initramfs -o /boot/initrd.img-2.6.31-14-generic /lib/modules/2.6.31-14-generic
 
gksudo initramfs-tools -o /boot/initrd.img-2.6.31-14-generic /lib/modules/2.6.31-14-generic
 
these completed with errors not being able to find the file
 
or
 
mkinitramfs -o /boot/initrd.img-2.6.31-14-generic /lib/modules/2.6.31-14-generic
 
or 
sudo mkinitramfs -o /boot/initrd.img-2.6.31-14-generic /lib/modules/2.6.31-14-generic
 
And it doesn't look like it's doing anything. I hit enter and almost immediately is closes without any error or reponse.

---

