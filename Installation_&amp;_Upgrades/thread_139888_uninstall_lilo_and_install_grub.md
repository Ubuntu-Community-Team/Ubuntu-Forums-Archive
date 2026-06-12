---
title: "uninstall lilo and install grub"
date: 2006-03-05
forum: Installation &amp; Upgrades
---

### Post by SVFUSiON on 2006-03-05
Is there a way to uninstall lilo and install GRUB using the livecd. I have messed my lilo up trying to add windows vista. Lilo only boots to windows vista without asking me or anything. I really don't even like Lilo, I think it is crap :p .

---

### Post by Xian on 2006-03-05
Can you not chroot into the Ubuntu install from the LiveCD and issue the proper apt-get commands??

---

### Post by SVFUSiON on 2006-03-05
i am not real sure what chroot is and I don't know what apt-get commands they would be. sudo apt-get remove lilo?

---

### Post by Xian on 2006-03-05
Mount your Ubuntu installation from the LiveCD, then chroot to that partition as su. This will allow you to act as the admin, use apt to install and remove the needed applications, and make the required configurations.

Installing grub is much easier if you have the InstallCD.
If you do then [read here](http://www.ubuntuforums.org/showthread.php?t=24113).

# chroot /path/to/ubuntu /bin/bash
# mount /proc
# apt-get remove lilo
# apt-get install grub

Then you'll need to install grub to the MBR.
# grub-install /dev/<your_partition_name>

And set up your grub config at /boot/grub/menu.lst.
# gedit /boot/grub/menu.lst

---

### Post by SVFUSiON on 2006-03-05
doing the method of the installcd,

4. Mount your appropriate linux partions

Where do you go to mount? I think I am overlooking? :-k

---

### Post by Xian on 2006-03-05
[QUOTE=SVFUSiON]Where do you go to mount? I think I am overlooking? :-k[/QUOTE]

It's all in the manual partitioning section.
You use that module to set your mount points.

Highlight the partition and choose then a new screen will appear.
There should be a mount point (or similar) option you can select.

But as mentioned don't format them....

---

### Post by SVFUSiON on 2006-03-05
here is my problem now, I reinstalled Ubuntu, I hit the "Install GRUB" it installed to the "MBR" or whatever the default is. For some reason, it is still booting to lilo, and I can not even get back to vista. here is my partition tables

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/hdc1 * 1 30402 244204033+ 7 HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
Windows Vista is Install here/dev/hdd1 3 79889 40262656 7 HPFS/NTFS
Partition 1 does not end on cylinder boundary.
Ubuntu is here /dev/hdd2 * 79895 151933 36306900 83 Linux
Partition 2 does not end on cylinder boundary.
/dev/hdd3 151933 155056 1574370 5 Extended
Partition 3 does not end on cylinder boundary.
/dev/hdd5 151933 155056 1574338+ 82 Linux swap / Solaris

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 4499 36138186 7 HPFS/NTFS

At this point i have no idea what is going on,
I can't even find lilo anymore, where is it? where did grub go? How can I get my to normal lol. I use Ubuntu as a main OS but I still need vista to report bugs.

---

### Post by SVFUSiON on 2006-03-06
anyone know what i need to do? If I try apt-get install grub from the live cd it ask me to put it some other cd.

---

