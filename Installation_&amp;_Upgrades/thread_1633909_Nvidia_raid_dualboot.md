---
title: "Nvidia raid dualboot"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by asvestomix on 2010-11-29
Hello, I would like to make a dual-boot I already have installed win7 (64bit)
in my nvidia raid 0 array in wich i had made 3 partitions... My goal is to have a dual-boot with win 7 and ubuntu without any unexpectable data loss, firstly I booted with ubuntu 10.10 (64bit) live cd and i installed the kpartx package that was needed for the gparted to see my raid array.. now the things are bit complicated because i am afraid if i do something wrong maybe i lost the whole array in which i have all my data (i don't have a backup media yet), so what partition should i split now to make a partition for ubuntu? Again to keep my data as safe as possible is important... I fount a tutorial for the whole procedure but they don't saying anything about raid and already partitioned disks ([http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/)..here](http://www.hackourlives.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/)..here) i attach a photo from my gparted.

---

### Post by AbeJarano on 2010-11-29
Is 'unelectable' unselectable?  Do you mean all windows files should be seen in Ubuntu?

There's no way to guarantee data safety without a backup! 

Your third partition labelled Windows could shrink 10 or so GB and if the shrink goes wrong you would be able to reinstall Windows but I think you've data or installed programs there.

Again, anytime you use low level disk writing/formatting tools there is risk of a mistake, mostly on our part, of an error affecting all data there that is impossible for us to fix! I'm not responsible and won't help if something goes wrong!

---

### Post by asvestomix on 2010-11-29
> **AbeJarano said:**
> Is 'unelectable' unselectable?  Do you mean all windows files should be seen in Ubuntu?

There's no way to guarantee data safety without a backup! 

Your third partition labelled Windows could shrink 10 or so GB and if the shrink goes wrong you would be able to reinstall Windows but I think you've data or installed programs there.

Again, anytime you use low level disk writing/formatting tools there is risk of a mistake, mostly on our part, of an error affecting all data there that is impossible for us to fix! I'm not responsible and won't help if something goes wrong!

sorry i mean unexpectable i am not sure is this is a correct word i mean something tha you dont expect to happend.. anyway my partition market as windows is just widows files i dont care if something goes worng there but i care if the whole volume is destroyed anyway i would like to make it as safe as possible .. sorry if my english are bad

---

### Post by ronparent on 2010-11-30
From you partition table, the main problem I see is that you already have three primary partition on your aqrray. If you try to create and install Ubuntu to unpartitioned space in a primary partition the install will most likely fail (because between the partiton for / and the one for swap you will be trying to create five primary partitions - which gparted will not allow. What you need to do is to use gparted to create an extended partition with sufficient unallocated space to install Ubuntu to. Post if you need further explanation.

---

### Post by asvestomix on 2010-11-30
> **ronparent said:**
> From you partition table, the main problem I see is that you already have three primary partition on your aqrray. If you try to create and install Ubuntu to unpartitioned space in a primary partition the install will most likely fail (because between the partiton for / and the one for swap you will be trying to create five primary partitions - which gparted will not allow. What you need to do is to use gparted to create an extended partition with sufficient unallocated space to install Ubuntu to. Post if you need further explanation.
What i did was to shrink 11gb from the "windows" labelled partition and after that in the installation at advanced partition settings i created an logical 9.5gb part from the unallocated space and used it as root "/" ( if i used it as primary then the remaining space would marked as unusable),
then i used the remaining space for swap. that worked good i thing expect that the first time i booted in windows after the shrink it did a check disk, now what i would like to now  is if possible to change the order from grub.

---

### Post by asvestomix on 2010-11-30
Does any one know if it is possible to change the priority in grub and choose which OS would boot first?

---

### Post by asvestomix on 2010-12-01
Bump

---

### Post by AbeJarano on 2010-12-02
In /boot/grub/menu.lst you would change the order of the systems listed there --- towards the end of the file.

---

### Post by asvestomix on 2010-12-02
hello, i went to /boot/grub/ but i couldn't find any menu.lst

---

### Post by ronparent on 2010-12-02
There is no menu.lst for grub 2. The equivalent is /boot/grub/grub.cfg. That file should not be edited if for no other reason that it is rewritten each time grub-update is run. The method for customizing your grub menu is described here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

