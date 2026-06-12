---
title: "Ooops Did something wrong with Ubuntu 11.04 clean install? Windowns 7 not booting."
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by azitizz on 2011-06-14
I recently did a fresh install of ubuntu 11.04 and seemed to have made a mistake with re-partitioning perhaps? 

I cant boot into windows anymore. I know all files are still there and intacct as I can access them from Ubuntu, but Something is wrong with the Booting of Windows now. 

I get to a screen which gives me system recovery options. When I perform the startup repair it scans for a few secnds and comes up with an error message 

"...System volume on disk is corrupt. Repair action: File system repair (chkdsk)...error code 0x1f" 

I even seems to have access to files on windows from this screen when I try a "Windows Complete system restore" It gives me the option to look on the hard drive or on a disk (I only have a Toshiba windows 7 upgrade disk and it doesnt seem to be helping) 

Any suggestions if the right files are contained on my hard drive, or if I can load them off a USB stick?

Could this repair be possible from Ubuntu?

---

### Post by travlemon on 2011-06-15
> **azitizz said:**
> I recently did a fresh install of ubuntu 11.04 and seemed to have made a mistake with re-partitioning perhaps? 

I cant boot into windows anymore. I know all files are still there and intacct as I can access them from Ubuntu, but Something is wrong with the Booting of Windows now. 

I get to a screen which gives me system recovery options. When I perform the startup repair it scans for a few secnds and comes up with an error message 

"...System volume on disk is corrupt. Repair action: File system repair (chkdsk)...error code 0x1f" 

I even seems to have access to files on windows from this screen when I try a "Windows Complete system restore" It gives me the option to look on the hard drive or on a disk (I only have a Toshiba windows 7 upgrade disk and it doesnt seem to be helping) 

Any suggestions if the right files are contained on my hard drive, or if I can load them off a USB stick?

Could this repair be possible from Ubuntu?

Hello, yes something may have gone wrong when you installed Ubuntu, but it sounds like the fix should be straightforward.

Try booting from your Windows 7 disc and entering the recovery console.  In the recovery console, run the command [B]fixmbr

[/B]Alternatively, you can run **chkdsk /r** and that might do the job as well.

That should repair your hard drive's master boot record, and make it point to your Windows installation once again.

---

### Post by coffeecat on 2011-06-15
> **travlemon said:**
> Try booting from your Windows 7 disc and entering the recovery console.  In the recovery console, run the command **fixmbr**

It sounds as though the OP only has an OEM recovery disc, not a Microsoft disc, in which case it would not have the repair console, unfortunately.

@azitizz, I would advise **not** running fixmbr. (It wouldn't work in Windows 7 anyway, since that XP command has been deprecated in Windows 7 in favour of 'bootrec /FixMbr'.) If you reinstall the Windows mbr from a Windows repair console, you will overwrite the grub code in the mbr so you would end up being able neither to boot into Ubuntu because you wouldn't get the grub menu, and not being able to boot into Windows because it is currently broken.

A chkdsk from a repair console might be successful where one from within the system (as is happening now) is failing. Or it could be that there is a problem within the Windows boot sector within the C: partition, which is quite a separate matter from the mbr, but I think this is less likely. I was going to post you a link to a site from which you could download a Windows 7 repair CD ISO, but unfortunately it is now showing the message, "*Downloads have suspended pending copyright clarification."* I'll post the link anyway in case the clarification takes place sooner rather than later:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Do you have access to a functioning Windows 7 installation? At work, or a friend/relative? If so, it is a trivial matter to create a repair CD from within Windows. See here:

[http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)

Boot up with that and there are several utilities there that might help, but please do not repair the mbr for the reasons given above. It will only make your situation worse.

Last thing. This may not help, but it might give us some useful information. Boot into Ubuntu and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there. Post the contentsof the RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for legibility. It may show us something useful about the Windows partition boot sector.

---

### Post by azitizz on 2011-06-15
Thanks Coffeecat. Heres the results of my Boot info script: ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos3)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda4: __________________________________________________________________________

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

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   236,757,547   233,683,500   7 NTFS / exFAT / HPFS
/dev/sda3    *    236,759,040   480,583,679   243,824,640  83 Linux
/dev/sda4         480,583,680   488,396,799     7,813,120  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        8C348E52348E3F68                       ntfs       TOSHIBA SYSTEM VOLUME
/dev/sda2        1E96BDD596BDADA1                       ntfs       S3A6748D007
/dev/sda3        c649f9e3-8fa4-437f-b28d-d142d96e92e5   ext4       
/dev/sda4        6c931919-daad-427f-90c0-7a0665702734   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,user_xattr,commit=0)


=========================== sda3/boot/grub/grub.cfg: ===========================

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
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root c649f9e3-8fa4-437f-b28d-d142d96e92e5
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos3)'
search --no-floppy --fs-uuid --set=root c649f9e3-8fa4-437f-b28d-d142d96e92e5
set locale_dir=($root)/boot/grub/locale
set lang=en_CA
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
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c649f9e3-8fa4-437f-b28d-d142d96e92e5
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c649f9e3-8fa4-437f-b28d-d142d96e92e5 ro   quiet splash acpi_osi= vt.handoff=7
	initrd	/boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	set gfxpayload=$linux_gfx_mode
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c649f9e3-8fa4-437f-b28d-d142d96e92e5
	echo	'Loading Linux 2.6.38-8-generic ...'
	linux	/boot/vmlinuz-2.6.38-8-generic root=UUID=c649f9e3-8fa4-437f-b28d-d142d96e92e5 ro single 
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
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c649f9e3-8fa4-437f-b28d-d142d96e92e5
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(/dev/sda,msdos3)'
	search --no-floppy --fs-uuid --set=root c649f9e3-8fa4-437f-b28d-d142d96e92e5
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda2)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(/dev/sda,msdos2)'
	search --no-floppy --fs-uuid --set=root 1E96BDD596BDADA1
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

=============================== sda3/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3       /               ext4    errors=remount-ro,user_xattr 0       1
# swap was on /dev/sda4 during installation
UUID=6c931919-daad-427f-90c0-7a0665702734 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda3: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 147.030044556 = 157.872308224  boot/grub/core.img                             1
 163.245754242 = 175.283793920  boot/grub/grub.cfg                             1
 115.526630402 = 124.045774848  boot/initrd.img-2.6.38-8-generic               2
 147.028324127 = 157.870460928  boot/vmlinuz-2.6.38-8-generic                  1
 115.526630402 = 124.045774848  initrd.img                                     2
 147.028324127 = 157.870460928  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb 

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by drs305 on 2011-06-15
Windows requires the boot flag (*) on it's partition, but Ubuntu does not. Currently the boot flag is on Ubuntu (sda3) but it should be on sda2.

Move the boot flag (Gparted, Disk Utility, etc) to ... I think sda2 but if sda1 is a Windows boot partition it may need to go there. A Windows user will tell you. Your files look ok on quick inspection so  moving the boot flag to sda2 (or sda1) might be all you need to get Windows to boot.

---

### Post by Quackers on 2011-06-15
Boot flag to sda2 would be the first thing I would try, as drs305 says :-)

---

### Post by azitizz on 2011-06-15
Thats pretty good news. Any quick tutorials on how to move the boot flag? I can do this within Ubuntu or would it be done from a windows console? 
Thanks alot for all your time.
Long live Ubuntu!

---

### Post by drs305 on 2011-06-15
If you are familiar with Gparted, you can start it, highlight the partition, then Partition, Manage Flags, and then set the boot flag.

In Disk Utility, highlight the partition, then in the bottom pane select "Edit Partition" and tick "make bootable".

If you don't know how to start them, just type the name in "Dash" (click upper left icon).

---

### Post by azitizz on 2011-06-15
> **drs305 said:**
> If you are familiar with Gparted, you can start it, highlight the partition, then Partition, Manage Flags, and then set the boot flag.

In Disk Utility, highlight the partition, then in the bottom pane select "Edit Partition" and tick "make bootable".

If you don't know how to start them, just type the name in "Dash" (click upper left icon).

Thanks, Ive never used Gparted before but I just installed it and will give it a try tomorrow. Will post the results.
Thanks again. gnight

---

### Post by coffeecat on 2011-06-16
> **drs305 said:**
> Windows requires the boot flag (*) on it's partition, but Ubuntu does not. Currently the boot flag is on Ubuntu (sda3) but it should be on sda2.

@drs305, a question. Is this necessarily so when using grub to boot Windows? The boot flag is certainly needed for Windows to boot when using the Windows mbr, but I thought the boot flag was merely there for the Windows mbr code to find the bootable partition. I'd been led to understand that when grub chainloads to the Windows partition boot sector, it passes the boot process directly to the Windows boot files thus bypassing the need for a boot flag, or is this wrong? On one of my machines I have Windows 7 with its usual 100MB boot partition with the boot flag set, but unusually all the Windows boot files are in the C: partition as well. Grub has set up menu entries for both partitions and  Windows boots from either. It's an interesting observation.

---

### Post by drs305 on 2011-06-16
coffeecat,

Thanks for bringing this up. I think I misunderstood the problem (even with the RESULTS.txt. I was thinking the OP couldn't boot Windows and that the Ubuntu installation didn't succeed. Rereading it I now see that Ubuntu is most likely working and that Windows won't boot from the Grub menu.

You are correct as far as I know. It's what is in the MBR that really matters. If it's Grub, it doesn't care where the boot flag is because it is going to point to a particular partition. If Windows is controlling the boot, it looks for a boot flag (and not per se a partition). I don't know enough details about the inner workings of Windows to know if the boot flag would be needed after the boot files start working, but I wouldn't think so.  So I've probably confused the OP since he is trying to get Windows to boot from Grub.

In any case it would not be a bad idea to get the boot flag back where it can do some good, but this probably won't fix a Grub boot of Windows.

---

### Post by coffeecat on 2011-06-16
@drs305, thanks for clarifying that. My guess is that the OP's best hope is to create a Windows 7 repair disc using a friend/relative/co-worker's Windows 7, seeing as the neosmart link has removed the downloads.

---

### Post by azitizz on 2011-06-19
Hi there, so I made a win 7 repair usb drive using an image I found online. However It seems the same problem occurs when i make a startup repair. It comes back with a msg: 
*"system volume on disk is corrupt" repair action: File system repair (chkdsk)...error code 0x1f".*

 I seem to have access to files on windows from the repair screen (on usb image or on the hard drive) when I click on "Windows Complete system restore" It gives me the option to look on the hard drive or on a disk (I only have a Toshiba windows 7 upgrade disk and now the iso image usb repair disc)

Is the beeot flag moving option still going to be relevant to my case?
Thanks for any tips one may have

---

### Post by azitizz on 2011-06-23
I think I understand now that the boot flag shuffle wont solve my problem.

Im able to access all windows files from Ubuntu, so why couldnt I simply fetch the relevant files from Ubuntu, then save tehm on a usb stick or a cd?

Thanks

---

### Post by coffeecat on 2011-06-24
> **azitizz said:**
> 
Im able to access all windows files from Ubuntu, so why couldnt I simply fetch the relevant files from Ubuntu, then save tehm on a usb stick or a cd?

If chkdsk is repeatedly giving you the same error then I have no further ideas as to how you can repair Windows - sorry. If you can mount the Windows partition in Ubuntu and copy your personal files onto another medium, then that would be a good idea. It's interesting that there must be filesystem corruption yet you can access your files. I guess the corruption must only involve Windows system files.

---

### Post by Quackers on 2011-06-24
If it is a Windows system file problem sfc/scannow could be worth a look. I've never used it but heard about it a while ago. 
Good luck with it :-)
[http://www.sevenforums.com/tutorials/1538-sfc-scannow-command-system-file-checker.html](http://www.sevenforums.com/tutorials/1538-sfc-scannow-command-system-file-checker.html)

Actually this one is more appropriate for you
[http://www.sevenforums.com/tutorials/139810-sfc-scannow-run-command-prompt-boot.html](http://www.sevenforums.com/tutorials/139810-sfc-scannow-run-command-prompt-boot.html)

---

### Post by YesWeCan on 2011-06-25
Just a thought. Although Grub ignores the boot flag can the same be said for the Windows System Repair?

---

### Post by Quackers on 2011-06-25
I think the Windows repair functions need the boot flag in the correct place.

---

### Post by YesWeCan on 2011-06-25
> **azitizz said:**
> I think I understand now that the boot flag shuffle wont solve my problem.
It might make your Windows repair work. In Ubuntu, you can set the boot flag for Windows using
[COLOR="DarkGreen"]sudo sfdisk /dev/sda -A2[/COLOR]
or use Disk Utility.

---

### Post by azitizz on 2011-06-25
> **YesWeCan said:**
> It might make your Windows repair work. In Ubuntu, you can set the boot flag for Windows using
[COLOR="DarkGreen"]sudo sfdisk /dev/sda -A2[/COLOR]
or use Disk Utility.

Great Ill be trying that soon. Thanks. For the above commands, will they move the boot flag or is this simply to access the place where I can move it.

I also now have this program, Gparted. will that do the job as well? (Im still an habitual graphical interface user... slowly getting familiar with the terminal...)

---

### Post by Mycurl on 2011-06-26
I have a problem when laoding Ubuntu.....i did'nt have clear monitor to see ubuntu screen.....trying to adjust screen resolution...but still cant get as per normal window screen ....why its happen....my screen very blur when im loading ubuntu....help me:(

---

### Post by Quackers on 2011-06-26
Is this from a live cd? Can you get to the "try Ubuntu" desktop?

---

