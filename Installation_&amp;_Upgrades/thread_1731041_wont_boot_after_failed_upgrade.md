---
title: "wont boot after failed upgrade"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by jrdbarnhart on 2011-04-16
I was running 10.10 and I started to upgrade to 11.04 beta2. And while it was in the middle of applying the updates it shutdown on its own. When I went to boot it back up it originally told me something about the drive is unavailable and asked if i wanted to do an automatic or manual recovery. Neither of those worked so created a live cd of 10.10 and it will boot to that with no problem. I did some research and thought that it may be the grub bootloader so i upgraded that to version 1.98 and now all it does is go to a black screen with the prompt  "grub>". So my question is what do i do? I would reinstall 10.10 but I cannot loose any of the data that is on the disk.

---

### Post by Dutch70 on 2011-04-16
Hi, let's have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and [COLOR="Red"]copy/paste the info  **between code tags.[/COLOR]**

To put it between code tags, just click the # symbol in the toolbar & [COLOR="Red"]paste it between [CODE] [ /CODE] tags.[/COLOR]

---

### Post by jrdbarnhart on 2011-04-16
.

---

### Post by jrdbarnhart on 2011-04-17
bump

---

### Post by Dutch70 on 2011-04-18
If you don't put it between code tags as suggested, it loses it's formatting and makes it difficult to tell anything about. That's probably why everyone is passing it up. Look at my response again. They're difficult enough to read when they're posted correctly.

---

### Post by jrdbarnhart on 2011-04-18
Okay ill give it another shot thanks


```

Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #1 for (,msdos1)/boot/grub.

sda1: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.10
Boot files/dirs: /etc/fstab /boot/grub/core.img

sda2: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 2,048 300,298,239 300,296,192 83 Linux
/dev/sda2 300,300,286 312,580,095 12,279,810 5 Extended
/dev/sda5 300,300,288 312,580,095 12,279,808 82 Linux swap / Solaris


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/loop0 squashfs 
/dev/sda1 e2ff097b-2830-49af-9483-6e287dbf79d4 ext4 
/dev/sda2: PTTYPE="dos" 
/dev/sda5 0a50b8a1-fe3e-4ad3-a75d-bbec77722143 swap 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

aufs / aufs (rw)
/dev/sr0 /cdrom iso9660 (ro,noatime)
/dev/loop0 /rofs squashfs (ro,noatime)


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
/dev/sda1 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=0a50b8a1-fe3e-4ad3-a75d-bbec77722143 none swap sw 0 0

=================== sda1: Location of files loaded by Grub: ===================


81.7GB: boot/grub/core.img
81.7GB: boot/vmlinuz-2.6.35-22-generic
81.7GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda2

00000000 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff |................|
*
00000050 8f a5 b5 ff 83 ab c7 ff 98 c5 e5 ff 9a c7 e6 ff |................|
00000060 9b c8 e7 ff 9d c9 e7 ff 9e ca e8 ff 9e ca e8 ff |................|
00000070 7a af d8 ff 3d 78 af ff 00 41 88 ff 00 41 88 ff |z...=x...A...A..|
00000080 3b 76 ae ff 76 ab d6 ff 48 80 b3 ff 4a 81 b5 ff |;v..v...H...J...|
00000090 4d 84 b6 ff 50 86 b8 ff 53 89 ba ff 56 8b bb ff |M...P...S...V...|
000000a0 58 8d bd ff ac c7 df ff ff ff ff ff ff ff ff ff |X...............|
000000b0 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff |................|
*
00000110 90 a6 b5 ff 79 9c b6 ff 9a c7 e6 ff 9b c8 e7 ff |....y...........|
00000120 9d c9 e7 ff 9e ca e8 ff 9f cc e9 ff a0 cb e9 ff |................|
00000130 76 ab d6 ff 3b 76 ae ff 00 41 88 ff 00 41 88 ff |v...;v...A...A..|
00000140 39 74 ad ff 72 a7 d3 ff 4b 81 b5 ff 4d 84 b6 ff |9t..r...K...M...|
00000150 50 86 b8 ff 53 89 ba ff 56 8b bb ff 58 8d bd ff |P...S...V...X...|
00000160 5a 8f bf ff ae c8 df ff ff ff ff ff ff ff ff ff |Z...............|
00000170 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff |................|
*
000001b0 ff ff ff ff ff ff ff ff ff ff ff ff ff ff 00 fe |................|
000001c0 ff ff 82 fe ff ff 02 00 00 00 00 60 bb 00 00 00 |...........`....|
000001d0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
*
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200

```

---

### Post by Dutch70 on 2011-04-18
I'm certainly not a pro here, but one thing I notice is that in your fstab, your / partition is not identified by the UUID. I would try booting to the live cd/usb & editing the fstab.
Change this...
```
/dev/sda1 / ext4 errors=remount-ro 0 1
```
To this...
```
# / on /dev/sda1 
UUID=e2ff097b-2830-49af-9483-6e287dbf79d4 / ext4 errors=remount-ro 0 1
```

To edit your fstab, use this command to open it & don't forget to save it when you're finished.
```
gksudo gedit /etc/fstab
```

Before rebooting, update grub2
```
sudo update-grub
```

Try to reboot into the installed system.

*Also, please delete your first boot info script that's not in code tags.*

---

### Post by jrdbarnhart on 2011-04-18
> **richerdjohn said:**
> If you are working is online basis then you must want to update your system according to rules and work.you want to installing all those new things are lunching in market in his system.

Not really sure what you are getting at here. I can get online using the live cd if thats what you mean. I cannot update anything though. I will try tonight what Dutch70 recommended and report back the progress

---

### Post by jrdbarnhart on 2011-04-19
I tried updating the fstab but to no avail. it opened and there were only a few lines of code and i added the recommended lines but after i attempted to reboot, which didnt work i had to use the live cd again,  the edits were gone. I at least updated the grub for some reason it was telling me that it wasnt even installed but i know it was before so i reinstalled it yet again. I am willing to try about anything except wiping the harddrive clean.

---

### Post by Dutch70 on 2011-04-19
Did you click "save" in fstab before you closed it? :confused:

---

### Post by jrdbarnhart on 2011-04-19
I did save the fstab when i closed the file.  And here are the contents of the fstab file. I am not really sure what I am doing with it honestly


```

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0

```

---

### Post by Dutch70 on 2011-04-20
Run this command again and paste the entire contents of fstab.
```
gksudo gedit /etc/fstab
```

---

### Post by jrdbarnhart on 2011-04-20
That is the entire content of the file, I presume that there there should be alot more to it?

---

### Post by Dutch70 on 2011-04-20
Yes, it should look more like this. This is your UUID's.

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=e2ff097b-2830-49af-9483-6e287dbf79d4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0a50b8a1-fe3e-4ad3-a75d-bbec77722143 none            swap    sw                0       0
```

At this point I don't see how it can hurt to paste that into fstab. You may be looking at a reinstall anyway. Unfortunately that can happen when you upgrade to a beta, sometimes when you upgrade to an official release. I've never been able to upgrade. That's why it's a really good idea to have a separate partition for /home.

---

### Post by jrdbarnhart on 2011-04-20
i changed the fstab tried to reboot. did not work. i checked the fstab again and it was like i never changed it. i realize that i will most likely need to reinstall. so my question is now. how do i get my files off of the harddrive?

---

### Post by johnieutah on 2011-04-28
Hello, 

I have the exact same problem.  I was upgrading from 10.10, everything seemed to be going fine one minute, the next time I looked at the screen it was blank.  I assumed everything had gone ok and the laptop had powered down.

Booting up gives the same error as stated before, 'cannot mount/' or words to that affect.

I've run the boot script as advised:-


```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048    78,125,055    78,123,008  83 Linux
/dev/sda2          78,127,102   312,580,095   234,452,994   5 Extended
/dev/sda5          78,127,104    82,030,591     3,903,488  82 Linux swap / Solaris
/dev/sda6          82,032,640   312,580,095   230,547,456  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders, total 15794175 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    15,794,174    15,794,112   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       b24dea33-5a03-654f-894e-41dcdbfd42ba   ext2                                     
/dev/sda1        0f9a0dce-4d13-4654-9c28-0b827d94ee45   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        e743f947-928b-4bc3-9a1d-d86fff6101b5   swap                                     
/dev/sda6        33dd091b-5fa3-47c5-aa51-b1fa772d4f4a   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        067F-7B60                              vfat       MYLINUXLIVE                   
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
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
menuentry 'Ubuntu, with Linux 2.6.35-28-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.35-28-generic ...'
    linux    /boot/vmlinuz-2.6.35-28-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.35-27-generic ...'
    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 0f9a0dce-4d13-4654-9c28-0b827d94ee45
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
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

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

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
UUID=0f9a0dce-4d13-4654-9c28-0b827d94ee45 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=33dd091b-5fa3-47c5-aa51-b1fa772d4f4a /home           ext4    defaults        0       2
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


   6.5GB: boot/grub/core.img
  13.7GB: boot/grub/grub.cfg
   2.0GB: boot/initrd.img-2.6.32-25-generic
    .2GB: boot/initrd.img-2.6.35-22-generic
    .4GB: boot/initrd.img-2.6.35-23-generic
  14.2GB: boot/initrd.img-2.6.35-24-generic
  14.6GB: boot/initrd.img-2.6.35-25-generic
   2.4GB: boot/initrd.img-2.6.35-27-generic
  14.5GB: boot/initrd.img-2.6.35-28-generic
   7.0GB: boot/vmlinuz-2.6.32-25-generic
   6.7GB: boot/vmlinuz-2.6.35-22-generic
   6.7GB: boot/vmlinuz-2.6.35-23-generic
   6.7GB: boot/vmlinuz-2.6.35-24-generic
   1.0GB: boot/vmlinuz-2.6.35-25-generic
   6.7GB: boot/vmlinuz-2.6.35-27-generic
   6.7GB: boot/vmlinuz-2.6.35-28-generic
  16.5GB: boot/vmlinuz-2.6.38-8-generic
  14.5GB: initrd.img
   2.4GB: initrd.img.old
   6.7GB: vmlinuz
   6.7GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb1

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 08 c0 07  |.X.SYSLINUX.....|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  c0 ff f0 00 20 3c 00 00  00 00 00 00 02 00 00 00  |.... <..........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 60 7b 7f 06 4e  4f 20 4e 41 4d 45 20 20  |..)`{..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 f0  e7 73 00 66 ba 00 00 00  |..E}.f...s.f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

I have my 160GB drive partitioned in to OS and DATA.  Can I fix this boot error or is it a case of burning a 11.04 CD and reinstalling the OS? - I'm assuming I can tell the installation that home is on the 2nd partition of something later??

Cheers!

---

