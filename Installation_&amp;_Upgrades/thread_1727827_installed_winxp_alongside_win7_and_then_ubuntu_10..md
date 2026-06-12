---
title: "installed winxp alongside win7 and then ubuntu 10.10, can't load win 7"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by chrisneedshelp on 2011-04-13
When I load into winXP I can see the files for winXP and win7.  When I load into ubuntu I can only see winXP.  i did a sudo update-grub and got the windows loader, which then shows me winXP and ubuntu.  what i would love is one boot page that has listed winXP, win7, and ubuntu.  FWIW this is an acer netbook, winXP is on D:/ and win7 is on F:/, i used the windows installer wubi for ubuntu 10.10.

---

### Post by Hedgehog1 on 2011-04-13
** Wubi Install ** my instructions were wrong...

---

### Post by bcbc on 2011-04-13
Windows combines it's boot files when you install a new windows on a computer with an existing windows. So there is only one 'boot partition' and therefore Ubuntu can only see one.

If you installed with Wubi, you cannot use Grub to boot - you have to go through the windows boot manager. If you try and bypass the windows boot manager, then only the Wubi will boot, and fixing this  is difficult.

If you want to use grub instead of the windows boot manager, replace Wubi with a normal dual boot. You'll still only be able to boot xp and win7 via the windows boot manager.

---

### Post by chrisneedshelp on 2011-04-13
? was to the wubi installation instruction note.

to the later one...i think i understand, but have some questions but need to reboot to clarify what the current status is.  brb

---

### Post by chrisneedshelp on 2011-04-13
okay, so when i boot i am in the windows boot loader and have a choice of windows xp or ubuntu.  if i choose windows xp it loads windows xp.  if i choose ubuntu it loads grub and i can choose ubuntu or windows 7 loader.  If i then choose ubuntu it loads ubuntu 10.10 and if I choose windows 7 loader it loads be back to the original page.

i think i may have got myself into a mess.

Generally I would have just loaded win7 into a partition less than the disc size, then winXP, leaving disc size, then ubuntu.  on this occasion i hadn't that option as there is no win7 disc available so I was trying to do this without needing to load win7.

---

### Post by bcbc on 2011-04-13
Ok... if you install an earlier version of windows on a computer with a newer version already installed, then it doesn't combine the boot files. So XP likely doesn't know about windows 7, but it would have set it's partition as the boot partition.

I'm not really clear on what's going on, but I'd suggest running the [bootinfoscript]("http://bootinfoscript.sourceforge.net/").

---

### Post by chrisneedshelp on 2011-04-13
i am trying to use that but despite being absolutely sure i am typing the correct directory it repeatedly says not such file or directory....ugh

---

### Post by chrisneedshelp on 2011-04-13
go it...

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1              16,065    25,157,789    25,141,725   f W95 Ext d (LBA)
/dev/sda5              16,128    25,157,789    25,141,662   7 HPFS/NTFS
/dev/sda2    *     25,167,872    25,372,671       204,800   7 HPFS/NTFS
/dev/sda3          25,382,700   312,579,759   287,197,060   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0       f1fc1f84-8b01-4d65-ad70-5e2b7de101b1   ext4                                     
/dev/sda1: PTTYPE="dos" 
/dev/sda2        7EF6DD81F6DD39DB                       ntfs       SYSTEM RESERVED               
/dev/sda3        1646DFA446DF8343                       ntfs       Acer                          
/dev/sda5        20C4F49FC4F4787C                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/loop0       /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda3        /host                    fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda2/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect

C:\wubildr.mbr = "Ubuntu"


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

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
    search --no-floppy --fs-uuid --set 1646dfa446df8343
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.35-22-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.35-22-generic
}
menuentry "Ubuntu, Linux 2.6.35-22-generic (recovery mode)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 1646dfa446df8343
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
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set 7ef6dd81f6dd39db
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

============================= sda3/Wubi/etc/fstab: =============================

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

================= sda3/Wubi: Location of files loaded by Grub: =================


   4.5GB: boot/grub/grub.cfg
    .9GB: boot/initrd.img-2.6.35-22-generic
  13.6GB: boot/vmlinuz-2.6.35-22-generic
    .9GB: initrd.img
  13.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1

00000000  49 c4 e9 6f 01 9b e3 2f  34 87 f1 e5 ef c7 61 a5  |I..o.../4.....a.|
00000010  8a 12 05 48 ad ae ee 53  b1 bc 78 4a 35 21 09 14  |...H...S..xJ5!..|
00000020  cb ab 01 00 55 a3 db dd  5a 51 80 34 47 e7 c4 f5  |....U...ZQ.4G...|
00000030  bf bf 3f 5a 5a 28 57 fe  7f 50 39 87 bb 69 5f 37  |..?ZZ(W..P9..i_7|
00000040  64 19 19 f2 11 4f 2a 30  bb 4e e3 95 6d 2b 36 ec  |d....O*0.N..m+6.|
00000050  eb 16 86 2a 56 e2 c1 a0  bb 38 68 5e 02 25 62 77  |...*V....8h^.%bw|
00000060  8f 2b 0c 80 2b 09 c6 d6  de be 06 20 95 04 9c b4  |.+..+...... ....|
00000070  80 9e e5 bf 8c 85 d3 5b  15 25 15 da 29 a0 c6 2f  |.......[.%..)../|
00000080  d4 70 68 5c a2 6c e2 44  96 8b f6 f6 e9 6a b5 4f  |.ph\.l.D.....j.O|
00000090  9b 00 e9 f2 7d 7d af 60  7c f9 8a e2 9b b3 df b1  |....}}.`|.......|
000000a0  47 f6 93 b7 ab bf 4f 79  c7 de c3 a1 c0 2d 14 a6  |G.....Oy.....-..|
000000b0  09 59 b4 68 1e 36 0a 6c  13 df c3 28 13 cb 8f 72  |.Y.h.6.l...(...r|
000000c0  68 da 9e 04 5e 83 cf be  46 63 71 2b c3 e1 57 de  |h...^...Fcq+..W.|
000000d0  b3 70 92 bc 0e 89 a0 93  0f d0 e9 fe cb b2 b3 e3  |.p..............|
000000e0  69 8b 3b 43 19 69 33 58  00 75 f6 c7 d7 24 b6 c3  |i.;C.i3X.u...$..|
000000f0  9b 02 3e 5f a8 13 c1 d1  1f 12 b1 5f 51 59 26 29  |..>_......._QY&)|
00000100  44 71 cd 6e 44 72 5e fc  71 e5 fa d1 42 31 c8 ed  |Dq.nDr^.q...B1..|
00000110  d5 a1 7f 37 b9 3c 91 a5  73 50 5d 6d 3b 9b 91 e8  |...7.<..sP]m;...|
00000120  14 fb f8 e5 24 98 8d 3a  fa 7c f4 71 ba d4 1d 7f  |....$..:.|.q....|
00000130  4e c3 f9 51 7a 6e 14 62  7d 47 6f 9f 37 28 4a 12  |N..Qzn.b}Go.7(J.|
00000140  b1 ba 8f ca 09 60 c9 89  ba 9a e5 ff 05 a2 ea e1  |.....`..........|
00000150  32 ef 8f a3 51 59 e5 e9  70 bf 91 5a ae 87 74 cc  |2...QY..p..Z..t.|
00000160  45 cd 39 ca a8 74 6a a6  16 c9 71 4f fe a5 52 9d  |E.9..tj...qO..R.|
00000170  1d 93 7c fe 60 ee ab 3f  0a f1 7b f6 bb e6 83 e5  |..|.`..?..{.....|
00000180  e5 26 d8 95 fe fa e4 b5  4f 1e 89 6a 4d 97 06 d9  |.&......O..jM...|
00000190  c5 5f 12 c5 1e 51 20 12  29 6c 0f f6 fc d5 f2 29  |._...Q .)l.....)|
000001a0  4d 62 32 27 62 7d 7b 6f  af a1 30 34 84 63 79 77  |Mb2'b}{o..04.cyw|
000001b0  d1 89 00 34 e0 9a 16 f5  ff 02 70 e7 f7 59 00 01  |...4......p..Y..|
000001c0  01 01 07 fe ff ff 3f 00  00 00 9e a1 7f 01 00 00  |......?.........|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by bcbc on 2011-04-13
It looks to me that XP has hijacked your win7 boot partition. The win7 boot files are there, but they are being ignored. So Ubuntu thinks it's win7, but it just boots XP (the boot sector is XP). So you probably need to boot from a windows 7 repair disc that you can download, and then repair your win 7 and it should pick up win 7 as well as XP. Then you'll end up with Win7 or XP, XP or Ubuntu, Ubuntu or Win7.  :)

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

Check out microsoft or windows forums for other people who have done this. (You are not alone)

---

### Post by chrisneedshelp on 2011-04-13
seems clear enough said the blind man in front of a cliff...i'll be happy to try it and post feedback.  thank you for your help.

---

### Post by bcbc on 2011-04-13
Sorry that last bit was me rambling about what your menus would look like after the repair:
1. Win 7 or Win XP (pick XP)
2. XP or Ubuntu (since you installed Wubi in XP, pick Ubuntu)
3. Ubuntu or Win 7


Basically you need to let Win 7 take ownership of /dev/sda2 again. And the only way is to repair the boot sector and then rebuild the BCD to include Windows XP as a boot option.

---

### Post by chrisneedshelp on 2011-04-13
well i tried that and after a while it said it could not repair.  after rebooting i found my options in a windows boot manager for ubuntu and windows 7.  windows 7 will not load, fails soon after the splash screens loads.  ubuntu will not load either as it says i need to run a windows repair because the mbr file is missing (/wubildr.mbr)

---

### Post by bcbc on 2011-04-13
> **chrisneedshelp said:**
> well i tried that and after a while it said it could not repair.  after rebooting i found my options in a windows boot manager for ubuntu and windows 7.  windows 7 will not load, fails soon after the splash screens loads.  ubuntu will not load either as it says i need to run a windows repair because the mbr file is missing (/wubildr.mbr)

That doesn't sound good. I have read reports that windows repair needs to be run multiple times. Some people have said 3 times. I would persist getting win7 to repair itself. I'd be very surprised if it couldn't recover. Regarding Ubuntu, you can probably sort that out after you fix windows.

I am puzzled that you now have Windows 7 and Ubuntu as your boot options. That doesn't make much sense.

---

### Post by chrisneedshelp on 2011-04-13
it didn't make sense to me either and i was also surprised that it didn't work, but i will try a few more times.

---

### Post by bcbc on 2011-04-13
Just bear in mind that none of your data is affected. OS boot issues look more serious than they are. However, reinstalling will often wipe out that good data - so while it might 'fix' the issue, it's a sledgehammer approach.

Same goes for Wubi. Reinstalling will remove your existing install.

If you do give up on the repair, boot an ubuntu live CD, plug in an external drive and image your hard drive or manually copy all your data first. For wubi it's the files in \ubuntu\disks that are important (in your case it's just the root.disk)

---

### Post by chrisneedshelp on 2011-04-13
i'm not quite prepared to give up yet, but would be nice to boot.  I have had boot issues before and always been able to repair them but that was back before win7 and with grub, not grub 2.  things have changed quite a bit since then.  

as of now i have tried the windows repair three times.  in each case it boots from the disk, conducts its work, then reboots onto the hard drive and opens a repair utility.  after a lengthy time it says 'startup repair cannot repair this computer automatically'  then either send info to ms or not.  there is no restore point available either

---

### Post by bcbc on 2011-04-13
I think the manual commands are:
bootrec /fixmbr  (probably not required since you have not messed with this)
bootrec /fixboot (repair boot sector)
bootrec /RebuildBCD

I really am not qualified with win7 repairs. here is a site: [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

Or, [http://support.microsoft.com/kb/927391](http://support.microsoft.com/kb/927391)

---

### Post by samacaster on 2011-04-13
I would like to add that when you get the repair disc from neosmart use the command prompt option.

At the command prompt window switch to the drive where win7 is located.

bcbc gave the correct commands to type. They are:

1. bootrec.exe /fixmbr  - fixes the master boot record on the 1st sector of the 1st partition

2. bootrec.exe /fixboot - if the boot is corrupt this will address it

3. bootrec.exe /rebuildbcd - This will change the entire boot configuration data!!

It will scan for active boot files for windows installs only! If grub is on the 1st partition it will be moved (don't worry, it's still there)

Upon completion you'll see a message that says all repairs successful, or something to that effect.

Reboot and if all went well you'll boot into windows 7. Then you can get EasyBCD from Neosmart and add winxp and Ubuntu to the BCD.

---

### Post by Mark Phelps on 2011-04-13
Selecting Startup Repair from the Windows menu and running it three times accomplishes the same results as entering the three commands -- it just takes longer as you have to reboot twice.

IF you still have problems afterward, and can get into Win7, consider installing EasyBCD from Neosmart Technologies.  That will give you a GUI app that will allow you to add entries to the BCD. That should then allow you to modify your OS selection menu to include all three.

---

### Post by chrisneedshelp on 2011-04-14
sorry, work caught up with me and i've been off a day or so.

tried all those commands to no avail, but didn't think to transfer to the drive win7 is on, haven't played with dos for a while, and cd: f/ is not working, but will research, thanks for the suggestion.

trying repair three times did not have the desired result, i've tried it 6 times with still no change

---

### Post by chrisneedshelp on 2011-04-14
well, when i am booted on the repair disk i am in drive x: and it will not let me change over to e: where my win7 partition is, ugh

---

