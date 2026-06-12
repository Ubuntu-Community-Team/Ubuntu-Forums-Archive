---
title: "installing ubuntu on second drive"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by bryanmc95 on 2011-06-28
Hey Guys, I have a dell xps 410 tank,running vista home,and a blank d drive,how do I install ubuntu on my d drive without trashing vista on my c driv,can i just install it to d,using grub,how do i go about doing this without trashing my sytem??

---

### Post by oldfred on 2011-06-28
Welcome to the forums.

Is your d: drive really another drive or just another partition. Windows uses them both interchangeably. Linux uses sda, sdb, sdc for drives and sda1, sda2, sda3 for partitions where the final number is partition and the letters are drives.

Post this from a Ubuntu liveCD terminal:

```
sudo fdisk -lu
```

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by C.S.Cameron on 2011-06-28
Unplug your vista drive, insert the Live CD and install.
Use manual partitioning if you want something fancy.
Plug in the vista drive.
Boot, Select the Ubuntu drive in BIOS as first HDD.
Once in Ubuntu run update grub.

---

