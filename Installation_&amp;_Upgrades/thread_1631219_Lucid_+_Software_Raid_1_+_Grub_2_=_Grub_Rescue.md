---
title: "Lucid + Software Raid 1 + Grub 2 = Grub Rescue"
date: 2010-11-26
forum: Installation &amp; Upgrades
---

### Post by mrrrk on 2010-11-26
Hi
 
I'm trying to get Ubuntu 10 installed on an old HP DL320G2 which has "Fake Raid". I've set the BIOS up for separate drives (2 x Raid 0 array with one disk each) and installed the OS with software RAID 1 according to the instructions here ([https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)). Every time I try to boot, I end up with the Grub rescue prompt. I can get booted by entering:
 
set prefix=(hd0,1)/boot/grub
set root=(hd0,1)
insmod /boot/grub/linux.mod
linux /vmlinuz root=/dev/md0 ro
initrd /initrd.img
boot
 
I've tried to figure this out looking at this ([https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)) but I'm really not clear on what I need to do! I'm not sure if Grub's failing to open the grub.cfg file or if there's a problem with the file itself. It seems to contain lines like root='(md0)' and my guess is thay should be (hd0,1) since the RAID maybe isn't doing it's thing until the OS gets up and running? Tried editing the file against the warnings but that wasn't successful (rescue prompt again)!
 
Any advice for this Linux beginner on how to get my machine to boot without my intervention much appreciated!

---

### Post by dino99 on 2010-11-26
you cant boot on raid0, point.

what is usefull with raid0 by the way ?

sudo dmraid -rE

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by mrrrk on 2010-11-26
Sorry, I think you misunderstood.  My mention of Raid 0 is a red herring - I used that in BIOS to make two separate disks from the on-board fake-raid controller.  I'm trying to achieve *RAID 1*, i.e.  mirrored disks for fault tolerance.  Linux does not support (as far as I can tell) the kind of 'fake raid' that these cheap controllers provide.  So my original question stands.

(btw, RAID 0 or RAID 0+1 is supposed to offer increased read performance.  Handy for DB reporting applications, etc...)

---

