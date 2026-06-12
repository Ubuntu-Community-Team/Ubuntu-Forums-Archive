---
title: "Dual-boot now is single boot"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by virsto on 2011-06-09
I have a dual-boot system (Windows Vista (32-bit) with Ubuntu) and very recently went through a rather long process of upgrading Ubuntu from 10.9 to 10.10 and was very careful that I kept all my old configuration files. 

After what seemed to be a successful upgrade to 10.10, a restart was attempted. But, now I am unable to boot to either system!!

I get the following when I try to boot:

...
...
Veriflying DMI Pool Data ............
error: the symbol 'grub_xputs' not found-
grub rescue>

What can I do to continue with the boot process? How can I use grub rescue to fix grub for booting?

Please help.
:(

---

### Post by Rubi1200 on 2011-06-09
Hi,
you can take a look at the fantastic guide put together here by drs305:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If you are able to boot into Ubuntu with this then run ```
sudo update-grub
``` afterwards.

If that doesn't help, then please use a LiveCD/USB to download and run the boot info script.

There is a link at the bottom of my post with instructions.

---

### Post by virsto on 2011-06-09
> **Rubi1200 said:**
> Hi,
you can take a look at the fantastic guide put together here by drs305:
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

If you are able to boot into Ubuntu with this then run ```
sudo update-grub
``` afterwards.

If that doesn't help, then please use a LiveCD/USB to download and run the boot info script.

There is a link at the bottom of my post with instructions.
**sudo update-grub**

gives-- error: cannot find a device for /.

Note, I have a Ubuntu 9.x installation CD and I am able to boot from this CD. But, I have no connection to the internet on the computer with the problem! Thus, I do not see how I can run the script that you mentioned.

If I boot from my LiveCD (Ubuntu 9.x installation CD) and then give

**sudo blkid**

I get the following:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="EA......" LABEL="SYSTEM" TYPE="ntfs"
/dev/sdb1: UUID="4A......" LABEL="APPLIC" TYPE="ntfs"
/dev/sdb2: UUID="9E......" LABEL="MISC" TYPE="ntfs"
/dev/sdb5: UUID="1c......"  TYPE="ext4"
/dev/sdb6: UUID="37......"  TYPE="swap"
/dev/sdd1: LABEL="TREKSTOR" UUID="01..." TYPE="vfat"
/dev/sdc1: LABEL="MAXTOR" UUID="18..." TYPE="vfat"

How do I identify the boot device and how do I reference it using (hdX,Y)?

If I execute

**sudo fdisk  -l**

....
....
   Device  Boot        Start          End    Blocks       Id       System
/dev/sda1  *                 1      30402  ....              7       HPFS/NTFS
...
...
    Device Boot        Start                                  ID     System
/dev/sdb1                     1                                  7      HPFS/NTFS      
/dev/sdb2              45610                                  7      HPFS/NTFS
/dev/sdb3              71060                                  5      Extended
/dev/sdb5              71060                                83      Linux
/dev/sdb6              90379            ....        ...     82      Linux swap / Solaris

How can I use this information to fix the problem when I am unable to boot either OS (Windows Vista and Ubuntu)? Note, I am using my laptop (Windows 7) for connection to the internet.

---

### Post by virsto on 2011-06-09
Note, from the prompt

grub rescue> 

if I give the command

**ls**

then I get
(hd0) (hd0,1) (hd1) (hd1,6) (hd1,5) (hd1,2) (hd1,1) (hd2) (hd2,1) (hd3) (hd3,1)

What information is contained in this and how can I use it to fix my problem --- still unable to boot either OS!

---

### Post by Rubi1200 on 2011-06-09
I will take a quick guess and say you should follow the instructions in the guide I linked to and try using hd1,5 plus the relevant changes as described there.

Let me know what happens.

---

### Post by drs305 on 2011-06-09
My guess is also that it would be sdb5 (hd1,5).

However, the "xputs" error message normally indicates that Grub wasn't fully installed. But you can try to boot from the Grub prompt and see how far you get.

You could install Grub 2 with the 'chroot' process but using a 9.10 CD would install an older version of Grub2. It might get your system booting at least. If you cannot boot from the Grub prompt and want to try the 'chroot' method, the instructions are in the thread linked to by "Chroot" in my signature line.

P.S. Rubi1200 - the "Ubuntu Member" logo looks great!

---

### Post by virsto on 2011-06-09
I have made some progress by using the following:

1. Fix GRUB

  
[B]sudo mkdir /media/sdb5 sudo mount /dev/sdb5 /media/sdb5

sudo grub-install --root-directory=/media/sdb5 /dev/sdb[/B]  
which I believe fixed GRUB in my Ubuntu 10.10 system.

I then fixed the boot for my Windows Vista system,

Booted from my Vista DVD and used "Repair your computer" and
used the terminal (command window),
[B]
bootrec.exe /fixboot

bootrec.exe /fixmbr[/B]  
which indeed fixed the boot for Windows Vista.

However, now I can only boot to Windows Vista --- I never get a screen
that allows me to choose the system I will boot to now!!

How do I recover the capability to choose the OS (Vista or Ubuntu)? At the moment
I am unable to boot Ubuntu.

---

### Post by virsto on 2011-06-09
Thanks for your help Digg. I did look at the guide but I do not believe it was applicable to my situation at the time. 

Note, I have recovered my Windows Vista now; but, am looking for a way to boot my other OS --- so far I have not figured out how to boot to my Ubuntu system --- never get a screen that allows me to choose the system.

---

### Post by virsto on 2011-06-09
After repairing the boot record in Windows Vista on my dual-boot system (see my postings under **Upgrade to 10.10 --- grub_xputs**) I can now boot to Windows Vista. Unfortunately, I no longer get a screen during the boot process that allows me to choose between Ubuntu and Windows Vista! 

That is, I now have a single-boot system --- to Windows Vista.

I have not tampered with the partitions in anyway and thus, it seems quite likely that my Ubuntu is still intact.

How can I recover my dual-boot capaiblity? Is it possible to force a boot to Ubuntu and then use some tools to fix GRUB (this is probably where things need to be changed).[B]?

[/B]

---

### Post by drs305 on 2011-06-09
> **virsto said:**
> 
[B]sudo mkdir /media/sdb5 sudo mount /dev/sdb5 /media/sdb5

sudo grub-install --root-directory=/media/sdb5 /dev/sdb[/B]  
which I [COLOR="DarkRed"]believe[/COLOR] fixed GRUB in my Ubuntu 10.10 system.

Were you able to boot into Ubuntu after you did this?

When you 'fixed' Windows, it overwrote any Grub2 information stored in the MBR. So if Windows now works, and Ubuntu worked before you ran the commands which fixed Windows, you are just about finished.

All you should have to do is to tell the MBR to point to the grub files. You would do this with the following commands from the LiveCD (or use the ones you previously used in the same manner):
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```
Make sure your computer's BIOS boots the sdb drive first.

Just to emphasize, if your Grub wasn't returned to working order the last time you did this, don't do it now either. The second command will cause your Windows not to boot if Ubuntu doesn't either. It can be easily repaired, but there is no point in breaking Windows unless you have a reasonable chance Grub 2 will boot.

---

### Post by oldfred on 2011-06-09
To confirm where everything is at, run this from liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by virsto on 2011-06-09
But, how can I do this on my PC? That is, I am unable to run Ubuntu on my PC. Yes, I have an Ubuntu CD that can serve as a LiveCD; but, I do not understand how I can use your procedure.

Would you please expand a little on your suggestion. Note, I do have access to the internet but not via Ubuntu.

---

### Post by virsto on 2011-06-09
> **drs305 said:**
> Were you able to boot into Ubuntu after you did this?

When you 'fixed' Windows, it overwrote any Grub2 information stored in the MBR. So if Windows now works, and Ubuntu worked before you ran the commands which fixed Windows, you are just about finished.

All you should have to do is to tell the MBR to point to the grub files. You would do this with the following commands from the LiveCD (or use the ones you previously used in the same manner):
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```Make sure your computer's BIOS boots the sdb drive first.

Just to emphasize, if your Grub wasn't returned to working order the last time you did this, don't do it now either. The second command will cause your Windows not to boot if Ubuntu doesn't either. It can be easily repaired, but there is no point in breaking Windows unless you have a reasonable chance Grub 2 will boot.

This makes good sense to me; but, when tried to update the GRUB I was never able to boot into Ubuntu on my PC, so I doubt it will work (as you have noted). I can use a liveCD (with Ubuntu 9.x on it); but, do not know how I can fix the GRUB AND insure that my bootup sequence finds it and allows me to choose my OS. Perhaps you could expand on how I might accomplish this (liveCD or ?). Note, sdb5 contains Linux.

Thanks for your help and support on this.

---

### Post by YesWeCan on 2011-06-09
Hi there.
Does your PC have more than one hard disk?
Is your PC able to boot off a USB stick?

I ask because Vista is generally not very tolerant of Grub's MBR, as you have probably already noticed, so it can save you a lot of grief if your Grub MBR is on another disk. Another HD will do. A really convenient way is to install Ubuntu to a USB stick and boot off that (you don't use the OS on the USB but you use its Grub facilities to boot Ubuntu on your HD, and Vista).

---

### Post by drs305 on 2011-06-09
> **virsto said:**
> Perhaps you could expand on how I might accomplish this (liveCD or ?). Note, sdb5 contains Linux.


You would do this by 'chrooting' into your Ubuntu partition from the LiveCD. Chroot allows the LiveCD's system files to act on the files in your real installation. Once you mount your real partition and then mount the LiveCD's system files, you chroot into your partition and become root (sudo no longer required).  Then you install Grub2. 

In my guide, I have the user first check for an Internet connection (since you will need to install from the repositories), then remove Grub and finally reinstall it. Removing it first ensures that you get fresh, uncorrupted Grub files. 

I could give you the commands here but the guide includes a few explanations of what you will see or be asked, plus there is now a link to a good site with graphics. 

In your case, you would mount and chroot into sdb5, and install grub to sdb.

Here is the link:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

If you successfully accomplish this, Grub will once again be in the sdb MBR and will point to the Grub2 files and menu. Windows should be found during the installation and included as an option in the Grub menu.

---

### Post by virsto on 2011-06-09
> **YesWeCan said:**
> Hi there.
Does your PC have more than one hard disk?
Is your PC able to boot off a USB stick?

I ask because Vista is generally not very tolerant of Grub's MBR, as you have probably already noticed, so it can save you a lot of grief if your Grub MBR is on another disk. Another HD will do. A really convenient way is to install Ubuntu to a USB stick and boot off that (you don't use the OS on the USB but you use its Grub facilities to boot Ubuntu on your HD, and Vista).

Yes, I have two HDs and I have Ubuntu installed. However, during an Ubuntu upgrade to 10.10 something happened to the grup, even though I was careful to keep all configuration files (when asked during the upgrade). After the upgrade I was unable to boot either my Vista or Ubuntu. 

I can see the Ubuntu files on sdb5 from Windows Vista but I still do not know how to fix the problem.  Any suggestions?

---

### Post by virsto on 2011-06-09
> **virsto said:**
> But, how can I do this on my PC? That is, I am unable to run Ubuntu on my PC. Yes, I have an Ubuntu CD that can serve as a LiveCD; but, I do not understand how I can use your procedure.

Would you please expand a little on your suggestion. Note, I do have access to the internet but not via Ubuntu.

I can access the Ubuntu files on sdb5 (where Ubuntu is installed) from Windows Vista --- perhaps this could be useful for fixing the problem.

---

### Post by drs305 on 2011-06-09
Threads merged.

Threads about the same issue lead to duplication of effort and sometimes confusion. Since the one thread led into the other, and you were still seeking input on both, I've joined them to provide a more complete picture for the 'helpers'.

---

### Post by oldfred on 2011-06-09
You showed you installed grub2's boot loader to sdb. Have you tried booting sdb with either a change in BIOS or one time boot key on BIOS boot screen (f12 on my system).

You can use liveCD and download boot script with the liveCD. Instructions on using boot script are on link to download.

---

### Post by virsto on 2011-06-09
I finally was able to get info on my Ubuntu system using boot_info_script.sh

```
   
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 1141873810 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb2 and looks at sector 1141879314 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdc1 and looks at sector 1141867466 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdd1 and looks at sector 1141867690 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x011382f0

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0564b259

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   732,721,143   732,719,096   7 NTFS / exFAT / HPFS
/dev/sdb2         732,721,152 1,141,559,271   408,838,120   7 NTFS / exFAT / HPFS
/dev/sdb3       1,141,562,835 1,465,144,064   323,581,230   5 Extended
/dev/sdb5       1,141,562,898 1,451,922,569   310,359,672  83 Linux
/dev/sdb6       1,451,922,633 1,465,144,064    13,221,432  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 203.9 GB, 203927060480 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398295040 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x617523e2

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   398,267,414   398,267,352   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1d16751d

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        E45E9EF65E9EC12A                       ntfs       SYSTEM
/dev/sdb1        4A5C56EB5C56D175                       ntfs       APPLIC
/dev/sdb2        9E60F96860F94813                       ntfs       MISC
/dev/sdb5        1c2739db-9258-4b62-b736-be3857c711e9   ext4       
/dev/sdb6        37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4   swap       
/dev/sdc1        18EC-3E16                              vfat       MAXTOR
/dev/sdd1        0108-16A0                              vfat       TREKSTOR

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdc1        /media/MAXTOR            vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1        /media/TREKSTOR          vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sr0         /cdrom                   iso9660    (rw)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="10"
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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set e45e9ef65e9ec12a
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1c2739db-9258-4b62-b736-be3857c711e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-2.6.32-26-generic              2
               =                boot/initrd.img-2.6.35-28-generic              2
               =                boot/vmlinuz-2.6.32-26-generic                 1
               =                boot/vmlinuz-2.6.35-28-generic                 1
               =                initrd.img                                     2
               =                initrd.img.old                                 2
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

I hope that this can be of help in resolving the problem.

---

### Post by YesWeCan on 2011-06-09
> **virsto said:**
> Yes, I have two HDs and I have Ubuntu installed. However, during an Ubuntu upgrade to 10.10 something happened to the grup, even though I was careful to keep all configuration files (when asked during the upgrade). After the upgrade I was unable to boot either my Vista or Ubuntu. 

I can see the Ubuntu files on sdb5 from Windows Vista but I still do not know how to fix the problem.  Any suggestions?
It is easy to muck it up, believe me. Loads of people end up not being able to boot one thing or another.

The way Grub works is that it is in 3 pieces. 2 of these are at the start of a disk, in the MBR sector and in several sectors immediately after, and the bulk of it is actually in the Ubuntu root partition.

When Vista repairs its boot system for you it will over-write the MBR sector with a DOS version. This wipes piece 1 of Grub away. The Vista boot-loader is unaware that there is a Ubuntu partition so it doesn't offer it to you in its menu.

The first 2 pieces of Grub do not need to be on the same disk as the Ubuntu root partition. So this means you could install Grub pieces 1 & 2 to your second HD (provided it does not also have a Vista OS installed on it). Then you configure the bios to boot the second HD instead of the first. You can always boot Vista directly off the first if you ever need to.

To arrange this follow the instructions drs305 and Oldfred will give you. :)

---

### Post by YesWeCan on 2011-06-09
> **virsto said:**
> I can access the Ubuntu files on sdb5 (where Ubuntu is installed) from Windows Vista --- perhaps this could be useful for fixing the problem.
Unfortunately, Vista does not have the tools necessary to reinstall Grub. So this must be done using a Ubuntu live CD/USB.

---

### Post by oldfred on 2011-06-09
Boot script shows a couple of problems. But have you tried booting from sdb? Change BIOS or one time boot key to select the drive that is sdb - 750GB drive.

It looks like you have installed grub2's boot loader to several partitions. We almost never install to a partition, just MBR or the first sector of a hard drive. Especially with multiple drives you do not need to install grub to a partition. Not sure if it will cause issues with NTFS. I know if it is a boot partition it is a big problem.

In the Vista partition you have another issue as part of grub was installed to it. 

> sda1: ___________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                      [COLOR=Red] /boot/grub/core.img[/COLOR]


Windows is not case sensitive like Ubuntu is. So you have two identical folders from windows view of /boot & /Boot. You need to delete the /boot folder but be careful not to delete /Boot as it has the essential windows file BCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by virsto on 2011-06-09
> **drs305 said:**
> Were you able to boot into Ubuntu after you did this?

When you 'fixed' Windows, it overwrote any Grub2 information stored in the MBR. So if Windows now works, and Ubuntu worked before you ran the commands which fixed Windows, you are just about finished.

All you should have to do is to tell the MBR to point to the grub files. You would do this with the following commands from the LiveCD (or use the ones you previously used in the same manner):
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```Make sure your computer's BIOS boots the sdb drive first.

Just to emphasize, if your Grub wasn't returned to working order the last time you did this, don't do it now either. The second command will cause your Windows not to boot if Ubuntu doesn't either. It can be easily repaired, but there is no point in breaking Windows unless you have a reasonable chance Grub 2 will boot.

I am a little lost now --- problem still unsolved and it is now 02:45 in the morning, and I need some rest.

What I have now done:
1. Used the boot_repair program from a liveCD (Ubuntu 10.04 secure 32-bit) 

    I got the following window after it did some searching

    Repair of the computer boot
    **********************
   There is no boot backup on this computer.
   This will reinstall GRUB bootloader..
   Do you want to continue?

   I responfed Yes. Then next window 

  LAST CONFIRMATION
  ***********************
  Are you sure you want to reinstall GRUB bootloader?

  I responded Apply

  The defaults in Advanced settings resulted in completion with no errors.

  I then tried to boot up and I now could only boot into Ubuntu!

2.  I then went through several iterations of fixing my Windows Vista boot record and
  it seems that if I put the GRUB bootloader on sbc or sdb (using the Advanced
  setting option in boot_repair) then I would only be able to boot into Windows Vista.
  I also used my Windows Vista CD to repair the boot record several times (when  boot_repair overwrote the boot record on sda).

I am not sure where to go from here. I still can only boot one of my systems and never get a screen during bootup that allows me to choose from Vista or Ubuntu.

Note, when I use the default setting in boot_repair (GRUB bootloader placed on sda) I do get a screen that looks familiar for choosing the system, BUT windows is not an option and thus I can only boot into Ubuntu!

Several questions:
1. Where should boot_repair place the GRUB bootloader? (in Advanced settings)
2. Where should the boot record for Windows Vista be located?
3. Should I edit boot configuration file (used by GRUB)? And if yes, how and what should be changed?
4. Should I try to recover my old Ubuntu system (before the update) --- I do have backups? [Assuming that I can still access them using my liveCD].

---

### Post by drs305 on 2011-06-09
Take things one step at a time.

Get Windows to boot. This would mean you have probably also fixed (removed) the /boot/grub/core.img file on sda1.
Once Windows boots, it means your BIOS is first looking at sda and booting the Windows bootloader, which is what you want.

Once Windows is booting and running properly, *then* boot the LiveCD. I don't remember how the Boot Repair app works from the LiveCD. If it lets you pick the partition of the OS *and* allows you to install *only to sdb*, then you can use it. Do not use it if it wants you to install to sdb**5** or any other partition number.

If you can't use Boot Repair, boot the LiveCD:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```
Don't install to a partition, only sdb.

Now STOP.
What you have is the Windows bootloader on sda and the GRUB2 bootloader on sdb. In order to now boot Ubuntu, you will need to change the BIOS to boot sdb (your Ubuntu drive) first.

Once you do that, you should get the Grub menu *with* an option to boot Windows.

If you don't get a Windows option but do get Ubuntu, boot to Ubuntu (not with the CD) and then run:
```
sudo update-grub
```

---

### Post by virsto on 2011-06-10
> **drs305 said:**
> Threads merged.

Threads about the same issue lead to duplication of effort and sometimes confusion. Since the one thread led into the other, and you were still seeking input on both, I've joined them to provide a more complete picture for the 'helpers'.

Thanks for this --- sorry if it caused any problems. ;)

---

### Post by virsto on 2011-06-10
> **drs305 said:**
> Take things one step at a time.

Get Windows to boot. This would mean you have probably also fixed (removed) the /boot/grub/core.img file on sda1.
Once Windows boots, it means your BIOS is first looking at sda and booting the Windows bootloader, which is what you want.

Once Windows is booting and running properly, *then* boot the LiveCD. I don't remember how the Boot Repair app works from the LiveCD. If it lets you pick the partition of the OS *and* allows you to install *only to sdb*, then you can use it. Do not use it if it wants you to install to sdb**5** or any other partition number.

If you can't use Boot Repair, boot the LiveCD:
```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb

```Don't install to a partition, only sdb.

Now STOP.
What you have is the Windows bootloader on sda and the GRUB2 bootloader on sdb. In order to now boot Ubuntu, you will need to change the BIOS to boot sdb (your Ubuntu drive) first.

Once you do that, you should get the Grub menu *with* an option to boot Windows.

If you don't get a Windows option but do get Ubuntu, boot to Ubuntu (not with the CD) and then run:
```
sudo update-grub
```

Ok, I have followed your suggestions as close as possible but still no solution.
Here is summary of what I did.

1. Placed GRUB on scb (using boot_repair) [actually it was already there]
2. Changed the BIOS to boot from scb (my hd2) 

   This worked; **but did not get an option to boot Windows**.  But my upgrade to
   10.10.4 Ubuntu seems to be working fine.
3. Executed 

     ```
sudo update-grub
```   and here is the result

  root@virgil-desktop:/home/virgil# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.32-26-generic
Found initrd image: /boot/initrd.img-2.6.32-26-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done
root@virgil-desktop:/home/virgil# 

What next?

---

### Post by Rubi1200 on 2011-06-10
Try the following command from within the Ubuntu install:

```
sudo os-prober
```

If it tells you the package is not installed, then install it with:

```
sudo apt-get install os-prober
```

then run the first command again.

Let us know if this makes a difference (you may want to also run the update-grub command again as well to see if Windows was picked up).

---

### Post by virsto on 2011-06-10
Here are the current RESULTS.txt after running 

```
sudo bash ~/Desktop/boot_info_script.sh
```

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/mnt/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 1141873810 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb2 and looks at sector 1141879314 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdc1 and looks at sector 1141867690 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdd1 and looks at sector 1141867466 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   732,721,143   732,719,096   7 NTFS / exFAT / HPFS
/dev/sdb2         732,721,152 1,141,559,271   408,838,120   7 NTFS / exFAT / HPFS
/dev/sdb3       1,141,562,835 1,465,144,064   323,581,230   5 Extended
/dev/sdb5       1,141,562,898 1,451,922,569   310,359,672  83 Linux
/dev/sdb6       1,451,922,633 1,465,144,064    13,221,432  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 203.9 GB, 203927060480 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398295040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   398,267,414   398,267,352   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E45E9EF65E9EC12A                       ntfs       SYSTEM
/dev/sdb1        4A5C56EB5C56D175                       ntfs       APPLIC
/dev/sdb2        9E60F96860F94813                       ntfs       MISC
/dev/sdb5        1c2739db-9258-4b62-b736-be3857c711e9   ext4       
/dev/sdb6        37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4   swap       
/dev/sdc1        0108-16A0                              vfat       TREKSTOR
/dev/sdd1        18EC-3E16                              vfat       MAXTOR

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /mnt                     ext4       (rw)
/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/TREKSTOR_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd1        /media/MAXTOR_           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=============================== StdErr Messages: ===============================

/home/virgil/Desktop/boot_info_script.sh: line 2457: cd: /
/mnt/: No such file or directory

```

Perhaps this can be used to solve the problem.;)

---

### Post by virsto on 2011-06-10
> **oldfred said:**
> Boot script shows a couple of problems. But have you tried booting from sdb? Change BIOS or one time boot key to select the drive that is sdb - 750GB drive.

It looks like you have installed grub2's boot loader to several partitions. We almost never install to a partition, just MBR or the first sector of a hard drive. Especially with multiple drives you do not need to install grub to a partition. Not sure if it will cause issues with NTFS. I know if it is a boot partition it is a big problem.

In the Vista partition you have another issue as part of grub was installed to it. 



Windows is not case sensitive like Ubuntu is. So you have two identical folders from windows view of /boot & /Boot. You need to delete the /boot folder but be careful not to delete /Boot as it has the essential windows file BCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

I now went back to your posting (oldfred (#23)) and removed the folder: /boot ,which contained the file /boot/grub/core.img.

This had no effect that I could see. Here is the current RESULTS from boot_info_script.sh

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdb and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdc and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for (,msdos5)/boot/grub.
 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sdd and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 5 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb1 and looks at sector 1141873810 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdb2 and looks at sector 1141879314 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdb3: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdc1 and looks at sector 1141867690 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub2 (v1.97-1.98)
    Boot sector info:   Grub2 (v1.97-1.98) is installed in the boot sector of 
                       sdd1 and looks at sector 1141867466 of the same hard 
                       drive for core.img, but core.img can not be found at 
                       this location. No errors found in the Boot Parameter 
                       Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   488,394,751   488,392,704   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048   732,721,143   732,719,096   7 NTFS / exFAT / HPFS
/dev/sdb2         732,721,152 1,141,559,271   408,838,120   7 NTFS / exFAT / HPFS
/dev/sdb3       1,141,562,835 1,465,144,064   323,581,230   5 Extended
/dev/sdb5       1,141,562,898 1,451,922,569   310,359,672  83 Linux
/dev/sdb6       1,451,922,633 1,465,144,064    13,221,432  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 203.9 GB, 203927060480 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398295040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1                  63   398,267,414   398,267,352   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        E45E9EF65E9EC12A                       ntfs       SYSTEM
/dev/sdb1        4A5C56EB5C56D175                       ntfs       APPLIC
/dev/sdb2        9E60F96860F94813                       ntfs       MISC
/dev/sdb5        1c2739db-9258-4b62-b736-be3857c711e9   ext4       
/dev/sdb6        37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4   swap       
/dev/sdc1        0108-16A0                              vfat       TREKSTOR
/dev/sdd1        18EC-3E16                              vfat       MAXTOR

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sdb5        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdc1        /media/TREKSTOR_         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdd1        /media/MAXTOR_           vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


=========================== sdb5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
set default="10"
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
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=1c2739db-9258-4b62-b736-be3857c711e9 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 1c2739db-9258-4b62-b736-be3857c711e9
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sdb5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=1c2739db-9258-4b62-b736-be3857c711e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=37b8de30-efa4-4e1d-9d8e-f3f48dfa8ec4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sdb5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 544.482239723 = 584.633353216  boot/grub/core.img                             1
 568.605252266 = 610.535240704  boot/grub/grub.cfg                             1
 563.659920692 = 605.225231360  boot/initrd.img-2.6.32-26-generic              2
 563.966832161 = 605.554775040  boot/initrd.img-2.6.35-28-generic              2
 561.203656197 = 602.587837440  boot/vmlinuz-2.6.32-26-generic                 1
 562.937359810 = 604.449387520  boot/vmlinuz-2.6.35-28-generic                 1
 563.966832161 = 605.554775040  initrd.img                                     2
 563.659920692 = 605.225231360  initrd.img.old                                 2
 562.937359810 = 604.449387520  vmlinuz                                        1
 561.203656197 = 602.587837440  vmlinuz.old                                    1

 
```

and as you can see this "rogue" boot file has been removed.

Note, the problem is still there --- unable to get a screen that gives me the possibility to choose either Vista or Ubuntu. If I wish to boot Windows Vista I need to change the disk boot priority back to sda (hd0) --- not convenient :(

---

### Post by drs305 on 2011-06-10
virsto,

We are getting close. Please run the commands *Rubi1200* provided in Post #28. We have to determine whether os-prober is installed and working. It is not adding an entry into your Grub menu configuration file, so it appears it is not running.

If it is not installed, install os-prober. If it is installed, make sure the script that runs it is executable:
```
sudo chmod +x /etc/grub.d/30_os-prober
sudo update-grub
```
As the second command runs, watch the terminal. If it finds Windows you should see it mentioned as the command runs.

If you still don't get a Windows entry, we can try building a manual custom entry for it.

---

### Post by virsto on 2011-06-10
> **Rubi1200 said:**
> Try the following command from within the Ubuntu install:

```
sudo os-prober
```If it tells you the package is not installed, then install it with:

```
sudo apt-get install os-prober
```then run the first command again.

Let us know if this makes a difference (you may want to also run the update-grub command again as well to see if Windows was picked up).

Ok! Eureka! :D
Thanks to all of you who did not give up on me and especiallly to Rubi1200 and drs305 who got me on the right track. My system is again working as a dual-boot system (Vista and Ubuntu 10.10.4).

A short summary of my own thoughts on this problem:
1. Have a liveCD for Ubuntu (e.g. Ubuntu 10.04 secure) handy which has the boot_repair program on it.
2. Have a CD (or DVD) that you can use to boot the other operating system (e.g. Windows Vista) handy.
3. Have boot_info_script.sh on your Ubuntu system (see my earlier postings in this thread). **The information obtained when this script is executed can be very, very useful for troubleshooting.**
4. [COLOR=Red]Warning![/COLOR] boot_repair is a great program; but, it may not always solve your problem (see my earlier postings in this thread).
5. Search the Ubuntu forum for problems that are similar to your own.

Finally, a recommendation.
I am impressed by the Ubuntu development team --- they are doing a fantastic job and just keep rolling out the upgrades. However, I would like to see them take GRUB more seriously, i.e., this seems to be a weak link in the upgrade chain --- I and many others have had many headaches with GRUB when running multiple OS's. It can be useful to have programs like boot_repair and I commend those who write such programs; but, IMHO it would be more useful to have more bells and whistles built into Ubuntu to reduce GRUB problems during the upgrade process.

Best regards, and thanks again! ;)

---

### Post by Rubi1200 on 2011-06-10
Excellent! I am really pleased you got this sorted out in the end :D

Please mark this Solved using the Thread Tools near the top of the page.

---

### Post by LG_Auction on 2011-06-17
My problem is I installed Natty 64 bit along side an XP 32.

I can only get the Natty to start. Holding the shift key does not bring up grub.  Here is my boot_info_script results. Any help would be appreciated! Thanks in advance

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   253,180,789   253,180,727   7 NTFS / exFAT / HPFS
/dev/sda2         253,181,950   488,396,799   235,214,850   5 Extended
/dev/sda5         253,181,952   484,466,687   231,284,736  83 Linux
/dev/sda6         484,468,736   488,396,799     3,928,064  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        98BC6352BC632A48                       ntfs       
/dev/sda5        2b85940f-c2bb-4779-b28b-6a69e75aa3bc   ext4       
/dev/sda6        ee7340b3-c5ba-4f4d-85dd-cb68a6355926   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect /usepmtimer
--------------------------------------------------------------------------------

=========================== sda5/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 2b85940f-c2bb-4779-b28b-6a69e75aa3bc
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos5)'
search --no-floppy --fs-uuid --set=root 2b85940f-c2bb-4779-b28b-6a69e75aa3bc
set locale_dir=($root)/boot/grub/locale
set lang=en_US
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
play 480 440 1
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b85940f-c2bb-4779-b28b-6a69e75aa3bc
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=2b85940f-c2bb-4779-b28b-6a69e75aa3bc ro   quiet splash vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b85940f-c2bb-4779-b28b-6a69e75aa3bc
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=2b85940f-c2bb-4779-b28b-6a69e75aa3bc ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b85940f-c2bb-4779-b28b-6a69e75aa3bc
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos5)'
	search --no-floppy --fs-uuid --set=root 2b85940f-c2bb-4779-b28b-6a69e75aa3bc
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Home Edition (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos1)'
	search --no-floppy --fs-uuid --set=root 98BC6352BC632A48
	drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=2b85940f-c2bb-4779-b28b-6a69e75aa3bc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ee7340b3-c5ba-4f4d-85dd-cb68a6355926 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 160.864662170 = 172.727115776  boot/grub/core.img                             1
 144.882915497 = 155.566845952  boot/grub/grub.cfg                             1
 147.296875000 = 158.158815232  boot/initrd.img-2.6.38-8-generic               2
 160.859378815 = 172.721442816  boot/vmlinuz-2.6.38-8-generic                  1
 166.852302551 = 179.156295680  grub/core.img                                  1
 147.296875000 = 158.158815232  initrd.img                                     2
 160.859378815 = 172.721442816  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  1d 91 3a 6c ee b1 4a 03  8d a1 80 11 c0 bf 7b be  |..:l..J.......{.|
00000010  ce 87 d9 60 1f 64 37 80  3d d5 4b 1f ac a7 3f fa  |...`.d7.=.K...?.|
00000020  cd 9e d6 bb e8 df ed e5  df 98 43 42 5e 38 03 80  |..........CB^8..|
00000030  a9 f8 9c ac c6 25 74 bd  7b d7 9c 08 87 2c 6b 5d  |.....%t.{....,k]|
00000040  4f a1 13 cd af b5 77 68  0b 5d fc d6 3c a7 d1 53  |O.....wh.]..<..S|
00000050  83 9b 11 c4 c1 4f a4 60  01 0e 3a f8 f9 ad c1 36  |.....O.`..:....6|
00000060  c6 a1 fc a4 7f 0b 71 07  d8 c9 b5 77 b8 2f 6e de  |......q....w./n.|
00000070  ec b6 e4 c9 cd a8 60 0d  3e 3f 24 f5 88 47 58 f0  |......`.>?$..GX.|
00000080  42 c2 7f b2 c1 e7 ce 9f  45 a6 f6 a2 6f e5 52 6c  |B.......E...o.Rl|
00000090  35 63 d3 d6 cb c3 dc 9d  51 44 73 53 85 19 85 f8  |5c......QDsS....|
000000a0  6f 2e 3f 5b b8 3b 8a 95  7f 60 3f 10 b1 20 0d 3d  |o.?[.;...`?.. .=|
000000b0  52 ae a6 46 3d aa 5b 4e  75 13 6f 48 63 60 27 d5  |R..F=.[Nu.oHc`'.|
000000c0  5e 90 38 ac 6a 4b 00 ef  1e 98 8d 1b 53 48 9c 2c  |^.8.jK......SH.,|
000000d0  b6 99 a0 16 54 b5 5b 93  b2 c6 0b 10 ef 29 4c 81  |....T.[......)L.|
000000e0  64 e9 5e 7d 5a 86 26 d1  05 ca 90 a3 f9 8a db b3  |d.^}Z.&.........|
000000f0  14 aa 30 2d 43 b2 35 87  72 30 24 cf 97 fe 00 a8  |..0-C.5.r0$.....|
00000100  86 03 df 8f 71 bd 68 fe  aa 29 bf 2e 38 7d 70 17  |....q.h..)..8}p.|
00000110  17 b5 1b 74 e3 88 5f 2f  69 01 b8 dc 53 0a b0 a7  |...t.._/i...S...|
00000120  46 e3 b6 ab 61 ac 79 ed  52 cd 20 25 49 97 94 b8  |F...a.y.R. %I...|
00000130  93 34 c8 4f 84 be 67 da  1b 1a 86 03 76 e6 f5 db  |.4.O..g.....v...|
00000140  0a 7b 64 c8 e8 01 36 96  d3 8b 97 18 11 8a a7 f3  |.{d...6.........|
00000150  24 72 2d 27 75 d2 7d 6c  08 e5 61 a6 75 fc 06 af  |$r-'u.}l..a.u...|
00000160  6e 6c 57 26 9a b1 d0 2b  ef ed 68 90 c1 d2 73 47  |nlW&...+..h...sG|
00000170  9a 17 19 e3 4f 7b 72 d9  ef e3 9c 70 f8 8b 05 55  |....O{r....p...U|
00000180  41 f7 68 9e 20 48 aa 95  80 5a b2 ab c5 ec 38 a1  |A.h. H...Z....8.|
00000190  a1 8c 9f 49 57 d0 0a a0  e0 53 ee c7 85 e7 1e b9  |...IW....S......|
000001a0  b1 0e 4c ab a4 09 97 4a  11 48 ac c4 44 48 0d ca  |..L....J.H..DH..|
000001b0  98 f7 b0 37 b7 d0 29 e8  a9 e2 b2 a6 e2 3c 00 fe  |...7..)......<..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 20 c9 0d 00 fe  |........... ....|
000001d0  ff ff 05 fe ff ff 02 20  c9 0d 00 f8 3b 00 00 00  |....... ....;...|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error

---

### Post by arubislander on 2011-06-17
I think you should start a new thread for your problem, after trying the solutions posted here that is.

You see, this thread has already been marked solved, so it is unlikely to be revisited by people able to help you.

---

### Post by oldfred on 2011-06-17
LG_Auction, even though the title may be similar to your problem boot issues are almost always unique, so it is better to start your own thread.

I do not see anything in your script that looks unusual. You do have two core.img in different folders but I do not think that is an issue.

Have you just tried:

sudo update-grub

os-prober should find your windows install.

Sorry arubislander, I just copied first name from last post and did not notice your post popped in. See post below.
Maybe oldfred should start paying attention.

---

### Post by arubislander on 2011-06-17
[deleted]

---

