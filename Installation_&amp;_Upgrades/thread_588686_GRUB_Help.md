---
title: "GRUB Help"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by 1mikelli1 on 2007-10-23
I have 3 systems loaded windows XP, Vista, and Ubuntu

XP was first and installed as primary drive (disk 1)
Vista was second and the vista boot loader was put on disk 1
It works but vistaboot pro and BCD edit sometime give a arning.

I removed all cables so I wouldnt mess up windows my kids would kill me.

I installed ubuntu

I reconnected the drives with the bios recognizing the disks in the order below order.

After that I went back to XP and used BCDedit to add an UBUNTU entry which has the option of locating grub when it is not on the boot device.

NEOGrub will look for menu.1st located in /boot/grub on the ubuntu drive.

It finds the file but will not go into ubuntu without an edit of grub (I hit E twice and change the drive from (hd0,0) to (hd2,0), save and boot and its all OK.
:popcorn:

I believe since I installed as a primary and repositioned it as secondary Hd0 to hd3 is in order.   If I change the bios order and boot device to ubuntu it boots fine also.




I tried editing the menu.1st as above no no luck.


can someone help with some ideas.




I have a PCI express ati x1300 (512k) made by vision tech
core 2 duo 2.4g
4 gig ram

disk 1 sata 300 win XP
disk 2 sata 300 win vista
disk 3 sata 150 ubuntu 7.10 (recent upgrade)

---

### Post by rollerdiscoman on 2007-10-23
The file is not "grub.1st", its "menu.lst". You should be able to go to terminal and type: 

"sudo gedit /boot/grub/menu.lst" 

It will ask your password, of course.
In the file that opens, find your entries (located after the line that says "## ## End Default Options ##"). Change the partitions it boots off of, ans save the changes.

Please tell me if this works : )

---

### Post by 1mikelli1 on 2007-10-24
it worked after drive priorities change vista bootloader loads grub using menu.lst. I changed the drive from (hd0,0) TO (HD2,0)

boots fine.  So The secret was vista boot loader edit using neogrub and bcdedit

---

