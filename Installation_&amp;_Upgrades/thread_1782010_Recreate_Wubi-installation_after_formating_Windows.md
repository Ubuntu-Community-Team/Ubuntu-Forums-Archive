---
title: "Recreate Wubi-installation after formating Windows ?"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by dodik4711 on 2011-06-14
Hi everybody, 

is it possible to recreate the whole wubi installation?    

Thats the situation: I only have 1 partition on my HD so i installed ubuntu via wubi and it worked perfectly fine. Recently though, i had to format my Windows but i backed up the whole installation folder of wubi/ubuntu. 
  Now i want to get my wubi installation back. I know i can access the *.disk files with several tools, but im not opting for recovering some folders. I want the complete installation running again. So is there an easy way to recreate it? 

Thanks in advance

---

### Post by Frogs Hair on 2011-06-14
It may be possible , but I don't know how you would mount the virtual disk in Windows without the installer . The mbr and wubildr are now missing from Windows and Ubuntu won't boot without these .

---

### Post by dodik4711 on 2011-06-14
Well my approach was to install ubuntu with wubi and than simply replace the wohle wubi/ubuntu directory with the backup i made before formating windows.

I knew that it wouldnt work but i hoped it would anyway ^^

So now when i select Ubuntu from the Windows boot loader i get to the grub loader which seems to work correctly. But when i choose a kernel in order to boot ubuntu it says:
```

error: no such device: 72F08016F07FDF33
error: no such disk
```Any ideas ?

---

### Post by Rubi1200 on 2011-06-14
Hi and welcome to the forums dodik4711 :)

I think we can get this fixed for you, but it will require a few steps.

First thing to do is boot the computer and select Ubuntu but don't attempt to boot because it won't work (as you know).

Instead, highlight the first entry and press "c" to get a command prompt.

Then enter the following commands to find your install:

```
search -s -f -n /ubuntu/disks/root.disk
echo $root
```What you should see is an output similar to this:

> (hd0,1) = /dev/sda1
(hd0,2) = /dev/sda2
(hd0,5) = /dev/sda5
(hd1,1) = /dev/sdb1In other words, the commands will show you for example that Wubi is on hd0,5

Based on what the output is you can identify the Wubi install.

Then, hit "Esc" to go back to the menu or type "reboot" if for some reason you get stuck.

Once you have the information you need, go back to the main menu and this time press "e" to edit.

Use the arrow keys and find the line that starts with "search".

Now change where it says (hdX,Y) to the correct partition and /dev/sdaY to the correct partition.

Then hit "CTRL"+"X" to boot.

Once back in Ubuntu, open a terminal with "Ctrl+Alt+T" and run this command:

```
sudo update-grub
```That should be it!

If you get stuck or encounter any other issues, feel free to ask.

---

### Post by dodik4711 on 2011-06-14
Wow thanks for the detailed instruction Rubi1200! :D

Unfortunately it didnt work completely. This is the output i got.

```

search -s -f -n /ubuntu/disks/root.disk
echo $root

hd0,msdos3

```And when i press "e" in the grub loader i see that.

```

insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 72F08016F07FDF33
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=72F08016F07FDF33 loop=/u\
initrd /boot/initrd.img-2.6.38-8-generic

```So the only line i could change was:
```

set root='(/dev/sda,msdos6)'

```into
```

 set root='(/dev/sda,**msdos3**)'
 
```but when i press "Ctrl+x" i get the old message.

```
error: no such device: 72F08016F07FDF33 error: 
no such disk
```

---

### Post by Rubi1200 on 2011-06-14
Oops, my mistake there :(

Follow the instructions again to edit the menu entry:

this time 

for the first set root use
> hd0,msdos3
In other words:
> set root='(/dev/sda,msdos3)'
Then delete the whole search line:
> search --no-floppy --fs-uuid --set=root 72F08016F07FDF33Finally, change the value here:
> linux /boot/vmlinuz-2.6.38-8-generic root=UUID=72F08016F07FDF33 loop=/u\to this:
> linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda3 loop=/u\Then Ctrl + X to boot and the update-grub command back in Ubuntu.

---

### Post by dodik4711 on 2011-06-15
Hmm, that didnt do the trick either.

So i edited the boot parameters from
```

insmod part_msdos 
insmod ntfs 
set root='(/dev/sda,msdos6)' 
search --no-floppy --fs-uuid --set=root 72F08016F07FDF33 
loopback loop0 /ubuntu/disks/root.disk 
set root=(loop0) 
linux /boot/vmlinuz-2.6.38-8-generic root=UUID=72F08016F07FDF33 loop=/ubuntu/disks/root.disk 
initrd /boot/initrd.img-2.6.38-8-generic

```to
```

insmod part_msdos 
insmod ntfs 
set root='(/dev/sda,msdos3)' 
loopback loop0 /ubuntu/disks/root.disk 
set root=(loop0) 
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk 
initrd /boot/initrd.img-2.6.38-8-generic 
```after pressing Ctrl+X i get this message.
```
error: no such disk
```

---

### Post by dodik4711 on 2011-06-15
Ok my fault. Misunderstood your advice first, but now i was able to boot into linux with these parameters.
```

insmod part_msdos 
insmod ntfs 
set root='([COLOR=Red]hd0,msdos3[/COLOR])' 
loopback loop0 /ubuntu/disks/root.disk 
set root=(loop0) 
linux /boot/vmlinuz-2.6.38-8-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk 
initrd /boot/initrd.img-2.6.38-8-generic

```But updating grub with "sudo update-grub" broke the grub-loader somehow. Though "sudo update-grub" didnt fail, i now cannot boot into the grub-loader. So when i pick "Ubuntu" from the Windows bootloader my machine restarts instantly with following error messages.

```

Try (hd0,0): NTFS5: No wubildr
Try (hd0,1): NTFS5: 

```

---

### Post by Rubi1200 on 2011-06-15
Okay, well this is progress...sort of.

The next thing to do is check whether the wubildr and wubildr.mbr files are where they should be, namely at the root the drive where Wubi is installed.

If they are not, copy them from their current location and place them there.

If that still doesn't do the trick, then please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by dodik4711 on 2011-06-15
Yes the wubildr files are definety present in the root folder.

Here's the content of result.txt. Though i have to say, that i didnt boot from a live cd, but from a working standard wubi installation.
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe /wubildr /wubildr.mbr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /wubildr /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Platte /dev/sda: 500.1 GByte, 500107862016 Byte
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848   307,202,047   306,995,200   7 NTFS / exFAT / HPFS
/dev/sda3         307,202,048   976,771,071   669,569,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0       4c3a4390-70e7-4eae-83b1-ac42fe4fdc0b   ext4       
/dev/sda1        4A9639D49639C0ED                       ntfs       System-reserviert
/dev/sda2        D0E6473CE6472258                       ntfs       
/dev/sda3        AEF0840FF083DBC9                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


======================== sda3/Wubi/boot/grub/grub.cfg: =========================

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
}

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
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.35-22-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set aef0840ff083dbc9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set aef0840ff083dbc9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 4a9639d49639c0ed
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

============================= sda3/Wubi/etc/fstab: =============================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
--------------------------------------------------------------------------------

================= sda3/Wubi: Location of files loaded by Grub: =================

           GiB - GB             File                                 Fragment(s)

  10.250339508 = 11.006218240   boot/grub/grub.cfg                             1
   2.437500000 = 2.617245696    boot/initrd.img-2.6.35-22-generic              2
   6.155895233 = 6.609842176    boot/vmlinuz-2.6.35-22-generic                 1
   2.437500000 = 2.617245696    initrd.img                                     2
   6.155895233 = 6.609842176    vmlinuz                                        1



```

---

### Post by Rubi1200 on 2011-06-15
Hi and thanks for the script results.

Before we proceed, a quick question:
are these the results from the new wubi install without the old root.disk you wanted to use or the old root.disk copied over the new install?

Did that make sense?

If this is the new wubi install without the root.disk you wanted, then this is what I suggest you do.

Mount the old root.disk from within the working wubi install with this command:
```
 sudo mount -o loop /host/ubuntu/disks/OTHERroot.disk /mnt
```Change to the correct path as needed.

Once mounted, do this to open the grub.cfg file:
```
 gedit /mnt/boot/grub/grub.cfg
```
Copy and paste the contents of that file into a new post here and wrap with code tags as with the boot script.

Thanks.

---

### Post by dodik4711 on 2011-06-15
Yes you guessed it. Its not the root.disk i backed up, but the root.disk from a clean wubi installation (on the formatted windows).

The grub.cfg of the backed up disk looks like this.

```

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
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root AEF0840FF083DBC9
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ntfs
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root AEF0840FF083DBC9
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.38-8-generic-pae" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root AEF0840FF083DBC9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=AEF0840FF083DBC9 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-8-generic-pae (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root AEF0840FF083DBC9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic-pae root=UUID=AEF0840FF083DBC9 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic-pae
}
menuentry "Ubuntu, Linux 2.6.38-8-generic" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root AEF0840FF083DBC9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=AEF0840FF083DBC9 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.38-8-generic
}
menuentry "Ubuntu, Linux 2.6.38-8-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos3)'
    search --no-floppy --fs-uuid --set=root AEF0840FF083DBC9
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.38-8-generic root=UUID=AEF0840FF083DBC9 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 4A9639D49639C0ED
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

```

---

### Post by Rubi1200 on 2011-06-15
Hi,
well there is a fairly easy way to fix this and a slightly more complex way.

I chose the easy way for you ;)

Simply reinstall wubi 11.04 as a clean install and then copy the root.disk you want over the new one.

That should solve it, although there may be one or two other steps involved.

Let me know how it goes.

(by the way, full credit goes to forum member bcbc who has been helping from behind the scenes)

---

### Post by dodik4711 on 2011-06-15
Yes, thank you for your help Rubi1200.
It worked perfectly. :D

---

### Post by Rubi1200 on 2011-06-16
Excellent! I am really pleased this worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

Enjoy!

---

