---
title: "Issue with grub and external USB Ubuntu 11.10 install"
date: 2011-12-10
forum: Installation &amp; Upgrades
---

### Post by rmc_0 on 2011-12-10
I'm rather new to Linux altogether and wanted to give Ubuntu a try. Months ago, I installed 11.04 onto an external USB hard drive and ran it alongside OS X 10.7. I tried to upgrade once 11.10 went gold, but had problems with the finished installation, so I decided to format my external drive and start fresh.

For a long time, I would get the 'grub-install ... has failed. This is a fatal error' message, but after trying a bunch of things, I eventually got 'round all that and completed the installation. However, every time I have done so and tried to boot from the external drive via rEFIt, I get chucked to grub-rescue, with the message:

```

Starting grubx64.efi
error: no such device:
88e2c264-ab87-4de6-a9a8-64aa4bbc6855

```

Like I said, I get this message *every* time I install Ubuntu, changing minor things every time, hoping for different results. I'm at the end of my rope here, how have I botched this thing and how can I un-botch it?

---

### Post by fantab on 2011-12-10
> **rmc_0 said:**
> However, every time I have done so and tried to boot from the external drive via rEFIt, I get chucked to grub-rescue, with the message:

```

Starting grubx64.efi
error: no such device:
88e2c264-ab87-4de6-a9a8-64aa4bbc6855

```Like I said, I get this message *every* time I install Ubuntu, changing minor things every time, hoping for different results. I'm at the end of my rope here, how have I botched this thing and how can I un-botch it?

Does you computer use UEFI instead of BIOS? Can you set your desktop to boot USB devices first? Where did you install GRUB, /dev/sda (by default GRUB will be installed here) or /dev/sdb (USB)?

Here is some info about [**UEFI BOOTING**]("https://help.ubuntu.com/community/UEFIBooting")
Also check this **[additional info]("http://refit.sourceforge.net/")**.

If you can set your Desktop to boot USB devices first then install GRUB to the USB disk on which you have installed.
(I don't use mac and I am not much versed in it. I have just provided you some cursory help for you to work on until you get an authoritative solution).

---

### Post by rmc_0 on 2011-12-11
I'm dual-booting with a MacBook Pro 5,4 (late 2009/early '10), running OS X 10.7.2; this machine uses the older EFI rather than UEFI.

GRUB was installed on /dev/sdb. 

I suppose it would be helpful if I include the partitions I made on the drive:

[LIST]
[*]EFI boot partition, 258MB
[*]swap partition, 2GB
[*]root, 10GB, ext4
[*]/home, ~307GB, ext4
[/LIST]
Additionally, I installed Ubuntu following the instructions found **[here]("http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/")**. It worked just fine for 11.04, though I did run into problems booting my MBP, which were solved by installing rEFIt.

Anyway, in the times where GRUB would not fully install with 11.10, I had tried to install it on a partition using an ext2 filesystem. Like I said, this worked when I installed both Ubuntu and Kubuntu versions 11.04, and I hadn't noticed the available EFI boot partition option. After choosing that option instead, everything would go fine until trying to boot from the external drive.

Like I said, I get the exact same message with the exact same error code every time I try to reinstall Ubuntu, so I know it has to be something specific, though of course I don't know what.

Did I do things wrong with the partitioning? Is it an issue with rEFIt? And what is grubx64.efi in terms of GRUB2?

---

### Post by fantab on 2011-12-11
> **rmc_0 said:**
> I'm dual-booting with a MacBook Pro 5,4 (late 2009/early '10), running OS X 10.7.2; this machine uses the older EFI rather than UEFI.

GRUB was installed on /dev/sdb. 

I suppose it would be helpful if I include the partitions I made on the drive:

[LIST]
[*]EFI boot partition, 258MB
[*]swap partition, 2GB
[*]root, 10GB, ext4
[*]/home, ~307GB, ext4
[/LIST]
Assuming the partitions you described above are on /dev/sdb allow me to suggest that you remove partition EFI Boot partition and try installing GRUB directly to /dev/sdb. 

You did not answer, "can you get your system to boot USB Devices First when they are plugged in?" If you can then you must.

Also check to see what type of Partition table your /dev/sdb is using. 

Post the output of **[Boot Info Script]("http://bootinfoscript.sourceforge.net/")**.

---

### Post by rmc_0 on 2011-12-21
Okay, my apologies for the lack of a prompt response, I've been rather busy lately.

Anyway, I looked into the 'Startup Disk' option on OSX, and the external USB drive I'm using never came up. But rEFIt recognizes the drive and allows me to choose it when I start up my laptop, so that's never been an issue. After all, I did have 11.04 running and able to boot with no problem before.

I've tried a few times to install 11.10 without making an EFI boot partition, to no avail. Every time I've tried to install, boot partition or no, I've always chosen /dev/sdb as my grub install destination. That said, you can probably get the full story from the result of the boot info script that I'll be posting below.

Finally, as to the partition table type that /dev/sdb is using, I don't know where to look for that, sorry. If you could kindly point me in the right direction, I'd be happy to tell you.

All that out there, here are the results from the boot info script:

```

   Boot Info Script 0.60    from 17 May 2011   ============================= Boot Info Summary: ===============================   => Syslinux MBR (3.00-3.35) is installed in the MBR of /dev/sda.  => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector      9856109 of the same hard drive for core.img. core.img is at this location      and looks for  on this drive.  sda1: __________________________________________________________________________      File system:       vfat     Boot sector type:  Unknown     Boot sector info:   According to the info in the boot sector, sda1 starts                         at sector 0. But according to the info from fdisk,                         sda1 starts at sector 40.     Operating System:       Boot files:          sda2: __________________________________________________________________________      File system:       hfsplus     Boot sector type:  -     Boot sector info:       Operating System:       Boot files:          sda3: __________________________________________________________________________      File system:       hfsplus     Boot sector type:  -     Boot sector info:       Operating System:       Boot files:          sdb1: __________________________________________________________________________      File system:       swap     Boot sector type:  -     Boot sector info:    sdb2: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:  Ubuntu 11.10     Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img  sdb3: __________________________________________________________________________      File system:       ext4     Boot sector type:  -     Boot sector info:       Operating System:       Boot files:          ============================ Drive/Partition Info: =============================  Drive: sda _____________________________________________________________________  Disk /dev/sda: 250.1 GB, 250059350016 bytes 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sda1                   1       409,639       409,639  ee GPT /dev/sda2    *        409,640   487,127,591   486,717,952  af HFS / HFS+ /dev/sda3         487,127,592   488,397,127     1,269,536  ab Darwin boot   GUID Partition Table detected.  Partition    Start Sector    End Sector  # of Sectors System /dev/sda1              40       409,639       409,600 EFI System partition /dev/sda2         409,640   487,127,591   486,717,952 Hierarchical File System Plus (HFS+) partition (Mac OS X) /dev/sda3     487,127,592   488,397,127     1,269,536 Apple Boot partition (Mac OS X)  Drive: sdb _____________________________________________________________________  Disk /dev/sdb: 320.1 GB, 320072932864 bytes 255 heads, 63 sectors/track, 38913 cylinders, total 625142447 sectors Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes  Partition  Boot  Start Sector    End Sector  # of Sectors  Id System  /dev/sdb1                   1            33            33  ee GPT /dev/sdb2                  34     3,906,284     3,906,251  82 Linux swap / Solaris /dev/sdb3    *      3,906,285    23,437,535    19,531,251  83 Linux /dev/sdb4          23,437,536   625,140,661   601,703,126  83 Linux   GUID Partition Table detected.  Partition    Start Sector    End Sector  # of Sectors System /dev/sdb1              34     3,906,284     3,906,251 Swap partition (Linux) /dev/sdb2       3,906,285    23,437,535    19,531,251 Data partition (Windows/Linux) /dev/sdb3      23,437,536   625,140,661   601,703,126 Data partition (Windows/Linux)  "blkid" output: ________________________________________________________________  Device           UUID                                   TYPE       LABEL  /dev/loop0                                              squashfs    /dev/sda1        70D6-1701                              vfat       EFI /dev/sda2        fc674b67-6e47-341b-b474-4b9752d98ee2   hfsplus    Macintosh HD /dev/sda3        bd9d8aae-9935-3ee5-8518-ea8c119ab92e   hfsplus    Recovery HD /dev/sdb1        5bc6a705-e61b-4138-8225-1912ecf7666c   swap        /dev/sdb2        e68f3f70-7bef-4734-a7c3-39b040d9ce4d   ext4        /dev/sdb3        c3f75a25-f815-4c84-9e8e-03d145b869c1   ext4         ================================ Mount points: =================================  Device           Mount_Point              Type       Options  /dev/loop0       /rofs                    squashfs   (ro,noatime) /dev/sr0         /cdrom                   iso9660    (ro,noatime)   =========================== sdb2/boot/grub/grub.cfg: ===========================  -------------------------------------------------------------------------------- # # DO NOT EDIT THIS FILE # # It is automatically generated by grub-mkconfig using templates # from /etc/grub.d and settings from /etc/default/grub #  ### BEGIN /etc/grub.d/00_header ### if [ -s $prefix/grubenv ]; then   set have_grubenv=true   load_env fi set default="0" if [ "${prev_saved_entry}" ]; then   set saved_entry="${prev_saved_entry}"   save_env saved_entry   set prev_saved_entry=   save_env prev_saved_entry   set boot_once=true fi  function savedefault {   if [ -z "${boot_once}" ]; then     saved_entry="${chosen}"     save_env saved_entry   fi }  function recordfail {   set recordfail=1   if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi }  function load_video {   insmod vbe   insmod vga   insmod video_bochs   insmod video_cirrus }  insmod part_gpt insmod ext2 set root='(hd1,gpt2)' search --no-floppy --fs-uuid --set=root e68f3f70-7bef-4734-a7c3-39b040d9ce4d if loadfont /usr/share/grub/unicode.pf2 ; then   set gfxmode=auto   load_video   insmod gfxterm   insmod part_gpt   insmod ext2   set root='(hd1,gpt2)'   search --no-floppy --fs-uuid --set=root e68f3f70-7bef-4734-a7c3-39b040d9ce4d   set locale_dir=($root)/boot/grub/locale   set lang=en_US   insmod gettext fi terminal_output gfxterm if [ "${recordfail}" = 1 ]; then   set timeout=-1 else   set timeout=10 fi ### END /etc/grub.d/00_header ###  ### BEGIN /etc/grub.d/05_debian_theme ### set menu_color_normal=white/black set menu_color_highlight=black/light-gray if background_color 44,0,30; then   clear fi ### END /etc/grub.d/05_debian_theme ###  ### BEGIN /etc/grub.d/10_linux ### if [ ${recordfail} != 1 ]; then   if [ -e ${prefix}/gfxblacklist.txt ]; then     if hwmatch ${prefix}/gfxblacklist.txt 3; then       if [ ${match} = 0 ]; then         set linux_gfx_mode=keep       else         set linux_gfx_mode=text       fi     else       set linux_gfx_mode=text     fi   else     set linux_gfx_mode=keep   fi else   set linux_gfx_mode=text fi export linux_gfx_mode if [ "$linux_gfx_mode" != "text" ]; then load_video; fi menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     set gfxpayload=$linux_gfx_mode     insmod gzio     insmod part_gpt     insmod ext2     set root='(hd1,gpt2)'     search --no-floppy --fs-uuid --set=root e68f3f70-7bef-4734-a7c3-39b040d9ce4d     linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e68f3f70-7bef-4734-a7c3-39b040d9ce4d ro   quiet splash vt.handoff=7     initrd    /boot/initrd.img-3.0.0-12-generic } menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {     recordfail     insmod gzio     insmod part_gpt     insmod ext2     set root='(hd1,gpt2)'     search --no-floppy --fs-uuid --set=root e68f3f70-7bef-4734-a7c3-39b040d9ce4d     echo    'Loading Linux 3.0.0-12-generic ...'     linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=e68f3f70-7bef-4734-a7c3-39b040d9ce4d ro recovery nomodeset      echo    'Loading initial ramdisk ...'     initrd    /boot/initrd.img-3.0.0-12-generic } ### END /etc/grub.d/10_linux ###  ### BEGIN /etc/grub.d/20_linux_xen ### ### END /etc/grub.d/20_linux_xen ###  ### BEGIN /etc/grub.d/20_memtest86+ ### menuentry "Memory test (memtest86+)" {     insmod part_gpt     insmod ext2     set root='(hd1,gpt2)'     search --no-floppy --fs-uuid --set=root e68f3f70-7bef-4734-a7c3-39b040d9ce4d     linux16    /boot/memtest86+.bin } menuentry "Memory test (memtest86+, serial console 115200)" {     insmod part_gpt     insmod ext2     set root='(hd1,gpt2)'     search --no-floppy --fs-uuid --set=root e68f3f70-7bef-4734-a7c3-39b040d9ce4d     linux16    /boot/memtest86+.bin console=ttyS0,115200n8 } ### END /etc/grub.d/20_memtest86+ ###  ### BEGIN /etc/grub.d/30_os-prober ### menuentry "Mac OS X (32-bit) (on /dev/sda2)" --class osx --class darwin --class os {     insmod part_gpt     insmod hfsplus     set root='(hd0,gpt2)'     search --no-floppy --fs-uuid --set=root 27d24f089399c2a7         load_video         set do_resume=0         if [ /var/vm/sleepimage -nt10 / ]; then            if xnu_resume /var/vm/sleepimage; then              set do_resume=1            fi         fi         if [ $do_resume = 0 ]; then            xnu_uuid 27d24f089399c2a7 uuid            if [ -f /Extra/DSDT.aml ]; then               acpi -e /Extra/DSDT.aml            fi            xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid            if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then               xnu_mkext /System/Library/Extensions.mkext            else               xnu_kextdir /System/Library/Extensions            fi            if [ -f /Extra/Extensions.mkext ]; then               xnu_mkext /Extra/Extensions.mkext            fi            if [ -d /Extra/Extensions ]; then               xnu_kextdir /Extra/Extensions            fi            if [ -f /Extra/devprop.bin ]; then               xnu_devprop_load /Extra/devprop.bin            fi            if [ -f /Extra/splash.jpg ]; then               insmod jpeg               xnu_splash /Extra/splash.jpg            fi            if [ -f /Extra/splash.png ]; then               insmod png               xnu_splash /Extra/splash.png            fi            if [ -f /Extra/splash.tga ]; then               insmod tga               xnu_splash /Extra/splash.tga            fi         fi } menuentry "Mac OS X (64-bit) (on /dev/sda2)" --class osx --class darwin --class os {     insmod part_gpt     insmod hfsplus     set root='(hd0,gpt2)'     search --no-floppy --fs-uuid --set=root 27d24f089399c2a7         load_video         set do_resume=0         if [ /var/vm/sleepimage -nt10 / ]; then            if xnu_resume /var/vm/sleepimage; then              set do_resume=1            fi         fi         if [ $do_resume = 0 ]; then            xnu_uuid 27d24f089399c2a7 uuid            if [ -f /Extra/DSDT.aml ]; then               acpi -e /Extra/DSDT.aml            fi            xnu_kernel64 /mach_kernel boot-uuid=${uuid} rd=*uuid            if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then               xnu_mkext /System/Library/Extensions.mkext            else               xnu_kextdir /System/Library/Extensions            fi            if [ -f /Extra/Extensions.mkext ]; then               xnu_mkext /Extra/Extensions.mkext            fi            if [ -d /Extra/Extensions ]; then               xnu_kextdir /Extra/Extensions            fi            if [ -f /Extra/devprop.bin ]; then               xnu_devprop_load /Extra/devprop.bin            fi            if [ -f /Extra/splash.jpg ]; then               insmod jpeg               xnu_splash /Extra/splash.jpg            fi            if [ -f /Extra/splash.png ]; then               insmod png               xnu_splash /Extra/splash.png            fi            if [ -f /Extra/splash.tga ]; then               insmod tga               xnu_splash /Extra/splash.tga            fi         fi } ### END /etc/grub.d/30_os-prober ###  ### BEGIN /etc/grub.d/40_custom ### # This file provides an easy way to add custom menu entries.  Simply type the # menu entries you want to add after this comment.  Be careful not to change # the 'exec tail' line above. ### END /etc/grub.d/40_custom ###  ### BEGIN /etc/grub.d/41_custom ### if [ -f  $prefix/custom.cfg ]; then   source $prefix/custom.cfg; fi ### END /etc/grub.d/41_custom ### --------------------------------------------------------------------------------  =============================== sdb2/etc/fstab: ================================  -------------------------------------------------------------------------------- # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sdb2 during installation UUID=e68f3f70-7bef-4734-a7c3-39b040d9ce4d /               ext4    errors=remount-ro 0       1 # /home was on /dev/sdb3 during installation UUID=c3f75a25-f815-4c84-9e8e-03d145b869c1 /home           ext4    defaults        0       2 # swap was on /dev/sdb1 during installation UUID=5bc6a705-e61b-4138-8225-1912ecf7666c none            swap    sw              0       0 --------------------------------------------------------------------------------  =================== sdb2: Location of files loaded by Grub: ====================             GiB - GB             File                                 Fragment(s)                 =                boot/grub/core.img                             1                =                boot/grub/grub.cfg                             1                =                boot/initrd.img-3.0.0-12-generic               2                =                boot/vmlinuz-3.0.0-12-generic                  1                =                initrd.img                                     2                =                vmlinuz                                        1  ======================== Unknown MBRs/Boot Sectors/etc: ========================  Unknown BootLoader on sda1  00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .| 00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......| 00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........| 00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| 00000040  00 00 29 01 17 d6 70 45  46 49 20 20 20 20 20 20  |..)...pEFI      | 00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....| 00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 fc  |.|......^.......| 00000070  ac 84 c0 74 06 b4 0e cd  10 eb f5 30 e4 cd 16 cd  |...t.......0....| 00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di| 00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke| 000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....| 000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................| * 000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.| 00000200   ========= Devices which don't seem to have a corresponding hard drive: =========  sdc   =============================== StdErr Messages: ===============================  unlzma: Decoder error awk: cmd. line:36: Math support is not compiled in awk: cmd. line:36: Math support is not compiled in awk: cmd. line:36: Math support is not compiled in awk: cmd. line:36: Math support is not compiled in awk: cmd. line:36: Math support is not compiled in awk: cmd. line:36: Math support is not compiled in  
```

---

### Post by fantab on 2011-12-22
The Boot Info Script you have provided is not readable.

You can use **[Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php")** to find out what partition table you are using on ExHDD. I think you will have to use GPT partition table.

Here is more info on **[(U)EFI Booting.]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")** Following is the word of caution from the same link:

> From Ubuntu 11.04 onwards (x86_64 only), the ISO CD supports UEFI  booting and the Ubuntu installer will try to set up the bootloader for  (U)EFI boot. But the installer **formats the EFI System Partition**  to FAT16 (even if the filesystem is non-empty) and also uses  efibootmgr, therefore Intel Macs may fail to boot due to corrupted  firmware. This feature is not recommended on Mac models because it can [corrupt the firmware.]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/774089")  You will need to reflash the firmware to repair it. 

---

### Post by rmc_0 on 2011-12-27
Sorry about that with the unreadable Boot Info Script, I don't know what happened there, and I even tried to edit it to read properly. Ugh.

Welp, so anyway, I just got fed up with the whole thing and decided to just set up a dual boot arrangement on my main hard drive, using the external drive for extra space.

With just a bit of finagling with gdisk (after completely wiping my hard drive that didn't want to let me make new partitions), I managed to get it to work, and I'm happy with the results. I'm going to have to do it all over again soon, as I'm waiting to receive a new internal hard drive to replace the one I currently have, but that's okay, it really wasn't a problem.

I apologize for having wasted your time (I'm not being sarcastic or anything, if it sounds like it), and I do appreciate your help. I'm just happy now that I got everything to work.

Thanks!

---

