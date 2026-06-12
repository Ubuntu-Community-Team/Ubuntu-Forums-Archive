---
title: "Dual Booting issue"
date: 2020-07-18
forum: Installation &amp; Upgrades
---

### Post by elvic on 2020-07-18
I have windows 10 on one operating system on one SSD and I have Ubuntu 20.04 on another SSD. I dont plan to keep this SSD drive with Ubuntu in this PC so I would like to give it its own bootloader. When I hit F9 to load boot devices i have UEFI option for windows boot manager but I dont see grub. Legacy options I see the Windows SSD and the Ubuntu SSD but when I load the Ubuntu it takes me to the GRUB terminal. The command "boot" says "must load kernel first". Using Boot-Repair on a live USB doesn't really help it freezes up on one part.

I'm on a live USB now. 

~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0   1.9G  1 loop /rofs
loop1    7:1    0  27.1M  1 loop /snap/snapd/7264
loop2    7:2    0    55M  1 loop /snap/core18/1705
loop3    7:3    0 240.8M  1 loop /snap/gnome-3-34-1804/24
loop4    7:4    0  62.1M  1 loop /snap/gtk-common-themes/1506
loop5    7:5    0  49.8M  1 loop /snap/snap-store/433
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0    16M  0 part 
&#9500;&#9472;sda2   8:2    0 223.1G  0 part 
&#9492;&#9472;sda3   8:3    0   500M  0 part 
sdb      8:16   0 111.8G  0 disk 
&#9500;&#9472;sdb1   8:17   0   512M  0 part 
&#9500;&#9472;sdb2   8:18   0     1M  0 part 
&#9500;&#9472;sdb3   8:19   0   513M  0 part 
&#9492;&#9472;sdb4   8:20   0 110.8G  0 part 
sdc      8:32   1 115.4G  0 disk 
&#9492;&#9472;sdc1   8:33   1 115.4G  0 part /cdrom
ubuntu@ubuntu:~$ 


Windows is on /dev/sda
Ubuntu is on /dev/sdb
Live USB is on /dev/sdc


~$ sudo file -s /dev/sdb
/dev/sdb: DOS/MBR boot sector; partition 1 : ID=0xee, start-CHS (0x0,0,2), end-CHS (0x3ff,255,63), startsector 1, 234441647 sectors, extended partition table (last)



Going into GParted I have these partitions:

/dev/sdb1 EFI SYSTEM PARTITION fat32 512.mb 35.61mb(USED) 476.39(UNUSED) boot,esp
/dev/sdb2(!) ext5 1.00MiB --   -----   bios_grub
/dev/sdb3 FAT32 513.mib 1.04mb(USED) 511.96mb (UNUSED) msftdata
/dev/sdb4 ext4 110.79gb 8.90gb(USED) 101.89gb(UNUSED)


During the Windows Installation I'm assuming it installed its Boot Loader on /dev/sdb3 which I am not afraid to remove. Windows bootloader works fine and that SSD will stay on this PC.

I'm trying to have 2 functioning bootloaders that work independent of each other with Windows working first and Ubuntu loading if I hit the f9 option and choose which device to boot. I've been at it for about 4 days now so any help is appreciated.

---

### Post by elvic on 2020-07-18
[https://paste.ubuntu.com/p/3KkDZJTtGx/](https://paste.ubuntu.com/p/3KkDZJTtGx/)



this is the BootInfo Summary for Boot-Repair

---

### Post by oldfred on 2020-07-18
It looks like you do have an ESP on the Ubuntu drive & the UEFI boot entry is using that.

```
&#9492;&#9472;sda3 vfat     4270-FB42                            [COLOR=#ff0000]248ccb94-00ca-463a-bb63-a52f2cfbd891 [/COLOR]            EFI system partition
sdb                                                                                                   
&#9500;&#9472;sdb1 vfat     7C8B-2D15                            [COLOR=#0000ff]45eb6bdd-eae1-44a7-b608-893664bc401f [/COLOR]            EFI System Partition

Line 101 UEFI entries which use GUID/PARTUUID
Boot0000* ubuntu    HD(1,GPT,[COLOR=#0000ff]45eb6bdd-eae1-44a7-b608-893664bc401[/COLOR]f,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* USB Floppy/CD    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0500000001)..BO
Boot0002* USB Hard Drive    VenMedia(b6fef66f-1495-4584-a836-3492d1984a8d,0200000001)..BO
Boot0003* Windows Boot Manager    HD(3,GPT,[COLOR=#ff0000]248ccb94-00ca-463a-bb63-a52f2cfbd891[/COLOR],0x1be23800,0xfa000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS

```

Most users do have both Windows & Ubuntu/grub's boot files in one ESP. But you have them separate.
But you also show old BIOS boot loaders in MBR which are invalid and will never work.  Just never try to boot in BIOS/Legacy/CSM boot mode.

---

