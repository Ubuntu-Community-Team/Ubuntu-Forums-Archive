---
title: "Windows 7 DVD fails to restore the bootloader"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by Lisiano on 2012-05-13
I was helping a good friend install a dual boot system on her laptop. Per always, I booted using a Ubuntu LiveUSB and partitioned the disks as follows
[LIST]
[*]sda[LIST]
[*]sda1 - Extended
[*]sda5 - Ubuntu root
[*]sda6 - Swap
[*]sda7 - Home
[/LIST]
[*]sdb[LIST]
[*]sdb1 - Windows 7[/LIST]
[/LIST]
Then proceeded to install Windows 7, it refused to install, claiming there were no "System partitions", so I wiped sda from the Win7 DVD and proceeded, it started installing Win7 to sdb1 and created it's evil 100mb Recovery partition on sda1, when the install finished, we did the user setup and rebooted into the LiveUSB and deleted the 100mb partition and recreated the intended sda layout, then installed Ubuntu.

After the install, I booted into the Win7 DVD and tried the system repair to fix the missing bootloader, one thing that was odd was that the "OS Selection" was blank, as in it did not show that there was Win7 installed, I tried to fix it anyway and it reported success so I rebooted into Ubuntu, updated grub, Win7 not found, again, Win7 not found. Then I manually tried telling Grub to chainload sdb1 (hd1,msdos1), it complained about "BOOTMGR not found". So I'm posting here, hoping someone knows how to get Win7 to boot.

P.S. I can't remove the disks, the screw threads are stripped(?).
P.P.S. I think this might work [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392) but could anyone confirm this? The owner left with only Ubuntu working on her laptop for now.

---

### Post by darkod on 2012-05-13
If you wiped sda, what ubuntu are we talking about? Or that was a type and you meant sdb?

In ubuntu, did you try:
sudo update-grub

It should pick up win7 and make an entry automatically in grub2 boot menu, why are you insisting on win7 bootloader.

---

### Post by Lisiano on 2012-05-13
By Ubuntu I mean a fresh install of Ubuntu 12.04 (As in, sda was blank), the layout above is the disk layout we wanted.
When Win7 refused to install, I removed the premade sda partitions and continued the install, then later restored them using Gparted.

And yes I did try, it only reported the kernels, recovery modes and  memtest. And yes, as I said in the OP, I tried manually telling Grub to boot Win7, it failed with "BOOTMGR is missing"

I'm talking about the Win7 bootloader because without it on the partition Win7 is, it won't boot. Just gives this error
```
BOOTMGR is missing
Press ctrl+alt+del to restart
``` Or something along those lines.

---

### Post by darkod on 2012-05-13
If it created the small 100MB system reserved partition, that's where bootmgr is, not on the big C: partition. But if all is well with the boot files update-grub would pick it up.

I think you are missing the win7 boot files and that's why update-grub is not picking it up.

You can try repairing the win7 boot process from the DVD using the command prompt. First make sure you set the boot flag on the C: partition, or on the small 100MB partition depending how you want to do the repair process, with or without the small partition.

Also, you better disconnect the ubuntu disk temporarily because windows is stupid about other disks.

Then at the repair command prompt try:
bootrec /fixmbr (only if you want the windows bootloader to be installed on the MBR)
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd

Restart. That should get win7 going.

After that connect the ubuntu disk, make it first in boot order and do the update-grub.

---

### Post by jadtech on 2012-05-13
the little 100mb partition windows makes is the boot manager  not a recocovery paartition if you delete that windows wont boot ..

---

### Post by Lisiano on 2012-05-13
@darkod please re-read the 1st post, I said I removed the partition and as I said, I can't remove the disks because the threads on the screws are stripped.

@jadtech It's also a recovery partition, it lets you boot into a Windows Recovery Environment, the same as the Win7 DVD Repair menu. It comes only with Win7 Ultimate, Business and Enterprise I reckon.
It is also possible to remove the partition by deleting it and "Fixing" Win7 using the DVD. Which I did on my own systems. Always worked. EDIT: For some reason (Assuming because of the 2 hard drives) it fails to detect Win7 and "Fix" BOOTMGR.

---

### Post by darkod on 2012-05-13
OK, I missed that. The rest still applies. Try to fix it from a command line. If you need help booting into it, the procedure is here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The message about system partitions from win7 installer might have been if you didn't set a boot flag on the sdb1 partition you had prepared in advance. But anyway, that's besides the point now.

---

### Post by Lisiano on 2012-05-13
Currently recreating the setup on a VM, since as I said, the laptop is with the owner. I think I'll be able to test it in about 20-30 minutes, depending on how long it takes to install Win7 and Ubuntu.

---

### Post by darkod on 2012-05-13
I think not having the boot flag is preventing it restore the boot files. It puts them where the boot flag is, so without it it can't select the destination.

With deleting the 100MB partition the boot flag went with it. Just set one on sdb1 and try the repair again, hopefully it will work.

---

### Post by Lisiano on 2012-05-13
Installed Win7 on the VM, it successfully created the 100mb (Or 104mb as reported by Ubiquity) now waiting for Ubuntu to finish installing, then going to test the boot flag theory by removing the boot flag and trying to "Fix" Win7.

---

### Post by wilee-nilee on 2012-05-13
> **jadtech said:**
> the little 100mb partition windows makes is the boot manager  not a recocovery paartition if you delete that windows wont boot ..

Correct, generally but with the commands darkod posted you can add the missing /bootmgr /Boot/BCD to the C partition.

Some times those files are already there as well, and the C just needs a boot flag.

---

### Post by Lisiano on 2012-05-13
The Win7 DVD is failing to notice Win7 installed. Chainloading hd1,msdos1 leads to BOOTMGR missing, update-grub does nothing. So this all means I successfully mimicked the setup.

Now going to try bootrec (With the boot flag on).

Result: /fixboot - Element not found (Translated from Russian)
/scanos - Finds Win7 on C:\Windows
/rebuildbcd - Finds Win7 then after typing Y or A says "Element not found".
EDIT: /fixmbr - Kills Grub (The VM doesn't even display "BOOTMGR is missing", goes straight to PXE booting).

Also, with and without the boot flag, on the "Pick an OS to restore" step it doesn't detect Win7 installed.

> **wilee-nilee said:**
> Some times those files are already there as well, and the C just needs a boot flag.
Checked, there is no C:\Boot nor C:\bootmgr so a boot flag in this case will do nothing, chainloading using Grub replaces the flag actually.

---

### Post by wilee-nilee on 2012-05-13
> **Lisiano said:**
> The Win7 DVD is failing to notice Win7 installed. Chainloading hd1,msdos1 leads to BOOTMGR missing, update-grub does nothing. So this all means I successfully mimicked the setup.

Now going to try bootrec (With the boot flag on).

Result: /fixboot - Element not found (Translated from Russian)
/scanos - Finds Win7 on C:\Windows
/rebuildbcd - Finds Win7 then after typing Y or A says "Element not found".

Also, with and without the boot flag, on the "Pick an OS to restore" step it doesn't detect Win7 installed.


Checked, there is no C:\Boot nor C:\bootmgr so a boot flag in this case will do nothing, chainloading using Grub replaces the flag actually.

Yes, grub will boot windows without a bootflag, but a windows repair will not work without a active partition, which is a boot flag. I suspect there is some windows code that can work without the partition active, but I don't know it.

---

### Post by darkod on 2012-05-13
You might have better luck on the windows forums. This is a windows issue and why it can't repair its own installation.

We have definitely seen cases where repair has worked for missing boot files. Not sure if you have some specific setup so it gets very confused when its 100MB partition is deleted.

You can also try running the boot info script from the link in my signature that will show many details about your setup.

---

### Post by Lisiano on 2012-05-13
If only there was something like this on Win except for Bootmgr..
```
sudo grub-install /dev/sdb1
```

I wouldn't go to the Windows forums since I think they would just suggest to reinstall Windows and keep the 100mb partition (Which I don't want as it WILL create problems later).
Here is the boot-info-script results, though again, this is a VM. (The 2nd Grub is from me fixing the killed Grub, sda2 is Home, forgot to tick Logical)
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 5 for .

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 12.04 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 64.4 GB, 64424509440 bytes
255 heads, 63 sectors/track, 7832 cylinders, total 125829120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046    28,172,287    28,170,242   5 Extended
/dev/sda5               2,048    19,531,775    19,529,728  83 Linux
/dev/sda6          19,533,824    28,172,287     8,638,464  82 Linux swap / Solaris
/dev/sda2          28,172,288   125,827,071    97,654,784  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 64.4 GB, 64424509440 bytes
255 heads, 63 sectors/track, 7832 cylinders, total 125829120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   125,827,071   125,825,024   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        821b2555-a11c-488d-8a8e-9b95a334a2a0   ext4       
/dev/sda5        7f15c702-ae5c-482d-a406-b1abbdcd2ef5   ext4       
/dev/sda6        84f7e0b2-7b66-40ac-82b9-9ba90d6b30db   swap       
/dev/sdb1        A414D2B214D28728                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /home                    ext4       (rw)
/dev/sda5        /                        ext4       (rw,errors=remount-ro)


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
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set=root 7f15c702-ae5c-482d-a406-b1abbdcd2ef5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos5)'
  search --no-floppy --fs-uuid --set=root 7f15c702-ae5c-482d-a406-b1abbdcd2ef5
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
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
function gfxmode {
    set gfxpayload="$1"
    if [ "$1" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
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
menuentry 'Ubuntu, with Linux 3.2.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7f15c702-ae5c-482d-a406-b1abbdcd2ef5
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=7f15c702-ae5c-482d-a406-b1abbdcd2ef5 ro   quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.2.0-23-generic
}
menuentry 'Ubuntu, with Linux 3.2.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7f15c702-ae5c-482d-a406-b1abbdcd2ef5
    echo    'Loading Linux 3.2.0-23-generic ...'
    linux    /boot/vmlinuz-3.2.0-23-generic root=UUID=7f15c702-ae5c-482d-a406-b1abbdcd2ef5 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.2.0-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7f15c702-ae5c-482d-a406-b1abbdcd2ef5
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos5)'
    search --no-floppy --fs-uuid --set=root 7f15c702-ae5c-482d-a406-b1abbdcd2ef5
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
    if sleep --verbose --interruptible 3 ; then
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
--------------------------------------------------------------------------------

=============================== sda5/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=7f15c702-ae5c-482d-a406-b1abbdcd2ef5 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=821b2555-a11c-488d-8a8e-9b95a334a2a0 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=84f7e0b2-7b66-40ac-82b9-9ba90d6b30db none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.2.0-23-generic               2
               =                boot/vmlinuz-3.2.0-23-generic                  1
               =                initrd.img                                     2
               =                vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: (stdin): Compressed data is corrupt
unlzma: (stdin): Compressed data is corrupt
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in

```

---

### Post by wilee-nilee on 2012-05-13
Windows being on a sdb disc I have rarely seen fixed.

I would pull the sda out and try it again, but the bootscript would be a great help here..

---

### Post by Lisiano on 2012-05-13
I'd would have happily installed with only sdb connected but the screw threads are stripped, both drives.

EDIT: Question, could pushing the Boot folder and bootmgr from my local Win7 install to sdb work?

---

### Post by darkod on 2012-05-13
Since you can't take the disks out, at least switch their boot order in BIOS. In case it helps windows thinking it's on the first disk.

Since you are testing in a VM anyway, why don't you try this: Try a new install on sdb1. As I said, the initial error it reported might have been if sdb1 didn't have a boot flag. That's why it refused to install on your prepared partition. And if you create partitions with the win7 installer it will create the 100MB partition.

Your sdb1 now has the boot flag. Boot up with the win7 dvd and make a new install on sdb1 with formatting the partition. Formatting is fine, as long as you don't create partitions with the installer.

It should be able to install onto sdb1 now. In that case, it will put the boot files on the same partition not creating the 100MB one.

It would still be a good idea to make sdb first in boot order before the windows install, otherwise it will put the bootloader on sda, your intended ubuntu disk. Not that it's a problem, you can always put grub2 over it. Just mentioning it.

---

### Post by Lisiano on 2012-05-13
I took only one look at that laptops BIOS... I don't want to get into it again, it's weird. It had a option to toggle if the laptop can charge... And it didn't have the option to change the order in which hard drives are tried (The laptop is relatively new). Either way, trying copying files. So far, I get an error when I chainload.

EDIT: I didn't make the partitions on the VM in advance, just told the installer to make a new partition on "Drive 1" using up all the available space. It made a 100mb partition on "Drive 0".

---

### Post by wilee-nilee on 2012-05-13
I would just reinstall with windows on the sda and Ubuntu on the sdb that should work I would think. We can see by the windows boot partition defaulting to the sda that there is a problem with a standard install.

I see the same problems of fixing a windows boot on the same HD as a Linux setup when Linux is before the windows partition.

I think the installer for windows is just limited in these ways in a stock use of it. A crack, IT person, can probably get around this stuff though.

---

### Post by darkod on 2012-05-13
> **Lisiano said:**
> 
EDIT: I didn't make the partitions on the VM in advance, just told the installer to make a new partition on "Drive 1" using up all the available space. It made a 100mb partition on "Drive 0".

OK, but now that it exists there is nothing stopping you doing a new win7 install on the existing partition right? It's a new empty OS anyway. Try a new install and that might sort your issues because when you use existing partition it doesn't want to create the small 100MB partition and it puts all boot files on the partition you select as destination. That's what you want, right?

And once the new install is there with all boot files, update-grub will have no problem adding it.

---

### Post by Lisiano on 2012-05-13
I'm so gonna ```
shred -x -n 8 -z -f
``` the VM once this is over.

Anyway, sdb1 is marked as system, when trying to reinstall, the installer tells me it will move stuff to Windows.old, I accept and it states "The setup couldn't create or a find an existing system partition. Extra information can be found in the installation log." (Translated from Russian). Any idea where the log is?

EDIT: Think I found it. It basically says it checked if the partition I wish to use has enough free space then went on to find the System disk or partition and says that everything "doesn't meet criteria for system volumes..."

---

### Post by darkod on 2012-05-13
I know windows is sometimes idiotic but I have never seen this. And I have also installed few times on previously prepared partition so that it will not create the 100MB one.

If you tell it to install on sdb1, it should do it.

You have a serious windows problem man. :) And it's not even installed. Wait when you install it and the real problems start. :)

---

### Post by Lisiano on 2012-05-13
Heh, why do you think I love Linux? Boot problems? grub-install and update-grub and you are all set. Broken dependencies? apt-get -f install. Unconfigured stuff? dpkg -a configure. Only got a disk with an old grub or even lilo? chroot and you are all set. Want to move your system to a newer rig? Just move the disk.
> Windows - more problems than you can shake a stick at.

Hmm... On rage, deleted swap, it fails, deleted root, it passed... Hmm. Maybe if I move root 200mb (Extra space just incase) then maybe it will create it's evil 100mb partition.. Then maybe I could move boot/ and bootmgr to C: and it might decide to accept defeat and boot. Or at least let /rebuildbcd work.

EDIT: Ctulhu and Flying Spagheti Monster bless VMs.

EDIT2: Interesting. Before, Ubuntu did not detect any users on Win7 but when reinstalling Ubuntu this time, it detected and even marked Win7 as "Windows 7 (loader)". Maybe plainly moving the files works... If it does, then I want to find the person who made the 100mb partition creation decision and strangle him/her with my own hands.

---

### Post by Lisiano on 2012-05-13
!@#$%^&*()_+-=... God dammit. Plainly moving files _works_. Ubuntu easily detected Windows 7 on sdb1 and offered in Grub. I hate the Windows devs even more now.

I'll keep this unsolved until I try this on actual hardware, aka the laptop.
Either way, time to shred this darn VM.


P.S.> **wilee-nilee said:**
> I see the same problems of fixing a windows boot on the same HD as a Linux setup when Linux is before the windows partition.Installing Ubuntu on my own systems then installing Windows later worked fine, though I did use a trick to halt the Installer from creating the 100mb partition, it didn't work on the laptop or the VM though.
> **wilee-nilee said:**
> I think the installer for windows is just limited in these ways in a stock use of it. A crack, IT person, can probably get around this stuff though. Maybe, though if that IT person doesn't know how to think outside the box, he will hardly do it. For example, MS recomends using audit mode to install software. That mode fails a lot if you try to install a driver or anything that might install a dll. I find opening CMD on the Welcome Screen and then opening notepad, navigating to the files I want to install, then installing them this way is _way_ faster and _always_ works (Well, except for Chrome as it install into AppData). Either way, the guidelines and the way it installs stuff, is for lunatics I say. Why must we still use primary partitions when we can easily shove it into a logical one? Linux lets us do it for a long time now.

---

