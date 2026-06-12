---
title: "Grub: error:out of disc, grub rescue, 10.04"
date: 2010-08-30
forum: Installation &amp; Upgrades
---

### Post by abrav on 2010-08-30
I have spent several days trying to install Ubuntu 10.04 but with no success. I hope some friendly soul can help me.

I had a functional 9.10 but with wireless networking problems. During trying to fix these problems I managed to totally screw the network settings up, so I decided to start fresh with 10.04.

After the first attempt to install 10.04 I got to the grub rescue>. I tried tips from several threads but nothing that worked. Eventually I found out that it may be due to my 9.10 boot partition(?) having screwed up the grub installation. So, I rebooted from the LiveCD and removed all partitions using Gparted - and ran a new install of 10.04. Still the same problem: I get no further than the error message 

error: out of disk.
grub rescue>

I have followed all three methods in [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD) but still my system stops with the grub rescue>.

In the link there is also a header "Grub shows rescue prompt (and does not continue to boot)" which suggests I may have a problem with my Bios etc. But the information there is too short for me to know what to do, I need a step-by-step instruction.

I have also tried to run the lines in grub rescue, suggested in the same link. I get stuck there, however:

ls gives me 
(hd0) (hd0,1)

set prefix=(hdX,Y)/boot/grub
returns no error

set root=(hdX,Y)
returns no error

set responds with the prefix as above, and with root set to root=hd0,1

But when I issue
ls /boot
I get the response
error: out of disk

I can, however, list the disk contents with
ls (hd0,1)/

I am rather inexperienced with Ubuntu but have managed to install it with MythTV a couple times in the past. But this bootup-problem seems far above my head. Is there anyone with some ideas on what I can try?

---

### Post by Rubi1200 on 2010-08-30
Take a look here and see if anything helps:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Out_Of_Disk)

---

### Post by abrav on 2010-08-30
Thanks, Rubi1200, but I do not manage to end up in the (normal) grub menu. I tried both holding down shift and <ESC>, but in both cases I come to the error: out of disk.

---

### Post by Rubi1200 on 2010-08-30
Strange! Even a fresh install didn't help? Did you by chance have a RAID setup previously?

---

### Post by oldfred on 2010-08-30
You are not actually typing set root =(hdX,Y) are you?

The X is the drive or 0 and the y is the partition or 1 in your case from the ls command.

so 

#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition
insmod ext2
set root=(hd0,1)
# in the next command sda1 represents (hd0,1), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sda1 ro 
initrd /initrd.img
boot
Install grub to MBR after booting:
sudo grub-install /dev/sda
sudo update-grub

---

### Post by oldfred on 2010-08-30
Duplicate post, sorry.

---

### Post by abrav on 2010-08-30
Rubi1200: No, the only disk in the computer is a 340 MB SCSI disk.

oldfred: No, I type 
set root=(hd0,1)
sorry about that, I copied the text from the link.

I have tried the insmod and linux commands, but the response is something like 
command not found

(do not have my computer handy right now)

I will try your suggestions and get back as soon as I can.

---

### Post by abrav on 2010-08-30
OK, I have tried the suggestions you had, Oldfred. Try explaining this to me:

ls returns
(hd0) (hd0,1)

ls (hd0,1)/ returns
a list of directories (./ ../ lost+found ...)

ls (hd0,1)/boot and ls (hd0,1)/boot/
both return
error: out of disk.


I also went ahead and executed 
insmod ext2
no error message
set root=(hd0,1)
no error message
linux /vmlinuz root=/dev/sda1 ro
Unknown command 'linux'

I hope you have some  good ideas.

---

### Post by oldfred on 2010-08-30
Lets see what this shows:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by abrav on 2010-08-30
Ok, here goes

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   476,332,031   476,329,984  83 Linux
/dev/sda2         476,334,078   488,396,799    12,062,722   5 Extended
/dev/sda5         476,334,080   488,396,799    12,062,720  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2112 MB, 2112356352 bytes
255 heads, 63 sectors/track, 256 cylinders, total 4125696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     4,112,639     4,112,608   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        0c52c4ed-0fc5-49ad-b20f-0678986e7287   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d1db7ecd-6bb2-44de-a5da-155b03c50408   swap                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        4C7B-A925                              vfat       FREE-DOS                      
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FREE-DOS          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0c52c4ed-0fc5-49ad-b20f-0678986e7287
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0c52c4ed-0fc5-49ad-b20f-0678986e7287
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c52c4ed-0fc5-49ad-b20f-0678986e7287
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0c52c4ed-0fc5-49ad-b20f-0678986e7287 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c52c4ed-0fc5-49ad-b20f-0678986e7287
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=0c52c4ed-0fc5-49ad-b20f-0678986e7287 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c52c4ed-0fc5-49ad-b20f-0678986e7287
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0c52c4ed-0fc5-49ad-b20f-0678986e7287
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0c52c4ed-0fc5-49ad-b20f-0678986e7287 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d1db7ecd-6bb2-44de-a5da-155b03c50408 none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


 240.6GB: boot/grub/core.img
 240.6GB: boot/grub/grub.cfg
 240.6GB: boot/initrd.img-2.6.32-24-generic
 240.6GB: boot/vmlinuz-2.6.32-24-generic
 240.6GB: initrd.img
 240.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 56 6c 61 44 4f  53 20 20 00 02 08 22 00  |.X.VlaDOS  ...".|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 20 00 00 00  |........?... ...|
00000020  e4 c0 3e 00 a9 0f 00 00  00 00 00 00 02 00 00 00  |..>.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 25 a9 7b 4c 46  52 45 45 2d 44 4f 53 20  |..)%.{LFREE-DOS |
00000050  20 20 46 41 54 33 32 20  20 20 b8 e0 1f b9 00 7c  |  FAT32   .....||
00000060  fa 8e d0 8b e1 fb 8b f1  8b f9 8e c0 50 33 c0 8e  |............P3..|
00000070  d8 b8 03 7d 50 b9 00 02  fc f3 a4 cb 00 00 10 00  |...}P...........|
00000080  01 00 00 00 60 00 9c 1f  59 00 00 00 00 00 0d 0a  |....`...Y.......|
00000090  4c 6f 61 64 69 6e 67 20  46 72 65 65 44 4f 53 20  |Loading FreeDOS |
000000a0  6b 65 72 6e 65 6c 20 2e  2e 2e 00 4f 6b 2e 0d 0a  |kernel ....Ok...|
000000b0  53 74 61 72 74 69 6e 67  20 46 72 65 65 44 4f 53  |Starting FreeDOS|
000000c0  20 2e 2e 2e 0d 0a 00 0d  0a 45 72 72 6f 72 20 6c  | ........Error l|
000000d0  6f 61 64 69 6e 67 20 46  72 65 65 44 4f 53 20 6b  |oading FreeDOS k|
000000e0  65 72 6e 65 6c 21 20 50  72 65 73 73 20 61 6e 79  |ernel! Press any|
000000f0  20 6b 65 79 20 74 6f 20  72 65 62 6f 6f 74 20 2e  | key to reboot .|
00000100  2e 2e 00 0e 1f be 8e 7c  e8 cb 00 2e 8b 0e 88 7c  |.......|.......||
00000110  2e c7 06 88 7c 00 00 51  b4 41 bb aa 55 cd 13 59  |....|..Q.A..U..Y|
00000120  72 35 81 fb 55 aa 75 2f  be 7e 7c 51 b8 00 42 cd  |r5..U.u/.~|Q..B.|
00000130  13 59 72 17 2e 81 06 82  7c 00 02 2e 83 16 84 7c  |.Yr.....|......||
00000140  00 2e ff 06 86 7c e2 e3  eb 7c 90 be c7 7c e8 85  |.....|...|...|..|
00000150  00 33 c0 cd 16 cd 19 51  52 b4 08 cd 13 80 e1 3f  |.3.....QR......?|
00000160  8a d9 fe c6 8a fe 5a 59  72 e1 80 fb 00 74 dc 2e  |......ZYr....t..|
00000170  89 1e 7c 7c 2e 8b 1e 84  7c 8e c3 33 db 51 53 52  |..||....|..3.QSR|
00000180  33 d2 2e a1 86 7c 2e 8b  1e 7c 7c 32 ff f7 f3 8b  |3....|...||2....|
00000190  ca 41 33 d2 2e 8b 1e 7c  7c 8a df 32 ff f7 f3 8b  |.A3....||..2....|
000001a0  da 8a e8 80 e4 c0 02 cc  5a 8a f3 5b b8 01 02 cd  |........Z..[....|
000001b0  13 59 72 97 81 c3 00 02  8c c0 15 00 00 8e c0 2e  |.Yr.............|
000001c0  ff 06 86 7c e2 b7 be ab  7c e8 0a 00 8a da b8 60  |...|....|......`|
000001d0  00 50 33 c0 50 cb b4 0e  ac 3c 00 74 04 cd 10 eb  |.P3.P....<.t....|
000001e0  f7 c3 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by oldfred on 2010-08-30
As near as I can tell script looks normal. I thought there might be some partition or format type error that caused a reading error. 

If this perhaps a new larger hard drive in an older system. Some old systems could not boot from partitions beyond about 137GB?

Have you tried reinstalling grub2 to the MBR. If though it looks correct sometimes reinstalling fixes something.

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by abrav on 2010-08-31
I had tried that as part of the procedures described at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2). I tried it again now, and the grub-install finishes with a message that there were no errors. But the same results at bootup.

In the link just quoted, there is a short passage under the title "Grub shows rescue prompt (and does not continue to boot)" which says there might be a buggy bios involved. Could that be it? I do not understand, however, how to go about to create that small partition they talk about. Could you give me a step-by-step instruction of what I should run to implement the suggestion there?

I appreciate the work you put in to help me. It is rather frustrating that a fresh install of 10.04 does not work on my machine.

I want to stress that my machine was functional under 9.10 up until a few days ago, except for the networking problems I  had with the wireless card. (I btw seem to have the same problems in 10.04 running off the LiveCD, but that is a later question...) So I think it is fair to rule out most hardware related issues?

---

### Post by oldfred on 2010-08-31
If 9.10 worked then I do not think you need the boot partition and it is not an old BIOS issue. Sometimes BIOS issues can make a difference. We keep finding new versions that use the BIOS settings where old versions and windows ignored the settings and worked before. you might check if something is not standard, but I do not know all the correct settings.

Lets first try chrooting into your system from a liveCD and totally reinstalling grub2 and housecleaning, updating.

to chroot:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda1 to correct partition
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Then once in chroot of your system
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by abrav on 2010-08-31
I am afraid I get stuck on the first line of commands. There is no /etc/resolv.conf on my LiveCD. What should I do?

---

### Post by oldfred on 2010-08-31
I cannot easily look at my install cD as it still is an ISO. But I have a resolv.conf in my system.

That was added because sometimes you could not get INTERNET connection without it. You could try without. You are just running the ling command not the comments?

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev  && sudo mount --bind /proc /mnt/proc && sudo mount  --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf  /mnt/etc/resolv.conf && sudo chroot /mnt
```

---

### Post by abrav on 2010-09-02
I have a problem connecting to Internet also. Could that be because of my missing resolv.conf? That file should be in /etc when I have booted from the LiveCD, should it not? Simply not there, and without Internet I cannot run the upgrade.

---

### Post by abrav on 2010-09-05
I finally gave up trying and loaded the installation on a USB stick and reinstalled after deleting all partitions. After the new installation ubuntu works.

---

### Post by oldfred on 2010-09-05
Sometimes reinstall is the best fix.

Glad you got it working.

---

### Post by abrav on 2010-09-06
should I mark this thread as solved? It kind of was not through any information given here?

---

