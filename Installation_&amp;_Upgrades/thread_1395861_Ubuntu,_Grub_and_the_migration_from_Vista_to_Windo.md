---
title: "Ubuntu, Grub and the migration from Vista to Windows 7"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by laur3ooo on 2010-02-01
In an attempt to forgo Windows forever that lasted almost 4 months I installed Ubuntu 9.10 on my first hdd with special partitions for my root, home, music dirs. I installed Ubuntu having both of my hdd's connected. All went well. 2 weeks ago i decided i needed Windows once more so i removed my 1st hdd that had Ubuntu installed on it so as to install Windows 7 on the 2nd hdd and not to have my grub corrupted. It seemed Windows 7 had problems installing from a sata optical drive or something because it couldn't find the drivers for a storage device (even though i provided all the drivers relevant to my motherboard). After that i tried to install Windows Vista with the intent to upgrade to windows 7. I installed Vista on my second hdd without problems. After i made sure it installed properly and i did a clean boot of the system i plugged in my Ubuntu hdd and i wasn't surprised Ubuntu booted without an option for Vista. This was expected behaviour. We all know GRUB is, by defaut, in "quiet mode" on Karmic so i "unhid" the GRUB and added an option for Windows Vista and all was well again. Sometime after this i was planning to upgrade to Windows 7 because my clean install wouldn't work. So i removed once again my Ubuntu HDD to do an upgrade so as not to screw up GRUB or the MBR.

I then started the Windows install from within Vista with the intent to do a full upgrade and replace procedure but i was again haunted by issues. I was faced with SPWIZENG.DLL and autorun.dll errors when i stared the install and this seemed weird since my Vista and Windows 7 iso files come from my MSDN account. I got the same error after i re downloaded and reburned the Win 7 iso. So after some web documenting i used the (official Microsoft) tool that allows the transfer from an iso to a bootable usb stick. I started the upgrade from the stick and all went without problems. After i made sure all my Vista profile settings and files are on Windows 7 and i made sure it overwrote the Vista installation i did a clean boot of the system and after that i connected my first hdd.

Now i get some unnexpected behaviour. Since both of my Windows installs occured on the second hdd and without the Ubuntu one attached i was expecting to have Grub popup and default boot to Ubuntu (the situation was true for Vista). But i was surprised when the system booted showed a short MBR Error 3 message and booted to Windows 7. This might have ben expected if i installed Win 7 with the Ubuntu hdd conected but it was not the case. Even weirder is the fact that if i remove my Ubuntu Hdd Win7 boots without that MBR Error 3 message and if i remove my Windows hdd and plugin the Ubuntu one it boots without problems also. This behaviour might suggest i have Windows 7 on my primary hdd and and Ubuntu ont the secondary but it is the other way around.

Also both hdds are SATA set to IDE mode from the BIOS so it is not master vs slave cabling issue.

Thanks in advance and please read all of my post before suggesting something.

---

### Post by darkod on 2010-02-01
With more than one hdd it is important not only which OS is where, but also which bootloader you have on which disk. Very often you think one, and the actual situation is another.
Boot with the ubuntu cd (or usb stick) into the live desktop, download the script in my signature, move it on desktop for example and execute it in terminal with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Copy the content here and wrap it in CODE tags (with the text selected hit the # button in the toolbar above).

---

### Post by laur3ooo on 2010-02-01
```
============================= Boot Info Summary: ==============================

 => No known boot loader is installed in the MBR of /dev/sda
sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /etc/fstab

sda10: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda10 and 
                       looks at sector 28437038 of the same hard drive for 
                       core.img, core.img is at this location on /dev/sda and 
                       looks on partition #10 for /grub.
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/grub.conf /grub/core.img

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda11 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5e0522ca

Partition  Boot         Start           End          Size  Id System

/dev/sda2    *             63   488,392,064   488,392,002   f W95 Ext d (LBA)
/dev/sda5          76,999,545   188,249,669   111,250,125   b W95 FAT32
/dev/sda6         188,249,733   288,945,089   100,695,357   b W95 FAT32
/dev/sda7         288,945,153   488,392,064   199,446,912   b W95 FAT32
/dev/sda8                 189     6,297,479     6,297,291  82 Linux swap / Solaris
/dev/sda9           6,297,543    27,262,304    20,964,762  83 Linux
/dev/sda10   *     27,262,368    28,627,829     1,365,462  83 Linux
/dev/sda11         76,742,568    76,999,544       256,977   b W95 FAT32
/dev/sda12         28,627,893    76,742,504    48,114,612  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda10       478ac052-5924-477b-a42e-d68bc11b3301   ext2                                     
/dev/sda11       6A12-194D                              vfat       ACRONIS OS                    
/dev/sda12       4bd1707f-3634-4cd0-8b6c-8882bc94caea   ext4                                     
/dev/sda5        5F81-7889                              vfat                                     
/dev/sda6        69C6-D703                              vfat       PROGRAME                      
/dev/sda7        53A1-DA2B                              vfat       Jocuri                        
/dev/sda8        945cddf8-9997-4651-85b1-335e7c1c1256   swap                                     
/dev/sda9        124a2ddf-8ffc-4755-9eda-31b3797938a8   ext4                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda9        /                        ext4       (rw,errors=remount-ro)
/dev/sda10       /boot                    ext2       (rw)
/dev/sda12       /home                    ext4       (rw)
/dev/sda5        /home/roman/Muzic&#259;      vfat       (rw,utf8,umask=007,gid=46)
/dev/sda7        /media/jocuri            vfat       (rw,utf8,umask=007,gid=46)
/dev/sda6        /media/programe          vfat       (rw,utf8,umask=007,gid=46)


=============================== sda9/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda9 during installation
UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda10 during installation
UUID=478ac052-5924-477b-a42e-d68bc11b3301 /boot           ext2    defaults        0       2
# /home was on /dev/sda12 during installation
UUID=4bd1707f-3634-4cd0-8b6c-8882bc94caea /home           ext4    defaults        0       2
# /home/roman/Muzic&#259; was on /dev/sda5 during installation
UUID=5F81-7889  /home/roman/Muzic&#259; vfat    utf8,umask=007,gid=46 0       1
# /media/jocuri was on /dev/sda7 during installation
UUID=53A1-DA2B  /media/jocuri   vfat    utf8,umask=007,gid=46 0       1
# /media/programe was on /dev/sda6 during installation
UUID=69C6-D703  /media/programe vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda8 during installation
UUID=945cddf8-9997-4651-85b1-335e7c1c1256 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

============================= sda10/grub/grub.cfg: =============================

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
set root=(hd0,9)
search --no-floppy --fs-uuid --set 124a2ddf-8ffc-4755-9eda-31b3797938a8
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 478ac052-5924-477b-a42e-d68bc11b3301
	linux	/vmlinuz-2.6.31-17-generic root=UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 ro   quiet splash
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 478ac052-5924-477b-a42e-d68bc11b3301
	linux	/vmlinuz-2.6.31-17-generic root=UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 ro single 
	initrd	/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 478ac052-5924-477b-a42e-d68bc11b3301
	linux	/vmlinuz-2.6.31-16-generic root=UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 ro   quiet splash
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 478ac052-5924-477b-a42e-d68bc11b3301
	linux	/vmlinuz-2.6.31-16-generic root=UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 ro single 
	initrd	/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 478ac052-5924-477b-a42e-d68bc11b3301
	linux	/vmlinuz-2.6.31-14-generic root=UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 478ac052-5924-477b-a42e-d68bc11b3301
	linux	/vmlinuz-2.6.31-14-generic root=UUID=124a2ddf-8ffc-4755-9eda-31b3797938a8 ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sdb2)" {
	insmod ntfs
	set root=(hd1,2)
	search --no-floppy --fs-uuid --set b45879265878e88e
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================ sda10/grub/grub.conf: ============================

title Windows Vista
    rootnoverify (hd1,0)
    map (hd0) (hd1)
    map (hd1) (hd0)
    chainloader +1


=================== sda10: Location of files loaded by Grub: ===================


  13.9GB: grub/core.img
  13.9GB: grub/grub.cfg
  13.9GB: grub/grub.conf
  13.9GB: initrd.img-2.6.31-14-generic
  13.9GB: initrd.img-2.6.31-16-generic
  13.9GB: initrd.img-2.6.31-17-generic
  13.9GB: vmlinuz-2.6.31-14-generic
  13.9GB: vmlinuz-2.6.31-16-generic
  13.9GB: vmlinuz-2.6.31-17-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sda

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 a0 fd 9f 01 00 00  |.......|........|
000001b0  00 00 80 00 00 35 0e 00  ca 22 05 5e 52 00 00 00  |.....5...".^R...|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 01  |................|
000001d0  01 00 0f fe ff ff 3f 00  00 00 42 45 1c 1d 00 00  |......?...BE....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```
Now that i've looked at this log file i remebered i put the Ubuntu boot files in the /boot partition and i used to have Acronis OSS installed at some point but it would not recognize Vista or Windows 7 so i uninstalled it and pointed the default boot to Ubuntu. After that i edited grub to put a Vista option also. Also this script was run without the second hdd attached cause else i can not boot Ubuntu.

---

### Post by darkod on 2010-02-01
You should have left the other hdd connected too. That's why I said to boot with ubuntu cd, you should be able to boot the cd and the live desktop regardless of the bootloader mess on the hdds.
OK, so since it looks like you have / on /dev/sda9, /boot on /dev/sda10 and no bootloader on the sda MBR at all (it seems to be installed on /dev/sda10 instead), you could try this:

Connect the other hdd or not, your choice. Boot with the ubuntu cd, Try Ubuntu option, and in terminal execute:

sudo mount /dev/sda9 /mnt
sudo mount /dev/sda10 /mnt/boot
sudo grub-install --root-directory=/mnt/ /dev/sda

That will put grub2 on the MBR of /dev/sda, where you want it. There was no need to force grub2 to get installed on /dev/sda10, the boot partition.
If you reboot without the cd that should enable you to boot ubuntu. Even when you connect the other hdd it should still allow you to boot ubuntu as long as sda is the first hdd in boot order in BIOS.

PS. Why all these FAT32 partitions? Ubuntu can read/write NTFS just fine, and also windows can access them. Any shared partitions are better to be NTFS.

---

### Post by laur3ooo on 2010-02-01
Yes i realize now i was better off installing grub to /sda rather than /sda10 but i wanted to install it there so as to do as little modifications as possible to any boot record of either OS by using an external Bootloader like Acronis OSS or GAG. I have since given up on that prospect and think that modifing GRUB config files to my liking would be an easier alternative.

Those FAT32 partiutions are old partitions, older than most of the others if you look at the extended partition number assigned to them. I dreaded to convert them before i installed Ubuntu because of time restraints and dread to convert them now because i'm too lazy to research how to modifiy the fstab file corectly after i convert. :)

---

