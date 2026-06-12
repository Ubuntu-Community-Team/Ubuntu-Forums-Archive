---
title: "Dual Boot FreeBSD 12 and Ubuntu 18"
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by apatel415 on 2019-03-04
Laptop: ASUS ZenBook UX303UB

Trying to dual boot my laptop between FreeBSD 12 & Ubuntu 18. Deleted original EFI partition which came with WIN 10 and partitioned as such:
```

# parted /dev/sda print
Model: ATA HFS512G32MND-321 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  200MB   199MB   fat32           EFI System Partition  boot, esp
 2      200MB   25.2GB  25.0GB  linux-swap(v1)
 3      25.2GB  179GB   154GB   btrfs
 4      179GB   281GB   102GB                   FreeBSD
 5      281GB   512GB   231GB
```

Installed Ubuntu specifing sda1 for EFI, sda2 (swap), sda3 (/). sda5 unused as of now. Mount points as such:
```

# cat /etc/fstab | grep -v "#"
UUID=66f41fc0-c825-42ab-bfbf-7ef504399248 /               btrfs   defaults,subvol=@ 0       1
UUID=66f41fc0-c825-42ab-bfbf-7ef504399248 /home           btrfs   defaults,subvol=@home 0       2
UUID=6973a1b7-1777-40d7-81a1-1a7d49ff52c4 none            swap    sw              0       0
UUID=65B4-6DC3    /boot/efi    vfat    defaults    0    1
```

Ubuntu boots fine, then boot FreeBSD 12 and install on sda2 using default UFS disk option. Intall goes smoothly, no errors. Following this guide [https://wiki.freebsd.org/Laptops/Lenovo_Yoga_3_14/DualBoot](https://wiki.freebsd.org/Laptops/Lenovo_Yoga_3_14/DualBoot) - add following grub entry.
```

# cat /boot/grub/custom.cfg 
set default="3"
set timeout=5
set timeout_style=menu

menuentry "FreeBSD" {
insmod part_gpt
insmod fat
insmod chain
set root=(hd0,gpt4)
chainloader /EFI/BOOT/bootx64.efi
}
```

Reboot and select FreeBSD option and get error:

error: file "/EFI/BOOT/bootx64.efi" not found.

File is there:
```
# ls -latrR /boot/efi
/boot/efi:
total 1
drwxr-xr-x 3 root root 512 Dec 31  1969 .
drwxr-xr-x 4 root root 512 Feb 21 23:38 EFI
drwxr-xr-x 1 root root 328 Feb 21 23:41 ..

/boot/efi/EFI:
total 2
drwxr-xr-x 3 root root 512 Dec 31  1969 ..
drwxr-xr-x 4 root root 512 Feb 21 23:38 .
drwxr-xr-x 3 root root 512 Feb 21 23:38 ubuntu
drwxr-xr-x 2 root root 512 Feb 22 16:54 BOOT

/boot/efi/EFI/ubuntu:
total 3707
-rwxr-xr-x 1 root root   71400 Feb 21 23:37 fwupx64.efi
drwxr-xr-x 2 root root     512 Feb 21 23:37 fw
drwxr-xr-x 4 root root     512 Feb 21 23:38 ..
drwxr-xr-x 3 root root     512 Feb 21 23:38 .
-rwxr-xr-x 1 root root 1334816 Feb 22 16:54 shimx64.efi
-rwxr-xr-x 1 root root 1269496 Feb 22 16:54 mmx64.efi
-rwxr-xr-x 1 root root 1116024 Feb 22 16:54 grubx64.efi
-rwxr-xr-x 1 root root     128 Feb 22 16:54 grub.cfg
-rwxr-xr-x 1 root root     108 Feb 22 16:54 BOOTX64.CSV

/boot/efi/EFI/ubuntu/fw:
total 1
drwxr-xr-x 2 root root 512 Feb 21 23:37 .
drwxr-xr-x 3 root root 512 Feb 21 23:38 ..

/boot/efi/EFI/BOOT:
total 3794
drwxr-xr-x 4 root root     512 Feb 21 23:38 ..
-rwxr-xr-x 1 root root 1334816 Feb 22 16:54 bkpbootx64.efi
drwxr-xr-x 2 root root     512 Feb 22 16:54 .
-rwxr-xr-x 1 root root 1213032 Feb 22 16:54 fbx64.efi
-rwxr-xr-x 1 root root 1334816 Feb 22 16:54 bootx64.efi

```
Additional info:```


# efibootmgr -v
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,0003
Boot0000* Freebsd    HD(4,GPT,b415be0f-c332-47d8-ba7d-78e525c92fe4,0x14d0e000,0xbebc000)/File(\efi\boot\bootx64.efi)
Boot0003* ubuntu    HD(1,GPT,0a2f6dca-9f3a-49ca-bbff-75c2cc87ced2,0x800,0x5f000)/File(\EFI\UBUNTU\SHIMX64.EFI)
```

FreeBSD entry added with following command. Ubuntu create during install 
```
# efibootmgr -c -d /dev/sda -p 4 -L "Freebsd" -l "\efi\boot\bootx64.efi"
```

CSM and Fast Boot are disabled in BIOS. Although I tried enabling after and had same results. 

Thanks in advance for help.

---

