---
title: "Install Ubuntu 8.04.1 to Flash Drive."
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by Rumel on 2008-08-04
I recently bought a Super Talent Pico 8gb flash drive. I wanted to install Ubuntu Hardy Heron to it. I fired up the live cd today selected install, and formatted the drive to ext3, I then told Ubuntu to install to that drive (sdc) and then to install Grub to sdc. When the installation was finished and I tried to boot from the drive, it said the MBR was missing or something along those lines. It boots fine without the flash drive in there, but the install on the flash drive is not right. So my question is how do I install to a flash drive?

(My pc can boot from USB)

---

### Post by tamoneya on 2008-08-05
try following this guide.  It has worked well for me in the past: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

---

### Post by Rumel on 2008-08-06
Alright I used the lilo deal at the bottom and I think that helped some. Now I just need to reinstall grub on to the flashdrive. How do I go about doing that? When I installed Ubuntu it asks about hd0 I have to choose something else for the flashdrive right?

---

### Post by dileepm on 2008-08-07
Try this [http://www.scribd.com/doc/4090276/Installing-Ubuntu-In-Pen-Drive](http://www.scribd.com/doc/4090276/Installing-Ubuntu-In-Pen-Drive)

---

### Post by Rumel on 2008-08-09
Alright so I went into the live cd and I went to terminal and ran.```
sudo apt-get install lilo
lilo -M /dev/sdc
```
I then reran the install and when I got to page 7 on the install I went into advanced and changed grub to install to sdc instead of hd0. I restarted and grub ran right, until I selected Ubuntu to boot up. Then it would give me an error 21. I booted up the live cd again and remapped everything in the /boot/grub/menu.lst to (hd0,0). I then rebooted and I could boot up to the main screen of Ubuntu. Once I logged in though everything hung. Gnome never came up. I restarted the X server a couple of times and the only thing I could boot into was failsafe terminal. So anyone got any ideas?

---

### Post by kmslogic on 2008-08-10
It seems like the actual install guide you want for a 4gb flash drive is this one: [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/) which I followed, but which didn't quite work...

I booted the Ubuntu 8.04 CD, and went to install, selected the flash drive under "guided, use entire disk", and on the "ready to install" page I clicked advanced to tell it to write the boot record to the flash drive instead of to hd0 (an accident waiting to happen which is why the setup guide suggests disconnecting local hard drives during installation).

It went though the process of partitioning and installing files to the flash drive and on reboot it does boot GRUB on the flash drive but then returns an error 21 which implies to me that it's not recognizing the partitions it created on the flash drive, or that the drive information has changed somehow since reboot.

I've gone through this entire process twice, but at the moment I'm stuck with an error 21 when booting from the flash drive.

---

### Post by kshaff03 on 2008-08-10
Rumel,

I had the same problem today. I installed using the Live CD to a Transcend JF V30 4GB USB thumb drive. Upon booting, I recieved a message stating that Grub couldn't mount the selected partition (or something very similiar).  I loaded up the live CD and then changed the references in the menu.lst on the thumbdrive from hd1 to hd0. (not sure what this does, I'm a complete newb).

Rebooted and Ubuntu loaded and everything is working so far.  This is on a Dell Latitude D620 notebook.

---

### Post by Rumel on 2008-08-10
> **kmslogic said:**
> It seems like the actual install guide you want for a 4gb flash drive is this one: [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/](http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/) which I followed, but which didn't quite work...

I booted the Ubuntu 8.04 CD, and went to install, selected the flash drive under "guided, use entire disk", and on the "ready to install" page I clicked advanced to tell it to write the boot record to the flash drive instead of to hd0 (an accident waiting to happen which is why the setup guide suggests disconnecting local hard drives during installation).

It went though the process of partitioning and installing files to the flash drive and on reboot it does boot GRUB on the flash drive but then returns an error 21 which implies to me that it's not recognizing the partitions it created on the flash drive, or that the drive information has changed somehow since reboot.

I've gone through this entire process twice, but at the moment I'm stuck with an error 21 when booting from the flash drive.

Alright, you have everything right. You just need to go into the live cd again, and plug in your flash drive. Then you want to go into a terminal and open up your menu.lst. For mine I did-```
cd /media/disk/boot/grub
sudo gedit menu.lst
```
I then changed it to read hd0 instead of sdc. I think you have to do this because when you boot with your flash drive that's your only drive, so now it is HD0 instead of your normal hard drive. Although you have to run grub install to your flash drive. So I think this is something that always has to be fixed.
[QUOTE=kschaff03]Rumel,

I had the same problem today. I installed using the Live CD to a Transcend JF V30 4GB USB thumb drive. Upon booting, I recieved a message stating that Grub couldn't mount the selected partition (or something very similiar). I loaded up the live CD and then changed the references in the menu.lst on the thumbdrive from hd1 to hd0. (not sure what this does, I'm a complete newb).

Rebooted and Ubuntu loaded and everything is working so far. This is on a Dell Latitude D620 notebook. [/QUOTE]
Dang your lucky. After login it just hangs. I have no clue what to do now.

---

