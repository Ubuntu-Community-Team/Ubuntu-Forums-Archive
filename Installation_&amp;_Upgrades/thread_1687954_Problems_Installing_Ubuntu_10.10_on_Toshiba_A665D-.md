---
title: "Problems Installing Ubuntu 10.10 on Toshiba A665D-S6051"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by rubensaid on 2011-02-14
Community! I'm a new user here and I'm trying to be a new Ubuntu User.
 
Today an Ubuntu 10.10 official CD arrived to my house and I tried to install it on my new Toshiba laptop ([http://us.toshiba.com/computers/laptops/satellite/A660/A665D-S6051](http://us.toshiba.com/computers/laptops/satellite/A660/A665D-S6051)), but a problem accurred..
 
I insert the CD, boot from that.... the language selector appears, select one, then I choose Install UBUNTU but a black screen appears with only a underline flashing...
It stays over 10 minuts...
 
Even if I choose another option like Try UBUNTU without install the same problem occurs
 
I hope someone helps me... I'm really interested in become an Ubuntu User
 
 
**Notes:** There's a Windows 7 Professional 32-bits in my laptop... but 4 partitions exist... 2 in NTFS (Windows' C and D), 1 in FAT32 (to shared files) and 1 unformatted to install UBUNTU
 
PD: I'm learning English so please excuse my wrong grammar.

---

### Post by lukeiamyourfather on 2011-02-14
Try the alternate installer which doesn't have a GUI, just a command line interface for the install.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by rubensaid on 2011-02-15
Thanks a lot!! I'll try it... but now I have a question...
 
Use the i386.iso or amd64.iso image, is it the same? My laptop has a amd x64 processor but I prefer to use x86 systems... is there any problem if I use the i386.iso image? could be this the problem?

---

### Post by Quackers on 2011-02-15
That shouldn't be a problem.
One thing I have noticed with a lot of Toshibas is that they need boot options (such as acpi=off, or other acpi related option) quite often. 
Also, what graphics card are you using?

---

### Post by rubensaid on 2011-02-15
Ummm I don't know anything about it.. (acpi)

About my laptop's Graphic Card

> AMD M880G Chipset with ATI Mobility Radeon&#8482; HD 4250 Graphics 
with 256MB-1917MB dynamically allocated shared graphics memory

You can see all information related with my laptop model on [http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A665D-S6051.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A665D-S6051.pdf)

---

### Post by rubensaid on 2011-02-19
wow... I downloaded the Alternate CD i386 to try to install UBUNTU again...
Unfortunately the same problem occurs...
 
I don't know why the CD's can not continue the installation...!
 
Anybody can help me, please?

---

### Post by Quackers on 2011-02-19
When booting from the live cd have you tried selecting "try ubuntu" rather than "install ubuntu"?
What happens then?

---

### Post by TomSerato on 2011-02-19
I had a similar problem with my Toshiba A135. 

When you boot the CD, hit any key at the keyboard image (little rectangle = man in circle). Then click F6 for Other Options. Check off the following options: acpi=off, noapic, nolapic and nomodeset. 

That should at least get you on your way.

See [http://ubuntuforums.org/showthread.php?p=10089820#post10089820](http://ubuntuforums.org/showthread.php?p=10089820#post10089820) for additional instructions.

---

### Post by rubensaid on 2011-02-20
@Quackers I get the same response for each option... (try ubuntu, install it,...)

@TomSerato I'm gonna try it... I hope it works for me too

Thanks everybody

/// RESULTS //

I'm following your advice and all seems very well...  I might change the post status to SOLVED in a moment

Thanks again!!

// FINALLY //

The installation finished succesfuly. My computer restarts and the select menu appears.. I select the first option to run UBUNTU but the underline in the dark screen appears again.

I'm very dissapointed... What do you think is happening?

---

### Post by rubensaid on 2011-02-20
OK, I've seen some post that seems to show the same problem and I noted that is very useful use de Boot Info Script.. so I've used it.

Here its content

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #8 for (,msdos8)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /BOOTMGR /BOOT/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda9: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros, 976773168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2           3,074,048   231,384,194   228,310,147   7 HPFS/NTFS
/dev/sda3         955,572,224   976,773,119    21,200,896  17 Hidden HPFS/NTFS
/dev/sda4         231,384,256   955,572,223   724,187,968   f W95 Ext d (LBA)
/dev/sda5         231,384,258   640,993,499   409,609,242   7 HPFS/NTFS
/dev/sda6         640,993,563   850,722,074   209,728,512   b W95 FAT32
/dev/sda7         953,573,376   955,572,223     1,998,848  82 Linux swap / Solaris
/dev/sda8         850,722,816   923,570,175    72,847,360  83 Linux
/dev/sda9         923,572,224   953,569,279    29,997,056  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        58BE7B4CBE7B2224                       ntfs       System                        
/dev/sda2        0AEEC054EEC039A9                       ntfs       LPR 1                         
/dev/sda3        F010C6A810C6755E                       ntfs       HDDRECOVERY                   
/dev/sda4: PTTYPE="dos" 
/dev/sda5        C444731544730986                       ntfs       LPR 2                         
/dev/sda6        14F4-3E04                              vfat       SHARED                        
/dev/sda7        eaa7c762-0840-486d-b8cf-cf526ee2b589   swap                                     
/dev/sda8        6e11b236-d741-4316-95a0-e4983bac9a2b   ext4                                     
/dev/sda9        bc43e5e9-ad58-452e-83db-90743d8bbf8f   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda5        /media/LPR 2             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda8/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 6e11b236-d741-4316-95a0-e4983bac9a2b
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos8)'
search --no-floppy --fs-uuid --set 6e11b236-d741-4316-95a0-e4983bac9a2b
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 6e11b236-d741-4316-95a0-e4983bac9a2b
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=6e11b236-d741-4316-95a0-e4983bac9a2b ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 6e11b236-d741-4316-95a0-e4983bac9a2b
    echo    'Loading Linux 2.6.35-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-25-generic-pae root=UUID=6e11b236-d741-4316-95a0-e4983bac9a2b ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 6e11b236-d741-4316-95a0-e4983bac9a2b
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos8)'
    search --no-floppy --fs-uuid --set 6e11b236-d741-4316-95a0-e4983bac9a2b
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 58be7b4cbe7b2224
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set f010c6a810c6755e
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

=============================== sda8/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=6e11b236-d741-4316-95a0-e4983bac9a2b /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda9 during installation
UUID=bc43e5e9-ad58-452e-83db-90743d8bbf8f /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=eaa7c762-0840-486d-b8cf-cf526ee2b589 none            swap    sw              0       0

=================== sda8: Location of files loaded by Grub: ===================


 457.1GB: boot/grub/core.img
 444.3GB: boot/grub/grub.cfg
 438.4GB: boot/initrd.img-2.6.35-25-generic-pae
 457.1GB: boot/vmlinuz-2.6.35-25-generic-pae
 438.4GB: initrd.img
 457.1GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  37 5e 07 e7 f1 89 11 df  f0 8b 6e 44 25 aa 08 12  |7^........nD%...|
00000010  57 e5 52 2f b9 75 f0 df  95 48 bd db 61 15 e9 45  |W.R/.u...H..a..E|
00000020  7d 69 4f 48 40 fc 16 71  1c d9 d5 dd 32 01 7b 01  |}iOH@..q....2.{.|
00000030  e2 e0 09 e8 0f 3d 0c aa  6a 42 bb fd b1 11 e8 56  |.....=..jB.....V|
00000040  5d 93 0a c4 15 86 d5 62  0d f7 3a 68 c8 1f 99 95  |]......b..:h....|
00000050  0a cf 7c d1 44 b6 5d 64  2b 9f 86 23 e9 1b 90 ae  |..|.D.]d+..#....|
00000060  7e 3b 58 94 f5 97 e8 1c  07 dd 77 bd 24 7a 40 69  |~;X.......w.$z@i|
00000070  98 37 97 3a 75 38 a9 9c  ab c9 95 fa c2 b6 97 50  |.7.:u8.........P|
00000080  72 38 0f e7 33 c8 b4 d2  b9 57 9e 96 11 a4 c6 37  |r8..3....W.....7|
00000090  2a 26 ad 84 7c 3c d3 e6  b8 7c 0f 58 fb 45 34 fe  |*&..|<...|.X.E4.|
000000a0  6a 26 b6 22 7a 6a ad 9a  22 69 fe c1 4d 53 d0 5a  |j&."zj.."i..MS.Z|
000000b0  06 3c db f7 1f 5e 7e f1  e2 db 9e 7e 87 9c 73 9f  |.<...^~....~..s.|
000000c0  1a 87 28 2a fd 53 e6 1d  ff af fa bb c3 75 d7 be  |..(*.S.......u..|
000000d0  bf dd 73 52 ef 03 32 3d  13 93 b4 55 fa e6 ee 4a  |..sR..2=...U...J|
000000e0  f0 27 ac bd 7d e5 94 d5  27 94 67 e2 02 5c 7b c7  |.'..}...'.g..\{.|
000000f0  80 fd 4a 66 76 47 71 af  5c 55 0f d0 37 1c a2 a9  |..JfvGq.\U..7...|
00000100  92 c2 66 b8 af 39 9f c7  87 39 6f 71 49 03 9c 03  |..f..9...9oqI...|
00000110  bb ab 2b dd ac fd d8 13  da 33 40 bd fd b6 1d b9  |..+......3@.....|
00000120  d7 df 3a 7a 67 80 9f 57  cc 3f 53 96 10 f5 a9 ef  |..:zg..W.?S.....|
00000130  78 6e 9f 4e ab 4e e9 61  db 86 f9 b5 ce ba 45 54  |xn.N.N.a......ET|
00000140  64 46 c1 c1 5f 86 dd 73  ae cb 1e 90 92 50 db b1  |dF.._..s.....P..|
00000150  13 dd 05 f5 3e ac 05 e7  86 e8 1c 45 b1 d0 fc 63  |....>......E...c|
00000160  c0 9f 4e 44 41 41 7c 2a  72 79 57 3a 8d 2a 3d c7  |..NDAA|*ryW:.*=.|
00000170  01 39 5b 0f 23 4e 27 4e  4d 87 9d 1e 06 b9 34 23  |.9[.#N'NM.....4#|
00000180  ef 2e 80 e3 f5 ab 4a f3  02 3e db 69 be 8d 27 a1  |......J..>.i..'.|
00000190  d6 fd 38 04 6b 27 51 6d  ec 83 45 5b cc ea 27 2a  |..8.k'Qm..E[..'*|
000001a0  ae fd 72 a8 35 af dd b4  6d 06 bd 32 1f a9 0b 0b  |..r.5...m..2....|
000001b0  02 4c 84 57 e8 15 06 01  c0 9b ec 14 f4 3f 00 fe  |.L.W.........?..|
000001c0  ff ff 07 fe ff ff 02 00  00 00 1a 24 6a 18 00 fe  |...........$j...|
000001d0  ff ff 05 fe ff ff 1c 24  6a 18 3f 34 80 0c 00 00  |.......$j.?4....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

I hope someone can help me

PD. I'm running the Try UBUNTU mode.

---

### Post by Quackers on 2011-02-20
If you used a boot option to run the live cd you will need to use that option to boot the final installation. Which option did you use (eg acpi=off,nomodeset etc)?

WHen the grub menu shows and the system you want to boot is highlighted (Ubuntu) press the "e" key. On the next screen navigate to the end of the line which ends with "quiet splash" and, using the backspace key, delete those words, then type in the boot option you used earlier (acpi=off or whatever) then press ctrl+X to boot.

It may be that that boot option will not be required if graphics drivers are installed (via System > Admin > Additional Drivers). 
If that is not the case, the boot option can be made permanent using the guide below. Scroll down the page for that.

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by rubensaid on 2011-02-20
Wow!!! It's amazing.... You are a genius

I'm really glad.. Thanks a lot everybody specially to Quackers

---

### Post by goldenskylark on 2011-03-29
Hi All

Just to say i had a similar problem installing 10.10 on my new Toshiba Satellite c660d, but thanks to the assistance of this thread  its all sorted, phew:D
much appreciation

Ubuntu Community....where no problem is too big or too small!
Viva Linux

---

### Post by Quackers on 2011-03-29
Glad to hear you solved your problems :-)

---

