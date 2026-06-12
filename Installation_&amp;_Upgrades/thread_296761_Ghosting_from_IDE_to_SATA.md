---
title: "Ghosting from IDE to SATA"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by bricktop on 2006-11-10
Hi Guys,

A bit stuck, must note that I am a toal noob. I am trying to ghost a linx drive using G4L and moving the image from an IDE disk to a SATA disc. both same size drives.

the whole imaging process runs without any errors, the restore also goes fine, the problem comes at first boot, I am assuming that it images the boot record and refferences hda1 as the original was an IDE drive and the new system is using SATA, sda1. It hangs at boot and i get the following:

"ALERT! /dev/sda1 does not exist"
dropping to shell.

Can anybody help with getting this up and running. This is a test run to check what complication i wil run into when i virtualise our Linux machines, We have an old legacy Redhat machine running Sybase that is our main objective but would like to get the Ubuntu boxes up first.

Cheers

---

### Post by irw on 2006-11-10
Have you updated /etc/fstab & grub?

Do you have any other partitions on the SATA drive - sda referes to  the drive, sda1 refers to the first partition on it.

---

### Post by bricktop on 2006-11-10
Ok now I am confused. This is the situation, i made an image using g4l of an ubuntu system usig an IDe drive. I then restored the image to a SATA drive. Where do i need to upate the fstab and grub on the new or old system and how. 

Sorry as i said i am a noob.

---

### Post by irw on 2006-11-10
in a terminal:```
sudo gedit /etc/fstab
``` and look at the any lines referring to /dev/hda1 - they will need to change to /dev/sda1 (or hda2 -> sda2 etc).

To see this Grub listing:
```
sudo gedit /boot/grub/
```


What may be easier to get grub working for you might be to re-install it using a live CD - [see here how to do this]("http://ubuntuforums.org/showthread.php?p=121355#post121355")

---

### Post by bricktop on 2006-11-10
Ok, I think i may have restored the image incorrectly. Is it neccessary to format the new machine before i restore the image to it? What should the condition of the drive be? Totally unpartitioned or formatted?

---

