---
title: "Can't go back to windows! (grub issue, though)"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by LePresident on 2010-05-22
Hey everyone,

My case is the next:

I have a laptop with two different OS: windows vista and ubuntu 10.04.  The first partition at my hard disk drive contains windows, while the 2nd contains ubuntu and of course I was able to select any of them with the grub.

Now, here is my issue:

A few days ago I decided I had to reinstall ubuntu 10.04, so I did it and now I can't access to the windows partition. The grub starts as usual, and when I choose ubuntu everything works fine, but when I choose vista, nothing happens, nothing appears, but a black screen with a white intermittent line.

¿¿WHY?? ¿What can I do to access windows?.  I know windows sucks and I really don't wanna comeback, but sometimes I have to for any reason out of my hands.

Help for Christ's sake! T.T

---

### Post by bcbc on 2010-05-22
Try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If it turns out you don't have grub2 installed in the boot sector of windows, then post the results of the bootinfoscript (as described in the above link)

---

### Post by LePresident on 2010-05-23
> **bcbc said:**
> Try this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If it turns out you don't have grub2 installed in the boot sector of windows, then post the results of the bootinfoscript (as described in the above link)

Do I have to start the bootinfoscript from a live cd? The very first ubuntu OS I got installed in my laptop was 9.10 and then upgraded to 10.04... which live cd do I have to use?

---

### Post by confused57 on 2010-05-23
You can run it from your Ubuntu installation or a live cd.

---

### Post by LePresident on 2010-05-23
Ok, this are the results:

```
 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 222630819 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /ntdetect.com

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 223670051 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 223673019 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    16,370,234    16,370,172  27 Hidden HPFS/NTFS
/dev/sda2    *     16,370,235   164,794,769   148,424,535   6 FAT16
/dev/sda3         164,794,770   213,134,354    48,339,585   7 HPFS/NTFS
/dev/sda4         213,134,355   312,576,704    99,442,350  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        663C206E16D9B5D2                       ntfs       PQSERVICE                     
/dev/sda2        BC2C39642C391ABA                       ntfs       ACER                          
/dev/sda3        60E81AB5E81A8A04                       ntfs       DATA                          
/dev/sda4        87d6fb8b-8d60-4656-9309-c7f5677ff679   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda4        /                        ext4       (rw,errors=remount-ro)


=========================== sda4/boot/grub/grub.cfg: ===========================

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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 87d6fb8b-8d60-4656-9309-c7f5677ff679
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
set root='(hd0,4)'
search --no-floppy --fs-uuid --set 87d6fb8b-8d60-4656-9309-c7f5677ff679
set locale_dir=($root)/boot/grub/locale
set lang=es
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
menuentry 'Ubuntu, con Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 87d6fb8b-8d60-4656-9309-c7f5677ff679
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=87d6fb8b-8d60-4656-9309-c7f5677ff679 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, con Linux 2.6.32-22-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 87d6fb8b-8d60-4656-9309-c7f5677ff679
    echo    'Cargando Linux 2.6.32-22-generic ...'
    linux    /boot/vmlinuz-2.6.32-22-generic root=UUID=87d6fb8b-8d60-4656-9309-c7f5677ff679 ro single 
    echo    'Cargando el disco RAM inicial...'
    initrd    /boot/initrd.img-2.6.32-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 87d6fb8b-8d60-4656-9309-c7f5677ff679
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,4)'
    search --no-floppy --fs-uuid --set 87d6fb8b-8d60-4656-9309-c7f5677ff679
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 663c206e16d9b5d2
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Recovery Environment (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set bc2c39642c391aba
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda4/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda4 during installation
UUID=87d6fb8b-8d60-4656-9309-c7f5677ff679 /               ext4    errors=remount-ro 0       1
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda4: Location of files loaded by Grub: ===================


 113.8GB: boot/grub/core.img
 109.5GB: boot/grub/grub.cfg
 110.1GB: boot/initrd.img-2.6.32-22-generic
 109.7GB: boot/vmlinuz-2.6.32-22-generic
 110.1GB: initrd.img
 109.7GB: vmlinuz
```

---

### Post by bcbc on 2010-05-23
You have installed grub2 over your windows boot sector. That link I gave you tells you how to fix it.

---

### Post by LePresident on 2010-05-23
> **bcbc said:**
> You have installed grub2 over your windows boot sector. That link I gave you tells you how to fix it.

I followed every single step that you gave me from that site and at the sixth screen I didn't have any BackupBS tab... and I don't have any windows cd because vista was already installed when I bought this laptop... now what, please? :confused:

---

### Post by LePresident on 2010-05-23
By the way, at the sixth screen I chose accidentally the rebuild BS tab but quited immediately.  Is this dangerous?:(

---

### Post by LePresident on 2010-05-23
This is the last screen I got:

```
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
     Partition                  Start        End    Size in sectors
 2 * FAT16 >32M            1019   0  1 10257 254 63  148424535

Boot sector
Bad

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.









[  Quit  ]  [Rebuild BS]  [  Dump  ]  [Repair FAT]
                            Return to Advanced menu

```

---

### Post by LePresident on 2010-05-23
Please, help! I gotta feelin'.... that I'm close! XD

---

### Post by darkod on 2010-05-23
This is what worries me:

/dev/sda2    *     16,370,235   164,794,769   148,424,535   6 [COLOR=Red]FAT16[/COLOR]

Your vista partition is reported as FAT16, when it should be NTFS. On top of that, you do have grub2 installed onto the partition, as the script showed.

Besides that, there are minor issues like having wubi inside vista. Why didn't you remove it before installing the full ubuntu?

---

### Post by LePresident on 2010-05-23
> **darkod said:**
> This is what worries me:

/dev/sda2    *     16,370,235   164,794,769   148,424,535   6 [COLOR=Red]FAT16[/COLOR]

Your vista partition is reported as FAT16, when it should be NTFS. On top of that, you do have grub2 installed onto the partition, as the script showed.

Besides that, there are minor issues like having wubi inside vista. Why didn't you remove it before installing the full ubuntu?

Hum, because when I was trying to install ubuntu for the first time I used wubi, but for any reason the installation wasn't successful at all. Wubi could only install the grub.  So I restarted my laptop and completed the installation from the grub using the live cd. Then I became a ubuntu addict and never came back to windows to errase wubi... am I clear?:confused::lolflag:
Wouldn't it be easier to reinstall any windows version and reformat the partition to NTFS?  I don't have anything usefull anymore there.  I can reinstall all the programs.

---

### Post by LePresident on 2010-05-23
C'mon guys, there gotta be a solution... I know you are smart enought! XD

---

### Post by darkod on 2010-05-23
> **LePresident said:**
> 
Wouldn't it be easier to reinstall any windows version and reformat the partition to NTFS?  I don't have anything usefull anymore there.  I can reinstall all the programs.

Yes. If you don't mind deleting the partition and all data on it, and reinstalling windows, it will definitely be easier.

Just format the vista partition as ntfs either in live mode or from ubuntu, and install there.

You will have to reinstall grub2 back to the MBR after that. Windows will overwrite it.

---

### Post by byStanderone on 2010-05-23
...would suggest that you take a closer look into your box, i think you do have an installer or system restorer that's saved somewhere in your hdd...well just in case you really did wipeout your vista.

---

### Post by LePresident on 2010-05-23
> **darkod said:**
> Yes. If you don't mind deleting the partition and all data on it, and reinstalling windows, it will definitely be easier.

Just format the vista partition as ntfs either in live mode or from ubuntu, and install there.

You will have to reinstall grub2 back to the MBR after that. Windows will overwrite it.

Is it possible to install windows from ubuntu? how? mounting an .iso image of windows?

By the way, how do I reinstall grub2 from the MBR? U_U'  sorry, I'm a noob!

---

### Post by darkod on 2010-05-23
> **LePresident said:**
> Is it possible to install windows from ubuntu? how? mounting an .iso image of windows?

By the way, how do I reinstall grub2 from the MBR? U_U'  sorry, I'm a noob!

I thought you had windows install dvd. Without install media you can't reinstall. Possibly you could use the recovery partition that you seem to have, but depending how the process is set up, that recovery might wipe the whole hdd destroying also all of your ubuntu data.

Otherwise, reinstalling grub2 to the MBR of disk /dev/sda, when your ubuntu partition is /dev/sda4 in your case would be booting into live mode with the ubuntu cd and executing:

sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

But if you have no windows reinstall media, you might wanna try and save this /dev/sda2 partition which seems wrongly reported as FAT16. Try scanning with TestDisk. You can run it from ubuntu, install it with:

sudo apt-get install testdisk

then:

sudo testdisk

---

### Post by darkod on 2010-05-23
Example how to recover a partition here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by confused57 on 2010-05-23
> **LePresident said:**
> Is it possible to install windows from ubuntu? how? mounting an .iso image of windows?

By the way, how do I reinstall grub2 from the MBR? U_U'  sorry, I'm a noob!

You could possibly reinstall Vista, using the PQSERVICE recovery partition(sda1). 

Normally, Acer & other manufacturers use a special mbr that you can press a combination of keys(e.g. Alt+F10) to access the recovery partition, but if the mbr is overwritten this function is no longer available.

First download a copy of Super Grub Disk, which may be able to boot(chainload) to your recovery partition:
[http://www.supergrubdisk.org/wiki/BootRecoveryPartition](http://www.supergrubdisk.org/wiki/BootRecoveryPartition)
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

You'll then need to download a Vista Rescue disk iso, which should enable you to repair the mbr to boot into Vista:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I've never personally done this, but it seems to be the best approach to reinstalling Vista, using the recovery partition.

---

### Post by LePresident on 2010-05-23
> **darkod said:**
> I thought you had windows install dvd. Without install media you can't reinstall. Possibly you could use the recovery partition that you seem to have, but depending how the process is set up, that recovery might **wipe the whole hdd** destroying also all of your ubuntu data.


Now, that's dramatic! :-?

> **darkod said:**
> 

But if you have no windows reinstall media, you might wanna try and save  this /dev/sda2 partition which seems wrongly reported as FAT16. Try  scanning with TestDisk. You can run it from ubuntu, install it with:

sudo apt-get install testdisk

then:

sudo testdisk 

I've already tried that before. The first one who answered this thread  suggested me to do that.  Thanks anyway! I really appreciate your help! :D

---

### Post by LePresident on 2010-05-23
> **confused57 said:**
> You could possibly reinstall Vista, using the PQSERVICE recovery partition(sda1). 

Normally, Acer & other manufacturers use a special mbr that you can press a combination of keys(e.g. Alt+F10) to access the recovery partition, but if the mbr is overwritten this function is no longer available.

First download a copy of Super Grub Disk, which may be able to boot(chainload) to your recovery partition:
[http://www.supergrubdisk.org/wiki/BootRecoveryPartition](http://www.supergrubdisk.org/wiki/BootRecoveryPartition)
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html]("http://members.iinet.net.au/%7Eherman546/SuperGrubDiskPage.html")

You'll then need to download a Vista Rescue disk iso, which should enable you to repair the mbr to boot into Vista:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

I've never personally done this, but it seems to be the best approach to reinstalling Vista, using the recovery partition.

I got an acer aspire 5580 so this option seems to be very plausible. I'm gonna start the download of the vista recovery disc this night and will do the whole process tomorrow in the morning, cuz my network is a little bit slow  U_U'

---

### Post by darkod on 2010-05-24
> **LePresident said:**
> Now, that's dramatic! :-?



I've already tried that before. The first one who answered this thread  suggested me to do that.  Thanks anyway! I really appreciate your help! :D

Just to remind you that the link provided about testdisk at the start of the thread is not the same procedure. That was a procedure about removing grub2 from a partition boot sector.

What I was talking about, and the link provided has a guide about it, is scanning the disk with testdisk and if it finds the partition correctly as ntfs, it will write it as ntfs in the partition table.

If that succeeds no reinstall is needed.

You might still need to do the testdisk procedure to remove grub2 from the partition, but the main thing is to be recognized as ntfs again.

---

### Post by confused57 on 2010-05-24
> **darkod said:**
> Just to remind you that the link provided about testdisk at the start of the thread is not the same procedure. That was a procedure about removing grub2 from a partition boot sector.

What I was talking about, and the link provided has a guide about it, is scanning the disk with testdisk and if it finds the partition correctly as ntfs, it will write it as ntfs in the partition table.

If that succeeds no reinstall is needed.

You might still need to do the testdisk procedure to remove grub2 from the partition, but the main thing is to be recognized as ntfs again.

This would definitely save a lot of time and would be easier, then he could boot Windows from Ubuntu or use the Vista Rescue cd to restore Vista's IPL to the mbr.

---

### Post by LePresident on 2010-05-26
Hey

Just to say thanks a lot to darko, confused and the people that tried to help me.  I really appreciate your help.

Finally I reinstalled windows (got Tiny XP), then ubuntu and now my laptop works as always should have :guitar:

No more vista headaches, though! Now I only have a little issue related to my battery.  As long as I work at Tiny XP plugged to my battery everything goes fine, but when I'm working at ubunt, my laptop all of a sudden truns off after a few seconds the fan is on, and yes, my battery has charge.

Is like if ubuntu can't stand my battery! >S    However, If I plug my laptop to the current adaptor everything goes fine! 

Is it a bugg at ubunt? :confused:

---

