---
title: "kubuntu 20.04 dual boot clean install with win10 - won't boot windows"
date: 2020-05-03
forum: Installation &amp; Upgrades
---

### Post by bugeps on 2020-05-03
1st clean install in 10 years, and I messed it up.  Had a working dual boot win10 / kubuntu 18.04 prior to installing 20.04.  The installer wouldn't let me just install it into the existing linux partition, and then failed to load grub.  I ended up reformatting what I thought was the EFI partition, which destroyed the windows boot info.  Or did it?  Looking at it now I see "Partition Table: msdos", so  I wonder if it is actually MBR with a "BIOS" that can go both ways.  Anyway, I thought I'd see if you folks know of a fix before I give up on the win10 partitions.  I use it rarely, but often enough to make it worth keeping.

After  the install it booted straight into linux.  I found a /boot/grub/custom.cfg suggestion (I don't even remember a /boot/grub directory before):
```
"Windows (UEFI)" {
    search --set=root --file /EFI/Microsoft/Boot/bootmgfw.efi
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi
    }
```
that brought grub out with a windows entry (I used to have 2 entries), but the windows entry failed with, "no such device: /EFI/Microsoft/Boot/bootmgfw.efi".

So then I had the great idea to try boot-repair!  Of course I had it write grub into both locations it suggested, because it said that was a thing to do, and I wonder now if I overwrote the MBR sector.  If it was MBR.  The pastebin  is:    [https://paste.ubuntu.com/p/gNMGRHKxx4/](https://paste.ubuntu.com/p/gNMGRHKxx4/).

It booted straight into linux again, so I ran boot-repair again, because I had seen an option to make the windows partition the first boot choice.  To see if it would force a boot attempt.  Now grub shows up with a windows selection, but of course it won't boot (silently returns to grub).  The pastebin for that one is:  [https://paste.ubuntu.com/p/fPZxRJXjwr/](https://paste.ubuntu.com/p/fPZxRJXjwr/) .  The option in boot-repair to repair the windows boot sector was not enabled.

So the questions I have are:

Is this MBR or EFI?
If MBR, is it possible that there is a working win10 MBR record that I might recover?  Perhaps via a new linux installation eliminating the EFI block?  Maybe it was a win10 restore partition, not EFI?
If EFI, is it possible to recover the windows EFI block from within linux?  There is a copy of bootmgfw.efi present in a backup location.
Or maybe /dev/sda1 is where the answer lies?  It is a System_Reserved windows primary partition that can be flagged as boot.

Some additional information:
$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-28-generic
Found initrd image: /boot/initrd.img-5.4.0-28-generic
Found linux image: /boot/vmlinuz-5.4.0-26-generic
Found initrd image: /boot/initrd.img-5.4.0-26-generic
Adding boot menu entry for UEFI Firmware Settings
done

(What's the deal with 5.4.0-28 AND 5.4.0-26, above?)

$ sudo parted -l
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  106MB   105MB   primary   ntfs
 2      106MB   506GB   506GB   primary   ntfs
 3      506GB   506GB   512MB   primary   fat32           boot, esp
 4      506GB   1000GB  494GB   extended
 5      506GB   516GB   9999MB  logical   linux-swap(v1)
 6      516GB   1000GB  484GB   logical   ext4

KDE Partition Manager:
/dev/sda1    ntfs            Primary    Not mounted      System_Reserved                       100MB  boot flag not set, can be set (enabled).
/dev/sda2    ntfs            Primary    mounted             Windows 10                                471GB  boot flag not set, cannot be set (disabled).
/dev/sda3    fat32          Primary    Not mounted      EFI created during linux install    488MB  boot flag set, can be unset (enabled).
/dev/sda4    extended                   Not mounted                                                           460GB  boot flag not set, can be set  (enabled).
/dev/sda5    linuxswap Logical     mounted "none"  linuxswap                                    9.31GB  boot flag not set, cannot be set (disabled).
/dev/sda6    ext4          Logical     mounted   "/"       kubuntu 20.04                              451GB  boot flag not set, cannot be set  (disabled).

Any insight would be appreciated.  Thanks

Paul

---

### Post by oldfred on 2020-05-03
It looks like you have Windows in BIOS boot mode and installed Ubuntu in UEFI boot mode to same drive.
That does not work.

Windows only boots from MBR partitioned drives with BIOS.
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu lets you install in UEFI mode to MBR drives, but should not. And if Windows is also on same drive it cannot work.
Windows has to have its boot flag on a primary NTFS partition with boot files. Often first or second smaller partition.
UEFI has to have boot/esp flag on the ESP - efi system partition.
You can only have one boot flag per drive. 

The girl in the white dress lives in the blue house. The boy wearing red shorts lives in the green house. Who lives in the brown house.
OOPs wrong puzzle. :)

If you only have one drive, move boot flag to sda1. Install Windows boot loader and make sure Windows fast start up is off and make a Windows repair/recovery flash drive if you do not have one.
Then use Boot-Repair from Ubuntu booted in BIOS mode to install grub to MBR of drive. Grub will offer to boot Windows, but only boots working Windows. When Windows turns fast start up back on or needs chkdsk, grub will not boot it. You then have to restore a Windows boot loader and maybe fix using f8 for internal repairs when booting. Or use repair/recovovery flash drive. And then restore grub.

Better to have two drives with Windows 8 or 10 or just use UEFI for both, but that would be a total reinstall of Windows.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by bugeps on 2020-05-04
Fixed!  Thank you!  I had done so much without thinking things through that I was down to zero confidence.  I moved the boot flag to sda1 and reran the linux installer.  I deleted sda4, 5, and 6, and made 2 new primary partitions, swap and linux root, though I just read that a swap partition isn't normally used any more, but it's all good.  I had to push through 2 or 3 pretty dire warnings about the error I was making by not having an EFI partition.  I turned on legacy only boot in BIOS, fast start up and  secure boot were already off.  It booted directly in to linux (no grub).  I ran sudo update-grub which returned:

$ sudo update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-28-generic
Found initrd image: /boot/initrd.img-5.4.0-28-generic
Found linux image: /boot/vmlinuz-5.4.0-26-generic
Found initrd image: /boot/initrd.img-5.4.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 10 on /dev/sda1
Found Windows 10 on /dev/sda2
done

Very nice.  Thank you again!
Paul

---

### Post by dragonfly41 on 2020-05-04
[COLOR=#000000]> The girl in the white dress lives in the blue house. The boy wearing red shorts lives in the green house. Who lives in the brown house.[/COLOR]
[COLOR=#000000]OOPs wrong puzzle.

These many, many discussions on dual boot problems brings to mind Danny Kaye.
[/COLOR][h=1][The Pellet with the Poison's in the Vessel with the Pestle - The Court (7/9) Movie CLIP (1956) HD]("https://www.youtube.com/watch?v=TJ9f2rnjB84")[/h]

---

