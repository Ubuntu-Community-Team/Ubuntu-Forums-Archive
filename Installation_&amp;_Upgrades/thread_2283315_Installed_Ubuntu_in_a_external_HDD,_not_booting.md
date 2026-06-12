---
title: "Installed Ubuntu in a external HDD, not booting"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by ivan90 on 2015-06-21
Hello, this is my first time using Ubuntu, I wanted to intall it on a external HDD so I could plug it on my win7 laptop and boot from there from time to time, I thought it would be easy but it isn't (at least for me:(), I created a live USB, booted from there, selected "other options" on install method, created a swap partition of 600 MB on my external HDD, and another partition ext4 about 45 GB, and marked it as "/" and selected that same partition for the bootloader <-(I have a feeling this is what I did horribly wrong), ubuntu installed succesfully and asked to restart the laptop. I did and when I tried to boot from the external HDD it justs stays there with a black screen, after a couple of seconds if brings me to my windows boot. Then I had the idea of creating a ubuntu entry using easyBCD and pointed to the ubuntu partition, and still cant boot from the external hdd.

I have no idea what to do, I've searched the forums and they all point to some grub repair or something like that, that i dont have a single clue what is, any help is greatly appreciated.

---

### Post by ubfan1 on 2015-06-21
Most likely, you needed to install the bootloader to the device /dev/sdb instead of the partition /dev/sdb1 (using your device letter and number).  You should be able to boot the  live media, and install grub to the device , or just reinstall using the device instead of the partition.

---

### Post by efflandt on 2015-06-21
If you installed grub to your "/" partition that only works if you have a regular DOS/Win mbr (or syslinux mbr.bin) at the beginning of the drive to initially boot and your "/" partition marked as a boot partition.

I sort of do that with my main drive because it also has Win7 and in rare cases Windows updates (one a service pack update and one more recent) can fail if not booting from a regular mbr. Win7 is using 3 partitions and I have grub on sda4 which is "/" for Ubuntu 14.04 (I have 8 GB RAM and do not hibernate, so I have no swap). I normally leave sda2 marked as boot for Windows and boot from grub the mbr of sdb (SSD) where I still have 12.04. But in a pinch I could use gparted to mark sda4 as the boot partition and switch BIOS to boot sda.

My suggestion would be to put Super GRUB2 [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) on CD or USB, use that to boot Ubuntu, and once in Ubuntu, install grub to the mbr of your external drive. This explains installing grub from a working system [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System) for example: **sudo grub-install /dev/sdb** or whatever drive your external is.

Or there is something called Boot-Repair that could likely automate that, but I have never tried that [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Although, you would want to make sure that grub ends up on your "external" drive and "NOT your internal" drive.[URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

---

### Post by ivan90 on 2015-06-21
Hello again!, thanks for yoour answers

> **ubfan1 said:**
> Most likely, you needed to install the bootloader to the device /dev/sdb instead of the partition /dev/sdb1 (using your device letter and number).  You should be able to boot the  live media, and install grub to the device , or just reinstall using the device instead of the partition.

I reinstalled Ubuntu and selected the "root" of the external hdd instead of a partition, now instead of a black screen it says file format unindentified or something like that, and goes into a " grub> " mode

> **efflandt said:**
> If you installed grub to your "/" partition that only works if you have a regular DOS/Win mbr (or syslinux mbr.bin) at the beginning of the drive to initially boot and your "/" partition marked as a boot partition.

I sort of do that with my main drive because it also has Win7 and in rare cases Windows updates (one a service pack update and one more recent) can fail if not booting from a regular mbr. Win7 is using 3 partitions and I have grub on sda4 which is "/" for Ubuntu 14.04 (I have 8 GB RAM and do not hibernate, so I have no swap). I normally leave sda2 marked as boot for Windows and boot from grub the mbr of sdb (SSD) where I still have 12.04. But in a pinch I could use gparted to mark sda4 as the boot partition and switch BIOS to boot sda.

My suggestion would be to put Super GRUB2 [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) on CD or USB, use that to boot Ubuntu, and once in Ubuntu, install grub to the mbr of your external drive. This explains installing grub from a working system [https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System) for example: **sudo grub-install /dev/sdb** or whatever drive your external is.

Or there is something called Boot-Repair that could likely automate that, but I have never tried that [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
Although, you would want to make sure that grub ends up on your "external" drive and "NOT your internal" drive.[URL="https://help.ubuntu.com/community/Boot-Repair"]
[/URL]

I tried using the boot-repair and it did something but lead to the same screen with the "file format unindentified" that I mentioned above, again I tried creating an ubuntu entry using easy bcd on windows, and it boot right into this screen (file attached).

---

### Post by oldfred on 2015-06-21
That error is from grub4dos. Have you tried just booting from sdb using BIOS or perhaps one time boot key like f10 or f12 (depends on system).
Grub4dos is the very old version of grub that EasyBCD uses. If you really want to use EasyBCD you should ask on their forum as they are more knowlegeable on it.
       [https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)
            [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

But since the external drive has its own MBR, you should just be able to install grub to the MBR of sdb or whatever drive it is. Then drive should also work on other computers, if video or Internet are not issues. But booting thru EasyBCD on sda would not let you configure external drive as a stand alone drive.

Not sure I have seen file format unidentified.
From your live installer post this:
sudo parted -l

---

### Post by ivan90 on 2015-06-21
Thanks for replying, I only was using easybcd since I was running out of ideas, if it is unnecesary or using it does more damage than good i will stop using it.

Well as I said when I tried to boot from the external hdd after installing ubuntu directly from the bios and i get a screen with an error (see attachments), ubuntu detects my external hdd as sdc, and i selected that drive for installing the boot loader, and sdc2 for installing ubuntu (see attachment), I simply dont know what i did wrong or where to start checking

this is what I get when i typed "sudo parted -l"

```
 Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  316MB  315MB   primary  ntfs
 2      316MB   298GB  298GB   primary  ntfs         boot
 3      298GB   318GB  19.6GB  primary  ntfs
 4      318GB   320GB  2142MB  primary  fat32        lba


Model:  USB DISK Pro (scsi)
Disk /dev/sdb: 8007MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8007MB  8006MB  primary  fat32        boot, lba


Model: TOSHIBA External USB 3.0 (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  758GB  758GB   primary  ntfs            boot
 2      801GB   841GB  40.0GB  primary  ext4
 3      841GB   841GB  600MB   primary  linux-swap(v1)
```

---

### Post by oldfred on 2015-06-21
At grub rescue>
Can you type this:
 configfile (hd0,2)/boot/grub/grub.cfg

Boot drive from BIOS in grub is always hd0 and you have sdc2 as Linux partition.

Or this:

 set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sdc2 ro
initrd (hd0,2)/initrd.img
boot

Not sure one system loads if /dev/sda2 or sdc2? May have to try both.

 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
      Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Is this a newer system? It shows USB3 port? Some systems just do not like USB3 and need USB2 to work.

---

### Post by ivan90 on 2015-06-21
> **oldfred said:**
> At grub rescue>
Can you type this:
 configfile (hd0,2)/boot/grub/grub.cfg

Boot drive from BIOS in grub is always hd0 and you have sdc2 as Linux partition.

Or this:

 set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sdc2 ro
initrd (hd0,2)/initrd.img
boot

Not sure one system loads if /dev/sda2 or sdc2? May have to try both.

Tried both commands, my grub said unrecgonized command to many of them, i verified i did not commit a typo, re-wrote them couple of times and nada. The ones not working were the "linux(hd0,2)/vmlinuz" and the other 2 below and the configfile.
> **oldfred said:**
> See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
      Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Is this a newer system? It shows USB3 port? Some systems just do not like USB3 and need USB2 to work.
This laptop is not new, has about 3 years, i tried changing the external hdd from the usb3 port to the usb2 but nothing changed. I read both threads, and I tried using the "ls" command mentioned in the grub rescue thread, but there are no (hd1,2) discs on my pc, all are (hd, msdosX) [where x is a number from 1/4], i still tried following the steps mentioned in the thread and couldn't locate the grub folder on all the hd listed by ls.

---

### Post by ubfan1 on 2015-06-21
Spaces are critical in the commands oldfred suggested.  The partition identification should work as either just a number or msdosx, but as oldfred suggested, maybe the hd0 should be something else, like (if a=0, b=1, so c=2) hd2.   At the grub prompt, you can use a tab to try to complete the command, and in that way, see what disks are available. e.g.
ls (hd TAB   and you should get a listing of hdx s  available to complete the command.  use the last one (highest number).

---

### Post by ivan90 on 2015-06-21
Hi again, sorry but nothing worked, i included spaces in the commands and still doesn't recognized these ones"linux (hd2,2)/vmlinuz root=/dev/sdc2 ro" and "initrd (hd2,2)/initrd.img", pressing tab to complete the command didnd't worked either, it doesn't do anything at all. 
Any other suggestions? I'm just about to give up installing ubuntu:(

---

### Post by ubfan1 on 2015-06-21
All the above assumes you are at the grub command line (grub>).  If you are at a grub menu, get to the command line by typing the letter c.
If something fails are you are left at the command line, that works too.
At the grub command line, the one with the grub> prompt, you type (no quotes) "ls (hd"  and then a TAB character.  If there is only one disk, it will be filled in as 0, if more than one, the choices will be listed, and you type one in. You can keep doing this for the partition choice too, eventually you can get to a line looking like "ls (hd2,msdos2)/", then type enter to get a directory of the partition you are looking at.  You should recognize the root level of a linux installation, with directories like /boot present.  You can then use the disk and partition to boot the machine, using the commands oldfred posted.

---

### Post by oldfred on 2015-06-21
Have you tried SuperGrub as posted above. It often boots anything.

Or have you tried running Boot-Repair and just post here the link on the Summary report. Without knowing details, any autofix may make it worse.

---

### Post by ivan90 on 2015-06-22
I've used boot-repair and couldn't fix anything, the link of the summary i think is this?[http://paste.ubuntu.com/11751321/](http://paste.ubuntu.com/11751321/)

---

### Post by oldfred on 2015-06-22
Install looks normal.

Some USB installs have issues like an old BIOS boot issue where BIOS system would only boot from first 137GB or all boot files must be inside first 137GB. If that is the issue you can have a smaller / (root) partition of 25GB inside the first 137GB or create a separate /boot partition just for kernels & grub to be inside 137GB boundary.

---

### Post by ivan90 on 2015-06-23
Hello again, sorry for not answering, had some busy days. Thanks a lot oldfred, you were right, I decided to re create all the partitions in the hdd and put the ubuntu partition as the first one and it finally booted with no issues. So I think the issue was that my ubuntu partition was out of the first 137gb and my BIOS was unable to boot from there.

Thanks to everyone for the time and patience to help this newbie :)

---

