---
title: "Ubuntu will install...but not boot up!"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by alfaalex101 on 2008-05-04
These are the steps I took to where I am now:

(60 gig hard drive, 512mb ram, Athlon XP2000+, Nvidia 6200 AGP, 1280x1024 running resolution)

1. Low level format
2. Install Windows XP
  -setup a 30gig NTFS partition
3. Windows XP successfully installs on the 30 gig partition
4. Install Ubuntu 8.04 (CD is free from errors)
  -manual partition setup

>created a 512mb swap partition set as Primary
>created a "whatever space is left" partition set as EXT3, mounted as  /  

5. Install successful.
6. Reboot (without CD in drive)
7. Ubuntu logo keeps looping the "loading" bar.



I'm pretty sure this is because the primary  /  EXT3 partition was not set as BOOTABLE: YES ..because there was no option for me to select when using the partition manager from Ubuntu :(. I'm using the CD right now as Live session user and I would really appreciate any help that wouldn't take me down the road of low level formatting, re-installing XP and such. I just want Ubuntu to boot. 

Thank you so much guys! :KS

---

### Post by Partyboi2 on 2008-05-04
What happens when you remove the splash option from boot?
Here is how to if you are not sure:
when you boot the system and see the grub menu, highlight the kernel you usually boot into and press "e" to edit then highlight the line starting with "kernel" and press "e" again then change splash to nosplash then press "enter" then "b" to boot.

---

### Post by alfaalex101 on 2008-05-04
These are the main areas of focus:

exception Emask 0x0 SAct 0x0 SErr 00 action 0x2

and

Idm_validatepartition_table(): Disk read failed



I'd also like to add that this hard drive has no errors or anything on it.


UPDATE: I've solved the problem! I switched my IDE cables from using the second slot to the first slot (to my hard drive and CD drive)!

---

