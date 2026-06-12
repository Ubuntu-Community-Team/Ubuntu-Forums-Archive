---
title: "Vista won't boot properly after Ubuntu Installation"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by Goldcoin on 2010-01-31
MMK. I installed Ubuntu 9.10 on my computer, partitioning my disk 12GB for Ubuntu and a 1GB buffer (swap), while leaving Vista and drive C: intact. 

When I installed Ubuntu there was no side-by-side option which I was expecting. However, I was able to install Ubuntu on the new partition just fine. I set the Ubuntu partition as a primary if that makes any difference.

My current situation: Ubuntu boots up fine from the Grub Menu, however, when I try to boot up Vista, it sends me to "system recovery options". 

Also when I try to access my hard drive from Ubuntu, I get this:
[img]http://img189.imageshack.us/img189/43/screenshotxu.png[/img]

Is there anything I can do to fix this? Please bear with me, as I'm new to this kind of thing. I'll try to give any more info. if necessary. Thx.

---

### Post by Goldcoin on 2010-02-01
Pssht. OK. Here's what I think happened. Somehow I screwed something up and Vista boots off of my recovery (third) partition. So every time I try to boot Vista up from GRUB it sends me to the recovery screen! How would I go about changing this, so I boot off of the first partition of my hard disk?

---

### Post by --Steve on 2010-02-01
I'm kind of a newbie, but I've been spending a lot of time lately trying to avoid your particular problem.   Vista installs a Boot Manager of its own.   GRUB may have written a new MBR over the MBR that Boot Manager created.   

(1) Hide all partitions and make sure the only "active" partition is the Vista partition.  (with a partition tool)  
(2) Change your boot sequence to 1st-CD/DVD, then 2nd the Drive with Vista.   
(3) Boot with your Vista DVD 
(4) There should be a repair option that will let you fix the boot process.   Sorry that I don't have any more info for this step.

The goal would be to try to put a new boot process on -only- the "active" Vista partition.  Otherwise you are just going to wipe out the MBR that GRUB just created, then you'll have to fix the GRUB boot-up.   IT MAY BE that the Vista repair will only let you fix the previous MBR and which case it will just wipe-out the new GRUB boot-up.   

I'll be watching this thread, as I don't know yet if GRUB and the VISTA Boot Manager can peacefully exist on the same system (using the -same- MBR) or if only one can be used.

Hope this helps, Good Luck!

---

### Post by --Steve on 2010-02-01
One more thing.   I believe you can configure GRUB to boot Vista.  But I'm pretty sure you'll need to first get Vista booting okay on it's own, then GRUB can be configured to start that working Vista boot process.

---

### Post by --Steve on 2010-02-01
Found another post that should help you some.
This user was able to install GRUB to the ubuntu partition (a Primary and 'B' bootable partition) and modify the Vista Boot mgr to load GRUB.  This is exactly the set-up I'm hoping to achieve. (But my set-up is XP on Drive-1 And Vista on Drive-2; I'm loading ubuntu to 60GB of freespace on Drive-1) I loaded the EasyBCD tool (that he is using) about a week ago.   At first I thought this tool was fantastic!  I can't quite recommend it though.   It is very easy to mess-up your boot records and not enough documentation for this tool.  (VERY DANGEROUS, I have already had to fix something I didn't mean to save)  The program is not being updated either.   Just learn to edit with Windows BCDEdit command.   

( see the link and info for the post below )  

* * * * *
[ i can paste this into the browser and it works ]
[http://ubuntuforums.org/showthread.php?t=1197908&highlight=partman](http://ubuntuforums.org/showthread.php?t=1197908&highlight=partman)

Name of thread:     
[ubuntu] I'm in the middle of the installation. Help me please! (Multi-page thread 1 2)  13 replies
First post: June 26th, 2009  User: pooja
Last post: June 29th, 2009  User: Polaris96

---

### Post by presence1960 on 2010-02-01
Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page and all credit is his.

Also how did you create the space for Ubuntu? Did you resize Vista from it's own disk management utility or did you use an outside partitioning utility to shrink Vista? If you resized Vista with a partitioning tool other than it's own disk management utility you are going to have to repair Vista with it's install DVD by doing the instructions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista/Windows 7. That will fix Vista, but then you are going to have to restore GRUB to MBR. The results from the boot info script will give me the info necessary to relay to you the exact commands to run to reinstall GRUB.

---

### Post by Goldcoin on 2010-02-01
I originally tried using Acronis, but I couldn't shrink the disk with it, so I had to use the Windows Utility to shrink sda1 to allow space for Ubuntu and a buffer (plus some space not designated to anything in particular). I guess it's a good thing Acronis wouldn't work for me!

I downloaded and ran the script. Here's the results:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       420764671 sectors, but according to the info from 
                       fdisk, it has 420774416 sectors.
    Mounting failed:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63   420,774,479   420,774,417   7 HPFS/NTFS
/dev/sda2         420,774,480   444,197,249    23,422,770  83 Linux
/dev/sda3         472,288,320   488,391,119    16,102,800   7 HPFS/NTFS
/dev/sda4         470,318,940   472,278,869     1,959,930   5 Extended
/dev/sda5         470,335,005   472,278,869     1,943,865  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F454A3EC54A3AFB2                       ntfs                                     
/dev/sda2        539ae419-7da4-4ba7-b0f4-8fd896634d21   ext4                                     
/dev/sda3        2C88743C8874071C                       ntfs       Recovery                      
/dev/sda5        823d7493-0334-4fb2-b541-ee8c250b6863   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
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
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=823d7493-0334-4fb2-b541-ee8c250b6863 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```

---

### Post by oldfred on 2010-02-01
Did you always boot thru a recovery partition? Or When you booted windows did it ask whether to boot the recovery or the install?

Windows combines the boot of two installs into one as standard pratice and moves some of its boot files to the partition with the boot flag set on.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Something moved the start of your first partition from 2048 (Win7/Vista std) to 63 which is the normal standard. Windows will work from sector 63 as you can install it over XP which starts at 63, but it will now require repairs.

I would make sure the boot flag is on your Vista install. You can set it with gparted. Only one partition can have a boot flag and linux does not need a boot flag to boot.

Then I would use the Vista CD to repair Vista. If you do not run the fixmbr command it will not overwrite grub. But just incase these are instructions to reinstall boot loaders:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Vista repair:
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Possibly better instructions from 
meierfra. using Ubuntu to repair windows Vista
[http://ubuntuforums.org/showthread.php?t=1350824](http://ubuntuforums.org/showthread.php?t=1350824)   post 10 on repair of Vista
I agree. But I recommend to use testdisk to fix your boot sector. (Vista's "fixboot" usually only repairs the boot code in the boot sector, but not the boot parameters)

---

### Post by Goldcoin on 2010-02-01
hmm. OK. As far as I know, I have been booting off the first partition which contains windows and all my files. The 3rd (sda3) partition was just my recovery drive (drive D:\ as they say in Windows).

 I don't have a Vista disk (B/c I was too lazy and dumb to burn one) but basically what you're saying is I can burn the bootrec.exe program to a disk and it will have the same effect? Then all I have to do is select "Repair Your Computer" and run: 
 
     bootrec.exe /fixboot 
   
and then

     bootrec.exe /fixmbr

for everything to be worked out?

---

### Post by oldfred on 2010-02-01
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc (repairs only) at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

---

### Post by presence1960 on 2010-02-01
I would burn that CD from neosmart. I would also run from that CD chkdsk /f a couple times before running those other commands.

---

### Post by Goldcoin on 2010-02-01
Ok. Vista's back.

However, GRUB is now gone. What can I do to get it back, or is there something better I can install in place of GRUB?

---

### Post by presence1960 on 2010-02-01
> **Goldcoin said:**
> Ok. Vista's back.

However, GRUB is now gone. What can I do to get it back, or is there something better I can install in place of GRUB?

Reinstall GRUB to MBR. Boot 9.10 Live CD, choose 'try ubuntu without any changes. When desktop loads open terminal and run ```
sudo mount /dev/sda2 /mnt
```
This will mount ubuntu / partition.

Next in terminal run ```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
This will put GRUB back on MBR. Reboot and remove the CD. Boot into ubuntu and open terminal and run ```
sudo update-grub
```

You should now be able to boot both OSs from GRUB.

---

### Post by Goldcoin on 2010-02-01
hmm. This is interesting. I'm back where I started now. For some reason, Windows is still booting from dev/sda3 in GRUB and it takes me to the recovery screen. I can access Ubuntu, but not Windows.

I tried simply editing Grub.cfg file, but that wouldn't work. I couldn't save it. :/ I'm wondering if I could use NeoGrub?


IDK if this helps, but here is my grub file.

```
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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
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
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
```A look into Gparted:

[IMG]http://img64.imageshack.us/img64/4416/screenshotluj.png[/IMG]


Disk Utility:

[IMG]http://img691.imageshack.us/img691/7500/screenshotpor.png[/IMG]


ALSO, when I try to run dskchk /f in Windows Vista, it says the drive can't be locked, and prompts me asking if I want to do the check when the system is restarted (Y/N). I say Y, but it doesn't seem to do anything upon restart, so I don't know...

Let me know if there are any other tests or checks you need me to do, and thanks for sticking with me here!

---

### Post by oldfred on 2010-02-02
When you said Vista was back, did it boot ok? Did you boot it several times to make sure? Did it want to run chkdsk until there were no errors after the reboot.

Also does the boot_info script still have trouble reading the Vista partition?

You can probably run chkdsk from the command line of the Vista RE disk without running fixboot which overwrites grub. chkdsk has several parameters that are different than my XP version, maybe /R or /P?

---

### Post by Goldcoin on 2010-02-02
Vista booted fine after running bootrec. I was able to do this at least twice. It didn't automatically try to run chkdsk after the reboot if that's what you mean. When I tried it manually, it wouldn't work.

I'll try running the boot_info script again and I'll post the results. EDIT: Here are the results. Still can't mount it from Ubuntu.

```
 ============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       420764671 sectors, but according to the info from 
                       fdisk, it has 420774416 sectors.
    Mounting failed:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1549f232

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   420,774,479   420,774,417   7 HPFS/NTFS
/dev/sda2         420,774,480   444,197,249    23,422,770  83 Linux
/dev/sda3         472,288,320   488,391,119    16,102,800   7 HPFS/NTFS
/dev/sda4         470,318,940   472,278,869     1,959,930   5 Extended
/dev/sda5         470,335,005   472,278,869     1,943,865  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        F454A3EC54A3AFB2                       ntfs                                     
/dev/sda2        539ae419-7da4-4ba7-b0f4-8fd896634d21   ext4                                     
/dev/sda3        2C88743C8874071C                       ntfs       Recovery                      
/dev/sda5        823d7493-0334-4fb2-b541-ee8c250b6863   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro)
/dev/sr0         /media/cdrom0            iso9660    (ro,nosuid,nodev,utf8,user=ubuntu)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root=(hd0,2)
search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
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
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,2)
    search --no-floppy --fs-uuid --set 539ae419-7da4-4ba7-b0f4-8fd896634d21
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 ro single 
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
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root=(hd0,3)
    search --no-floppy --fs-uuid --set 2c88743c8874071c
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda2 during installation
UUID=539ae419-7da4-4ba7-b0f4-8fd896634d21 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=823d7493-0334-4fb2-b541-ee8c250b6863 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 
```I'll try running chkdsk from the recovery disk too. What does /p do?

_**EDIT:**_

mmk. I ran 

```
X:\Sources> chkdsk /r 
```

using the vista recovery disk's terminal. It said it couldn't lock the current drive and that it was write protected. hmm...

---

### Post by Goldcoin on 2010-02-03
Bump.

I've tried checking the disk in Windows with /r and /f, but Ubuntu still doesn't recognize the drive, and I can't dual boot Vista and Ubuntu at the same time still.

---

### Post by Goldcoin on 2010-02-05
Bump

---

### Post by Goldcoin on 2010-02-08
Bump.

---

### Post by oldfred on 2010-02-08
X:\Sources> chkdsk /r

Are you sure that was not trying to run checkdisk on the cd? I think if it is from a command line you need a c: or d:?

If you install Vista's boot loader does it work? And if you install grub can you boot ubuntu? So the only problem is booting Vista from grub?

---

