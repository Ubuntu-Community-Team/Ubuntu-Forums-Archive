---
title: "Ubuntu 10.10 Installation Failure - GRUB?"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by pcsel on 2011-04-05
Okay I am starting to lose faith in this but my perseverence won't let me...  ;)

Here goes..

I have a Dell Inspiron 8600 (old yes I know) with a 1.4Ghz 1.5Gb RAM with a 150GB HDD installed.. It has run Windows XP Home Edition quite happily for quite a while.

I decided to get my 8Gb MicroUSB memory stick installation back from a friend and start to use that with the system.. Booted up fine ran for a few days and then hung.. no reason.. after a power reset.. I got the GRUB RESCUE> prompt with no commands available.I couldn't mount the drive from the Live DVD as it was locked and couldn't unlock the processes that were holding onto it!!

I eventually gave up and reformatted the USB stick and installed from scratch from a 10.10 DVD..The install was initially from text mode and after this failed after 2 days I ran through the install through the GUI. Each time the install completed and I had a fully working system selecting the boot device from F12 at startup. This then failed with the same sort of error.. Mmm I wondered duff USB card???   

So as I had a lot of space left on the internal HDD I decided to build another install via the GUI onto the HDD.. Install went okay DVD ejected etc upon reboot I got a 

Out Of Disk  error and back to the GRUB RESCUE> prompt and no commands!!

Frustrated at this I mounted the Live DVD again and ran various tests, the results of which are below:

Disk Utility shows all partitions healthy and no errors when tested. GParted the same.However when I run the boot info script I get the following:  Anyone any ideas? I can't even boot into Windows now :(

Thank for any responses

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   179,753,769   179,753,707   7 HPFS/NTFS
/dev/sda2         179,755,006   312,580,095   132,825,090   5 Extended
/dev/sda5         179,755,008   307,073,023   127,318,016  83 Linux
/dev/sda6         307,075,072   312,580,095     5,505,024  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        D2083D19083CFE53                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        632d410a-3f64-4900-b9d5-049cb7e0c1d1   ext4                                     
/dev/sda6        b69cf239-011b-4d44-b982-ca0ae45754d0   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 632d410a-3f64-4900-b9d5-049cb7e0c1d1
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 632d410a-3f64-4900-b9d5-049cb7e0c1d1
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 632d410a-3f64-4900-b9d5-049cb7e0c1d1
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=632d410a-3f64-4900-b9d5-049cb7e0c1d1 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 632d410a-3f64-4900-b9d5-049cb7e0c1d1
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=632d410a-3f64-4900-b9d5-049cb7e0c1d1 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 632d410a-3f64-4900-b9d5-049cb7e0c1d1
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set 632d410a-3f64-4900-b9d5-049cb7e0c1d1
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set d2083d19083cfe53
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 02e3e72d-fc2c-4621-b167-1a806c39d444
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=02e3e72d-fc2c-4621-b167-1a806c39d444 ro quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, with Linux 2.6.35-22-generic (recovery mode) (on /dev/sdc1)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 02e3e72d-fc2c-4621-b167-1a806c39d444
    linux /boot/vmlinuz-2.6.35-22-generic root=UUID=02e3e72d-fc2c-4621-b167-1a806c39d444 ro single
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=632d410a-3f64-4900-b9d5-049cb7e0c1d1 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b69cf239-011b-4d44-b982-ca0ae45754d0 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 143.7GB: boot/grub/core.img
 115.8GB: boot/grub/grub.cfg
  92.7GB: boot/initrd.img-2.6.35-22-generic
  92.7GB: boot/vmlinuz-2.6.35-22-generic
  92.7GB: initrd.img
  92.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  db af 20 0e a6 70 b5 26  57 13 5d 7c b9 7b 6b 04  |.. ..p.&W.]|.{k.|
00000010  81 0b 2a 97 71 3b 81 cc  b2 5f 90 29 11 bc ef 8b  |..*.q;..._.)....|
00000020  2d 33 c1 01 4d e3 2f b6  f3 41 a2 25 63 ac 8c 9b  |-3..M./..A.%c...|
00000030  b8 eb ea e9 46 3c f4 25  18 76 bd e9 37 97 bb 0a  |....F<.%.v..7...|
00000040  c2 e1 5b 6c fa 8d ae b9  e0 de d3 be 91 fb 69 a4  |..[l..........i.|
00000050  fe 3c a9 36 17 43 21 4d  0a c0 ba fe 8a a0 07 ac  |.<.6.C!M........|
00000060  a2 e8 c1 eb 33 16 1a 88  b0 c8 63 42 f3 37 7d 56  |....3.....cB.7}V|
00000070  53 23 3b 52 81 6b 4b d9  27 38 14 68 cc 8c 58 c4  |S#;R.kK.'8.h..X.|
00000080  0f d4 3c 4d 27 69 e0 be  60 2d 21 4a 34 8e 9e d4  |..<M'i..`-!J4...|
00000090  e6 aa 12 69 ed f2 94 6d  93 69 c1 f6 2c f5 17 26  |...i...m.i..,..&|
000000a0  e4 27 98 f9 6b 15 e5 71  24 cd 1c da 2a 89 3c cf  |.'..k..q$...*.<.|
000000b0  50 62 01 fd 5d 6e 1d 5a  96 99 bc 60 93 80 a8 2d  |Pb..]n.Z...`...-|
000000c0  f7 54 df 6c d3 e6 19 e4  d8 6e 38 52 a2 ea 29 56  |.T.l.....n8R..)V|
000000d0  e1 60 a2 c0 82 93 f3 11  4b 99 3e 7e 74 b4 f4 0a  |.`......K.>~t...|
000000e0  27 fc 99 6c 63 d7 99 84  3b bc 08 6f 0d e2 91 24  |'..lc...;..o...$|
000000f0  63 46 98 97 aa 0d 95 f7  8a e8 4d d1 2b 77 40 49  |cF........M.+w@I|
00000100  b3 00 33 e8 a4 ce 13 51  07 a0 fc 7b c2 36 af 10  |..3....Q...{.6..|
00000110  8e e5 92 a9 d0 4e 2c 50  88 d5 a7 dd b5 3c 16 64  |.....N,P.....<.d|
00000120  e5 ec 63 d4 79 d4 db fd  4e 1f 6b 8d 4c b3 10 6c  |..c.y...N.k.L..l|
00000130  ba 57 05 32 12 7c 3a 17  d5 f3 6e e0 54 0e 82 dc  |.W.2.|:...n.T...|
00000140  3f 86 5b 10 77 9c b1 93  e8 3b 2a e6 b8 c8 bf c1  |?.[.w....;*.....|
00000150  54 ef e5 d6 7f 4c 19 6c  09 0f c2 94 fb fe 65 26  |T....L.l......e&|
00000160  25 b4 af 58 6e 2c 0e 48  e9 dc aa ca ca 5a 41 16  |%..Xn,.H.....ZA.|
00000170  01 c6 80 d3 dc 3f ac 4d  f3 ed eb 56 db 91 6c c2  |.....?.M...V..l.|
00000180  80 b0 c4 99 08 a1 88 f6  98 c1 14 b1 f5 40 6e 1b  |.............@n.|
00000190  6c 4b ff 10 e1 5c e3 29  81 fb b6 f5 80 1c 13 54  |lK...\.).......T|
000001a0  48 60 2a 14 50 f3 4d f9  2e df 48 6e 24 98 1b 30  |H`*.P.M...Hn$..0|
000001b0  0f 18 6c 23 c8 48 6e 57  df a4 40 89 07 5a 00 fe  |..l#.HnW..@..Z..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 b8 96 07 00 fe  |................|
000001d0  ff ff 05 fe ff ff 02 b8  96 07 00 08 54 00 00 00  |............T...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by drs305 on 2011-04-05
Try booting into BIOS and check the reported disk size. Since you are using an older system it's possible your BIOS only sees the first 137GB of the drive.

If it reports the drive size incorrectly, the core.img file is currently too far into the disk to be located until after the system is fully booted. Your options are to create a separate /boot partition within the first 135GB or so of the drive, update your BIOS if possible or enable the 'large drive' feature if your BIOS already has that option.

---

### Post by Hedgehog1 on 2011-04-06
**Hey pcsel!**  Three gold stars for attaching the boot script to your first post! :KS :KS :KS

This does make the process of helping so much easier.



***The Hedge***

:KS

---

### Post by pcsel on 2011-04-06
Thanks DRS305 It is the dredded 28bit LBA problem.. I knew there was something I needed to check first..  Grey cells not as sharp as they used to be.

There is no BIOS fix for 48bit LBA support :( so I now have an NTFS and a EXT4 partitions as per the previous boot script code above. I have got the USB stick working again. I can see the partitions on the HDD ..sda5 etc. 

As the ext4 starts at 92Gb or so would that not work or do I need to create a boot there as well for that partition?

Thanks in advance

P

---

### Post by drs305 on 2011-04-06
> **pcsel said:**
> 
As the ext4 starts at 92Gb or so would that not work or do I need to create a boot there as well for that partition?

Glad you were able to find the issue. The fact that the partition starts at 92GB isn't good enough since files migrate over the disk and eventually could be moved beyond the limit.

The good news is the way your drive is currently set up. You will need to 'lock in' a space below the current limit. You could move your existing Ubuntu partition right and make a small partition at the beginning of the extended partition. I'd just delete the swap and recreate it after you were done (and update the swap UUID in fstab). The advantage is you don't mess with your Windows partition at all, which is probably good, and you can use Gparted. The disadvantage is that moving partitions 'right' means moving *all* bytes. It can take an hour or more, and it increases your chance of data loss a bit. (I do it often and haven't had a problem, but it is a consideration.)

The other option would be to shrink Windows just a bit and create a primary boot partition. The advantage is that it would be very quick. The disadvantage is you are messing with your Windows installation. If you do it this way, use a Windows partitioner to shrink Windows. Once you have created the space you can use Gparted to do the rest if you wish.

In either case, create a separate /boot partition. You can find posts about how to do this. You will need to update your fstab settings and definitely update Grub.

---

### Post by oldfred on 2011-04-06
While drs305's recommendations are fine & the standard answer, there is one other alternative in your case since your starting point is 92GB.

You can just shrink the install of Ubuntu below the 137GB and make the rest of the drive /home or a data partition. Or reinstall with a smaller / (root) that is totally inside the 137GB limit and the separate /home that is above the limit. Reading data from above 137GB is not an issue, just booting.

I prefer smaller roots with separate data whether /home or /data. Since your Ubuntu starts at 92GB you have lots of room for a root partition within the 137GB limit. My / are 20 to 25GB but all my user data is else where. And I use about 7GB in the root partitions I have.

---

### Post by drs305 on 2011-04-06
If you haven't changed your partitions yet, I'd agree with *oldfred*. I think that is a much better solution and I too like to keep data partitions separate. It will also allow you to shrink the partition from the 'right' so it will be relatively quick and you can use Gparted.

@ *oldfred*, 
You'd think as often as you point that out I'd remember it - at least on occasion.  ;-)

**ADDED:**
@*oldfred*
In response to your post below, I'm editing this one so the OP doesn't see a new reply. I figure you will see it eventually. ;-)

I've settled on / and /data, with an empty partition and a script to move /home right before I do an upgrade. I used to have a separate /home but I do lots of backups and it was easier just keeping the system together in one partition.

---

### Post by oldfred on 2011-04-06
@ drs305
I had Ubuntu installed for 2 or 3 years in just two partitions / & swap. I did have a (now NTFS) partitions for sharing with XP. But after converting to small root partitions and separte /home or /data , I seem to be promoting that a lot. It may be a bit more for new users to set up, but I think it is worth the effort. Let me know if I overdo it.:)

---

### Post by pcsel on 2011-04-06
OK guys thanks very much for all your help... I went with oldfred's solution of decreasing the partition to below the 137Gb limit.. I now have a fully functional Ubuntu 10.10 system with a 25Gb / and a 30Gb /data partitions With a GRUB loader that also boots into XP if required.

I will close the thread now as solved.. once again thanks for both your input, much appreciated.

Paul

---

### Post by oldfred on 2011-04-06
@pcsel
Glad you got it working. 
If you have more questions feel free to start a new thread.

@ drs305
I also have defaulted to / & /data with /home inside my /. But I keep several roots and only copy some settings from /home to a new install. But have old install to fall back on if need be. I back up only /home, some settings & my data as I have several working Ubuntu installs and feel I can easily reinstall if I ever have to. Each of us have different ideas on what is best and I do not think anyone is wrong as long as it works for them.

---

