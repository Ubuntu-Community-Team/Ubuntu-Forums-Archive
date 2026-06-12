---
title: "Boot choices disappeared (Ubuntu 10.10/Win 7)"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by Steve.Knnn on 2011-06-26
HI,

I am a relative newbie with Ubuntu -- only about three weeks.

I have Win7 and Ubuntu 10.10 installed.

Yesterday when presented with the boot choice by the Windows boot loader I chose Ubuntu.  Ubuntu started fine.

(Not sure, I know I "should" be but I ***think*** I accepted some updates.)

At some point I restarted to go into Windows, and received no boot choice.

Any suggestions what happened and what the fix is?

Steve

---

### Post by oldfred on 2011-06-27
Welcome to the forums.

If your first choice is windows or Ubuntu from a windows boot are you running wubi? Wubi uses the windows boot loader to boot.

If you do not have a liveCD download one and run this boot script.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by Steve.Knnn on 2011-06-29
OldFred,

Thanks for the help.

First.  I set up the dual-boot in accordance with this article on LifeHacker

 [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

All seemed to work fine for several weeks.  Boot choice of windows (1st choice) and Ubuntu appeared.  Then if I chose Ubuntu it went momentarily to Grub and then started 10.10

After the upgrade on Saturday, (the culprit I believe) all went wrong.  No boot choice, straight in Ubuntu.

Not ready for that "yet".

Still need some Win programs like Itunes for syncing my iPhone and iPad and Adobe Elements.

I will now follow the rest of your suggestion and post the results in awhile.

Steve

---

### Post by Steve.Knnn on 2011-06-29
OldFred, here goes.  Thanks again,  Steve

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 4 for (,msdos4)/boot/grub.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /ubuntu/winboot/menu.lst /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _____________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>.......CP.9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1458608 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         96,392   256,108,229   256,011,838   7 NTFS / exFAT / HPFS
/dev/sda3         319,594,496   976,773,119   657,178,624   7 NTFS / exFAT / HPFS
/dev/sda4         256,108,544   319,592,447    63,483,904  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4000 MB, 4000317440 bytes
114 heads, 49 sectors/track, 1398 cylinders, total 7813120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             16     7,813,119     7,813,104   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        07D7-0B0D                              vfat       DellUtility
/dev/sda2        CA5E54755E545BEF                       ntfs       OS
/dev/sda3        2152AA410AF7033B                       ntfs       Storage
/dev/sda4        ea5c4797-d8f8-4ccc-b90f-da734af65534   ext4       
/dev/sdb1        284B-AAF1                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== sda2/ubuntu/winboot/menu.lst: =========================

--------------------------------------------------------------------------------
debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
    find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
    configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
    fallback 2
    find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
    configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
    fallback 3
    find --set-root --ignore-floppies /menu.lst
    configfile /menu.lst

title find /boot/grub/menu.lst
    fallback 4
    find --set-root --ignore-floppies /boot/grub/menu.lst
    configfile /boot/grub/menu.lst

title find /grub/menu.lst
    fallback 5
    find --set-root --ignore-floppies /grub/menu.lst
    configfile /grub/menu.lst

title commandline
    commandline

title reboot
    reboot

title halt
    halt
--------------------------------------------------------------------------------

=========================== sda4/boot/grub/grub.cfg: ===========================

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
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set ea5c4797-d8f8-4ccc-b90f-da734af65534
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos4)'
search --no-floppy --fs-uuid --set ea5c4797-d8f8-4ccc-b90f-da734af65534
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ea5c4797-d8f8-4ccc-b90f-da734af65534
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ea5c4797-d8f8-4ccc-b90f-da734af65534 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ea5c4797-d8f8-4ccc-b90f-da734af65534
    echo    'Loading Linux 2.6.35-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-28-generic-pae root=UUID=ea5c4797-d8f8-4ccc-b90f-da734af65534 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-28-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ea5c4797-d8f8-4ccc-b90f-da734af65534
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos4)'
    search --no-floppy --fs-uuid --set ea5c4797-d8f8-4ccc-b90f-da734af65534
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set CA5E54755E545BEF
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

=============================== sda4/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=ea5c4797-d8f8-4ccc-b90f-da734af65534 /               ext4    errors=remount-ro 0       1
--------------------------------------------------------------------------------

=================== sda4: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 144.269035339 = 154.907697152  boot/grub/core.img                             1
 142.305969238 = 152.799870976  boot/grub/grub.cfg                             1
 122.960201263 = 132.027510784  boot/initrd.img-2.6.35-28-generic-pae          2
 144.376197815 = 155.022761984  boot/vmlinuz-2.6.35-28-generic-pae             1
 122.960201263 = 132.027510784  initrd.img                                     2
 144.376197815 = 155.022761984  vmlinuz                                        1

============================== sdb1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by Rubi1200 on 2011-06-29
Hi and welcome to the forums Steve.Knnn :)

Do you intentionally have both Wubi and regular Ubuntu installs?

Which version of Wubi is this? From the script results, I would guess 9.04 or earlier.

In any event, there are problems with the Wubi install and you may want to consider fixing that from the LiveCD:

```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

After the last command completes, mount the root.disk to make sure all is good:

```
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
```

Then reboot, taking out the CD.

---

### Post by Steve.Knnn on 2011-06-30
Re: Boot choices disappeared (Ubuntu 10.10/Win 7)
Hi and welcome to the forums Steve.Knnn 

[COLOR="Blue"]hi[/COLOR]

Do you intentionally have both Wubi and regular Ubuntu installs?

[COLOR="Blue"]Steve writes --- this printout came after I booted from Live CD on an USB stick.  I do not intentionally have both.  Maybe from an earlier experiment with Ubuntu several years ago?[/COLOR]


Which version of Wubi is this? From the script results, I would guess 9.04 or earlier.
[COLOR="black"][/COLOR]
[COLOR="Blue"]I do not know.[/COLOR]

In any event, there are problems with the Wubi install and you may want to consider fixing that from the LiveCD:
[COLOR="Blue"]Please assure me that this will not ruin windows setup.  Maybe will this fix that problem?[/COLOR]
Code:
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
After the last command completes, mount the root.disk to make sure all is good:

Code:
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
Then reboot, taking out the CD.

---

### Post by Rubi1200 on 2011-06-30
I see no harm in running the commands I suggested; their purpose is to fix what appears to be a damaged Wubi install.

---

### Post by Steve.Knnn on 2011-07-01
Thanks Rubi,

Here is what I got:

[COLOR=Blue]ubuntu@ubuntu:~$ sudo mkdir /media/win
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /media/win
ubuntu@ubuntu:~$ sudo fsck /media/win/ubuntu/disks/root.disk
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /media/win/ubuntu/disks/root.disk

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


ubuntu@ubuntu:~$ 

and then:

ubuntu@ubuntu:~$ sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ [COLOR=Black]

Now what do you suggest.

Thanks for your continued help.
Steve
[/COLOR]
[/COLOR]

---

### Post by Rubi1200 on 2011-07-01
Those errors suggest the root.disk is not in a good state. We can try and fix it, but I want to concentrate on trying to sort out the original problem of not being able to boot into Windows.

Is this still the situation?

If yes, use a LiveCD and do the following to reinstall GRUB:

```
sudo mount /dev/sda4 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```Reboot, taking out the CD, and once you are back in Ubuntu run the following command:

```
sudo update-grub
```Then check if you can boot into Windows again and let us know what happens.

---

### Post by Steve.Knnn on 2011-07-01
No success Rubi.

Followed your instructions.  "Update-grub" appeared to be successful (see screen info)

  	 	 	 	p { margin-bottom: 0.08in; }  [COLOR=Blue]steve@steve-Dell-XPS420:~$ sudo update-grub  [/COLOR]
 [COLOR=Blue][sudo] password for steve:  [/COLOR]
 [COLOR=Blue]Generating grub.cfg ...  [/COLOR]
 [COLOR=Blue]Found linux image: /boot/vmlinuz-2.6.35-28-generic-pae  [/COLOR]
 [COLOR=Blue]Found initrd image: /boot/initrd.img-2.6.35-28-generic-pae  [/COLOR]
 [COLOR=Blue]Found memtest86+ image: /boot/memtest86+.bin  [/COLOR]
 [COLOR=Blue]Found Windows 7 (loader) on /dev/sda2  [/COLOR]
 [COLOR=Blue]done  [/COLOR]
 [COLOR=Blue]steve@steve-Dell-XPS420:~$[/COLOR]
 
When I rebooted, I got 30 seconds of blinking cursor, then entered Ubuntu.

What now?
Steve

---

### Post by drs305 on 2011-07-02
From what I can tell, your 'real' Ubuntu installation is controlling things. I don't know if you were using the Wubi version earlier, and I don't know if the Wubi installation is usable if you access it. The good news is I think your problem is in the sda4 Grub menu:
> 
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=0
fi

This section tells Grub2 to boot without delay directly into choice 0 (Ubuntu Maverick on sda4). 

Since your grub.cfg doesn't contain a 'keystatus' check, you probably can't hold down the SHIFT key during boot to display the menu (although you could try). You *should* be able to press the ESC key to get the menu to display, but timing the ESC key press can be problematic.

In any case, once your system boots into Ubuntu, you can edit the timeout so the menu displays.
```
gksu gedit /etc/default/grub
```
The following line is most likely set to 0. Change it to 5 or 10 (or any positive value) so the menu displays for that many seconds before continuing (-1 would wait indefinitely for a selection).
> GRUB_TIMEOUT=[COLOR="Red"]0[/COLOR]
Make the change, save the file, then "sudo update-grub".

You should now see the Grub menu and have a choice of OS's.

From what you posted, it sounded like originally Windows was controlling things and you were using a Wubi installation of Ubuntu (at least during boot, although that boot menu may have taken you to sda4 as well). With the changes, you are now using your sda4 partition's Ubuntu (a full, normal installation). If Ubuntu doesn't look the same or you are missing files you had in Ubuntu a week or two ago, that is probably the reason.

---

### Post by Steve.Knnn on 2011-07-02
[SIZE=4][I][B][COLOR=Red]PROGRESS

[/COLOR][/B][/I][COLOR=Red][SIZE=2][COLOR=Black]I made the suggested change to 10 seconds.Now it goes to the GRUB menu with Ubuntu in the first position and Windows in the fourth.  When I chose Windows, it went to the Windows Boot Menu, then I chose Windows.

So two questions, can I make Windows the default if I do nothing?  That is desirable for my wife and daughter.

Then are there other changes that people see in my setup that should be addressed?

The GRUB code is now:
                                                                                                                                                                   [/COLOR][/SIZE][/COLOR][/SIZE]```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```[SIZE=4][COLOR=Red][SIZE=2][COLOR=Black]
[/COLOR][/SIZE] 
Thanks,Steve
[/COLOR][/SIZE]

---

### Post by drs305 on 2011-07-02
Yes, you can change the default OS. It is done with the "GRUB_DEFAULT=0" line in /etc/default/grub. If you want to manually make the change, review the "Tasks" link in my signature line.

However, I would recommend using a GUI app called Grub Customizer. It will let you do lots of things, including changing the default, rearranging the order of the menus, renaming and hiding entries, and much more. I wrote a guide about how to install and use it - click on the "Customizer" link in my signature line.

---

### Post by wiljohnson on 2011-07-02
Try holding down arrow down for about five seconds after getting blinking cursor -- then hit enter  
This works for my system.  I have a similar problem of no grub loader appearing after upgrading to 11.04 
Boots normally into Ubuntu and will boot into W Vista if I do the down arrow then enter

---

### Post by Rubi1200 on 2011-07-03
Hi Steve.Knnn,
excellent that you are able to boot both operating systems again :-)

If all issues are resolved, then please mark this Solved using the Thread Tools near the top of the page.

---

### Post by Steve.Knnn on 2011-07-03
[COLOR="Red"][SIZE="4"]**Thanks to each of you that helped solve this problem.   Steve**[/SIZE][/COLOR]

---

