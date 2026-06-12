---
title: "Ubuntu 14.04 boot hangs after CUPS loads OK"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by bradsturtevant on 2014-04-23
During boot process the last messages before hang are:
...
keys:
  * Starting Signal sysvinit that the rootfs is mounted          [ok]
...
  * Starting CUPS printing spooler / server                      [ok]
  * Starting cups-browsed Bonjour remote printer browsing daemon [ok]

Computer has no ACPI related BIOS settings. The computer is BIOS based (No UEFI factors in this case at all) and has two hardisks. I have installed 12.04 & 14.04 on disk drive 0. Windows 8.1 on disk 1. Windows and 12.04 boot fine. 

GRUB RELATED
============

grub2 is being used for boot on both 12.04 and 14.04
I have tried adding 'nomodeset' to grub menuentry for 14.04
Below are some of the grub menuentry for 14.04

menuentry "Ubuntu 14.04 LTS (14.04) (root=UUID=7c4987a5-8490-4440-8a44-f8eb4c7f19a6)" --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic root=UUID=7c4987a5-8490-4440-8a44-f8eb4c7f19a6 ro   $vt_handoff
    initrd /boot/initrd.img-3.13.0-24-generic
}
menuentry "Ubuntu 14.04 LTS (14.04) (/vmlinuz root=/dev/sdb4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /vmlinuz root=/dev/sdb4
    initrd /initrd.img
}
menuentry "Ubuntu 14.04 LTS (14.04) (/boot/vmlinuz-3.13.0-24-generic root=/dev/sdb4)" --class gnu-linux --class gnu --class os {
    insmod part_gpt
    insmod ext2
    set root='(hd0,gpt4)'
    search --no-floppy --fs-uuid --set=root 7c4987a5-8490-4440-8a44-f8eb4c7f19a6
    linux /boot/vmlinuz-3.13.0-24-generic root=/dev/sdb4
    initrd /boot/initrd.img-3.13.0-24-generic
}


GDISK, PARTITION RELATED
========================

Ubuntu has it's own disk drive (drive 0). Windows 8 uses another drive (drive 1)
Added a 1MB 'BIOS boot partition' (type ef02) as first partition using gdisk which seemed to help things along.
Also opted to 'make hybrid MBR' (in other words, protective MBR data) but I am not sure if that was a good idea or not.
Added 16GB swap partition
During both 12.04 & 14.04 installs used 'Something Else' option to tell installers to use 'BIOS boot partition' and 'swap' partitions, and then created new 100GB ext2 partition mounted on '/' (root).
So, 12.04 & 14.04 share swap and BIOS boot partitions.

Windows is completely seperate. I can adjust my BIOS to boot from disk 1, and Windows 8 will start right up with no knowledge of Ubuntu at all. When I boot from disk 0, then get a nice grub related menu allowing me select OS of either 12.04, 14.04 or Windows 8.

Ubuntu 14.04 is only OS that does not boot properly.

Any ideas?
Brad

---

### Post by bradsturtevant on 2014-05-02
On this older BIOS based (NO UEFI!) computer the two significant keys to  success, in order of importance seem to be 1) create a /boot partition!  - mine is 256MB (initially I only created swap and root partitions)  and;  2) Before starting Ubuntu install, unpartition the entire hard  disk using gdisk/fdisk and then use either Windows 8.1 or gdisk (from  Try Ubuntu terminal) to create a new GPT disk with a special 'BIOS boot  partition' of 128MB size (initially 1MB was used). Note: gdisk gives  boot partitions code type 'ef02 BIOS boot partition' and Windows 8.1  gives type '0C01  Microsoft reserved part' but both seem to work. And  also before Ubuntu install use gdisk to 'make hybrid MBR' or on Windows  8.1 you will get hybrid MBR and 128MB 'reserver part' automagically.  Note: You can only initialize a GPT hard disk on Windows 8.1 when disk  is completely blank (no partition tree).

---

