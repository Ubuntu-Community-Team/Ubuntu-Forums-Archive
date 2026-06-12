---
title: "Grub2 can't see Vista partition"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by tommyp on 2010-01-02
I have installed 9.10 to an existing Vista machine.  Here is the fdisk
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2              10        1315    10485760    7  HPFS/NTFS
/dev/sda3   *        1315       14031   102145543+   7  HPFS/NTFS
/dev/sda4           14032       19457    43584345    5  Extended
/dev/sda5           14032       19229    41752903+  83  Linux
/dev/sda6           19230       19457     1831378+  82  Linux swap / Solaris

```

For some reason, Grub2 cannot seem to add the Vista partition to it's menu.  When I run update-grub, this is what I get:
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

```

Any idea what it means and how I can fix this?

---

### Post by Moozillaaa on 2010-01-02
Start off running this script file, and post the results from your desktop (where results will be saved).

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

I think this info will be necessary to solve this one...

---

### Post by tommyp on 2010-01-02
Here it is:
```

============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot/grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
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
Disk identifier: 0xb0000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       144,584       144,522  de Dell Utility
/dev/sda2             145,408    21,116,927    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,116,928   225,408,014   204,291,087   7 HPFS/NTFS
/dev/sda4         225,408,015   312,576,704    87,168,690   5 Extended
/dev/sda5         225,408,078   308,913,884    83,505,807  83 Linux
/dev/sda6         308,913,948   312,576,704     3,662,757  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D8-0515" TYPE="vfat" 
sda2: UUID="2648553A485509C7" LABEL="RECOVERY" TYPE="ntfs" 
sda3: UUID="82AE57EBAE57D66F" LABEL="OS" TYPE="ntfs" 
sda5: UUID="b311c34c-dafc-41d0-b89b-5afcd127ea92" TYPE="ext4" 
sda6: UUID="0d8e9f5b-b6ab-438d-ae4c-ff73e5e34ce6" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/front/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=front)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
	insmod ntfs
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 82ae57ebae57d66f
	chainloader +1
}
menuentry "Microsoft Windows XP Embedded (on /dev/sda5)" {
	insmod fat
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set d85d-043c
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=================== sda3: Location of files loaded by Grub: ===================


  10.8GB: boot/grub/grub.cfg
  10.8GB: boot/initrd.img-2.6.31-14-generic
  10.8GB: boot/vmlinuz-2.6.31-14-generic

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root=(hd0,5)
search --no-floppy --fs-uuid --set b311c34c-dafc-41d0-b89b-5afcd127ea92
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
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set b311c34c-dafc-41d0-b89b-5afcd127ea92
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=b311c34c-dafc-41d0-b89b-5afcd127ea92 ro  splash vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set b311c34c-dafc-41d0-b89b-5afcd127ea92
	linux	/boot/vmlinuz-2.6.31-16-generic root=UUID=b311c34c-dafc-41d0-b89b-5afcd127ea92 ro single  splash vga=773
	initrd	/boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set b311c34c-dafc-41d0-b89b-5afcd127ea92
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=b311c34c-dafc-41d0-b89b-5afcd127ea92 ro  splash vga=773  quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set b311c34c-dafc-41d0-b89b-5afcd127ea92
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=b311c34c-dafc-41d0-b89b-5afcd127ea92 ro single  splash vga=773
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=b311c34c-dafc-41d0-b89b-5afcd127ea92 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=0d8e9f5b-b6ab-438d-ae4c-ff73e5e34ce6 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 115.4GB: boot/grub/core.img
 115.4GB: boot/grub/grub.cfg
 115.4GB: boot/initrd.img-2.6.31-14-generic
 115.4GB: boot/initrd.img-2.6.31-16-generic
 115.4GB: boot/vmlinuz-2.6.31-14-generic
 115.4GB: boot/vmlinuz-2.6.31-16-generic
 115.4GB: initrd.img
 115.4GB: initrd.img.old
 115.4GB: vmlinuz
 115.4GB: vmlinuz.old


```

Thanks

---

### Post by chaosdesigner on 2010-01-03
Hey I was having the same problem, just with windows 7. 

Here is how I fixed it:

You need to take a look at your grub.cfg file, which is locatet in /boot/grub/. This is what my old one said:

```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 32587b75587b36a7
	drivemap -s (hd0) ${root}
	chainloader +1
}

```

I used to have XP installed on that same partition but when I chose 'Microsoft Windows XP Professional' in Grub, it said it had a signature error. When doing the grub update I got the same error as you. So what I did was, that I deletet the 'search' and the 'drivemap' lines of the file. So this is how it looked afterwards:


```
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows 7 Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	chainloader +1
}

```

By the way, you need to edit the permissions before you can change something, that can easily be done with:

```
sudo chmod +rw grub.cfg
```

Everytime I ran the 'update-grub' command it deleted the whole section about my old xp, so if your grub.cfg doesnt have a section like that, just add one and put in your right device and partionion name.

fdisk -l should do the trick.

I hope that this helped you in any way, it did for me.

Greetings.

---

### Post by meierfra. on 2010-01-22
> /boot/grub/grub.cfg /bootmgr /Boot/BCD 

You have a "boot" and a "Boot" folder. Since ntfs partitions are case insensitive this leads to confusions. See this link for more details and how to fix it:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by tommyp on 2010-02-05
meiferfa is correct.  I'm guessing that a previous wubi install might have caused this.  Removing /boot directory allowed a clean update.

---

### Post by blue_bullet on 2010-12-01
This solved my problem.  I ran sudo update-grub from a terminal window.  Windows 7 could not be located.  I used the link here and did the rename on the boot directory.  Ran sudo update-grub again and all is well.  I can now dual boot to Ubuntu 10.10 and Windows 7.  This was caused by an update I presume to  the linux headers.  After the update I could not get to Windows 7.  I check it once a week just to make certain it is still there.

---

### Post by mikij1 on 2010-12-18
I have the same problem but I don't have solucion.

I can't boot Windows 7 with muy grub 2. I have Ubuntu 10.10 in Lenovo x301.
This is my sudo update grub:

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: no se puede acceder a /media/SW_Preload/Windows: No existe el archivo o directorio
Found Windows Recovery Environment (loader) on /dev/sda1
done

and dajunt my results of [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

What's my problem? what's my solucion?

Thanks... sorry my bad english

---

### Post by oldfred on 2010-12-18
You have the boot flag on sda1, so unless you moved it that was your windows boot, but you installed grub2 to the windows boot sector. 

```
sda1: ______________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  [COLOR=Red]Grub 2 is installed in the boot sector of sda1 and [/COLOR]
                       looks at sector 192210111 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

```You also did the same to sda3. But if sda3 (or sda2) is you main install you are missing  /Windows/System32/winload.exe??? Look in your partitions and see if you have the System32 folder.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD. You need to run this for both sda1 & sda3:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by mikij1 on 2010-12-18
Hi, thanks for your answer. I trying tha page say but In  the sixth  screen I not have  a "BackupBS"  tab,..

I have trying too repair the boot with cd of windows and nothing... I don't know what trying. With ubuntu 9.04 i haven't any problem but with grub 2...

---

### Post by oldfred on 2010-12-18
Did you select sda1 (and sda3 for the second time) on the fifth screen, before going to the 6th? Many have used these instructions, so I think they still are good.

If you do not even have a backup (unusual( then you can use the testdisk rebuild boot sector function.

As described, it has an option to "Recover NTFS boot sector from its backup"
Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

If that does not work you have ot use a windows CD to run repairs from its command line.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Vista/7
BootRec.exe /FixBoot #updates PBR or partition boot sector

---

### Post by mikij1 on 2010-12-19
Yes I trying in sda1 and sda3 but i haven't backub-bs in 6 screen.

With my windows disk I went to repair pc, cmd, bootrec /fixmbr and /fixboot .... no solution

I had to repair grub because I cant't boot ubuntu, i can't boot windows

Now, sudo update-grub...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: no se puede acceder a /var/lib/os-prober/mount/Windows: No existe el archivo o directorio   ***
Found Windows Recovery Environment (loader) on /dev/sda1 
done

*** can't access to /var/lib.....     don't exit achivo o directory..

sorry my inglish and thanks..

ah, this is not solution for me, i Itrying too [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by oldfred on 2010-12-19
Not sure what this is but an error here is not normal.
ls: no se puede acceder a /var/lib/os-prober/mount/Windows: No existe el archivo o directorio   ***

if you
```
cd /var/lib/os-prober/mount
```
and then do this 
```
ls -l
```

I do not have a mount nor  a/Windows under mount. Do not know if just tempory folder for osprober or not?

---

### Post by mikij1 on 2010-12-19
cd /var/lib/os-prober/mount
bash: cd: /var/lib/os-prober/mount: No existe el archivo o directorio  (don't exist file or directory)

cd /var/lib/os-prober/ 
ls -l
-rw-r--r-- 1 root root 10 2010-12-19 18:16 labels



I not if it involves but muy sistem windos call "SERVICE003" no Windows. I have "SW_Preload" too and "Lenovo".

I have this problem since Ubuntu 9.10 and can not find solution. 
Other solutions will not work to me. Is desperating. Thanks for your help

---

### Post by oldfred on 2010-12-19
I do not have that directory either and I do not get that error. Did you modify any of the grub files for custom entries or add an entry to 40_custom to boot something? Perhaps a typo in one or the other??

---

### Post by mikij1 on 2010-12-19
I trying to add some lines in  40_custom file, I saw in other page but no solution for me and delete that lines

now...
sudo update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: no se puede acceder a /media/SW_Preload/Windows: No existe el archivo o directorio
Found Windows Recovery Environment (loader) on /dev/sda1

where is /var/lib/mount/windows??? i don't understand nothing..

---

### Post by oldfred on 2010-12-19
Your boot script showed these partitions, note labels at right end.


```
/dev/sda1        DE4CA39A4CA36C49                       ntfs       SERVICEV003                   
/dev/sda2        D206BC7806BC5EE3                       ntfs       SW_Preload                    
/dev/sda3        38643F6F643F2ECE                       ntfs       Lenovo                        

```

---

### Post by mikij1 on 2010-12-20
I don't kwno what I am wrong. I go to System-Administration-Synaptic... I seach "grub" and check Grub2 and grub-pc to finally uninstalled...
Then I install again Grub2 as this page say [http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Cambiando_el_origen_de_la_carpeta_ra.C3.ADz](http://www.guia-ubuntu.org/index.php?title=Recuperar_GRUB#Cambiando_el_origen_de_la_carpeta_ra.C3.ADz)  in my partition 6 (of ubuntu / ) and when i run [B]boot_info_script... same again: grub2 installes on sda1 and sda2.

I do't undertand nothing.
[/B]

---

### Post by oldfred on 2010-12-20
Your page looks older as I cannot read it, but it refers to hda. Ubuntu converted to all drives as sda a couple of years ago.

If you installed grub to the partitions sda1 and sda2, you did not specify the install location as just sda, the drive without and partition numbers.

---

