---
title: "Grub not installing on disk or on live cd"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by mUNKYsTUFF on 2010-12-14
I recently received an edition of APC magazine with Ubuntu 9.10 on the demo disk. Wanting to install Ubuntu for a long time, I burnt the ISO and installed it alongside windows xp.
When I rebooted the pc, it loaded straight into windows. (grub had not installed)
i went back to the live cd and tried a manual install, to find grub was not on the image. I burnt a CD with super grub disk, but said that the install was not valid, although it was. 
This morning I burnt an image of Ubuntu 10.10, to upgrade or install grub, but this image has no grub either, and so I cant install.
What do I do? I don't mind whether I end up with 10.10 or 9.10, as long as I have Ubuntu, or my disk space back.
Thanks for help. :)

---

### Post by sikander3786 on 2010-12-14
Welcome to the forums :-)

Every Ubuntu disc has got Grub on it.

Instruction on how to install Grub from Live CD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Use a Live CD of 9.10 or newer versions.

If you are not sure, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Then we'll be able to see your setup and thus give you the exact commands to just copy/paste.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

Side Note: Remember, support for 9.10 is scheduled to end in April next year. I would suggest once the issue is fixed, upgrade it to the current release i.e, either 10.04 or 10.10.

---

### Post by mUNKYsTUFF on 2010-12-14
> **sikander3786 said:**
> Welcome to the forums :-)

Every Ubuntu disc has got Grub on it.

Instruction on how to install Grub from Live CD:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Use a Live CD of 9.10 or newer versions.

If you are not sure, post the output of bootinfoscript as per instructions here.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

Then we'll be able to see your setup and thus give you the exact commands to just copy/paste.

While posting, click the # icon in post menu and paste your text in between the generated code tags.

I know this must sound strange, but if it's any consolation, here is my terminal output when I tried to install grub to my disk:

ubuntu@ubuntu:~$ sudo grub-install --recheck /dev/sdb5
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).

---

### Post by mUNKYsTUFF on 2010-12-14
Sorry, didn't read post properly.
Ran boot info script and came up with this:

  ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=b535c9c1-44f0-49b9-9aa8-681262b3896a)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

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

/dev/sda1    *             63   312,576,704   312,576,642   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   216,074,249   216,074,187   7 HPFS/NTFS
/dev/sdb2         216,074,250   596,413,124   380,338,875   7 HPFS/NTFS
/dev/sdb3         596,413,125   817,917,344   221,504,220   7 HPFS/NTFS
/dev/sdb4         817,917,345   976,768,064   158,850,720   5 Extended
/dev/sdb5    *    817,917,408   970,213,544   152,296,137  83 Linux
/dev/sdb6         970,213,608   976,768,064     6,554,457  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        FC4078E94078ABD0                       ntfs       OLD_MAIN                      
/dev/sda: PTTYPE="dos" 
/dev/sdb1        8C742DE2742DD02E                       ntfs       Main                          
/dev/sdb2        FCECBA98ECBA4CA0                       ntfs       Data                          
/dev/sdb3        A4D8C36CD8C33AF6                       ntfs       Media\Swap                    
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        b535c9c1-44f0-49b9-9aa8-681262b3896a   ext4       Ubuntu                        
/dev/sdb6        b1b37d86-4496-423d-94d9-87d0b9ff2cab   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/Ubuntu            ext4       (rw,nosuid,nodev,uhelper=udisks)


================================ sdb1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=UTZRNE /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=UTZRNE-BAK 

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root=(hd1,5)
search --no-floppy --fs-uuid --set b535c9c1-44f0-49b9-9aa8-681262b3896a
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
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set b535c9c1-44f0-49b9-9aa8-681262b3896a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b535c9c1-44f0-49b9-9aa8-681262b3896a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,5)
    search --no-floppy --fs-uuid --set b535c9c1-44f0-49b9-9aa8-681262b3896a
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b535c9c1-44f0-49b9-9aa8-681262b3896a ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (loader) (on /dev/sdb1)" {
    insmod ntfs
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set 8c742de2742dd02e
    drivemap -s (hd0) ${root}
    chainloader +1
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
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb5 during installation
UUID=b535c9c1-44f0-49b9-9aa8-681262b3896a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=b1b37d86-4496-423d-94d9-87d0b9ff2cab none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sdb5: Location of files loaded by Grub: ===================


 419.3GB: boot/grub/core.img
 449.3GB: boot/grub/grub.cfg
 419.3GB: boot/initrd.img-2.6.31-14-generic
 419.3GB: boot/vmlinuz-2.6.31-14-generic
 419.3GB: initrd.img
 419.3GB: vmlinuz
```

---

### Post by drs305 on 2010-12-14
"grub-install" is a bit of a misnomer. The actual Grub2 package is called "grub-pc". 

EDIT:
Simultaneous Post: It appears G2 is installed for Ubuntu 9.04.
You can try this before doing the information posted simultaneously:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
Have your BIOS boot sda's Grub first.
END ADD


If you already have an installation, the best course of action is to chroot into it and then install Grub. Chroot-ing involves booting the LiveCD, mounting your Ubuntu partition, copying system files from the LiveCD to allow you to operate within your real installation, and then chroot-ing into it.

Once there, any commands you issue will act upon your real installation instead of the LiveCD. Go to this site and follow the chroot procedure. You do not need to run the purge commands in Step 3.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

---

### Post by mUNKYsTUFF on 2010-12-14
Which live cd should I be booting from?
9.10 or 10.10, (btw I would rather 10.10, but would that require a clean install?)

---

### Post by sikander3786 on 2010-12-14
Grub seems pretty ok from that boot script output and I suspect that your Bios is set to boot from sdb instead of sda (where Grub is actually installed). Recheck your boot order in Bios.

Not needed I hope: For re-installation of Grub, did you mount it prior to installing Grub?

```
sudo mount /dev/sdb5 /mnt
```

```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

---

### Post by mUNKYsTUFF on 2010-12-14
> **drs305 said:**
> 
EDIT:
Simultaneous Post: It appears G2 is installed for Ubuntu 9.04.
You can try this before doing the information posted simultaneously:

```
sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```Have your BIOS boot sdb first.
END ADD



I ran this code, and terminal replied ```
Installation finished. No error reported.
```
Does this mean grub is installed for Ubuntu 9.10?
I'm very new to all this so I apologise if I'm being tedious.

---

### Post by mUNKYsTUFF on 2010-12-14
If I boot from sda, will I still be able to run windows, as it is on sdb?

---

### Post by drs305 on 2010-12-14
> **mUNKYsTUFF said:**
> I ran this code, and terminal replied ```
Installation finished. No error reported.
```
Does this mean grub is installed for Ubuntu 9.10?
I'm very new to all this so I apologise if I'm being tedious.

You caught me editing but yes, it completed the commands. You now have grub on sdb and it should work properly. I had changed the boot drive to sda so you could have Grub2 on sda and Windows on sdb, but this should work for now.

Try rebooting. If it still fails, make sure the BIOS looks at sdb first.

Once you boot successfully, run "sudo update-grub" to be sure Windows is seen. We may put the Windows bootloader back on sdb, but one thing at a time.

---

### Post by mUNKYsTUFF on 2010-12-14
Thanks a heap!
I just booted into 9.10, and is working perfectly!
Not that I'm not grateful, but is there any way to upgrade to 10.10 without erasing my settings etc.?

---

### Post by drs305 on 2010-12-14
> **mUNKYsTUFF said:**
> Thanks a heap!
I just booted into 9.10, and is working perfectly!
Not that I'm not grateful, but is there any way to upgrade to 10.10 without erasing my settings etc.?

Not directly. Online you would have to upgrade to 10.04 and then 10.10. In truth it would probably be easier to do a clean install to 10.10.

Have you done much customization yet? There are things you can do to save a list of your currently installed packages, and you could move you /home to a new partition so you could save most of your personalized settings. If you haven't made many though, it would probably be faster to do a clean install that to try to save what you have.

But you know how much you've invested in the current setup, so it's your decision. Let us know and we can help you if you have questions.

---

### Post by mUNKYsTUFF on 2010-12-14
It doesn't really matter much I guess. After this saga, I can't really be bothered doing a clean install...
But thanks anyway, a lot! :D

---

### Post by drs305 on 2010-12-14
> **mUNKYsTUFF said:**
> It doesn't really matter much I guess. After this saga, I can't really be bothered doing a clean install...
But thanks anyway, a lot! :D


Another option is to do an online update to 10.04. Lucid is a LTS (long-term support) release, which means it will be supported for a much longer time than 9.10. Once you are on Lucid, you can always upgrade to Maverick down the road or wait until the next LTS version.

Here is the release/support schedule:
[https://wiki.ubuntu.com/Releases]("https://wiki.ubuntu.com/Releases")

---

