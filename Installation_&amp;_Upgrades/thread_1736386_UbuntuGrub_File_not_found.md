---
title: "Ubuntu/Grub File not found"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by justnew on 2011-04-22
Hi
I need personal help (google couldn't help me).
I just installed Backtrack on a second partition. My Ubuntu 10.10 worked fine, but after Backtrack installed its own version of Grub I get the error "File not found".
In my opinion the needed files exist.
menu.lst
```

# Backtrack's entrys
splashimage=7f21e144-0b81-498d-9283-4babb5c508b6/boot/grub/splash.xpm.gz

title        BackTrack 4 R2, kernel 2.6.35.8
uuid        7f21e144-0b81-498d-9283-4babb5c508b6
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=7f21e144-0b81-498d-9283-4babb5c508b6 ro quiet splash 
initrd        /boot/initrd.img-2.6.35.8
quiet

title        BackTrack 4 R2, kernel 2.6.35.8 (recovery mode)
uuid        7f21e144-0b81-498d-9283-4babb5c508b6
kernel        /boot/vmlinuz-2.6.35.8 root=UUID=7f21e144-0b81-498d-9283-4babb5c508b6 ro  single
initrd        /boot/initrd.img-2.6.35.8

title        BackTrack 4 R2, memtest86+
uuid        7f21e144-0b81-498d-9283-4babb5c508b6
kernel        /boot/memtest86+.bin
quiet

# old entry's (Ubuntu)
# linux installation on /dev/sda1.
title        'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os { (on /dev/sda1)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.35-28-generic root=UUID=f9ff90b1-4f04-4737-b1c7-9c66bf928513 ro quiet splash 
initrd        /boot/initrd.img-2.6.35-28-generic
savedefault
boot
```I checked and the 2 files are in /boot on sda1.
fdisk -l:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009f4b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25327   203438103+  83  Linux
/dev/sda2           25543       38914   107404703    5  Extended
/dev/sda3           25328       25542     1726987+  83  Linux
/dev/sda5           37485       38914    11474944   82  Linux swap / Solaris
/dev/sda6           25543       36993    91980094+  83  Linux
/dev/sda7           36994       37484     3943926   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4051 MB, 4051697664 bytes
125 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1021     3956344    c  W95 FAT32 (LBA)
```
And ls 
```
root@bt:/media/disk/boot# ls
System.map-2.6.35-22-generic  initrd.img-2.6.35-28-generic
System.map-2.6.35-28-generic  memtest86+.bin
abi-2.6.35-22-generic         memtest86+_multiboot.bin
abi-2.6.35-28-generic         vmcoreinfo-2.6.35-22-generic
config-2.6.35-22-generic      vmcoreinfo-2.6.35-28-generic
config-2.6.35-28-generic      vmlinuz-2.6.35-22-generic
grub                          vmlinuz-2.6.35-28-generic
initrd.img-2.6.35-22-generic
```
I hope you can help me and if there are any other informations needed just say it.

PS: If it's the wrong section pls excuse me and move it.

---

### Post by oldfred on 2011-04-22
Is Ubuntu on a ext4 partition. Backtrack's grub legacy may not work with ext4. Ubuntu updated its grub legacy with 9.04 to be able to use ext4. grub 0.97 has not be maintained for years and each distribution tweaks it.

I would just reinstall grub2 for Ubuntu.

Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)

 #Comments are anything after the #, enter commands in terminal session not sure if it would work from Backtrack boot or not.
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

