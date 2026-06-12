---
title: "Uefi dual-boot"
date: 2012-11-18
forum: Installation &amp; Upgrades
---

### Post by Ubunteras on 2012-11-18
Hello,

@mods: I m actually facing the same problem. Can I post here or should I open a new thread?

@PrinceOfJudah: boot info script is integrated in rescatux. You can put rescatux very easily in yumi. I just used it to create a log and it s really very informative. Unfortunately I don't know how to use the information...

---

### Post by YannBuntu on 2012-11-18
Hello
> **Ubunteras said:**
> @mods: I m actually facing the same problem. Can I post here or should I open a new thread?

Boot problems are generally unique. Please open a new thread, and indicate a link to it here.

---

### Post by Ubunteras on 2012-11-18
I burned ubuntu-secure-remix-12.10-64bits.iso on a DVD (couldn't get it on USB with YUMI) and then run boot repair disk. I just followed the instructions and it worked! I am able to boot both W8 and Ubuntu 12.10 on EFI mode. The only problem is, Grub2 is running before Windows bootloader and now I have 2 boot menus. So, my problem is almost solved.

---

### Post by coffeecat on 2012-11-18
> **Ubunteras said:**
> 
@mods: I m actually facing the same problem. Can I post here or should I open a new thread?

Please create your own threads. It is difficult to help someone when others chime in with issues that may or may not be relevant. I've moved both your posts and Yannbuntu's response to you into their own thread.

---

### Post by Ubunteras on 2012-11-23
Hello again,

As I stated before, I can now boot ubuntu 12.10 and W8 in UEFI without problem. But I still have 2 small issues:

1) The main bootloader is now Grub2. In its boot menu there is the option for windows. When I click there it jumps to the menu of the windows bootloader and then I can choose windows to boot. Can grub2 boot directly W8 without going through to the second menu and how can I configure it?

2) Following the instructions in a thread I ve created in addition to the swap and the root partition,  2 more partitions which were supposed to be needed for grub2 - one ext2 1 GB and one FAT32 250 MB. Do I need these 2 partitions? Has grub2 any files in these 2 partitions or can I remove them?

---

### Post by oldfred on 2012-11-23
When you just booted Windows with UEFI did you always have to go to efi menu to boot Windows? I think grub is just chain loading to the Windows efi entry, so it should be the same?

What partitions did you create? UEFI installs need a FAT32 efi partition, but if dual booting with Windows you use the one that already exists as you can only have one efi partition and it should be first on drive (Windows may have it second).

If using gpt and the old BIOS boot, grub needs a bios_grub partition, but that is not used with UEFI boot.

Post this:
sudo parted /dev/sda unit s print

---

### Post by Ubunteras on 2012-11-23
> When you just booted Windows with UEFI did you always have to go to efi menu to boot Windows? I think grub is just chain loading to the Windows efi entry, so it should be the same?

No, directly. But during the install of ubuntu I ve choosen the bootloader to be placed in the ext2 partition. Then I couldn't boot ubuntu and I ve noticed that the EFI menu of windows was appearing shortly and dissapearing. Very weird...

> What partitions did you create? UEFI installs need a FAT32 efi partition, but if dual booting with Windows you use the one that already exists as you can only have one efi partition and it should be first on drive (Windows may have it second).

Like I said I ve created alltogether 4 partitions. 1st fat32, 2nd ext2, 3rd root, 4th swap. So there was already a fat32 partition and I created another, which I placed before the ext2 and the root partition. The "boot repair disk" apparently repaired the first fat32 partition. That means I don't need the second fat32 partition. But what about the ext2 1 GB? Do I need it?


> Post this:
sudo parted /dev/sda unit s print

nick@ThinkPad-Edge-E530:~$ sudo parted /dev/sda unit s print
[sudo] password for nick: 
Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 500118192s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start       End         Size        File system     Name  Flags
 1      34s         262177s     262144s                           msftres
 2      264192s     2312191s    2048000s    ntfs                  diag
 3      2312192s    2844671s    532480s     fat32                 boot
 4      2844672s    254398463s  251553792s  ntfs
 6      254398464s  401199103s  146800640s  ntfs
 7      401199104s  401301503s  102400s     fat32                 bios_grub
 9      401301504s  403398655s  2097152s    ext2                  boot
10      403398656s  450603007s  47204352s   ext4
 8      450603008s  467380223s  16777216s   linux-swap(v1)
 5      467380224s  500117503s  32737280s   ntfs                  diag

---

### Post by oldfred on 2012-11-23
I think you can delete both of these.

7      401199104s  401301503s  102400s     fat32                 bios_grub
 9      401301504s  403398655s  2097152s    ext2                  boot

They are wrong anyway. bios-grub cannot be formated, and a boot flagged partition cannot be ext2 in UEFI. Even in BIOS you can only have one boot partition per drive, so I think that boot flag may confuse system.

       In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

---

### Post by Ubunteras on 2012-11-23
many thanks!!! I ll delete both of them...

---

