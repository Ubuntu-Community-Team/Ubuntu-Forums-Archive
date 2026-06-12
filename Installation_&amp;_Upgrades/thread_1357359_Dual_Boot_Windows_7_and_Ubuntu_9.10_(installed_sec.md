---
title: "Dual Boot Windows 7 and Ubuntu 9.10 (installed second)"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by zuperzz on 2009-12-17
Hey all,

I recently decided to dual boot Ubuntu 9.10 on my laptop (currently running Windows 7). When I run the installation I get as far as the "Prepare disk space" page where I am told that my computer is not currently running an OS. I know I do because when I take out the live disk I boot back into Windows 7. 

I would like to be able to dual boot but it seems the Ubuntu installation is not seeing the Windows 7 OS and therefore preventing me from installing them side by side. I ran *sudo fdisk -l* and pasted what I got below. 

I'd appreciate any help I could get. Thanks!


[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x475d475c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30402   244093952    7  HPFS/NTFS

Disk /dev/sdb: 400.1 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0f24f2d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801    c  W95 FAT32 (LBA)[/I]

---

### Post by darkod on 2009-12-17
The screenshot is showing /dev/sdb which does not have the win7. You are right, the message says "on this computer", not "on this disk" but I'm not sure. You can see under the Erase disk option in gray it ways win7 loader will be deleted if used /dev/sda.
First of all, where do you want to install? On /dev/sda next to win7?
Second, if not running raid, you can try while under the LiveCD in terminal:
sudo apt-get remove dmraid

Reboot and check if it will see the drives better this time.

---

### Post by zuperzz on 2009-12-17
Ahhh.... I realized my mistake. There was an external HHD attached to the comp via USB that I did not spot. 

But I have once again run into issues. I would like to install Ubuntu 9.10 side by side (dual boot) with Windows 7, and would like to partition Windows to have approx 185gb and Ubuntu to have approx 45 gb.

How exactly do I go about doing this?

---

### Post by unmole on 2009-12-17
Strange.
 This might not be the best way but you could tru wubi, giving ubuntu 45 GB

---

### Post by ottosykora on 2009-12-17
then tick specialy advanced and from there you can set 'by hand' what space you want allocate.

---

### Post by darkod on 2009-12-17
> **zuperzz said:**
> Ahhh.... I realized my mistake. There was an external HHD attached to the comp via USB that I did not spot. 

But I have once again run into issues. I would like to install Ubuntu 9.10 side by side (dual boot) with Windows 7, and would like to partition Windows to have approx 185gb and Ubuntu to have approx 45 gb.

How exactly do I go about doing this?

On this same screenshot I think you can use the divider in the bottom line to adjust how much room is left for win7 and how much ubuntu will take. Just slide the divider left/right.
You see, the top line is showing you the disk as it is, the bottom line as what it will be after. You're at the right place, just drag left/right to adjust the sizes of the OSs the way you like it.
And I don't personally recommend using wubi. It seems easier to install but that is not full ubuntu and it's working inside windows, on ntfs partition. Not the way you want to use linux.

---

### Post by alberto.ceccherini on 2009-12-19
hi were you successfull in installing 9.10 dual boot with windows7... i'm just a bit afraid to do it on my new Vaio laptop. Just waiting some feedbacks.
I tested yesterday with 9.04 live CD and when I tried to see the partition tool it was saying that there was windows vista installed instead of 7...
I would try but sony laptop come without a window cd ... just recovery disks..
Thanks

---

### Post by OrangeCrate on 2009-12-19
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by darkod on 2009-12-19
> **alberto.ceccherini said:**
> hi were you successfull in installing 9.10 dual boot with windows7... i'm just a bit afraid to do it on my new Vaio laptop. Just waiting some feedbacks.
I tested yesterday with 9.04 live CD and when I tried to see the partition tool it was saying that there was windows vista installed instead of 7...
I would try but sony laptop come without a window cd ... just recovery disks..
Thanks

I'm dual booting 9.10 and win7 on both my netbook and desktop. They work fine. I don't know what feedback exactly are you waiting for. Of course, sometimes unpredictable things happen, or when someone has "strange" setup of the partitions, etc. In general, Ubuntu 9.10 is working fine in dual boot with Win7.
As for showing Vista instead of 7, don't worry about that. The boot process for both is similar if not the same so sometimes it can be "reported" wrongly. The main thing is that your windows was discovered as existing.

---

### Post by alberto.ceccherini on 2009-12-21
Thanks, I'll do it, but just to be shure i'll be able to come back i think i will first make a new partition (where i want to install ubuntu) and make a new backup disk :-)
Alberto

---

### Post by darkod on 2009-12-21
> **alberto.ceccherini said:**
> Thanks, I'll do it, but just to be shure i'll be able to come back i think i will first make a new partition (where i want to install ubuntu) and make a new backup disk :-)
Alberto

Be careful when creating a partition first. Linux considers all existing partitions as unavailable. You would have to manually point ubuntu to use it. It's much complicated that way, and you can easily make a mistake. Don't blame ubuntu later.
You need to have UNALLOCATED space, not belonging to any partition, that's best. Or if you are doing the windows resize with the same step, just use the slider to split your drive between windows and ubuntu and that's it.

---

