---
title: "Make BIOS boot on a specific file"
date: 2018-06-08
forum: MINT
---

### Post by tappikid on 2018-06-08
I originally had Windows 10 on my 2TB Dell desktop. I installed Linux  Mint Cinnamon 18.3 "Sylvia" as a dual boot to try it with intent to  leave Windows. I then deleted every Windows type file and went to  resizing partitions with gparted & really messed things up somewhere  & was getting error flags. I then deleted all FAT32 files and  created a new one, partitioned at the beginning from instructions that I  found through the Ubuntu sites. I am truly not computer smart and have  made lots of troubles but I see my files there, I just can't boot into  them.

So after I deleted everything except for my Linux partition and the  swap, I then created the new FAT32 with a boot, esp flags. At this  point when I open gparted and view I don't get any errors that my backup GPT  table is corrupt so that seemed good. I just couldn't boot the computer  because there was no grub. I had wiped everything and just created a  blank partition for it.

I went to Bootloader and ran that & it installed grub. Boot  repair said the "boot was successfully repaired". Then gave me this URL  and said in case of problems indicate this URL:     [http://paste.ubuntu.com/p/qGgHCCnZrz/](http://paste.ubuntu.com/p/qGgHCCnZrz/)

There is a problem: I cannot boot the computer (except with my bootable USB) because I get a secure boot violation saying "invalid signature detected"

sudo efiboot mgr -v  shows:
0000 =ubuntu
0001 =USB


When I run  fdisk -l  in terminal, this is what shows:

isk /dev/loop0: 1.7 GiB, 1842749440 bytes, 3599120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 01619F1D-3F44-47DA-AFE4-A1DC9606DB7C

Device          Start        End    Sectors   Size Type
/dev/sda1      204800    8028159    7823360   3.7G EFI System
/dev/sda2  2444566528 2648481791  203915264  97.2G Linux filesystem
/dev/sda5     8028160 2444565570 2436537411   1.1T Linux filesystem
/dev/sda10 3903954944 3907026943    3072000   1.5G Linux swap
/dev/sda11 2648481792 3903954943 1255473152 598.7G Linux filesystem

Partition table entries are not in disk order.

Disk /dev/sdb: 14.9 GiB, 16004415488 bytes, 31258624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0cc3de76

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31258623 31256576 14.9G  c W95 FAT32 (LBA)

As I said, I can only boot with my bootable USB stick.

Boot repair said "make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file.

I do not know how to make the BIOS boot on that file. I need specific steps and I can do it but I do need specific steps.

When I boot I get 
"Secure Boot Violation" 
Invalid signature detected. Check secure boot policy in setup.

Thank you for any help!

---

### Post by Autodave on 2018-06-09
Hopefully, someone else will give you more help than I will. But, if it were my machine, I would copy everything off of it that I needed and then do a clean install. At the install screen, I would choose :Erase entire disk and install".  (This assuming that you do not want Windows on there any longer.

---

### Post by oldfred on 2018-06-09
Moved to Mint sub-forum.

In UEFI, turn off UEFI Secure Boot.
On my system it is "Windows" or "Other" and fine print says if booting Windows 7 in UEFI mode you must use Other as Windows 7 does not support UEFI Secure Boot.

---

