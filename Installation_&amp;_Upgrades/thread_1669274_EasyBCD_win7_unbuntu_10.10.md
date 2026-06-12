---
title: "EasyBCD win7 unbuntu 10.10"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by kbz1960 on 2011-01-17
Hi, I have everything installed following this guide. I read ahead and planned for this.
 
[http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/](http://www.linuxbsdos.com/2010/11/04/how-to-dual-boot-ubuntu-10-10-and-windows-7/)
 
I paid attention to this part in paticular.
 
> 
**[B]Note: It has been reported that Windows 7 tends to mess with the GRUB menu after a Windows update/upgrade. To avoid any issue that might arise from that, you need to install GRUB to the boot partition of the Ubuntu installation, then use EasyBCD to edit the Windows boot menu and add an entry for Ubuntu. This method was used in [[COLOR=#154a7f]how to dual-boot Fedora 14 and Windows 7[/COLOR]]("http://www.linuxbsdos.com/2010/11/09/how-to-dual-boot-fedora-14-and-windows-7/").**[/B]
 
So I followed these instructions
> 
The next step relevant to this tutorial is the boot loader configuration step. The boot loader used by Fedora 14 is GRUB Legacy. By default, it is installed in the Master Boot Record (MBR). What we want to do here is install it some place else, and the best alternative location to install GRUB, the GRand Unified Bootloader, is in the /boot partition (/dev/sda3) of the Fedora installation. The reason behind this choice of location is this: If it is installed in the usual location, Windows will likely overwrite parts of it the next time you upgrade/update Windows.
and installed GRUB in my /dev/sda2 which I made my /boot partition.
 
Following the directions in that link for EasyBCD knowing that Ubuntu 10.10 uses GRUB 2 and not legacy thinking it would still work the same.
> 
When in the *Add New Entry* tab, click on the *Linux* tab as shown. The two entries that we need to tweak here are in the Type and Device dropdown menus. **Since Fedora 14 uses GRUB Legacy as the boot loader, select that in the Type menu. Then select the partition you installed GRUB into from the Device menu.** In this example, GRUB (Legacy) was installed on the third primary partition, /dev/sda3, which is the /boot partition of the Fedora installation. With those completed, click on *Add Entry*, then on the Edit Menu tab to see what the new Windows boot menu looks like.
 
When I substitue GRUB 2 in place of GRUB (legacy) in the type box then the "device" button isn't clickable to direct it to where I have GRUB installed to add it.
 
What am I doing wrong or is not possible? If not possible they need to change the directions.
 
Thanks

---

### Post by wilee-nilee on 2011-01-17
Honestly unless you have to use easybcd it is a waste of time. Having a boot partition is not needed grub-legacy needs to be messed with grub2 is rather automatic.

You may need to try the easybcd forums for help, a few use it on this forum, but not many know the whole setup well enough to help you, probably. If you might consider that easybcd is not needed post the boot script in my signature link and wrap it in code tags as suggested in the signature.

---

### Post by kbz1960 on 2011-01-17
Well it went with just letting Grub do it's thing the first time and then I couldn't boot into windows.

---

### Post by wilee-nilee on 2011-01-17
> **kbz1960 said:**
> Well it went with just letting Grub do it's thing the first time and then I couldn't boot into windows.

Okay but you did not ask for help in your own thread in getting grub to work. does this make sense it may have just been something such as not resizing the Windows first and making sure it reboots. As it is I don't know enough about easybcd to help. If you want to run grub2 I can help, just giving you this option.

Personally I don't care what you use to boot with, I was just trying to let you know the limitations for help with easybcd on the UF.

---

### Post by wilee-nilee on 2011-01-17
> **kbz1960 said:**
> Well it went with just letting Grub do it's thing the first time and then I couldn't boot into windows.

Okay but you did not ask for help in your own thread in getting grub to work. Does this make sense it may have just been something such as not resizing the Windows first and making sure it reboots. As it is I don't know enough about easybcd to help. If you want to run grub2 I can help, just giving you this option.

Personally I don't care what you use to boot with, I was just trying to let you know the limitations for help with easybcd on the UF.

---

### Post by kbz1960 on 2011-01-17
> **wilee-nilee said:**
> Okay but you did not ask for help in your own thread in getting grub to work. Does this make sense it may have just been something such as not resizing the Windows first and making sure it reboots. As it is I don't know enough about easybcd to help. If you want to run grub2 I can help, just giving you this option.
 
Personally I don't care what you use to boot with, I was just trying to let you know the limitations for help with easybcd on the UF.
 
Din't mean anything by it but I've read so much about dual booting with win7 and linux not getting along and I experienced it. It was a new install of Ubuntu so I found the links and just redid it that way to avoid such problems. I even redid my windows to start all over.
 
I'll head on over to the easybcd forum and see if they have any help there if not I'd like your help if you're willing.
 
Thanks for the replies.

---

### Post by wilee-nilee on 2011-01-17
> **kbz1960 said:**
> Din't mean anything by it but I've read so much about dual booting with win7 and linux not getting along and I experienced it. It was a new install of Ubuntu so I found the links and just redid it that way to avoid such problems. I even redid my windows to start all over.
 
I'll head on over to the easybcd forum and see if they have any help there if not I'd like your help if you're willing.
 
Thanks for the replies.

No problem, there are very little problems with grub2 and windows here is my set up W7, and 3 Linux installs, on one HD, all booted with grub2. You will see problems, I mean who is posting success, on problems, same thing at the esaybcd forum they are biased to easybcd.

I have to read multiple papers today and write a paper so I will try to help If I can, but there are others who know this stuff, many actually.:)

---

### Post by kbz1960 on 2011-01-17
> **wilee-nilee said:**
> No problem, there are very little problems with grub2 and windows here is my set up W7, and 3 Linux installs, on one HD, all booted with grub2. You will see problems, I mean who is posting success, on problems, same thing at the esaybcd forum they are biased to easybcd.
 
I have to read multiple papers today and write a paper so I will try to help If I can, but there are others who know this stuff, many actually.:)
 
Well life happened for awhile LOL and I just posted over there. So since I've all ready installed by the directions in the link would I have to start all over again? When I let GRUB take over the booting last time I was able to get windows a couple times but the next time I tried it wouldn't start and I had to try the repair for windows and that wasn't working so I just reinstalled everything. I had just backed up so was not a big deal except for the time it takes.

---

### Post by wilee-nilee on 2011-01-17
> **kbz1960 said:**
> Well life happened for awhile LOL and I just posted over there. So since I've all ready installed by the directions in the link would I have to start all over again? When I let GRUB take over the booting last time I was able to get windows a couple times but the next time I tried it wouldn't start and I had to try the repair for windows and that wasn't working so I just reinstalled everything. I had just backed up so was not a big deal except for the time it takes.

Generally this is a fairly easy fix without reinstalling, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

Do this so we can see what is where. 

So when you boot the live Ubuntu cd go to system-admin-gparted, open it and take a screen shot and post it as well. It will also be helpful to see this and if there are any flags in gparted on the windows partitions. Load the image using the paper-clip in the reply panel to upload the image, and place it in the reply. I'm looking to make sure that Windows can be read by Ubuntu, and is not in need of a chkdsk.

I got all my reading done and my paper written so I'm just hanging again.

---

### Post by kbz1960 on 2011-01-17
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sdb
 => Syslinux is installed in the MBR of /dev/sdc

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *          2,048   143,362,047   143,360,000   7 HPFS/NTFS
/dev/sdb2         143,362,048   286,722,047   143,360,000  83 Linux
/dev/sdb3         286,722,048   488,396,799   201,674,752   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 2055 MB, 2055019008 bytes
255 heads, 63 sectors/track, 249 cylinders, total 4013709 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63     4,013,708     4,013,646   6 FAT16


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sdb1        1DE8137C5FBBCB59                       ntfs                                     
/dev/sdb2        cae1e033-9c15-49c5-a41f-fcd4f0810611   ext4                                     
/dev/sdb3        0325247F27F17AE0                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        B096-D191                              vfat       PENDRIVE                      
/dev/sdc: PTTYPE="dos" 
error: /dev/sda: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdc1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sdb2/grub/grub.cfg: =============================

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
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 32d57514-c326-4924-b9c3-d72754331426
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set cae1e033-9c15-49c5-a41f-fcd4f0810611
set locale_dir=($root)/grub/locale
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
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set cae1e033-9c15-49c5-a41f-fcd4f0810611
    linux    /vmlinuz-2.6.35-22-generic root=UUID=32d57514-c326-4924-b9c3-d72754331426 ro   quiet splash
    initrd    /initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set cae1e033-9c15-49c5-a41f-fcd4f0810611
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /vmlinuz-2.6.35-22-generic root=UUID=32d57514-c326-4924-b9c3-d72754331426 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set cae1e033-9c15-49c5-a41f-fcd4f0810611
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set cae1e033-9c15-49c5-a41f-fcd4f0810611
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 1de8137c5fbbcb59
    chainloader +1
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

=================== sdb2: Location of files loaded by Grub: ===================


  73.5GB: grub/core.img
  73.5GB: grub/grub.cfg
  73.4GB: initrd.img-2.6.35-22-generic
  73.4GB: vmlinuz-2.6.35-22-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdc1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 40 06 00  |.X.SYSLINUX..@..|
00000010  02 00 02 00 00 f8 f5 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  4e 3e 3d 00 80 00 29 91  d1 96 b0 4e 4f 20 4e 41  |N>=...)....NO NA|
00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 33 c9  |ME    FAT16   3.|
00000040  8e d1 bc f0 7b 8e d9 b8  00 20 8e c0 fc bd 00 7c  |....{.... .....||
00000050  38 4e 24 7d 24 8b c1 99  e8 3c fa fc 31 c9 8e d1  |8N$}$....<..1...|
00000060  bc 76 7b 52 06 57 8e c1  b1 26 bf 78 7b f3 a5 8e  |.v{R.W...&.x{...|
00000070  d9 bb 78 00 0f b4 37 0f  a0 56 20 d2 78 1b 31 c0  |..x...7..V .x.1.|
00000080  b1 06 89 3f 89 47 02 f3  64 a5 8a 0e 18 7c 88 4d  |...?.G..d....|.M|
00000090  bc 50 50 50 50 cd 13 eb  4b f6 45 b4 7f 75 25 38  |.PPPP...K.E..u%8|
000000a0  4d b8 74 20 66 3d 21 47  50 54 75 10 80 7d b8 ed  |M.t f=!GPTu..}..|
000000b0  75 0a 66 ff 75 ec 66 ff  75 e8 eb 0f 51 51 66 ff  |u.f.u.f.u...QQf.|
000000c0  75 bc eb 07 51 51 66 ff  36 1c 7c b4 08 cd 13 72  |u...QQf.6.|....r|
000000d0  13 20 e4 75 0f c1 ea 08  42 89 16 1a 7c 83 e1 3f  |. .u....B...|..?|
000000e0  89 0e 18 7c fb bb aa 55  b4 41 8a 16 74 7b cd 13  |...|...U.A..t{..|
000000f0  72 10 81 fb 55 aa 75 0a  f6 c1 01 74 05 c6 06 32  |r...U.u....t...2|
00000100  7d 00 66 b8 50 c5 01 00  66 ba 00 00 00 00 bb 00  |}.f.P...f.......|
00000110  7e e8 10 00 66 81 3e 24  7e 34 be f5 72 75 76 ea  |~...f.>$~4..ruv.|
00000120  38 7e 00 00 66 03 06 64  7b 66 13 16 68 7b b9 10  |8~..f..d{f..h{..|
00000130  00 eb 2b 66 52 66 50 06  53 6a 01 6a 10 89 e6 66  |..+fRfP.Sj.j...f|
00000140  60 b4 42 e8 7f 00 66 61  8d 64 10 72 01 c3 66 60  |`.B...fa.d.r..f`|
00000150  31 c0 e8 70 00 66 61 e2  da c6 06 32 7d 2b 66 60  |1..p.fa....2}+f`|
00000160  66 0f b7 36 18 7c 66 0f  b7 3e 1a 7c 66 f7 f6 31  |f..6.|f..>.|f..1|
00000170  c9 87 ca 66 f7 f7 66 3d  ff 03 00 00 77 17 c0 e4  |...f..f=....w...|
00000180  06 41 08 e1 88 c5 88 d6  b8 01 02 e8 37 00 66 61  |.A..........7.fa|
00000190  72 01 c3 e2 c9 31 f6 8e  d6 bc 6c 7b 8e de 66 8f  |r....1....l{..f.|
000001a0  06 78 00 be cc 7d e8 09  00 31 c0 cd 16 cd 19 f4  |.x...}...1......|
000001b0  eb fd 66 60 ac 20 c0 74  09 b4 0e bb 07 00 cd 10  |..f`. .t........|
000001c0  eb f2 66 61 c3 8a 16 74  7b cd 13 c3 42 6f 6f 74  |..fa...t{...Boot|
000001d0  20 65 72 72 6f 72 0d 0a  00 00 00 00 00 00 00 00  | error..........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sda 

```

---

### Post by kbz1960 on 2011-01-17
If it would be easier I can just reinstall Ubuntu if you have a better way to install it. I would really like to check it out and see how it runs. Don't think you get a good idea of how it runs off of the live usb or running in a virtural machine or inside of windows.

---

### Post by wilee-nilee on 2011-01-17
> **kbz1960 said:**
> If it would be easier I can just reinstall Ubuntu if you have a better way to install it. I would really like to check it out and see how it runs. Don't think you get a good idea of how it runs off of the live usb or running in a virtural machine or inside of windows.

Your missing the fstab in Ubuntu that is part of the boot, and may have gotten misplaced, I'm not sure how to slip that in.

So yeah a reinstall would be good delete that Ubuntu partition and make another ext4 leaving room for a swap if you want to hibernate in Ubuntu with gparted. The swap is another type of partition in the dropdown and should be equal to your ram. This will put you at the maximum of 4 primary partitions but in a workable setup.

I assume that since you installed before that you know to use the manual, set up.

Ask any more questions if needed. Windows looks good, no flags for work on it in gparted.

---

### Post by kbz1960 on 2011-01-17
Huh, that's odd. When I partitioned I made 
/dev/sda2 /boot
/dev/sda5 swap
/dev/sda6 /
/dev/sda7 /home.
 
It's bedtime for me so will have to wait until I get home from work tomorrow. I actually started out the first time following instructions for an 9. something version but didn't notice that until after I had it done. I have a data partion that I wanted to be able to use with Ubuntu also and that was part of the requirement.
 
If you have a better partioning scheme please let me know.
 
 
Thanks for all the help.

---

### Post by wilee-nilee on 2011-01-17
> **kbz1960 said:**
> Huh, that's odd. When I partitioned I made 
/dev/sda2 /boot
/dev/sda5 swap
/dev/sda6 /
/dev/sda7 /home. 
 
It's bedtime for me so will have to wait until I get home from work tomorrow. I actually started out the first time following instructions for an 9. something version but didn't notice that until after I had it done. I have a data partion that I wanted to be able to use with Ubuntu also and that was part of the requirement.
 
If you have a better partioning scheme please let me know.
 
 
Thanks for all the help.

I will not be available tomorrow very much but there are many others that can help.

So the script only shows the sdb HD, and a sdc, I assume the sdc is a thumb or pendrive to boot with I believe.

With what you show me I see two NTFS sdb1 would be C, sdb2 is the Ubuntu, and sdb3 is a NTFS probably the data. From looking at the partitions from the script and gparted.

When you boot with a thumb sometimes it switches how the partitions are read, so the sdb is probably actually sda, without the thumb booting.

---

### Post by kbz1960 on 2011-01-18
Can a mode mark this as dead cause I reinstalled and now have another problem that I will start a new thread on.
 
Thanks

---

### Post by Pillars of Creation on 2011-01-20
First off I just want to say that setting up a dual-boot between Windows 7 and Ubuntu with Easy BCD is a snap.

But if you’re going to use Easy BCD you want documentation that is written for it. See below.

Ubuntu Easy BCD documentation:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

“Note: It has been reported that Windows 7 tends to mess with the GRUB menu after a Windows update/upgrade. To avoid any issue that might arise from that, you need to install GRUB to the boot partition of the Ubuntu installation, then use EasyBCD to edit the Windows boot menu and add an entry for Ubuntu. This method was used in how to dual-boot Fedora 14 and Windows 7.”

All of this is basically incorrect. With Ubuntu 10.04 or 10.10 you want to install GRUB-2 to the MBR at the front of the hard drive, not the partition on which Ubuntu is installed to. Also note that these versions of Ubuntu use GRUB-2. This makes setting up the option to boot into Ubuntu in Easy BCD exceedingly easy because you don’t have to know what partition Ubuntu is it. Easy BCD picks up the config file from the first Ubuntu with GRUB-2 that it runs into.

On the other hand Fedora uses GRUB-1. It is also easy to set up but in this case you do have to know the partition in which it is installed to when you make the option to boot into the OS in Easy BCD.

If you need help with Easy BCD post a question over at the NeoSmart Forums
[http://neosmart.net/forums](http://neosmart.net/forums)

---

### Post by kbz1960 on 2011-01-21
Thanks, I got the dual boot thing down but don't think linux likes my laptop.

---

