---
title: "Install to USB"
date: 2010-11-30
forum: Installation &amp; Upgrades
---

### Post by PhoenixGI on 2010-11-30
I did a LiveCD to USB install, following the directions I found at [http://ubuntuforums.org/showpost.php?p=10117203&postcount=14](http://ubuntuforums.org/showpost.php?p=10117203&postcount=14) When I went to reboot to the USB stick, all I get is a black Screen (monitor is on and lit, just nothing on the display) No cursor or command prompt. I've tried holding shift to bring up the GRUB menu, changing splash quiet to nomodeset, or just adding nomodeset after the splash quiet thing.  I've even tried xforcevesa instead of nomodeset still black screen.  Looking at the logs nothing is current as of the last time I tried to boot the computer, it's strictly what was written when I installed it to the stick.  Other things I've checked/tried, Pressing CTRL+Alt+F1 at GRUB to get TTY, all I get is that blank screen.  I've Checked etc/default/grub to ensure the timeout was higher then 0.  The Install CD seems to be OK but I have (as it did another install successfully) but I haven't done any throughal checking of it (there was no check this disk on the first screen of the LiveCD) The USB sticks also seem to be ok (in windows though).  Using the disk utility on the live CD I did check the file system on the USB stick, the "/" partition came up clean.  Anybody have any other thoughts on this install, any thing else I can check?

---

### Post by oldfred on 2010-11-30
Flash drive should be just another drive. With it plugged in run this from the liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

---

### Post by PhoenixGI on 2010-11-30
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for (,msdos2)/boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 7998 MB, 7998537728 bytes
247 heads, 62 sectors/track, 1020 cylinders, total 15622144 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048       999,423       997,376   b W95 FAT32
/dev/sda2    *        999,424    10,999,807    10,000,384  83 Linux
/dev/sda3          10,999,808    13,000,703     2,000,896  83 Linux
/dev/sda4          13,000,704    15,620,095     2,619,392  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7558-5E77                              vfat                                     
/dev/sda2        d1b6df56-5c31-4b30-bf32-4ebb6098cbfe   ext4                                     
/dev/sda3        a5fed752-4dfc-447d-9011-ac424747786f   ext2                                     
/dev/sda4        05beaec3-19b8-4d27-9b5d-c44dccbabbc6   swap                                     
/dev/sda: PTTYPE="dos" 
error: block: No such file or directory
error: devices: No such file or directory
error: /dev/mapper/no: No such file or directory
error: found: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda2/boot/grub/grub.cfg: ===========================

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
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set d1b6df56-5c31-4b30-bf32-4ebb6098cbfe
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set d1b6df56-5c31-4b30-bf32-4ebb6098cbfe
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
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d1b6df56-5c31-4b30-bf32-4ebb6098cbfe
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d1b6df56-5c31-4b30-bf32-4ebb6098cbfe ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d1b6df56-5c31-4b30-bf32-4ebb6098cbfe
    echo    'Loading Linux 2.6.35-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.35-23-generic-pae root=UUID=d1b6df56-5c31-4b30-bf32-4ebb6098cbfe ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d1b6df56-5c31-4b30-bf32-4ebb6098cbfe
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set d1b6df56-5c31-4b30-bf32-4ebb6098cbfe
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

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=d1b6df56-5c31-4b30-bf32-4ebb6098cbfe /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=a5fed752-4dfc-447d-9011-ac424747786f /home           ext2    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=7558-5E77  /windows        vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda4 during installation
UUID=05beaec3-19b8-4d27-9b5d-c44dccbabbc6 none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


   1.9GB: boot/grub/core.img
   3.4GB: boot/grub/grub.cfg
   4.0GB: boot/initrd.img-2.6.35-23-generic-pae
   2.0GB: boot/vmlinuz-2.6.35-23-generic-pae
   4.0GB: initrd.img
   2.0GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```

---

### Post by oldfred on 2010-11-30
I do not see anything in the boot script. 

Not sure what the 4 lines of error on no such device relate to?? Generally the /dev/mapper relates to LVM or RAID which you would not have on a flash device and those entries can stay on a drive and cause problems.

If you hold shift from BIOS until menu, do you get a menu? If so then boot is ok, and it is a video, BIOS setting, or system requires some sort of boot parameter for hardware it does not support directly.

I have saved all these comments - see if any relate:

BIOS should be set for IDE compatibility mode
The mode for the disc was set to AUTO. Changed it to LBA. Then it worked.
Change SATA controller mode from AHCI to Compatibility 
So then I tried disabling "IDE DMA Transfer Access" which had no explanation in the BIOS as to what it did. Restarted the computer and Ubuntu booted up no problem. According to the motherboard manual "This item is used to enable or disable the DMA transfer function of the IDE hard drive."
BIOS in not updated to latest revision
BIOS not set to boot CD or USB first
BIOS shows floppy or firewire and you do not have those
changing newer BIOS SATA from 6 Gbs to a 3Gbs 
Other BIOS settings - Security or locked down Boot sector, Bitlocker
Disable Quickboot in BIOS 
Flexnet in Boot area (DRM "rights"/security)
Raid meta data on drive - even if one drive (Vendor happened to set it on)
NTFS partition needs chkdsk, gparted will not see drive if flag set, flag is set on resize
Other Drive errors - Partitions errors, corruption etc
Mixed MBR (msdos) & gpt partitions (either does work)
Video issues - use f6 to set nomodeset or other options or f4
Computer is older and does not meet minimum install standards
Install stops at partitions or only full disk install - (All four primary partitions used)
Various hardware issues - bad cables, loose cables, 
Search for Unique issue with your specific hardware.


Some settings:
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by oldfred on 2010-12-01
Yes but nothing seems to be helping. 

Can you get grub menu with shift key held down?

When you remove splash quiet, do you see the boot process starting with time (sec) and task?

My monitor always went to sleep, but I could see USB or hear Hard Drive kept working, so I knew it was still booting. nomodeset worked for me. Others depending on video card had to try other settings. The xforcevesa worked for many also.
What video card do you have.

---

### Post by C.S.Cameron on 2010-12-01
I hate to interrupt here, OldFred knows his stuff. 
But have you tried the drive on a second computer?

Also at the top of bootinfoscript output under "Drive sda ___", the partition sizes look a little strange to me.

Grub and fstab look ok to me, (but I'm no expert).

---

### Post by runeh76 on 2010-12-01
Try ext3.

---

### Post by PhoenixGI on 2010-12-01
Ok, lots of things here, which is cool, just don't want to miss anything.

> **oldfred said:**
> Yes but nothing seems to be helping. 

Can you get grub menu with shift key held down?

When you remove splash quiet, do you see the boot process starting with time (sec) and task?

My monitor always went to sleep, but I could see USB or hear Hard Drive kept working, so I knew it was still booting. nomodeset worked for me. Others depending on video card had to try other settings. The xforcevesa worked for many also.
What video card do you have.

I can get the Grub menu, but no matter which system option I chose I go to the blank screen, Removing splash quiet ad adding the nomodeset didn't seem to do anything at all, after I remove and add those lines, do I have to "save" it before I (I think its) press x so GRUB can continue to boot?

The thumb drive does start to flash like it's being accessed, but after letting it sit for up to 10 mins nothing is happening.  I've tried both xforcevesa and nomodeset.  Another note about the thumb drive.  I've had it connected both directly to the USB port on the PC and to a USB hub, with the same result.

The Video card I have is a nvidia GTS 250 from MSI.

I'm still looking at your BIOS settings notes, most are either all set or not applicable, or not available to be set. I am trying to look more into the APCI stuff.  Also the for the top 4 errors, the only drives I have enabled as I'm doing this is the CD drive (for the liveCD when needed) and the thumb-drive. So the lack of any other hard-drives might be what's throwing the errors.  Course I'm just guessing here, 
 
> **C.S.Cameron said:**
> I hate to interrupt here, OldFred knows his stuff. 
But have you tried the drive on a second computer?

Also at the top of bootinfoscript output under "Drive sda ___", the partition sizes look a little strange to me.

Grub and fstab look ok to me, (but I'm no expert).

I've taken the thumb-drive and attached it to my laptop, and it boots perfectly (I'm using it right now to type this up, Got my wireless card set up even).  Not knowing how well Ubuntu would react to going from PC to Laptop, every time I try one the the thumb-drives on the laptop, I reinstall to it before using it on the PC again. Which, as a side question; How well does Linux / Ubuntu handle going from computer to computer with a single install.  Could I take this thumb-drive between my laptop and PC and not have issues, even though they are completely different hardware (right down the the CPU and Video card different, AMD/ATI in the laptop, Intel/nVidia in the PC)

As far as the partition sizes, apparently I don't know how to do the math any more, it was suppose to be 5GB for "/", 512MB for "/dos", 1GB for "/home" and whatever was leftover for swap.  Looks like I was a MB off on "/dos" and 100MB off on "/". But that's probably where the strangeness of the sizes are coming from.

> **runeh76 said:**
> Try ext3.
For what? I think "/" is ext4 and "/home" is ext2.  I really don't know the difference between the 3 of them, I was just following the directions on that link I posted.  I'm very open to suggestions to better ways, though I would like at some point in time to know why I'm doing things that way. :D

---

### Post by runeh76 on 2010-12-01
> **PhoenixGI said:**
> Ok, lots of things here, which is cool, just don't want to miss anything.



I can get the Grub menu, but no matter which system option I chose I go to the blank screen, Removing splash quiet ad adding the nomodeset didn't seem to do anything at all, after I remove and add those lines, do I have to "save" it before I (I think its) press x so GRUB can continue to boot?

The thumb drive does start to flash like it's being accessed, but after letting it sit for up to 10 mins nothing is happening.  I've tried both xforcevesa and nomodeset.  Another note about the thumb drive.  I've had it connected both directly to the USB port on the PC and to a USB hub, with the same result.

The Video card I have is a nvidia GTS 250 from MSI.

I'm still looking at your BIOS settings notes, most are either all set or not applicable, or not available to be set. I am trying to look more into the APCI stuff.  Also the for the top 4 errors, the only drives I have enabled as I'm doing this is the CD drive (for the liveCD when needed) and the thumb-drive. So the lack of any other hard-drives might be what's throwing the errors.  Course I'm just guessing here, 
 


I've taken the thumb-drive and attached it to my laptop, and it boots perfectly (I'm using it right now to type this up, Got my wireless card set up even).  Not knowing how well Ubuntu would react to going from PC to Laptop, every time I try one the the thumb-drives on the laptop, I reinstall to it before using it on the PC again. Which, as a side question; How well does Linux / Ubuntu handle going from computer to computer with a single install.  Could I take this thumb-drive between my laptop and PC and not have issues, even though they are completely different hardware (right down the the CPU and Video card different, AMD/ATI in the laptop, Intel/nVidia in the PC)

As far as the partition sizes, apparently I don't know how to do the math any more, it was suppose to be 5GB for "/", 512MB for "/dos", 1GB for "/home" and whatever was leftover for swap.  Looks like I was a MB off on "/dos" and 100MB off on "/". But that's probably where the strangeness of the sizes are coming from.


For what? I think "/" is ext4 and "/home" is ext2.  I really don't know the difference between the 3 of them, I was just following the directions on that link I posted.  I'm very open to suggestions to better ways, though I would like at some point in time to know why I'm doing things that way. :D

Just suggestion, becouse when i tryed to install 10.10 to hd ext4 it didnt want to install. But when i changed to ext3, it did work. I dont see any reason why u should use ext4?

---

### Post by C.S.Cameron on 2010-12-01
> Which, as a side question; How well does Linux / Ubuntu handle going from computer to computer with a single install. 

Should not be a problem as long as you do not install any proprietary drivers, ie Nvidia.

Ext2, 3 or 4 all work for /home, I understand ext2 writes to disk less often, (for people woried about bricking their flash drive.

Not sure why it's not booting on your desktop, have you tried letting it sit there awhile, sometimes the first boot can be very slow.

---

### Post by PhoenixGI on 2010-12-01
> **C.S.Cameron said:**
> Should not be a problem as long as you do not install any proprietary drivers, ie Nvidia.

Cool, well that makes things a little easier, then I don't have to keep reinstalling every time I try the thumb-drive on my laptop. Definite time saver.

> **C.S.Cameron said:**
> Ext2, 3 or 4 all work for /home, I understand ext2 writes to disk less often, (for people worried about bricking their flash drive).

Eh, I don't have anything else to try at the moment.  Only takes about 20 minutes to do an install to the USB, I might as well give Ext3 a try.  maybe it's just some strange incompatibility with my system. On one hand I hope it is so I can get it going on the laptop.  On the other hand, I'm hoping not, cause then I'll have to figure out what the heck the incompatibility was with my desktop and Ext4.

> **C.S.Cameron said:**
> Not sure why it's not booting on your desktop, have you tried letting it sit there awhile, sometimes the first boot can be very slow.

Yes, I've let it sit for 5, 10, 20 minutes. I almost forgot about it the last time.  It's got to be something stupid, something that I'm looking at and saying "totally unrelated, that's not it", that is mucking things up here.  It works great on my laptop, I love it.  Just wish the desktop would cooperate.

---

### Post by oldfred on 2010-12-01
I agree with C.S.Cameron but to get it to work on your Nvidia card you may need the Nvidia driver.

Does recovery mode boot at all or do you have same no video issue? 

Not sure if this is most up to date but has some info.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I followed this set of instructions for special settings (I also link to C.S.Cameron install instructions):
It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Herman also experimented without swap when you have lots of memory and concluded some swap was still a good idea. I think he uses a swap file though.

You want journal to speed up system recovery if you have to do repairs or run fsck. But is partition is small then it does not take long to fsck anyway and without journal writing is reduced.

---

### Post by PhoenixGI on 2010-12-01
> **oldfred said:**
> I agree with C.S.Cameron but to get it to work on your Nvidia card you may need the Nvidia driver.

Does recovery mode boot at all or do you have same no video issue? 


recovery mode does not boot at all, exact same issue. Really I don't think it goes to far after GRUB.  after I select a menu item, or edit a menu item in grub then load it, the USB stick starts to flash, but it stops right there.  I was able to get a grub prompt once, but didn't' know what to do from there.

> **oldfred said:**
> 
Not sure if this is most up to date but has some info.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I followed this set of instructions for special settings (I also link to C.S.Cameron install instructions):
It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
Use ext2 or ext4 without journal
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

Herman also experimented without swap when you have lots of memory and concluded some swap was still a good idea. I think he uses a swap file though.

You want journal to speed up system recovery if you have to do repairs or run fsck. But is partition is small then it does not take long to fsck anyway and without journal writing is reduced.

I've made these changes to the thumb-drive I'm using on this laptop right now, but I can't really get that far to make those changes on the PC.  I suppose I could use this drive on the PC. As far as changing the video driver, it seems like all of those things are done after you can log-in either to a command prompt or desktop.  Sadly I'm not making it that far.

While working with someone else on this in the IRC channel I jokingly said, "I don't do easy problems". Ugh, this one is starting to get to me.

---

### Post by PhoenixGI on 2010-12-01
Quick side note, went to reinstall to one of the thumb-drives to make it Ext3 instead of 4.  Booted to liveCD no problem, Chose language, choose advanced (let me decide partitions) clicked on new partition table, clicked continue on the warning, and then noticed. 1TB free.  1 TB?? oh-oh, for most of this process I had disabled the HD on that PC so I didn't accidentally do anything to it.. well like what I just did.  Though I was more worried about installing GRUB to it, not sacking the whole thing.  I lucked out quitting out before going any further kept it from Killing the primary hard drive on that computer.  Needless to say I'm doing a full backup right now, maybe even imaging the drive.

---

### Post by runeh76 on 2010-12-01
Format that usb-stick with example gparted or disktool. And try again.

---

### Post by PhoenixGI on 2010-12-02
> **oldfred said:**
> I followed this set of instructions for special settings (I also link to C.S.Cameron install instructions):

Ubuntu Karmic Koala Encrypted Flash Memory Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)


Is that the link to C.S. Cameron's instructions? Seems like most of the special settings are done after the first boot, which I can't get though. ](*,)

Well it's a new day, time to try some new installs.

---

### Post by PhoenixGI on 2010-12-02
I've now tried formatting the thumb-drive as ext3 for my partitions, to no avail.  I double checked the BIOS, and sure enough there was a updated one that only added some CPU comparability.  But I figured why not. So I Updated BIOS.  Nope, still same problem.  Just for Kicks I tried using the "universal USB drive creator that Ubuntu.org promotes for making a LiveUSB drive.  The rational behind this was to see if it would boot.  Obviously if the LiveUSB wouldn't work, well then my PC just couldn't boot using a USB drive cause Live is about as fail safe as it gets.  Well It worked just fine, I'm using it to be logged into the forums and posting this message.  

So really I'm pretty much back where I started.  I have a Thumbdrive that I can install directly to that will work everywhere except when I do a full install of Ubuntu on it.  The Thumbdrive works, My PC can boot from it, just something that different between live and Installed is blocking me from progressing here.  I am able to get the GRUB menu if there's any tests there I could run. Let me know.

---

### Post by C.S.Cameron on 2010-12-03
A persistent install via usb-creator or Universal is not too awful, terrible bad.
About the only thing it won't do that a full install will is upgrade the kernel and install some proprietary drivers, (Nvidia).
I guess software updates are not advisable either and security is a little weak.
One advantage is that you can use them to install Ubuntu.
If 4GB of persistence is not enough you can make partitions named casper-rw and home-rw of whatever size will fit on the drive and delete the casper-rw persistence file.
Good luck.

---

### Post by PhoenixGI on 2010-12-03
> **C.S.Cameron said:**
> A persistent install via usb-creator or Universal is not too awful, terrible bad.
About the only thing it won't do that a full install will is upgrade the kernel and install some proprietary drivers, (Nvidia).
I guess software updates are not advisable either and security is a little weak.
One advantage is that you can use them to install Ubuntu.
If 4GB of persistence is not enough you can make partitions named casper-rw and home-rw of whatever size will fit on the drive and delete the casper-rw persistence file.
Good luck.

Running with a LiveUSB wasn't really the end state I was looking for.  I just wanted to make sure that I could boot and run from USB.  Granted since I was getting the GRUB menu, I guess I knew that, but just seeing the desktop on my PC cemented that what I was trying to achieve was indeed possible.

Where do we go from here.  I can boot and run the liveDisk on this PC, so we know that my PC is capable of Boot and Run from USB.  I have a Quad Core 2.4 GHz CPU and 4GB of RAM, so I have a PC capable of running Linux (yes I know In a privious post I think I said i had a 2.4 MHz CPU... just a small typo :) ).  When I boot, I can bring up the GRUB boot menu, and I can bring up the GRUB command Prompt.  But there's where it seems to stop.  As when I look at the logs from another install, nothing has been written to.  So there's something in GRUB that's hanging up.  Is there a way to manually run the boot process.  A step by step install.  I saw what looked like a few options in the previous version of GRUB, but I haven't seen anything as detailed for GRUB 2 yet. Course I'm just getting started looking.

---

### Post by PhoenixGI on 2010-12-03
It was just suggested to me in the IRC Channel that run grub-mkdevicemap

Unfortunately I was left with that as the person had to leave.  Do I do this after booting to the liveCD? or can I run that at the GRUB prompt?  I can't do it after booting into ubuntu, as I don't make it that far.  There is a certain logic that I can understand as to why I need to do this.  I'm just a little unsure on the how.

---

### Post by PhoenixGI on 2010-12-03
Major breakthrough.  I started to research the GRUB2 Command Prompt options, and came along a very helpful help page on GRUB2 [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) in there is the steps to manually start boot. 

```
set

linux /boot/vmlinuz-<your version> root=/dev/sdXY ro

initrd /boot/initrd-<your version>

boot
```

Using these commands from the GRUB prompt I'm able to start Ubuntu on my PC. Now I need to figure out what is wrong with the original GRUB2 config that is failing.  Yeah, it will be nicer when I don't have to manually "pull it up by it's bootstraps" but at least I can get Ubuntu to run on my PC with the USB ThumbDrive Install.

This thread isn't resolved until I get to that point though.

---

### Post by oldfred on 2010-12-03
Sometimes reinstalling from the working system or the dpkg reinstall works.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then after rebooting:
sudo update-grub

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by PhoenixGI on 2010-12-06
> **oldfred said:**
> Sometimes reinstalling from the working system or the dpkg reinstall works.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then after rebooting:
sudo update-grub

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Quick question, for most of this I've disabled the Hard drive, before I do this should I continue to have the HDD disabled (unplugged) or will that cause other errors.  I see that Linux "names" each device /dev/sdXXX my thumb-drive is SDA, I don't know if the a is cause it's the USB drive, or because its the first (and only) Drive.

---

### Post by oldfred on 2010-12-06
If it is the only drive it should be sda.

Not sure if it now makes a difference. It used to, as it saved the drive to install to as sda, sdb etc. Now I noticed on my system it saved as the hard drive name. But that was from my sdc drive which is unique. My sda & sdb are exactly the same drive names, so I do not know what it does then.

---

### Post by PhoenixGI on 2010-12-30
> **oldfred said:**
> Sometimes reinstalling from the working system or the dpkg reinstall works.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
If that returns any errors run:
sudo grub-install --recheck /dev/sdb
Then after rebooting:
sudo update-grub

to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Sorry for the delay, got caught up into a lot of things, including the holidays.  But now I'm back at it.  The first command resulted in 
```
Disk /dev/sda: 7998 MB, 7998537728 bytes
247 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 15314 * 512 = 7840768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008950c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          64      487424    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)
Partition 1 has different physical/logical endings:
     phys=(60, 206, 18) logical=(63, 195, 24)
Partition 1 does not end on cylinder boundary.
/dev/sda2   *          64         830     5859328   83  Linux
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(60, 206, 19) logical=(63, 195, 25)
Partition 2 has different physical/logical endings:
     phys=(790, 66, 44) logical=(829, 3, 60)
Partition 2 does not end on cylinder boundary.
/dev/sda3             830         957      976896   83  Linux
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(790, 66, 45) logical=(829, 3, 61)
Partition 3 has different physical/logical endings:
     phys=(911, 224, 17) logical=(956, 147, 46)
Partition 3 does not end on cylinder boundary.
/dev/sda4             957        1020      485376   82  Linux swap / Solaris
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(911, 224, 18) logical=(956, 147, 47)
Partition 4 has different physical/logical endings:
     phys=(972, 78, 2) logical=(1019, 244, 2)
Partition 4 does not end on cylinder boundary.
```

I do know that the boot partition is sda2.  I'm about to do the reinstall of grub, I'll let you know how that works.  I am getting pretty good at loading it manually from command line though.:lolflag:

---

### Post by PhoenixGI on 2010-12-30
The system still will not automaticly boot.  I don't get it, I can get it to run fine manually.  I think the next thing is to try a custom menu item for grub.  Please forgive me for saying this, but this is getting rather annoying.  Obviously it's not the fault of anybody that's has taken the time to help me, and the blame partially lies on my PC.  Still to see that it can work, and just some little process is mis-firing somewhere is rather frustrating.  I think I've learned more then any rookie should have to about grub2 right now.
](*,)

Anyhow putting down my wine :-({|= and getting back to working on it.

---

### Post by oldfred on 2011-01-01
I do not understand why you can manually boot but grub does not install to automatically boot.

A slightly easier manual boot that uses the link in root to the newest kernel in /boot.


Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

I am not sure these errors are normal and may be part of the problem. Drives do not use CHS - cylinders, head, sectors with LBA drives. Maybe a setting in BIOS to make sure you have LBA turned on?
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 32, 33) logical=(0, 33, 3)

This error is normal and can be ignored, and also relates to the difference with CHS, many of my partitions have this warning:
Partition 1 does not end on cylinder boundary.

---

