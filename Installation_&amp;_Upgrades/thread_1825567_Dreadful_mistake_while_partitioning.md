---
title: "Dreadful mistake while partitioning"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by savafan on 2011-08-15
Hi all. I hope someone can help me here. I have a Win7 laptop 64bit OS & I'm trying to dual boot it with Ubuntu 10.04.3....I've done this many times without error on Vista machines, but with Win7, there must have been something I missed.  In the process of dividing the HDD & setting up 100GB to use for Ubuntu, I believe that I deleted an important part of what Windows needs to run. (There was a small section there called &quot;Vista loader&quot; that is no longer there due to my error)..  As it sits right now, the dual boot screen is fine, Ubuntu loads fine, but Windows will not load at all. I have tried all of the repair options including using a recovery disc and all &quot;bootrec&quot; commands that I would know to bring this back. All files on the Windows side seem intact & unharmed.  I've reached out to an online friend that is well versed in these matters, & he seems quite stumped on this one.  Any help at all would be appreciated & if more info is needed, I'll be glad to provide what I can.  Thank you

---

### Post by coffeecat on 2011-08-15
One important difference between Windows 7 and Vista is that W7 usually comes with a separate 100-200MB partition labelled "SYSTEM" which contains the boot files. It's possible you deleted this. But even if you did, running bootrec from a repair disc should be able to write the boot files to the main C: partition, depending on what options you used. The other thing we need to look at is, if the SYSTEM partition is gone, whether your C: partition has the boot flag set.

It's fairly easy to find all this out and more. Boot up into Ubuntu, live CD or your permanent installation, and go to this site:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Download and run the boot info script according to the instructions there and post the contents of your RESULTS.txt file between [noparse]```
 and 
```[/noparse] tags for clarity. We can take it from there.

---

### Post by savafan on 2011-08-15
Thanks coffeecat, That seems easy enough to start, but evidently not. I cannot get a RESULTS.txt no matter what i try. I've followed the directions to a tee..

---

### Post by savafan on 2011-08-15
My mistake. here are the results:
```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 6 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /boot/BCD /Windows/System32/winload.exe

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   385,928,563   385,518,964  42 SFS
/dev/sda4         385,929,214   625,141,759   239,212,546   5 Extended
/dev/sda5         385,929,216   393,936,895     8,007,680  82 Linux swap / Solaris
/dev/sda6         393,938,944   625,141,759   231,202,816  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63   312,576,704   312,576,642   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda2        3CAA70B6AA706E70                       ntfs       SYSTEM
/dev/sda3        BA46A43846A3F2F5                       ntfs       
/dev/sda5        0192b6eb-fabb-4ba5-aea0-a35b67238488   swap       
/dev/sda6        b023844c-0e73-4591-ad1d-9f1d4f16418c   ext4       
/dev/sdc1        E8D453F7D453C70A                       ntfs       SG 160

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sdc1        /media/SG 160            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b023844c-0e73-4591-ad1d-9f1d4f16418c
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b023844c-0e73-4591-ad1d-9f1d4f16418c
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-33-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b023844c-0e73-4591-ad1d-9f1d4f16418c
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=b023844c-0e73-4591-ad1d-9f1d4f16418c ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b023844c-0e73-4591-ad1d-9f1d4f16418c
    echo    'Loading Linux 2.6.32-33-generic ...'
    linux    /boot/vmlinuz-2.6.32-33-generic root=UUID=b023844c-0e73-4591-ad1d-9f1d4f16418c ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b023844c-0e73-4591-ad1d-9f1d4f16418c
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,6)'
    search --no-floppy --fs-uuid --set b023844c-0e73-4591-ad1d-9f1d4f16418c
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3CAA70B6AA706E70
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set BA46A43846A3F2F5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=b023844c-0e73-4591-ad1d-9f1d4f16418c /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0192b6eb-fabb-4ba5-aea0-a35b67238488 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 203.977771759 = 219.019464704  boot/grub/core.img                             1
 252.002994537 = 270.586155008  boot/grub/grub.cfg                             1
 203.985561371 = 219.027828736  boot/initrd.img-2.6.32-33-generic              1
 203.976371765 = 219.017961472  boot/vmlinuz-2.6.32-33-generic                 1
 203.985561371 = 219.027828736  initrd.img                                     1
 203.976371765 = 219.017961472  vmlinuz                                        1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 30 7a 00 00 fe  |...........0z...|
000001d0  ff ff 05 fe ff ff 02 30  7a 00 00 e8 c7 0d 00 00  |.......0z.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdb 


```

---

### Post by coffeecat on 2011-08-15
Two problems that I can see.

The minor one is that somehow you've managed to create a small partition (sda1) covering sectors 63 to 2047. It's doing nothing and is superflous and shouldn't be there. It used to be that partitions started from sector 63. Nowadays (I believe to accommodate the newer advanced format drives) the start sector should be 2048. However, your drive in only 320GB, so I doubt this is causing a problem - just something to be aware of.

But... This little partition, and your two Windows 7 partitions (sda2 is the small SYSTEM partition so you didn't remove it) are all SFS/dynamic partitions. This is a proprietary Microsoft format and is a right royal pain when you are using Linux. I guess you must have used Windows Disk Management and you tried to create more than 4 primary partitions, in which case it converts them all from basic partitions to SFS.

My guess is that this is why grub cannot boot Windows. I believe that the only fix is to convert the SFS partitions back to basic ones, but I've never done this.

I'll pm a couple of people who know more about SFS/dynamic partitions than I so that they can comment.

---

### Post by savafan on 2011-08-15
Thanks for the help so far coffeecat. I'll watch this thread for updates.

---

### Post by Quackers on 2011-08-15
Have a look at this thread - in particular post #6

[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

---

### Post by savafan on 2011-08-15
Good point Quackers. The only problem being is that i do not have a Win7 disc. I do have a recovery disc sent by a friend, but I'm not sure that will work in this case.

If you could possibly layout the instructions here in this thread, i would surely appreciate it.

---

### Post by Quackers on 2011-08-15
If you don't have an installation disc you could try to make a repair disc and see if that works. You can make one from the Control Panel > Backup & Restore centre > left pane "make a recovery cd".
Of course if Windows is not bootable you may have to download a repair disc of the same architecture as your system (ie 32 bit/64 bit) and try that.

A recovery disc won't have the tools necessary, and, in any case, one from another computer won't do.
Did you make a set of recovery discs from your own pc? You should have done that first thing!
If you have a recovery partition (probably) you can re-install using that, but this will recover your system to the state it was in when you bought it. 
All data will be lost.

---

### Post by oldfred on 2011-08-15
Quackers linked to my post with most or all of the alternatives that I know to convert back often without data loss, but no guarantees.

Some have had success with all of them and a few have had failures with just about all of the ways listed. Windows offical policy is to totally backup, erase drive, and reinstall with new basic partitions.

Choices:
MiniTool Partition Wizard Professional Edition 5.2 from windows, testdisk from Ubuntu download, EASEUS Partition Master, another windows based system, and Linux's low level sfdisk partitioning tool.

---

### Post by coffeecat on 2011-08-15
@Quackers and @oldfred, a thought. What do you think?

The Windows partitions look OK. The Windows boot files are where they should be and sda2, the system partition, has the boot flag set. If I understand things correctly, Windows cannot boot only because it is grub trying to get the boot process going and grub can't deal with SRS partitions. Am I right?

But with the Windows boot files OK and the boot flag set on the correct partition, if the OP repairs the Windows mbr with "bootrec /FixMbr", then they *should* be able to boot into Windows (but not Ubuntu). The OP mentions bootrec in the first post, so I guess the recovery disc from a friend is providing that. (@savafan, am I right?)

So - if the OP repairs the Windows mbr and is able to boot into Windows, then they could run Easus or MiniTool in Windows, which they can't do at the moment.

And if Windows won't boot at all, at least the OP could reinstall grub to the mbr with the live Ubuntu CD to get back into Ubuntu again. Any flaw with this?

---

### Post by Quackers on 2011-08-15
Sounds reasonable :-)

---

### Post by savafan on 2011-08-15
For the record, in the repair program for Windows, i did try to get it back with the command "bootrec.exe.fixmbr"...No luck with that or any of the other commands I got from a Microsoft page.

This did make it impossible to get the dual boot screen & I had to re-install Ubuntu in order to at least be able to get to the files on the windows side.

BTW, this is not my machine. It belongs to a friend that is very interested in Ubuntu. I'll keep working on this & talk to her & see what she may want to do from here.

Thanks so far guys.

---

### Post by Hakunka-Matata on 2011-08-15
> **savafan said:**
> For the record, in the repair program for Windows, i did try to get it back with the command "[COLOR=Red]bootrec.exe.fixmbr[/COLOR]"...No luck with that or any of the other commands I got from a Microsoft page.

This did make it impossible to get the dual boot screen & I had to re-install Ubuntu in order to at least be able to get to the files on the windows side.

BTW, this is not my machine. It belongs to a friend that is very interested in Ubuntu. I'll keep working on this & talk to her & see what she may want to do from here.

Thanks so far guys.
Something looks a bit fishy with that command.  Look at [this]("http://support.microsoft.com/kb/927392") link for exact method to restore boot sector to Win 7.  Good Luck

---

### Post by oldfred on 2011-08-15
These are the basic commands from the windows sites:

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r  (have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by mcstat on 2011-08-16
I had the exact same problem, using the recovery disk might work but in my situation I could not find the partition with the windows 7 so you might have to activate the partition. Try this link it will show you how to activate the partition: [http://www.sevenforums.com/tutorials/71432-partition-mark-active.html](http://www.sevenforums.com/tutorials/71432-partition-mark-active.html)
That didn't work for me because it kept on saying the partition cannot be activated because it is corrupt, but yet it GParted it was marked as healthy; so you might have to end up reinstalling the OS.

---

### Post by Doug11 on 2011-08-16
IMO, I never had faith in using the windows repair. It never has worked much for me. However, I had more luck using third party software such as Spotmau to get the job done.

---

### Post by YesWeCan on 2011-08-16
it looks to me like sda2 is the boot partition for Win7 but grub.cfg is trying to boot (hd0,3). If grub.cfg were edited to choose (hd0,2) it might help. It might also boot Win7 if the MBR boot code was made standard again, although Ubuntu would not boot.

---

### Post by coffeecat on 2011-08-16
> **mcstat said:**
> you might have to activate the partition.


The Windows 7 boot partition (sda2) is already "active". Activating a partition in Windows terminology simply means setting the boot flag. The boot script output tells us that sda2 has the boot flag set already.

> **YesWeCan said:**
> it looks to me like sda2 is the boot partition for Win7 but grub.cfg is trying to boot (hd0,3). If grub.cfg were edited to choose (hd0,2) it might help. 

There are grub.cfg entries for both sda2 and sda3 already. 

```
## BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 3CAA70B6AA706E70
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set BA46A43846A3F2F5
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

But the OP does need to be sure they are trying to boot from the sda2 stanza.

@savafan, when you had the grub menu visible, did you try booting Windows from the first, sda2, entry?

---

### Post by YesWeCan on 2011-08-16
Must eat more carrots.

---

### Post by savafan on 2011-08-16
> **coffeecat said:**
> 
@savafan, when you had the grub menu visible, did you try booting Windows from the first, sda2, entry?

@coffeecat, I'm not exactly sure what you mean there. This is way beyond my knowledge as I understand things so far. I still have Ubuntu loaded to access any windows files I may need at this time. Taking things back with the generic recovery disc will disable my access to Ubuntu. I can & will do that again once I'm sure of what to do.

From what I am reading here, I need a repair/recovery disc from this machine. Is there any possible way to access that file or program from the Ubuntu side?? OR, will another machine using the same OS work? I do not mean the exact same OS as this one, just another machine with Win7 Home Premium on it.

Thanks everybody so far for the help. I'm just not sure where to start with all of the suggestions posted here, but it is a fresh new day & I will be happy to give this another go.

---

### Post by oldfred on 2011-08-16
It is best to have the same version Vista or 7 and 32 bit or 64 bit. 

Some things can be run from different versions. I have just used a Win7 repair USB to run chkdsk on my XP. But it put a Win7 boot sector in the ntfs partition and I had to run bootsect.exe to reinstall a XP boot sector.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by coffeecat on 2011-08-16
> **savafan said:**
> @coffeecat, I'm not exactly sure what you mean there.

I think we've moved on a bit from when you ran the boot script, but what I meant was that the grub menu then would have shown two entries for Windows:

"Windows 7 (loader) (on /dev/sda2)"

and

"Windows 7 (loader) (on /dev/sda3)"

causing grub to try to boot from partition sda2 or sda3. But looking again at your boot script output I see that both sda2 and sda3 have /bootmgr and /Boot/BCD, which means that in theory you should have been able to boot from either partition. When you have the small SYSTEM partition, usually only that has /bootmgr and /Boot/BCD.

Anyway, that's all a bit theoretical now.

---

### Post by savafan on 2011-08-16
> **oldfred said:**
> It is best to have the same version Vista or 7 and 32 bit or 64 bit. 



Here is what i did. I have another machine with the same version of Win7. (Home Premium & yes, they are both 64bit machines)..Though it is a completely different machine, the OS is the same version, though of course, not from the same original disc.

I created a Recovery disc from that other machine in hopes that this will work. I'll have to go through the "bootrec" steps again in hopes that it will.

I'll report back within 24 hours. my work schedule just got busy all of a sudden.

---

### Post by savafan on 2011-08-17
> **coffeecat said:**
> I think we've moved on a bit from when you ran the boot script, but what I meant was that the grub menu then would have shown two entries for Windows:

"Windows 7 (loader) (on /dev/sda2)"

and

"Windows 7 (loader) (on /dev/sda3)"

causing grub to try to boot from partition sda2 or sda3. But looking again at your boot script output I see that both sda2 and sda3 have /bootmgr and /Boot/BCD, which means that in theory you should have been able to boot from either partition. When you have the small SYSTEM partition, usually only that has /bootmgr and /Boot/BCD.

Anyway, that's all a bit theoretical now.

On the original boot screen, I have Ubuntu operational, but the 2 Windows boot options show only as (loader)...Nothing else beyond that. No "/dev/sda" anything.

Moving on. The repair disc I pulled from the other machine did not work. I went through all of the commands listed..FixMbr, FixBoot, ScanOs, & RebuildBcd all with a prefix of bootrec,exe/..These commands seemed to have taken & the FixMbr option did say it was successful, though it wasn't.

Windows still will not load at all & at this point the dual boot screen is not there & I cannot get to either OS.

On the screen that came up on what OS I wanted to repair, Windows should have been listed. It was not. Nothing there at all & It was telling me that I should use an option to Load Drivers. I did look at this option, but I would have no clue on what driver(s) to load or even how to do this, _but this may be what we are over looking_..

I would like to be able to repair this & have a functional dual boot option, but on a good note, if I cannot repair this the owner of the machine would be happy with Ubuntu as the only OS.

I would like to hear more suggestions & I will possibly decide to take this to a shop to see if it can be fixed professionally if I run into a dead end here, but at least I can get Ubuntu loaded again & let the owner decide.

---

### Post by oldfred on 2011-08-17
I think I have seen before that windows will not repair its own proprietary SFS/dynamic partitions with a repair CD. Did you try converting partitions from dynamic to basic? Since you have only 3 SFS partitions and probably have not used the dynamic part to bridge dynamic partitions across physical partitions, you should be able to convert back with any of the choices posted above.

---

### Post by savafan on 2011-08-17
> **oldfred said:**
> I think I have seen before that windows will not repair its own proprietary SFS/dynamic partitions with a repair CD. Did you try converting partitions from dynamic to basic? Since you have only 3 SFS partitions and probably have not used the dynamic part to bridge dynamic partitions across physical partitions, you should be able to convert back with any of the choices posted above.

oldfred,
If you could guide me on how to do this, I would appreciate it. Keeping in mind of course that I cannot boot the machine at all right now.

What do I need to do this?

---

### Post by oldfred on 2011-08-17
Quackers in Post #7 linked to most of the info I know. I have never done it but have seen several users convert without data loss. A few gave up and reinstalled. I think the mini tool is the one used to most.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)

Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

Post 96 using sfdisk - must have only 4 partitions
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk-10.html)
One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Used testdisk but see caveats in Post#7:
[http://ubuntuforums.org/showthread.php?t=1669418](http://ubuntuforums.org/showthread.php?t=1669418)
Used EASEUS Partition Master
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
Also used testdisk
[http://ubuntuforums.org/showthread.php?t=1675420](http://ubuntuforums.org/showthread.php?t=1675420)
Not sure if in "free" version, but older version had it & was free see 4.2:
[http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html](http://www.partitionwizard.com/help/convert-dynamic-disk-to-basic-disk.html)

---

### Post by savafan on 2011-08-23
I'd like to thank you all for the help & time put into this thread. This has been an interesting learning experience in many ways.

The machine is fixed, but I cannot exactly say how I did it to be honest. With 2 different repair discs, the Mini tool Partition Wizard, & the Mini Tool Power Data Recovery discs, something along the way seemed to have worked. I wish I could be more clear on what actually did solve this problem, but I cannot.

Thanks again everyone!

---

