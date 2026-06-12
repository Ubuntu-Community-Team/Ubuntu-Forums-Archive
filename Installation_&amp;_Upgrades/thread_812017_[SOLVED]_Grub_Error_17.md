---
title: "[SOLVED] Grub Error 17"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by ruialexbarbosa on 2008-05-29
Hi,

this is driving me insane!!!! Ok, sorry, here it goes:

I'm using Ubuntu 7.04
I have a hdd with:

Windows partition HDA1
Fat32 documents partition HDA5
EXT3 Linux (ubuntu) HDA6
Swap HDA7

I just reinstalled Windows, and now grub gives me error 17 (can't find partition). If I choose Windows it's fine, it will just boot normaly, if I choose Ubuntu... ERROR 17, can't find partition.

I tried making a supergrub pendrive to boot, but the same happens with the pendrive (I even disabled the HDD boot in the BIOS, to make sure the pen was booting).

How can I get my system working again?

Thanks for any advice

---

### Post by Pumalite on 2008-05-29
Boot your Live CD and post:
sudo fdisk -l

---

### Post by ruialexbarbosa on 2008-05-29
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913        9733    62822182+   5  Extended
/dev/hda5            1913        7654    46122583+   b  W95 FAT32
/dev/hda6            7655        9601    15639246   83  Linux
/dev/hda7            9602        9733     1060258+  82  Linux swap / Solaris

Disk /dev/sda: 262 MB, 262144000 bytes
255 heads, 63 sectors/track, 31 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          31      248976    b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by Pumalite on 2008-05-29
Post:
cat /boot/grub/menu.lst
And a screenshot of Gparted

---

### Post by ruialexbarbosa on 2008-05-29
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 
[IMG]http://farm4.static.flickr.com/3106/2534012747_5e0f6102e5_o.png[/IMG]

---

### Post by Pumalite on 2008-05-29
Try reinstalling Grub:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ruialexbarbosa on 2008-05-29
I tried that already... Didn't work...

---

### Post by Pumalite on 2008-05-29
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by ruialexbarbosa on 2008-05-29
Quick question,

When I put grub> find /boot/grub/stage1  it shows me (hd0,5), and if I go to /boot/grub/menu.lst it shows (hd0,6).

Could this have anything to do with it?

---

### Post by Pumalite on 2008-05-29
Try it at boot. In Grub, hit F6 and change (hd0,5) to (hd06) in the boot line and see if it works. If yes; then edit your menu.lst

---

### Post by ruialexbarbosa on 2008-05-29
Yes, I changed it and it worked.

Thanks very much for your help. All fine now.

---

