---
title: "How to move my installation to another PC ~(ALERT! on old HDD UUID)"
date: 2011-04-12
forum: Installation &amp; Upgrades
---

### Post by jjww on 2011-04-12
I have upgraded my sons PC and the new Mother Board won't take the original IDE drive (SATA Only) so I am left with a situation where I have an IDE drive with an Ubuntu 10.10 system installed that I need to copy over to my sons shiny new upgraded PC.

After a lot of searching around I found these instructions here [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) and set about the following actions

I installed Ubuntu 10.10 from a live CD on the system
I ran a tar command to back up the old HDD (as per instructions in the above link)
I copied the resulting tgz file accross to the new HDD via the network
Then I followed the instructions to restore the Ubuntu installation (But not re creating the folders I ommitted as they were already there on the new HDD after the installation) and all seemed to work well until I rebooted the new PC.

I'm now getting an alert on boot up stating
ALERT! dev/disk/by-uuid does not exist message and I'm being dropped into a shell
The UUID specified is that of the original HDD not the new one and I would like some advice on how best to proceed from here. I'm assuming that if I can fix this issue all will be good but I'm left wondering if the new hardware will be detected properly

Any help would be greatly appreciated

---

### Post by Dutch70 on 2011-04-12
Hi and welcome to UF

Lets *(and when I say "let's" I mean someone other than me)* have a look at your boot info script.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]

Then open a terminal (Cntrl+Alt+T) and run the following command...
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

To put it between code tags, just click the # symbol in the toolbar & paste it between [CODE] [ /CODE] tags.

---

### Post by ahears on 2011-04-12
Here's how to get the "Magic number" or UUID  for any drive in Ubuntu. enter ' ls -l /dev/disk/by-uuid '. This will give you the magic number or uuid to use in the grub.cfg or 40_custom file.

---

### Post by oldfred on 2011-04-12
The UUIDs are posted in the boot script along with lots of other info.

You probably have to update grub's UUIDs and fstab's UUIDs. Script will show what to change.

---

### Post by Hedgehog1 on 2011-04-12
> **jjww said:**
> ...all seemed to work well until I rebooted the new PC.

I'm now getting an alert on boot up stating
ALERT! dev/disk/by-uuid does not exist message and I'm being dropped into a shell
The UUID specified is that of the original HDD not the new one and I would like some advice on how best to proceed from here. I'm assuming that if I can fix this issue all will be good but I'm left wondering if the new hardware will be detected properly

Any help would be greatly appreciated

jjww,

Running the script from the LiveCD/LiveUSB that **Dutch70** requested in post#2 will give us the data to correct your GRUB UUID references and the **/etc/fstab** UUID references.

The changes are easy to make - but we do need that data to tell you specifically how to make the two changes.

***The Hedge***

:KS

p.s. - The two step are to:

* Update grub from the LiveCD/LiveUSB (this gives grub the current UUIDS for the new PC)

* Edit the /etc/fstab on the hard disk with the new UUIDs.

---

### Post by jjww on 2011-04-13
Thanks for all the responses
The following is te result from runing the boot script
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,928,949,759 1,928,947,712  83 Linux
/dev/sda2       1,928,951,806 1,953,523,711    24,571,906   5 Extended
/dev/sda5       1,928,951,808 1,953,523,711    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dab4c5c0-5042-43b4-9c26-7ab745b7d978   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        97075384-c0d3-48a3-b253-318487511b52   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/dab4c5c0-5042-43b4-9c26-7ab745b7d978 ext4       (rw,nosuid,nodev,uhelper=udisks)


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
search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=aeff18a3-027e-438f-bbde-98cdba5b8c45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=aeff18a3-027e-438f-bbde-98cdba5b8c45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=aeff18a3-027e-438f-bbde-98cdba5b8c45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=aeff18a3-027e-438f-bbde-98cdba5b8c45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=aeff18a3-027e-438f-bbde-98cdba5b8c45 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=aeff18a3-027e-438f-bbde-98cdba5b8c45 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set aeff18a3-027e-438f-bbde-98cdba5b8c45
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
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=953625f4-d052-4268-84e6-7327c057c1e3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
  21.6GB: boot/grub/grub.cfg
 705.5GB: boot/initrd.img-2.6.35-22-generic
 705.5GB: boot/initrd.img-2.6.35-24-generic
 705.5GB: boot/initrd.img-2.6.35-25-generic
    .8GB: boot/initrd.img-2.6.35-28-generic-pae
  21.6GB: boot/vmlinuz-2.6.35-22-generic
  23.6GB: boot/vmlinuz-2.6.35-24-generic
  23.6GB: boot/vmlinuz-2.6.35-25-generic
  23.6GB: boot/vmlinuz-2.6.35-28-generic-pae
    .8GB: initrd.img
  23.6GB: vmlinuz
  23.6GB: vmlinuz.old

```

---

### Post by Dutch70 on 2011-04-13
Ok, we need to get the UUID for / ...just to make sure.

please post the output of 
```
sudo blkid
```  

Also post the contents of your fstab.
```
sudo gedit /etc/fstab
```

All between code tags.

---

### Post by Dutch70 on 2011-04-13
Well, I was waiting for your post, but it looks like you got offline, so I'll give this a shot anyway. 

It looks like you're trying to boot to this UUID for "/" aka "root" 
aeff18a3-027e-438f-bbde-98cdba5b8c45

But you're actual UUID is...
dab4c5c0-5042-43b4-9c26-7ab745b7d978

It doesn't look like there is one listed in your fstab, it's just trying to boot to /dev/sda1.

So this is what you need to change in your fstab.
change this
```
/dev/sda1       /               ext4    errors=remount-ro 0       1
```

To this...
```
# / was on /dev/sda1       
UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 /               ext4    errors=remount-ro 0       1
```

It looks like you UUID for swap is incorrect too. Just change it to...
```
UUID=97075384-c0d3-48a3-b253-318487511b52 
```

To help you understand your fstab (**f**ile **s**ystem **tab**le), go here...
[[COLOR="Blue"]What is the Linux fstab and How Does It Work?[/COLOR]]("http://www.howtogeek.com/howto/38125/htg-explains-what-is-the-linux-fstab-and-how-does-it-work/")

.

---

### Post by Dutch70 on 2011-04-13
You will probably have to change it in grub.cfg also. Use this command to open it.
sudo gedit /boot/grub/grub.cfg 

Then change the UUID for root to the match your fstab.

You really only need to change the one in your latest kernel, you can use Synaptic or Ubuntu Tweak to remove your old grub menu entries later.

Change the part in red to your new UUID.

```
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set [COLOR="Red"]aeff18a3-027e-438f-bbde-98cdba5b8c45[/COLOR]
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=[COLOR="Red"]aeff18a3-027e-438f-bbde-98cdba5b8c45[/COLOR] ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set [COLOR="Red"]aeff18a3-027e-438f-bbde-98cdba5b8c45[/COLOR]
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=[COLOR="Red"]aeff18a3-027e-438f-bbde-98cdba5b8c45[/COLOR] ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
```

---

### Post by jjww on 2011-04-13
thanks for the responses
blkid  result is as follows
```

ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="dab4c5c0-5042-43b4-9c26-7ab745b7d978" TYPE="ext4" 
/dev/sda5: UUID="97075384-c0d3-48a3-b253-318487511b52" TYPE="swap" 

```
and the fstab contents on the HD look like this
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=953625f4-d052-4268-84e6-7327c057c1e3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by jjww on 2011-04-13
I have made the recommended changes to fstab and grub.cfg and I now get an error during boot up which states something along the line of Error, unable to mount with an option to manually mount or skip. If I skip I am dropped into a tty prompt in the desktop folder rather than booting up into gnome

---

### Post by Dutch70 on 2011-04-13
Ok...this is what your fstab should look like...
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
UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=97075384-c0d3-48a3-b253-318487511b52 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by Dutch70 on 2011-04-13
> **jjww said:**
> I have made the recommended changes to fstab and grub.cfg and I now get an error during boot up which states something along the line of Error, unable to mount with an option to manually mount or skip. If I skip I am dropped into a tty prompt in the desktop folder rather than booting up into gnome

Ok, please post a new boot info script.

---

### Post by jjww on 2011-04-13
Sorry, Scrap my last post. I had forgotten to coment out the dev /sda1 line on fstab.
After commenting that line out I now have a different issue.
As part of the boot up process I get an unable to update authority certificate error and a sanity check error.
Once these dialogues are ok'd I get the desktop up and I can log in using the original credentials but the desktop is empty and the original desktop settings are all gone.

It's always possible that I didn't zip up the original contents of the HDD properly but the files all seem to be there on the HDD so I still suspect a problem with the boot up settings.

New boot info script on it's way

---

### Post by Dutch70 on 2011-04-13
It's possible that running an update will take care of it also.
```
sudo apt-get update && sudo apt-get upgrade
```

go ahead and run that while we're having a look at your boot info script. 
I probably should have asked you to run the update first. ;)

---

### Post by jjww on 2011-04-13
New boot info script is as follows
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048 1,928,949,759 1,928,947,712  83 Linux
/dev/sda2       1,928,951,806 1,953,523,711    24,571,906   5 Extended
/dev/sda5       1,928,951,808 1,953,523,711    24,571,904  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        dab4c5c0-5042-43b4-9c26-7ab745b7d978   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        97075384-c0d3-48a3-b253-318487511b52   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
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
search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    echo    'Loading Linux 2.6.35-25-generic ...'
    linux    /boot/vmlinuz-2.6.35-25-generic root=UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    echo    'Loading Linux 2.6.35-24-generic ...'
    linux    /boot/vmlinuz-2.6.35-24-generic root=UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set dab4c5c0-5042-43b4-9c26-7ab745b7d978
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
# / was on /dev/sda1
UUID=dab4c5c0-5042-43b4-9c26-7ab745b7d978 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=97075384-c0d3-48a3-b253-318487511b52 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  21.6GB: boot/grub/core.img
 756.0GB: boot/grub/grub.cfg
 705.5GB: boot/initrd.img-2.6.35-22-generic
 705.5GB: boot/initrd.img-2.6.35-24-generic
 705.5GB: boot/initrd.img-2.6.35-25-generic
    .8GB: boot/initrd.img-2.6.35-28-generic-pae
  21.6GB: boot/vmlinuz-2.6.35-22-generic
  23.6GB: boot/vmlinuz-2.6.35-24-generic
  23.6GB: boot/vmlinuz-2.6.35-25-generic
  23.6GB: boot/vmlinuz-2.6.35-28-generic-pae
    .8GB: initrd.img
  23.6GB: vmlinuz
  23.6GB: vmlinuz.old

```

---

### Post by Dutch70 on 2011-04-13
I don't see anything wrong with the boot script, try running the update and then reboot.

ps. I could be overlooking something in the boot script, but let's see if the update takes care of it.

---

### Post by jjww on 2011-04-13
Hmm,
I'm unable to run anything when booting up with the HDD and I don't think running the update commands would actually apply anything if run when booted up from the live CD.
From your comments I'm pretty certain that something might have been missed when I zipped up the original HDD so I'm going to have a go at starting again from scratch then follow your instructions once I get back to the point where I have restored the original HDD files.
This may take some time.

---

### Post by Dutch70 on 2011-04-13
Ok, I'm going to ask a friend to take a look at this also. He may have more input or notice something I missed.

---

### Post by oldfred on 2011-04-13
If you are not the same user, you will not have the same /home or sometimes just in those who move /home have these errors:

Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)
#Replace all instances of username with your login name or use $USER
sudo chown username:username /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown username:username /home/username     
chmod 755 /home/username

.ICEauthority errors
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 600 $HOME/.ICEauthority

---

### Post by jjww on 2011-04-14
hedgehog, you mentioned that I should update grub from the live cd.
I'd appreciate it if you could indicate the steps I need to go through to achieve this

---

### Post by jjww on 2011-04-14
Steps taken so far are
1) Installed new hardware including new HDD in PC 1
2) plugged old HDD in to PC 2
3) backed up old HDD in PC 2 by using the following methods

[LIST]
[*]Mount old HDD
[*]Started a terminal session and ran sudo su to get root user
[*]cd /media then ran an ls command to get the name of the old HDD (In this case aeff18a3-027e-438f-bbde-98cdba5b8c45)
[*]then changed directory to the old HDD (cd aeff18a3-027e-438f-bbde-98cdba5b8c45)
[*]Backed up the old HDD by running the following command ```
tar cvpzf ./johnsbackup2.tgz --exclude=./proc --exclude=./lost+found --exclude=./mnt --exclude=./sys --exclude=./media .
```
[*]Whilst that was running I setup Ubuntu 10.10 (same version as on orig HDD) on PC 1 using a live CD from LXF magazine taking care to set the user name to be the same as the user name on the original HDD
[*]After setting up Ubuntu I restarted PC 1 so it was running from new HDD and set up a new shared folder. For this share to work an update and a re-boot was needed which took about 10 minuites
[*]Once the backup was complete (I ended up with a 115GB file) on PC 2 I copied the file across the network to the new shared folder on PC 1 (Would probably have been quicker at this point to plug the new HDD into PC 2 and copied the file directly accross using the same PC)
[*]3 hours later file copy was complete and on PC 1 I started a new terminal session as super user and moved the copied file from the shared folder to the root
[*]I then unpacked the file using ```
tar xvpfz johnsbackup2.tgz
``` and just let that run. It took about 1 hour to unpack everything by which time I was obviously needing to log in as the pc had gone into hibernatin mode. Interestingly enough I noticed that after logging back in I had all the original desktop files and folders so I was feeling pretty confident that all would be good
[*]I switched back into the terminal (It was still open after unpacking the backup file) and gedit fstab making the changes pointed out earlier in this thread and saving them
[*]I then ran ```
sudo update-grub
``` to automatically make the changes to the grub.cfg file that were needed as pointed out earlier in this thread
[*]Feeling pretty confident I re-booted PC 1 and after what looked like a normal boot sequence I was thrown into a tty1 terminal login prompt.
[*]So I logged in and ran the commands as outlined earleir 2 update the system ```
sudo apt-get update && sudo apt-get upgrade
``` this ran successfully so I re-booted and was thrown back to a tty1 terminal login prompt
[*]I logged back in and made the changes suggested earlier as follows
[*] ```
sudo chown $USER:$USER /home/username/.dmrc
chmod 644 /home/username/.dmrc
sudo chown $USER:$USER /home/username     
chmod 755 /home/username
```
[*]Re-booted and was thrown back to the tty terminal login prompt again
[/LIST]
So now I'm stuck!
If I try to run startx I get failed to load nvidea kernel module aborting and no screens found errors.
If I cn sort this out I think I'll have cracked it!
Any ideas?

---

### Post by jjww on 2011-04-14
The actual error I'm receiving now when runnning startx from the tty terminal is FATAL: Module nvidia not found so I guess I need to install the nvidia module. I'll do some searching to see what I can find out

---

### Post by oldfred on 2011-04-14
Add nomodeset on the linux line in the grub menu. Then you boot to a low quality mode that will let you install the nVidia driver.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by jjww on 2011-04-14
oldfred,  I worked this out whilst you were posting. Thanks to this page [http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there](http://askubuntu.com/questions/4662/where-is-the-x-org-config-file-how-do-i-configure-x-there) I sussed out that all I needed to do was to get rid of /etc/X11/xorg.conf which I did by moving it to a new file called origxorg.conf re-booted PC and ...

VOILA all is as it was, just as I'd hoped (For the time being anyway:))

Massive thank you to all those who helped me out in this thread.

---

### Post by Dutch70 on 2011-04-14
Nice work jjww!!!

Hope to see you around the boards.

---

