---
title: "Strange name for device"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by todak on 2009-10-14
I just updated and then rebooted due to a newer kernel being installed. Upon logging in, my second internal hard drive that I use for storage and backups, which used to be labelled as **40.0 GB Filesystem**, now is shown as per the attached image. Any reason for this odd naming convention? All of my removable media, such as CD/DVD drives and USB flash drives, retain their correct names; just the internal hard drive has a weird name.

---

### Post by VMC on 2009-10-14
Strange indeed. What does fdisk -l and blkid show.

---

### Post by todak on 2009-10-14
blkid produces ```
/dev/sda1: UUID="106b9362-60de-49ec-b232-6138a3451384" TYPE="ext4" 
/dev/sda5: UUID="27666630-dfb1-4b51-8ff3-35eb608e8b7e" TYPE="swap" 
/dev/sdb1: LABEL="133.1848;55" UUID="DFB8-4B0D" TYPE="vfat" 
/dev/sdd1: LABEL="" UUID="0D04-9F96" TYPE="vfat" 

```

fdisk -l produces ```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee239

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdd: 1027 MB, 1027416576 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004a4a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         124      995998+   b  W95 FAT32

```

---

### Post by kansasnoob on 2009-10-14
I've encountered some strange "renaming" behavior but I've not seen that before.

I think I'd file a bug report. Maybe against nautilus?

---

### Post by ranch hand on 2009-10-14
I don't think that Nautilus can re-label a partition.

I think I would go to gparted and re-label the bugger.  Just to be real safe I think I would use a LiveCD to do it.

Reboot and see what happens.  I wonder if one of the recent gparted updates has someting to do with this.

---

### Post by VMC on 2009-10-14
Well there it is in plain sight: LABEL="133.1848;55"

If its not mounted use "System > Administration > Disk Utility" to change the label.

Edit: By the way, those vfats have a rather odd looking UUID tag. I don't have any so I wouldn't know.

---

### Post by rifak on 2009-10-14
yes, i can confirm this..it's happening to me also. my internal hard drive partition is labeled correctly, but when i connect a usb flash drive or external hard drive it gets a weird label (the odd label is in /media/). as you can see in my attachment, the label on the desktop is correct and sensible, but in /media/ is where it's odd. not sure exactly what has caused this because it was doing this since i installed a fresh beta.

---

### Post by ranch hand on 2009-10-15
WOW, I have a dual disk external enclosure and it is not doing this to me.  I turn it on and off as it is needed (it is my 64bit test platform).  I even, at times, boot to OS' on it from grub2 on one of my internals.

---

### Post by VMC on 2009-10-15
Mines normal as well. I wonder if you guys experiencing this problem have same kind of hardware, like raid.

I have internal sata. If I plug in external usb drive it is normal also. I don't think fstab has anything to do with it. What's even weirder is that the OP didn't label that strange name. How did it get its name.

---

### Post by todak on 2009-10-15
I labeled the drive with its original name. There was no ill effect due to the automagic name change by the system. I was just curious as to what made it do that and what the goofy number may have meant. :confused: Oh, well. A mystery that may never be explained!:-?

---

