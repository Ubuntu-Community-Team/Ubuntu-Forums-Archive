---
title: "GRUB2 woes"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by ubnzxnehiopx on 2010-02-13
I am running Kubuntu Karmic, fully updated.  This was an upgrade over the Internet from Jaunty which was also upgraded from Intrepid.

Since it was an upgrade, grub stayed the same at the 0.97 version.

I wanted to upgrade it to GRUB2 since I want to dual boot and other things.

I have 3 hard drives in the box: the first is my Kubuntu system disk, ATA/IDE, with 6 partitions, /boot being the first, /tmp, /var, swap, etc.  the second drive is SATA with one partition only which I mount on /home. The third disk is a FreeBSD installation.

When I was able to boot up normally, Linux saw the drives as /dev/sda (the SATA home drive), /dev/sdb (the Kubuntu system disk) and /dev/sdc being the FreeBSD drive.  Note the switch of the first two disks.

Using the instructions I found here in the forum and other places on the Internet, I removed/purged grub from my machine, erased /boot/grub, installed grub-pc, and ran grub-install, verifying afterwards.

grub-install created /boot/grub/grub.cfg with "root (hd1,1)" which is as it should be if the Ubuntu system disk is the second drive in the search order.

The version of GRUB now installed is 1.97~beta4.  I can get to the GRUB menu by holding down the SHIFT key.

When I now try to boot up using my new GRUB2 installation, it shows the first Kubuntu splash screen as it should but then I get the maintenance prompt with "Mount of root filesystem failed"

Going back into the GRUB command line, typing "ls" gives me:
(hd0) (hd0,6) (hd0,5) (hd0,4) (hd0,3) (hd0,2) (hd0,1) (hd1) (hd1,1) (hd2) (hd2,1,f) (hd2,1,e) (hd2,1,d) (hd2,1,c) (hd2,1,b) (hd2,1,a) (hd2,1)  (hd3) (hd3,1,f) (hd3,1,e) (hd3,1,d) (hd3,1,c) (hd3,1,b) (hd3,1,a)  (hd3,1)

Two weirdnesses here: first, the first two disks are now interchanged: hd0 should be hd1 and vice versa; no wonder the "root (hd1,1)" doesn't work.  With this, I can't be sure that the UUIDs are correct in the "kernel" statements.  Also, note the duplication of the FreeBSD disk! hd3 is a phantom disk.

My only recovery is to boot up using a Kubuntu CD, mount all my partitions, chroot to it, remove grub-pc and all /boot/grub (probably /etc/default/grub.cfg as well) and reinstall plain old grub 0.97.

Has anyone else seen something like this? Does anyone have a fix for this? This looks like a pretty egregious bug; something about the FreeBSD disk may be confusing poor little Grub2's tiny brain?

TIA

---

### Post by tom4everitt on 2010-02-13
What is the menuentry for your kubuntu? If you press 'e' instead of 'c' in the grub menu you can see it directly, and also change (hd1,1) to (hd0,1) for example, to see if that works better.

---

### Post by ubnzxnehiopx on 2010-02-13
Tom, thanks for the reply.

Here is the menu entry from /boot/grub/grub.cfg (exactly as written by GRUB2's grub-install):

menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
        set quiet=1
        insmod ext2
        set root=(hd1,1)
        search --no-floppy --fs-uuid --set 983f218e-0f6c-414b-9371-41f5c8f5b0bf
        linux   /vmlinuz-2.6.31-20-generic root=UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
        initrd  /initrd.img-2.6.31-20-generic
}

Using 'e' in the grub menu for this entry, setting hd1 to hd0 in the "set root" statement and then booting with "CTRL-X" gives the same results, i.e., booting to the maintenance prompt.  Is there something else I need to do?

I just noticed something in this entry. Would the "insmod" statement need to load ext4?  When I mount the partitions in my chroot, they all say "ext4".  Could that be the problem?  How do I fix it then, if so? Why didn't grub-install use ext4? The old grub works just fine.

---

### Post by tom4everitt on 2010-02-13
I think the ext-systems are so similar that you can read an ext4 as an ext2 if you want. The only difference is that ext4 has some sort of journal speeding up things quite a bit, as I understand it. But try with insmod ext4 if you want.

As you said before it might be that UUID:s are also messed up, so I would suggest you switch the UUID:s present to (hdX,Y):s instead. The most important line probably being:

linux /vmlinuz-2.6.31-20-generic root=UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d ro crashkernel=384M-2G:64M,2G-:128M quiet splash

that would become 

linux /vmlinuz-2.6.31-20-generic root=(hd0,Y) ro crashkernel=384M-2G:64M,2G-:128M quiet splash

i think (where Y is your root partition, counting starting from 1).

---

### Post by ubnzxnehiopx on 2010-02-13
Ok, I tried that and I got a blank screen, had to hit the reset button.

After rebooting into the grub command line, running "ls /" was very interesting because it shows me that its root is (hdx, 6) not (hdx, 1). That is, it is using the actual root file system rather than the /boot partition.

How do I get it to use (hdX,6) as the root file system, but (hdX,1) as its own root for /boot?

I am also now finding it impossible to downgrade back to legacy GRUB.  I get the same "grub>" prompt, there too.

I would rather _not_ re-install Kubuntu right now if I don't have to, but this is really getting weird.

BTW, running "set" at the grub prompt gives:
prefix=(hd0,1)/grub
root=hd0,6

Why isn't this working??

---

### Post by presence1960 on 2010-02-13
Need to see exactly what you have on that machine & the boot process. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by ubnzxnehiopx on 2010-02-13
Here it is.  Thanks for that tool.  I hope you can see something wrong here.  It all looks ok to me.  Thanks.

```
============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /grub.
 => Testdisk is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ufs
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0006a86b

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,465,144,064 1,465,144,002  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000deb78

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63       417,689       417,627  83 Linux
/dev/sdb2             417,690     4,610,654     4,192,965  83 Linux
/dev/sdb3           4,610,655    14,603,084     9,992,430  82 Linux swap / Solaris
/dev/sdb4          14,603,085   240,107,489   225,504,405   f W95 Ext d (LBA)
/dev/sdb5          14,603,148    35,583,974    20,980,827  83 Linux
/dev/sdb6          35,584,038   240,107,489   204,523,452  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
16 heads, 63 sectors/track, 77545 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63    78,165,359    78,165,297  a5 FreeBSD


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        2893d242-ccc7-4af9-aa75-ae4e4fe2844e   ext4                                     
/dev/sdb1        983f218e-0f6c-414b-9371-41f5c8f5b0bf   ext4                                     
/dev/sdb2        fc925559-76ef-4827-9b4b-0d5ede56fcf0   ext4                                     
/dev/sdb3        8883afa0-4246-4027-9665-7f6a20359858   swap                                     
/dev/sdb5        14a40ff6-76ff-4fb7-93cd-e380ceea4395   ext4                                     
/dev/sdb6        59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d   ext4                                     
/dev/sdc1                                               ufs                                      
/dev/sdc5                                               ufs                                      
/dev/sdc7                                               ufs                                      
/dev/sdc8                                               ufs                                      
/dev/sdc9                                               ufs                                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


============================= sdb1/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,6)
search --no-floppy --fs-uuid --set 59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 983f218e-0f6c-414b-9371-41f5c8f5b0bf
    linux    /vmlinuz-2.6.31-20-generic root=UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 983f218e-0f6c-414b-9371-41f5c8f5b0bf
    linux    /vmlinuz-2.6.31-20-generic root=UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d ro single 
    initrd    /initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 983f218e-0f6c-414b-9371-41f5c8f5b0bf
    linux    /vmlinuz-2.6.31-19-generic root=UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d ro   crashkernel=384M-2G:64M,2G-:128M quiet splash
    initrd    /initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 983f218e-0f6c-414b-9371-41f5c8f5b0bf
    linux    /vmlinuz-2.6.31-19-generic root=UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d ro single 
    initrd    /initrd.img-2.6.31-19-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .1GB: initrd.img-2.6.31-19-generic
    .1GB: initrd.img-2.6.31-20-generic
    .0GB: vmlinuz-2.6.31-19-generic
    .0GB: vmlinuz-2.6.31-20-generic

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=983f218e-0f6c-414b-9371-41f5c8f5b0bf /boot           ext4    relatime        0       2
# /tmp was on /dev/sda2 during installation
UUID=fc925559-76ef-4827-9b4b-0d5ede56fcf0 /tmp            ext4    relatime        0       2
# /var was on /dev/sda5 during installation
UUID=14a40ff6-76ff-4fb7-93cd-e380ceea4395 /var            ext4    relatime        0       2
# swap was on /dev/sda3 during installation
UUID=8883afa0-4246-4027-9665-7f6a20359858 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=2893d242-ccc7-4af9-aa75-ae4e4fe2844e    /home        ext4    defaults,relatime,nodev,nosuid    1 2
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 3c 00 00 00 00 00 00  00 00 00 00 02 00 00 00  |.<..............|
00000010  00 00 00 00 00 00 00 00  12 00 02 00 00 00 00 00  |................|
00000020  00 00 00 00 00 16 1f 66  6a 00 51 50 06 53 31 c0  |.......fj.QP.S1.|
00000030  88 f0 50 6a 10 89 e5 e8  c0 00 8d 66 10 cb fc 31  |..Pj.......f...1|
00000040  c9 8e c1 8e d9 8e d1 bc  00 7c 89 e6 bf 00 07 fe  |.........|......|
00000050  c5 f3 a5 be ee 7d 80 fa  80 72 2c b6 01 e8 60 00  |.....}...r,...`.|
00000060  b9 01 00 be be 8d b6 01  80 7c 04 a5 75 07 e3 19  |.........|..u...|
00000070  f6 04 80 75 14 83 c6 10  fe c6 80 fe 05 72 e9 49  |...u.........r.I|
00000080  e3 e1 be a2 7d eb 4b 31  d2 89 16 00 09 b6 10 e8  |....}.K1........|
00000090  2e 00 bb 00 90 8b 77 0a  01 de bf 00 c0 b9 00 ae  |......w.........|
000000a0  29 f1 f3 a4 fa 49 74 14  e4 64 a8 02 75 f7 b0 d1  |)....It..d..u...|
000000b0  e6 64 e4 64 a8 02 75 fa  b0 df e6 60 fb e9 50 13  |.d.d..u....`..P.|
000000c0  bb 00 8c 8b 44 08 8b 4c  0a 0e e8 5a ff 73 2a be  |....D..L...Z.s*.|
000000d0  9d 7d e8 1c 00 be a7 7d  e8 16 00 30 e4 cd 16 c7  |.}.....}...0....|
000000e0  06 72 04 34 12 ea 00 00  ff ff bb 07 00 b4 0e cd  |.r.4............|
000000f0  10 ac 84 c0 75 f4 b4 01  f9 c3 2e f6 06 b0 08 80  |....u...........|
00000100  74 22 80 fa 80 72 1d bb  aa 55 52 b4 41 cd 13 5a  |t"...r...UR.A..Z|
00000110  72 12 81 fb 55 aa 75 0c  f6 c1 01 74 07 89 ee b4  |r...U.u....t....|
00000120  42 cd 13 c3 52 b4 08 cd  13 88 f5 5a 72 cb 80 e1  |B...R......Zr...|
00000130  3f 74 c3 fa 66 8b 46 08  52 66 0f b6 d9 66 31 d2  |?t..f.F.Rf...f1.|
00000140  66 f7 f3 88 eb 88 d5 43  30 d2 66 f7 f3 88 d7 5a  |f......C0.f....Z|
00000150  66 3d ff 03 00 00 fb 77  9d 86 c4 c0 c8 02 08 e8  |f=.....w........|
00000160  40 91 88 fe 28 e0 8a 66  02 38 e0 72 02 b0 01 bf  |@...(..f.8.r....|
00000170  05 00 c4 5e 04 50 b4 02  cd 13 5b 73 0a 4f 74 1c  |...^.P....[s.Ot.|
00000180  30 e4 cd 13 93 eb eb 0f  b6 c3 01 46 08 73 03 ff  |0..........F.s..|
00000190  46 0a d0 e3 00 5e 05 28  46 02 77 88 c3 52 65 61  |F....^.(F.w..Rea|
000001a0  64 00 42 6f 6f 74 00 20  65 72 72 6f 72 0d 0a 00  |d.Boot. error...|
000001b0  80 90 90 90 90 90 90 90  90 90 90 90 90 90 80 00  |................|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001f0  01 00 a5 fe ff ff 00 00  00 00 50 c3 00 00 55 aa  |..........P...U.|
00000200

```

---

### Post by ubnzxnehiopx on 2010-02-14
No one?  Oh well, do I _really_ have to re-install?  Drag.  Completely dead in the water here.

---

### Post by presence1960 on 2010-02-14
> **ubnzxnehiopx said:**
> No one?  Oh well, do I _really_ have to re-install?  Drag.  Completely dead in the water here.
```

=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sda6 during installation
UUID=59b9fecb-1a6b-41fc-9f7a-2bf01eb6c44d[/COLOR] /               ext4    relatime,errors=remount-ro 0       1
[COLOR="Red"]# /boot was on /dev/sda1 during installation
UUID=983f218e-0f6c-414b-9371-41f5c8f5b0bf /boot[/COLOR]         ext4    relatime        0       2
[COLOR="Red"]# /tmp was on /dev/sda2 during installation
UUID=fc925559-76ef-4827-9b4b-0d5ede56fcf0 /tmp [/COLOR]           ext4    relatime        0       2
[COLOR="Red"]# /var was on /dev/sda5 during installation
UUID=14a40ff6-76ff-4fb7-93cd-e380ceea4395 /var[/COLOR]            ext4    relatime        0       2[COLOR="Red"]
# swap was on /dev/sda3 during installation
UUID=8883afa0-4246-4027-9665-7f6a20359858[/COLOR] none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Your UUIDS in /etc/fstab are wrong. You need to fix them. /boot on sda1 does not exist. Your boot files are on sdb1 which is your root partition. I would eliminate the /boot entry.

Your / UUID should be 983f218e-0f6c-414b-9371-41f5c8f5b0bf

You can edit these entries by booting off the Live CD, choose "try ubuntu without any changes". When the desktop loads mount sdb6 (etc/fstab is in there) by going Places > Computer and highlighting the partition on left. When you see the fstab file you have the right partition mounted. Now open a terminal and run gksu nautilus. This will open a file browser with root priviledge. Navigate to your /etc/fstab and open the fstab file. make the changes I noted. Click Save on top toolbar & close file. Close all file browsers and reboot without the Live CD.

Your fstab is referring to the wrong partitions for some of your stuff and one partition does not exist. Is there any reason you made all those separate /boot,/var,/tmp. /etc/fstab partitions. Unless you have an older BIOS that can not read past a certain point on your hard disk there really is no need for all that. it can get you into trouble as those partitions fill up and you need to add more space to them.

---

### Post by ubnzxnehiopx on 2010-02-14
Thanks for the reply.

The comments are wrong in the fstab.  The comments are from my original installation before I was mounting a huge disk to /home; this changed the disk order.

When I boot up with a live cd, "sudo mount /dev/sdb6 /mnt", "sudo chroot /mnt" (after mounting /dev, /proc, etc...) , and then, as root "mount -a", I get everything mounted correctly.  If the UUIDs were messed up, wouldn't "mount -a" not work at all?

I don't remember the reason why I actually chose separate partitions, but this has been working for a couple of years now and just now messed up when I started messing with GRUB2.  Now I can't even revert back to legacy GRUB for some reason either.

Are you saying that GRUB can't handle a separate /boot partition? That is the way it looks to me; why did this just now start failing?

So, you are saying the only way out of my problem here is to merge the /boot partition into "/"?  That's a bug. A big one.  I guess I have no choice but to boot up gparted and do this...

What about the ghosting of the FreeBSD disk? "ls" shows a duplicate non-existent (hd3) with the same partition map.  Something else is going on here.

---

### Post by meierfra. on 2010-02-14
I have no clue what is causing your problem, but I want to point that there does not seem to be problem with Grub or fstab.

> no wonder the "root (hd1,1)" doesn't work.

Yes, "root=(hd1,1)" should be "root=(hd0,1)", but the root statement gets overwritten by the following "search" command.  So it does not matter that's wrong.


> Are you saying that GRUB can't handle a separate /boot partition? 

As far as I know, Grub 2 has no problems with separate boot partitions. 


>  it shows the first Kubuntu splash screen as it should but then I get the maintenance prompt with "Mount of root filesystem failed"
I suggest to run a file system check on /dev/sdb6.  Also check whether any of your partitions are  filled up.

---

### Post by ubnzxnehiopx on 2010-02-14
Thanks for the reply.

After rebooting with a live CD (DVD actually), and mounting all the partitions to be able to see 'df', /dev/sdb6 is 60% full.  No other partition is even close to being that full.

Running 'sudo fsck -fp' for both  /dev/sdb6, the "/" partition and /dev/sdb1 "/boot" came back clean.

The really weird part is that the maintenance shell actually has the proper root file system mounted (/dev/sdb6).  I can do 'mount -a' and get everything mounted correctly as it should be.  Why is it failing? Why does it think it can't do something?  I have tried this with and without the FreeBSD disk just to make sure, but still the same thing.

Help!
:icon_frown:

---

### Post by ubnzxnehiopx on 2010-02-14
I just solved it.  Nothing to do with grub at all.

I need to go right now, so I'll update this thread with why it now works (it's a bit involved and strange).

Thanks for all who tried to help... I'll be back to put a [SOLVED] on this thread soon.

---

### Post by tom4everitt on 2010-02-14
> **ubnzxnehiopx said:**
> 

How do I get it to use (hdX,6) as the root file system, but (hdX,1) as its own root for /boot?


Basically it works like this:

set root=(hdX,1) is where you choose your /boot, i.e where it will find the kernel.

to the kernel you then pass an argument about which partition it should use as its root partition (where it also will find /etc/fstab which decides further mounting). To the kernel you generally also pass arguments such as "quiet", "splash", "ro".

then you generally also need to specify an initrd. 

So theoretically this should suffice:

```

menuentry "Ubuntu, Linux 2.6.31-20-generic" {
  insmod ext2
  set root=(hdX,1)
  linux /vmlinuz-2.6.31-20-generic root=(hdX,6) ro quiet splash
  initrd /initrd.img-2.6.31-20-generic
}

```

If you want you can also execute each of these lines (in the same order) in the grub shell, which might give you a better idea of what/where it goes wrong.

ls (hdX,Y) is also a handy grub-shell command.

---

