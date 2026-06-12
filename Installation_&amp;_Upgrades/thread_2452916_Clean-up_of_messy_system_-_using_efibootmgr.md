---
title: "Clean-up of messy system - using efibootmgr"
date: 2020-10-30
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-10-30
I need to do these** tasks** :

1. verify location of OS  - such as /dev/sdxy 
2. delete unwanted OS
3. identify which "ubuntu" is currently in use 


I am using  efibootmgr and I can identify each "ubuntu" device. 

[B]Question to the forum: 
Is there way to accomplish the above tasks using just efibootmgr?  [/B]

Please note 

I still do not know what  is correct name / terminology of "ubuntu" label as used in efibootmgr.
I do not know how to locate such "ubuntu" 0 hence this post.
I do not want to disable "ubuntu"  using efibootmgr "just because"  I can - I do not want to risk unbootasble system.
Since efibootmgr source is UEFI firmware setup I can option that, prior to actual boot process- I can reshuffle UEFI boot sequence
or directly select specific "ubuntu".

Here is a snippet of my efibootmrg output: 


```

  	 	 	 	   [h=1]f@f-SATA:~$ efibootmgr -v[/h] BootCurrent: 0000
 Timeout: 3 seconds
 BootOrder: 0000,000C,000D,0002,000E,000F,0010,0011,0012,0013,0014,0015,0016,0017,0018
 Boot0000* ubuntu	HD(1,GPT,4f929080-5b02-4d52-a717-efffff17ed13,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
 Boot0002* Hard Drive 	BBS(HD,,0x0)..GO..NO........u.W.D.C. 

 Boot000C* ubuntu	HD(1,GPT,db6b86b5-a4cc-4395-a80a-f2a4e652586a,0x800,0x100000)/File(\EFI\ubuntu\grubx64.efi)..BO
 Boot000D* ubuntu	HD(2,GPT,44c98307-eb14-4cd8-ab7e-3138193729a1,0x100800,0x100800)/File(\EFI\ubuntu\grubx64.efi)..BO
 Boot000E* UEFI: Seagate	PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/USB(4,0)/HD(1,MBR,0x4294967229,0x3f,0x33dccfc1)..BO
 Boot000F* UEFI: Seagate	PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/USB(4,0)/HD(2,MBR,0x4294967229,0x3605f800,0xf5aec000)/HD(1,MBR,0x0,0x36060000,0x4e2f800)..BO
   .......


```

---

### Post by oldfred on 2020-10-30
You are showing 3 different ESP's as you have different GUIDs/partUUIDs.
You go from ESP, to grub entry in ESP, to grub in your install.
Your efibootmgr only shows which ESP is used.

The UEFI boot entry will tell you which ESP you are loading grub/Ubuntu boot files.
But then in ESP is  a tiny 3 line grub.cfg with configfile to full grub.cfg in your install.

compare your detailed efibootmgr output showing GUID/partUUID with partUUIDs of your ESP partitions.
lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint,partuuid
The mounted ESP will be the one you have booted with.
[/code]

```
[FONT=monospace][COLOR=#000000]BootCurrent: 0002 [/COLOR]
Timeout: 1 seconds 
BootOrder: 0002,0005,0019,0018,001A,001B,0010,0016 
Boot0002* focal HD(1,GPT,[COLOR=#ff0000]c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1[/COLOR],0x800,0x100000)/File(\EFI\FOCAL\SHIMX64.EFI)
[/FONT]
```

To see entry in ESP. Or mount other FAT32 partition and look at /EFI/ubuntu/grub.cfg to see UUID of install.
```
[FONT=monospace][COLOR=#54ff54]**fred@z170-focal-k**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo cat /boot/efi/EFI/ubuntu/grub.cfg [/COLOR]
[sudo] password for fred:  
search.fs_uuid [COLOR=#0000ff]54029c4f-0cbe-413e-80ce-78a4995b0551[/COLOR] root  
set prefix=($root)'/boot/grub' 
configfile $prefix/grub.cfg

```[FONT=monospace][COLOR=#54ff54][/COLOR][/FONT]

[/FONT]

```

fred@z170-focal-k:~$ lsblk -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid
NAME        FSTYPE   SIZE FSUSED LABEL     PARTLABEL            MOUNTPOINT UUID                                 PARTUUID
sda                931.5G                                                                                       
&#9500;&#9472;sda1      vfat   510.2M        ESP_B     EFI System Partition            F496-1330                            e58602b1-8fc4-46d1-991f-1d6511d9cdf4
nvme0n1            465.8G                                                                                       
&#9500;&#9472;nvme0n1p1 vfat     512M  11.9M ESP_NVME  esp_nvme             /boot/efi  [COLOR=#ff8c00]4954-C122[/COLOR]                            [COLOR=#ff0000]c90a60b4-dbf4-4ab4-af2c-e2c7c03eeed1[/COLOR]
&#9500;&#9472;nvme0n1p2 ext4    29.3G        focal_0   focal_0                         b913e1bc-6f08-4984-b653-9a604d95470a 043d0f2a-48f1-4bcd-8d8b-df02a242436c
&#9500;&#9472;nvme0n1p3 ext4    29.3G  11.1G focal_k   focal_k              /          [COLOR=#0000ff]54029c4f-0cbe-413e-80ce-78a4995b0551 [/COLOR]c4d96c9e-eebb-43e6-b1b0-7ece2306cfee
&#9492;&#9472;nvme0n1p5 ext4   195.3G 124.9G nvme_data nvme_data            /mnt/data  1a44f4af-6780-4bbd-ad0b-6385ed30830b dfd49ef3-46a6-4cad-8f64-7b1696fba6fb

```

Your fstab also has mount of ESP - efi system partition for reinstall or major update of grub.

```
[FONT=monospace][COLOR=#000000]# /boot/efi was on /dev/nvme0n1p1 during installation [/COLOR]
UUID=[COLOR=#ff8c00]4954-C122[/COLOR]  /boot/efi       vfat    umask=0077      0       1
[/FONT]
```

---

### Post by helen314 on 2020-10-30
I am getting the following error

f@f-SATA:~$ lsblk -o name,fstype,size,fsused
lsblk: unknown column: fsused
f@f-SATA:~$

---

### Post by helen314 on 2020-10-30
Fixed , just minor hiccup.

YES, I had to read the manual for "-options"  list. 
Thanks for the hint. 

Getting closer to my goal with your help.
Appreciate that very much .

CODE]
f@f-SATA:~$ lsblk -o label,NAME,FSTYPE,MOUNTPOINT,PARTTYPE /dev/sdc
LABEL         NAME   FSTYPE            MOUNTPOINT PARTTYPE
              sdc                                 
              &#9500;&#9472;sdc2 ext4                         0fc63daf-8483-4772-8e79-3d69d8477de4
              &#9500;&#9472;sdc7 ext4                         0fc63daf-8483-4772-8e79-3d69d8477de4
              &#9500;&#9472;sdc5 ext4                         0fc63daf-8483-4772-8e79-3d69d8477de4
              &#9500;&#9472;sdc3 swap              [SWAP]     0657fd6d-a4ab-43c4-84e5-0933c84b4f4f
              &#9500;&#9472;sdc1 vfat              /boot/efi  c12a7328-f81f-11d2-ba4b-00a0c93ec93b
              &#9500;&#9472;sdc8 ext4              /          0fc63daf-8483-4772-8e79-3d69d8477de4
              &#9500;&#9472;sdc6 ext4                         0fc63daf-8483-4772-8e79-3d69d8477de4
jim-desktop:0 &#9492;&#9472;sdc4 linux_raid_member            a19d880f-05fc-4d3b-a006-743f0f84911e
f@f-SATA:~$ 
[/CODE]

PS 
Looks as one cannot get away from UUID. 
Hint to real software hackers - build  a SIMPLE "tool tip" app to convent UUID to name -  if it is assigned. 
Or maybe somebody already made it ?

---

### Post by oldfred on 2020-10-30
I use labels with grub to boot other installs.
Have not changed mount of my data partition.

Shows UUID & label for mounting. Do not use device like /dev/sdXY. Older but fstab has not changed.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Set Labels for external devices gparted, Disk Utility or command line
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)
[http://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus](http://askubuntu.com/questions/147319/how-can-i-give-other-drives-and-partitions-short-meaningful-names-in-nautilus)

Use label to boot with grub
[https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359](https://askubuntu.com/questions/344125/how-to-add-a-grub2-menu-entry-for-booting-installed-ubuntu-on-a-usb-drive/344359#344359)

---

