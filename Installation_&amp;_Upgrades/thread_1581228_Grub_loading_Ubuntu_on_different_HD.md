---
title: "Grub loading Ubuntu on different HD"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by Twitch04 on 2010-09-24
Hey everyone. It's been awhile since I've been in the Ubuntu community [since roughly May], but I finally got around to installing Ubuntu 10.04 on the 10GB partition that I used to have 9.10 on. Here's what I did:

I made a Live CD of 10.04 and inserted it, ran GParted. In GParted I deleted the swap partition and the ext4 one, I think it was called that, it was the one that actually HAD Ubuntu on it [instructions given to my by my linux-using friend]. Then, what I wanted to do was install Ubuntu on my 1TB hard drive. So I resized the 1TB so that there was about 44GB unallocated, and I installed Ubuntu to that. 

However, stupidly, I failed to realize that when I deleted the 9.10 partition I messed up Grub. So I couldn't use the boot loader on my primary HD [a 100GB that had the 10GB Ubuntu partition on it], because it gave be the grub rescue message, and when I booted to my other hard drive, it just didn't do anything. It was stuck on the black screen with the flashing underscore/dash in the corner. So what I ended up doing as a temporary fix was popping the Live CD back in and installed Ubuntu 10.04 on the little 10GB partition that used to house 9.10. So then Grub was working fine on there, however, I now have two Ubuntu 10.04 partitions. Not to mention my 90GB Windows XP one that I primarily use.

However, now, when I boot up and in Grub select my 40GB partition, on /dev/sdb5, it doesn't work. while booting, I get this message:

```

[0.731497] VPS: Cannot open root device "sdb5" or unknown-block (0,0)
[0.731559] Please append a correct "root=" boot option; here are the available partitions:
[0.731638] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block (0,0)
```

It didn't say anything in the "here are the available partitions" part.

So essentially what I'd like to do is just have my Windows XP be on my 100GB hard drive, Ubuntu on a 40GB or so partition on my 1TB hard drive, and have the rest of that one just be free space. However, my friend warned me that it might be a pain to set it up that way, I assume it was because Grub might have trouble booting an OS that is on another hard drive than it's installed on.

I believe that's about all the info I have... Any and all help would be appreciated, thank you very much in advance, guys. Sorry if I made my explanation a tad complicated.

---

### Post by drs305 on 2010-09-24
Assuming you can boot to an Ubuntu desktop (not via the LiveCD), you should be able to install Grub2 on the partition on which the Ubuntu install you want to keep resides.

In the first command, designate where your Ubuntu resides (sda1, sdb5, etc - whichever one it is); i.e. replace XY
In the second command, **only** designate the Ubuntu drive (sda or sdb), not the partition; replace X.

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```

If this is not the drive that is booted to by your BIOS, change the BIOS boot order so it is.

If it doesn't see Windows after the first boot, run
```
sudo update-grub
```

---

### Post by Twitch04 on 2010-09-24
> **drs305 said:**
> Assuming you can boot to an Ubuntu desktop (not via the LiveCD), you should be able to install Grub2 on the partition on which the Ubuntu install you want to keep resides.

In the first command, designate where your Ubuntu resides (sda1, sdb5, etc - whichever one it is); i.e. replace XY
In the second command, **only** designate the Ubuntu drive (sda or sdb), not the partition; replace X.

```
sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```If this is not the drive that is booted to by your BIOS, change the BIOS boot order so it is.

If it doesn't see Windows after the first boot, run
```
sudo update-grub
```

Alright, that worked as far as making it so that when I booted to my 1TB, Grub came up. But I still had the same result when I tried to boot into Ubuntu 10.04 on /dev/sdb5.

Is there a chance that I should just try reinstalling Ubuntu on that partition?

---

### Post by drs305 on 2010-09-24
You might post the results of the boot info script so we can see exactly what is happening. 
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

If you haven't spent much time customizing Ubuntu a reinstall sometimes is faster than troubleshooting, but that's up to you. I'd recommend at least letting us look at the RESULTS.txt in case there is an easy and quick fix.

---

### Post by Twitch04 on 2010-09-24
> **drs305 said:**
> You might post the results of the boot info script so we can see exactly what is happening. 
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you haven't spent much time customizing Ubuntu a reinstall sometimes is faster than troubleshooting, but that's up to you. I'd recommend at least letting us look at the RESULTS.txt in case there is an easy and quick fix.

Alright, here's RESULTS.txt.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     6,940,079     6,940,017   b W95 FAT32
/dev/sda2           6,940,141   195,371,007   188,430,867   f W95 Ext d (LBA)
/dev/sda5           6,940,143   174,883,589   167,943,447   7 HPFS/NTFS
/dev/sda6         174,884,864   194,400,255    19,515,392  83 Linux
/dev/sda7         194,402,304   195,371,007       968,704  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,867,572,314 1,867,572,252   7 HPFS/NTFS
/dev/sdb2       1,867,573,246 1,953,523,711    85,950,466   5 Extended
/dev/sdb5       1,867,573,248 1,949,911,039    82,337,792  83 Linux
/dev/sdb6       1,949,913,088 1,953,523,711     3,610,624  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        423B-2BDF                              vfat       LOTHAR                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        06DCD6B8DCD6A16B                       ntfs       Meh                           
/dev/sda6        348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20   ext4                                     
/dev/sda7        2b93c951-2b57-4aef-bb03-bf27deadad8e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5B1ACAE459BA0D79                       ntfs       Sovereign                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        5fc7b45f-6838-4f1c-91fc-740fcf2ddd31   ext4                                     
/dev/sdb6        697f25a9-ab80-4d6a-8721-3bda6428b06b   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        880A-7677                              vfat       MYHAX                         
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/MYHAX             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ = "Unidentified operating system on drive E." 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5fc7b45f-6838-4f1c-91fc-740fcf2ddd31
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb5
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2b93c951-2b57-4aef-bb03-bf27deadad8e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
  92.9GB: boot/grub/grub.cfg
  94.7GB: boot/initrd.img-2.6.32-21-generic
  94.6GB: boot/vmlinuz-2.6.32-21-generic
  94.7GB: initrd.img
  94.6GB: vmlinuz

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=5fc7b45f-6838-4f1c-91fc-740fcf2ddd31 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=697f25a9-ab80-4d6a-8721-3bda6428b06b none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 964.9GB: boot/grub/core.img
 964.9GB: boot/vmlinuz-2.6.32-21-generic
 964.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  61 05 ad 62 02 66 2d 69  34 6d 75 95 0d 31 00 0c  |a..b.f-i4mu..1..|
00000010  82 6a 23 23 04 23 6c 0a  ac 75 64 7a 69 6c 04 6c  |.j##.#l..udzil.l|
00000020  61 43 23 23 73 68 6f 77  08 63 61 73 00 1e 67 61  |aC##show.cas..ga|
00000030  64 67 20 65 74 7a 6f 6e  82 3d 2e 61 16 75 40 0e  |dg etzon.=.a.u@.|
00000040  88 64 2d c2 27 68 6f 6c  19 c0 68 0d 0a 10 0b 01  |.d-.'hol..h.....|
00000050  45 73 74 79 90 6c 65 3d  22 82 42 3a 20 00 93 08  |Esty.le=".B: ...|
00000060  70 78 3b 41 3f 67 61 6d  65 00 73 69 6e 64 75 73  |px;A?game.sindus|
00000070  74 72 e0 79 2e 62 69 7a  46 25 81 12 c0 06 26 70  |tr.y.bizF%....&p|
00000080  40 8d c2 a2 23 66 40 39  75 72 0c 65 5f 83 38 84  |@...#f@9ur.e_.8.|
00000090  07 72 61 64 61 02 72 c4  4f 74 61 62 6c 65 74 b2  |.rada.r.Otablet.|
000000a0  73 40 06 65 65 c5 94 4a  38 67 c0 05 e0 6f 6c 6f  |s@.ee..J8g...olo|
000000b0  67 69 02 32 46 1a 04 96  c1 c0 38 68 75 6d 61 6e  |gi.2F.....8human|
000000c0  43 13 0f 2d 18 32 30 30  05 2d c0 64 72 69 63 07  |C..-.200.-.dric.|
000000d0  87 43 42 1e 01 bd 2a 3d  22 41 64 0a 41 c0 8e 65  |.CB...*="Ad.A..e|
000000e0  02 37 69 76 65 61 10 77  61 79 6f 00 a9 65 64 61  |.7ivea.wayo..eda|
000000f0  12 79 c4 29 62 65 c0 93  65 5f 68 40 6f 74 5f 74  |.y.)be..e_h@ot_t|
00000100  61 67 c1 2b 69 20 7a 6d  6f 64 6f 83 07 23 73 42  |ag.+i zmodo..#sB|
00000110  70 80 7b 72 31 36 30 00  32 6f 18 61 75 74 c2 05  |p.{r160.2o.aut..|
00000120  43 5d 6c 65 66 00 74 6e  61 76 63 6f 6e 74 c4 61  |C]lef.tnavcont.a|
00000130  69 00 ad 20 2b 20 84 1e  02 56 ac 3d 22 82 98 c1  |i.. + ...V.="...|
00000140  0d 6c 80 1e 77 00 f4 0f  c3 14 82 c4 84 60 43 f0  |.l..w........`C.|
00000150  3a 20 32 39 0a 32 80 33  20 80 98 67 69 6e 2d 11  |: 29.2.3 ..gin-.|
00000160  41 16 3a 20 31 21 1c 20  62 61 00 63 6b 67 72 6f  |A.: 1!. ba.ckgro|
00000170  75 6e 64 01 e0 48 61 67  65 3a 20 75 72 00 6c 28  |und..Hage: ur.l(|
00000180  68 74 74 70 3a 2f 80 2f  69 6d 67 2e 67 6f c9 0b  |http:/./img.go..|
00000190  00 2f 73 74 69 63 6b 79  6e 40 6f 74 65 2d 67 72  |./stickyn@ote-gr|
000001a0  a0 1c 67 10 69 66 29 3b  a9 08 72 65 70 c1 60 37  |..g.if);..rep.`7|
000001b0  3a 20 6e 6f 2d 43 01 aa  03 00 70 6f 73 69 00 01  |: no-C....posi..|
000001c0  41 b0 07 fe ff ff 02 00  00 00 17 9d 02 0a 00 fe  |A...............|
000001d0  ff ff 05 fe ff ff 19 9d  02 0a fa cc 29 01 00 00  |............)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by drs305 on 2010-09-24
The main grub configuration file (/boot/grub/grub.cfg) is not installed on sdb5. When you ran the commands in my previous post, did you use:

```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```

**[COLOR="DarkRed"]ADDED: [/COLOR]**You will also have to have BIOS point to this drive first, since you have G2 installed on both MBRs.  After you have run the commands above, check to see if you now have a grub.cfg file in sdb5's /boot/grub folder.

---

### Post by Twitch04 on 2010-09-24
> **drs305 said:**
> The main grub configuration file (/boot/grub/grub.cfg) is not installed on sdb5. When you ran the commands in my previous post, did you use:

```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```You will also have to have BIOS point to this drive first, since you have G2 installed on both MBRs.

Yeah, I did. It even said "Installation finished, no errors detected" or something like that. I'll do it again.

EDIT:
                                 ```
USER@USER-desktop:~$ sudo mount /dev/sdb5 /mnt
[sudo] password for USER: 
USER@USER-desktop:~$ sudo grub-install --root-directory=/mnt /dev/sdb
Installation finished. No error reported.
```Yeah.

EDIT AGAIN: No, there is no grub.cfg file in there.

---

### Post by drs305 on 2010-09-24
I was about to post about the fact that grub.cfg may still be missing.  Also I noticed that the "initrd" line in your sda6 grub entry for sda5 is missing. We'll deal with that later if necessary.

The way you are going to have to reset G2 is to purge and reinstall it. It takes about two minutes - the only drawback is it removes G2 for that time and if you lose power or internet you will be left without a bootloader.

Here is my post on how to purge and reinstall. It's pretty simple.
[http://ubuntuforums.org/showthread.php?t=1581099]("http://ubuntuforums.org/showthread.php?t=1581099")

Note: You don't have to use the LiveCD if you are already booted into a normal Ubuntu system. If you are already on sdb5, just start at Step 2.

---

### Post by Twitch04 on 2010-09-24
Bumping for input from others. I'm back to the original problem, essentially.

---

### Post by Twitch04 on 2010-09-26
Alright, I was told I should post a new RESULTS.txt after being helped out a bit, and here it is:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     6,940,079     6,940,017   b W95 FAT32
/dev/sda2           6,940,141   195,371,007   188,430,867   f W95 Ext d (LBA)
/dev/sda5           6,940,143   174,883,589   167,943,447   7 HPFS/NTFS
/dev/sda6         174,884,864   194,400,255    19,515,392  83 Linux
/dev/sda7         194,402,304   195,371,007       968,704  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63 1,867,572,314 1,867,572,252   7 HPFS/NTFS
/dev/sdb2       1,867,573,246 1,953,523,711    85,950,466   5 Extended
/dev/sdb5       1,867,573,248 1,949,911,039    82,337,792  83 Linux
/dev/sdb6       1,949,913,088 1,953,523,711     3,610,624  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 4025 MB, 4025810432 bytes
255 heads, 63 sectors/track, 489 cylinders, total 7862911 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  38     7,839,719     7,839,682   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        423B-2BDF                              vfat       LOTHAR                        
/dev/sda2: PTTYPE="dos" 
/dev/sda5        06DCD6B8DCD6A16B                       ntfs       Meh                           
/dev/sda6        348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20   ext4                                     
/dev/sda7        2b93c951-2b57-4aef-bb03-bf27deadad8e   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        5B1ACAE459BA0D79                       ntfs       Sovereign                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        e854c7bd-ecea-4a29-953a-9060e3db2323   ext4                                     
/dev/sdb6        0fd7d850-e630-4afa-88b0-7ca14756c3db   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        880A-7677                              vfat       MYHAX                         
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/Ubuntu 10.04 LTS i386 iso9660    (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)
/dev/sdc1        /media/MYHAX             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ = "Unidentified operating system on drive E." 

=========================== sda6/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5fc7b45f-6838-4f1c-91fc-740fcf2ddd31
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb5
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=2b93c951-2b57-4aef-bb03-bf27deadad8e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  94.6GB: boot/grub/core.img
  92.9GB: boot/grub/grub.cfg
  94.7GB: boot/initrd.img-2.6.32-21-generic
  94.6GB: boot/vmlinuz-2.6.32-21-generic
  94.7GB: initrd.img
  94.6GB: vmlinuz

=========================== sdb5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e854c7bd-ecea-4a29-953a-9060e3db2323
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd1,5)'
search --no-floppy --fs-uuid --set e854c7bd-ecea-4a29-953a-9060e3db2323
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e854c7bd-ecea-4a29-953a-9060e3db2323
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e854c7bd-ecea-4a29-953a-9060e3db2323 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e854c7bd-ecea-4a29-953a-9060e3db2323
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e854c7bd-ecea-4a29-953a-9060e3db2323 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e854c7bd-ecea-4a29-953a-9060e3db2323
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set e854c7bd-ecea-4a29-953a-9060e3db2323
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod fat
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 423b-2bdf
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 ro quiet splash
    initrd /boot/initrd.img-2.6.32-21-generic
}
menuentry "Ubuntu, with Linux 2.6.32-21-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set 348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20
    linux /boot/vmlinuz-2.6.32-21-generic root=UUID=348b6722-1e50-4ec8-8d6e-d1fa9f0a4f20 ro single
    initrd /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=e854c7bd-ecea-4a29-953a-9060e3db2323 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=0fd7d850-e630-4afa-88b0-7ca14756c3db none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 973.5GB: boot/grub/core.img
 986.4GB: boot/grub/grub.cfg
 973.5GB: boot/initrd.img-2.6.32-21-generic
 956.8GB: boot/vmlinuz-2.6.32-21-generic
 973.5GB: initrd.img
 956.8GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  61 05 ad 62 02 66 2d 69  34 6d 75 95 0d 31 00 0c  |a..b.f-i4mu..1..|
00000010  82 6a 23 23 04 23 6c 0a  ac 75 64 7a 69 6c 04 6c  |.j##.#l..udzil.l|
00000020  61 43 23 23 73 68 6f 77  08 63 61 73 00 1e 67 61  |aC##show.cas..ga|
00000030  64 67 20 65 74 7a 6f 6e  82 3d 2e 61 16 75 40 0e  |dg etzon.=.a.u@.|
00000040  88 64 2d c2 27 68 6f 6c  19 c0 68 0d 0a 10 0b 01  |.d-.'hol..h.....|
00000050  45 73 74 79 90 6c 65 3d  22 82 42 3a 20 00 93 08  |Esty.le=".B: ...|
00000060  70 78 3b 41 3f 67 61 6d  65 00 73 69 6e 64 75 73  |px;A?game.sindus|
00000070  74 72 e0 79 2e 62 69 7a  46 25 81 12 c0 06 26 70  |tr.y.bizF%....&p|
00000080  40 8d c2 a2 23 66 40 39  75 72 0c 65 5f 83 38 84  |@...#f@9ur.e_.8.|
00000090  07 72 61 64 61 02 72 c4  4f 74 61 62 6c 65 74 b2  |.rada.r.Otablet.|
000000a0  73 40 06 65 65 c5 94 4a  38 67 c0 05 e0 6f 6c 6f  |s@.ee..J8g...olo|
000000b0  67 69 02 32 46 1a 04 96  c1 c0 38 68 75 6d 61 6e  |gi.2F.....8human|
000000c0  43 13 0f 2d 18 32 30 30  05 2d c0 64 72 69 63 07  |C..-.200.-.dric.|
000000d0  87 43 42 1e 01 bd 2a 3d  22 41 64 0a 41 c0 8e 65  |.CB...*="Ad.A..e|
000000e0  02 37 69 76 65 61 10 77  61 79 6f 00 a9 65 64 61  |.7ivea.wayo..eda|
000000f0  12 79 c4 29 62 65 c0 93  65 5f 68 40 6f 74 5f 74  |.y.)be..e_h@ot_t|
00000100  61 67 c1 2b 69 20 7a 6d  6f 64 6f 83 07 23 73 42  |ag.+i zmodo..#sB|
00000110  70 80 7b 72 31 36 30 00  32 6f 18 61 75 74 c2 05  |p.{r160.2o.aut..|
00000120  43 5d 6c 65 66 00 74 6e  61 76 63 6f 6e 74 c4 61  |C]lef.tnavcont.a|
00000130  69 00 ad 20 2b 20 84 1e  02 56 ac 3d 22 82 98 c1  |i.. + ...V.="...|
00000140  0d 6c 80 1e 77 00 f4 0f  c3 14 82 c4 84 60 43 f0  |.l..w........`C.|
00000150  3a 20 32 39 0a 32 80 33  20 80 98 67 69 6e 2d 11  |: 29.2.3 ..gin-.|
00000160  41 16 3a 20 31 21 1c 20  62 61 00 63 6b 67 72 6f  |A.: 1!. ba.ckgro|
00000170  75 6e 64 01 e0 48 61 67  65 3a 20 75 72 00 6c 28  |und..Hage: ur.l(|
00000180  68 74 74 70 3a 2f 80 2f  69 6d 67 2e 67 6f c9 0b  |http:/./img.go..|
00000190  00 2f 73 74 69 63 6b 79  6e 40 6f 74 65 2d 67 72  |./stickyn@ote-gr|
000001a0  a0 1c 67 10 69 66 29 3b  a9 08 72 65 70 c1 60 37  |..g.if);..rep.`7|
000001b0  3a 20 6e 6f 2d 43 01 aa  03 00 70 6f 73 69 00 01  |: no-C....posi..|
000001c0  41 b0 07 fe ff ff 02 00  00 00 17 9d 02 0a 00 fe  |A...............|
000001d0  ff ff 05 fe ff ff 19 9d  02 0a fa cc 29 01 00 00  |............)...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```Still getting the same problem when I try to boot that partition. I'll try to take a photo of it, because there's more on the screen than just those 3 lines in the original post.

EDIT: Alright, attached to this post is a photo of the screen that comes up after I select the 40GB Ubuntu partition on /dev/sdb5.

---

### Post by drs305 on 2010-09-26
I'm going to let others chime in here because so far we haven't been able to get this resolved.

I *can* tell you why sdb5 isn't booting from the sda6 menu. If you compare the grub.cfg  entries for your sda6 boot (n the 10_linux section) and your sdb5 boot (in the 30_os-prober section), you will see the sdb6 section does not contain a line for the initrd image.

The reason may be (deduced from our conversations) that the initrd.img does not exist in sdb6's /boot folder.  You can check by mounting sdb6 and inspecting the contents. If the "ls" command returns an empty result, the image is missing. With no initrd image, the boot will fail.
```
sudo mount /dev/sdb6 /mnt
ls /mnt/boot | grep initrd
sudo umount /dev/sdb6
```

If this is the case, the question for everyone is why isn't the initrd image being created during an install? Or if it exists, why isn't the line being included in sda5's default menu entry?

---

### Post by Twitch04 on 2010-09-26
I'm not sure. I made sure when I wiped the sdb5 partition and reinstalled Ubuntu that nothing got messed up like last time, and nothing went wrong. The install finished [I didn't even skip the language packs and stuff towards the end like I normally do, haha] with no problems. But... Strange. I mean, it can't be the live CD since I installed THIS partition using the same live CD, and I'm using it right now.

EDIT:                      ```

USER@USER-desktop:~$ sudo mount /dev/sdb5 /mnt
USER@USER-desktop:~$ ls /mnt/boot
abi-2.6.32-21-generic         memtest86+.bin
config-2.6.32-21-generic      System.map-2.6.32-21-generic
grub                          vmcoreinfo-2.6.32-21-generic
initrd.img-2.6.32-21-generic  vmlinuz-2.6.32-21-generic

```

initrd.img is there. Bah!

---

### Post by drs305 on 2010-09-26
> **Twitch04 said:**
> initrd.img is there. Bah!

That is probably a good thing. Let's see if we can get your sdb5 install to work by selecting it from the sda6 menu.

We are going to edit the sda5 grub.cfg file. This is normally discouraged but for troubleshooting it's fine. We have to make the file writable. You *do not* run "update-grub" afterwards or it will wipe out the change (which is why we don't normally edit it in the first place.)


Boot to the sda5 install and open a terminal.

```
sudo chmod +w /boot/grub/grub.cfg  # make writable
gksudo gedit +111 /boot/grub/grub.cfg # open gedit at approximate line
```

Add the line for the initrd image:

> menuentry "Ubuntu 10.04 LTS (10.04) (on /dev/sdb5)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 5fc7b45f-6838-4f1c-91fc-740fcf2ddd31
    linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sdb5 [COLOR="Red"]ro[/COLOR]
    [COLOR="Red"]initrd /boot/initrd.img-2.6.32-21-generic[/COLOR]
}

Save the file, do NOT update grub, and reboot. Select your sdb5 menuentry:

Ubuntu 10.04 LTS (10.04) (on /dev/sdb5)

See if it now boots.

---

### Post by Twitch04 on 2010-09-26
You, sir, win an entire internet. That worked. Well, it worked the SECOND time. 

The first time a similar screen came up as before, in the photo, with all the lines scrolling by, but they were different. And it said something about a SanDisk Cruzer Micro, which is the model of my flash drive that was inserted into my computer's USB port at the time. So I restarted my computer, removing the flash drive and tried again and... well, here I am, using it. :D

So I'm going to assume the only reason it didn't work the first time was because my flash drive was inserted, which I don't entirely understand, but oh well, here I am, using the partition I wanted! Thank you, very much!

---

### Post by drs305 on 2010-09-26
> **Twitch04 said:**
> ... but oh well, here I am, using the partition I wanted! Thank you, very much!


Well, we aren't quite finished. If the reason it worked was because we manually added that line, the next time update-grub is run it *may remove* the initrd line from the menuentry.

If you continue to boot the sda6 grub menu (which was missing the initrd line, although the sdb5 one was not), update-grub may again remove the necessary line. The update is performed for several reasons including: manually by the user, and update of the grub package, and when a new kernel is installed.

You have a few options:
[LIST=1]
[*]Switch to have BIOS boot sdb (MBR) first, which would point to what I believe would be a working menuentry for sdb5.


[*]Continue to boot sda. You will need to create a custom menu entry if "update-grub" continues to omit the initrd reference. 

If you decide to go this way, probably the easiest thing to do is to make a backup of the current grub.cfg, run "sudo update-grub" and see if the sdb5 menuentry now includes the initrd line. If it does, you are done. If it doesn't, restore the backup and make a custom menu with the *correct* entry for sdb5. I can help you make that if you need assistance.
[/LIST]

If you want me to just leave you alone, I can do that too!

---

### Post by Twitch04 on 2010-09-27
Alright, I'll try backing up grub.cfg and running "sudo update-grub" when I get home from school in roughly 9 hours. Hopefully that works.

But the Grub on my other hard drive, which has the sdb5 partition, won't work. When you had me mess around in the command line in Grub and for some reason I couldn't get past a certain point and then it wouldn't load ANY parition? XD. Yeah.

The only thing is that IDEALLY, I just want the two partitions. Windows XP on my 100GB, Ubuntu on the 1TB's 40GB partition. So for now I just have to put up with XP having 10 less GB. lol. So somehow, yeah, I want to get the other HD's Grub working.'

And no, sir, you needn't leave me alone. I told you before, I like troubleshooting stuff like this. Even though you're more the one troubleshooting. XD.

---

