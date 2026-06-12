---
title: "Tried to Upgrade from 10.04 to 10.10...seems to have failed"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by Alterah on 2011-01-11
Hello,

I just tried to upgrade from 10.04 LTS to 10.10 and it appears to have failed. I had difficulties doing the upgrade from the Update Manager. I kept getting a "Could not calculate the update" error message. That prompted me to try the steps here:

[http://www.linuxquestions.org/questions/blog/kenny_strawn-513767/ubuntu-howto-upgrade-from-any-release-to-any-release-anytime-anywhere-3231/](http://www.linuxquestions.org/questions/blog/kenny_strawn-513767/ubuntu-howto-upgrade-from-any-release-to-any-release-anytime-anywhere-3231/)

That also did not work. It seems the new repositories are no longer valid. 

So, I tried removing xserver-xorg-video-nouveau and xserver-xorg-video-all and then doing the upgrade. This seemed to work and the upgrade seemed to go well. Restarted my computer and got the attached error. I typed in "exit" and it continued to boot up. I went to Update Manager and it prompted me for a partial upgrade. I clicked cancel on that. Also, my About Ubuntu says I am using 10.04LTS. 

In addition my Grub 2 screen was in a lower resolution than I normally have it at. I think I remember changing the resolution a long time ago to a higher resolution but forget what I did for that. 

Thanks for any and all help with this. Let me know if you need further information.

Edit: I forgot to include that I am running a dual boot system. I have Ubuntu installed on one hard drive and Windows XP on another.

Edit 2: I Above I mentioned that Update Manager is prompting me for a partial upgrade. I clicked cancel but still updated...now my About Ubuntu says I am running 11.04 (perhaps it said this all along and my quick glance didn't catch it the first time). I am going to bed for tonight. Some of the updates require me to restart my computer, though I am not going to do that at the moment. Thanks again for any help.

---

### Post by Dutch70 on 2011-01-12
For what it's worth, I had the same problem last night & ended up breaking some things trying to get it going. I ended up doing a fresh install of 10.10 because of that. Otherwise I would have waited for 11.04 before doing a fresh install. 

It is up & working great though.

Best Regards

---

### Post by Alterah on 2011-01-12
I would prefer not to have to do that. I never created a separate home partition and I have quite a bit on it. Is there some way I could revert back to 10.04? Thanks!

---

### Post by Quackers on 2011-01-12
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Alterah on 2011-01-12
Just to note, I can get past the screen in the picture. Do I still need to use a live cd. If so, does it matter which version of Ubuntu is on it? Thanks.

---

### Post by Quackers on 2011-01-12
Will it boot all the way? If so try going to synaptic package manager and in the lower left pane click on "status" and then on the "reload" button in the toolbar. When it reloads, you should see the word "upgradeable" in the left hand pane. Click on that and all available updates will appear in the main window. 
Right-click on each one and select "mark for installation" and watch to see if any errors are reported, or to make sure that nothing needed is going to be removed (without being replaced later). If there are problems with any just leave them and carry on. When everything is marked that can be, click on the "apply" tick in the toolbar, then on "install" and see how things go.
When finished, reboot, if required, then try the missing ones again.

EDIT and also please run the boot script from the desktop.

---

### Post by Alterah on 2011-01-13
Here are the results of the script. I am in the process of performing the upgrades. We'll see what happens. 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for (,msdos1)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Windows XP
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   275,799,887   275,799,825   7 HPFS/NTFS
/dev/sda2         275,799,888 1,953,521,135 1,677,721,248   f W95 Ext d (LBA)
/dev/sda5         275,799,951 1,953,521,135 1,677,721,185   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               2,048   175,362,047   175,360,000  83 Linux
/dev/sdb2         175,364,094   195,362,815    19,998,722   5 Extended
/dev/sdb5         175,364,096   195,362,815    19,998,720  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        60D019C2D0199F7A                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda5        7600FF8A00FF501B                       ntfs       Main                          
/dev/sda: PTTYPE="dos" 
/dev/sdb1        44be1473-f9ba-4edd-9123-7e3daa97e20f   ext4                                     
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        dee53677-a0d8-4925-acc8-c3f2467d8522   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext4       (rw,errors=remount-ro)
/dev/sda5        /media/Main              fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
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
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  insmod gfxterm
  insmod 
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod part_msdos
insmod ext2
set root='(hd1,msdos1)'
search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
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
menuentry 'Ubuntu, with Linux 2.6.32-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=44be1473-f9ba-4edd-9123-7e3daa97e20f ro  vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
    echo    'Loading Linux 2.6.32-27-generic ...'
    linux    /boot/vmlinuz-2.6.32-27-generic root=UUID=44be1473-f9ba-4edd-9123-7e3daa97e20f ro single  vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=44be1473-f9ba-4edd-9123-7e3daa97e20f ro  vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
    echo    'Loading Linux 2.6.32-26-generic ...'
    linux    /boot/vmlinuz-2.6.32-26-generic root=UUID=44be1473-f9ba-4edd-9123-7e3daa97e20f ro single  vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set 44be1473-f9ba-4edd-9123-7e3daa97e20f
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows XP Media Center Edition (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 60d019c2d0199f7a
    drivemap -s (hd0) ${root}
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb1 during installation
UUID=44be1473-f9ba-4edd-9123-7e3daa97e20f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=dee53677-a0d8-4925-acc8-c3f2467d8522 none            swap    sw              0       0

=================== sdb1: Location of files loaded by Grub: ===================


  25.9GB: boot/grub/core.img
  82.7GB: boot/grub/grub.cfg
  27.5GB: boot/initrd.img-2.6.32-26-generic
  27.9GB: boot/initrd.img-2.6.32-27-generic
  27.1GB: boot/vmlinuz-2.6.32-26-generic
  26.3GB: boot/vmlinuz-2.6.32-27-generic
  27.9GB: initrd.img
  27.5GB: initrd.img.old
  26.3GB: vmlinuz
  27.1GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  53 86 2b c4 a0 1c e1 31  64 3c dc f2 4c 5c 87 5d  |S.+....1d<..L\.]|
00000010  ed a4 53 bb 55 a9 b7 f8  92 6e e0 ab fd f7 f0 5e  |..S.U....n.....^|
00000020  4c ba bc ca 40 bc 16 f5  26 7a f4 35 cd 71 d7 4b  |L...@...&z.5.q.K|
00000030  31 2e ed 51 6f 76 93 6c  c2 e5 5d 38 94 f7 b6 34  |1..Qov.l..]8...4|
00000040  4f 9e d5 75 e8 5c f4 d6  1f 25 8a bb 53 98 95 be  |O..u.\...%..S...|
00000050  93 ef 33 2f 78 f7 8e bb  f8 c2 a4 89 bb b5 39 bc  |..3/x.........9.|
00000060  ab a5 b8 e1 f6 aa 6d 7f  03 75 4a b5 6a 7b fa 75  |......m..uJ.j{.u|
00000070  5f c7 91 6a 1f 1d 32 ef  11 01 de 02 e1 82 d0 74  |_..j..2........t|
00000080  1a 52 46 38 8b 71 52 3e  bc ca 48 71 87 57 49 aa  |.RF8.qR>..Hq.WI.|
00000090  ab c8 bc 33 8e ab fc 95  2a f6 e4 43 e5 de ea 0c  |...3....*..C....|
000000a0  70 37 1c 3d 72 e3 a4 aa  3a e8 65 02 1c d6 ab bf  |p7.=r...:.e.....|
000000b0  88 76 e6 5b 5d d8 1f 6a  4d 08 d7 74 86 d2 d1 ce  |.v.[]..jM..t....|
000000c0  3a ef e4 57 6d af da 07  b4 8a f2 5b 4f 5d 26 77  |:..Wm......[O]&w|
000000d0  4e 17 2d 54 d0 ab bc ab  44 fa b6 d2 6d 65 bd 3a  |N.-T....D...me.:|
000000e0  49 3c 75 da 9d 6a ba 5b  ef 35 f6 a3 d5 b5 d2 cc  |I<u..j.[.5......|
000000f0  10 ac e6 85 40 72 89 d2  b5 ef a4 19 15 57 f0 ea  |....@r.......W..|
00000100  ed 1d 55 d3 5d 64 e4 3b  5d de dc db bd db b7 ce  |..U.]d.;].......|
00000110  a4 c6 3c 8d 1b 6d c7 01  ca 71 52 ff 91 dc 9d 74  |..<..m...qR....t|
00000120  70 32 b5 2e 0f 8f 90 b1  d7 62 30 13 dc bf 4b ba  |p2.......b0...K.|
00000130  10 99 a4 9a 5d d0 81 60  6d 36 5c 49 bb 5a 1d 03  |....]..`m6\I.Z..|
00000140  48 fe 1d 14 13 23 64 de  4e 04 da 1f 6f 20 24 74  |H....#d.N...o $t|
00000150  7d fc 19 2c ab 1a aa a6  4d db c2 8f b3 54 f5 c1  |}..,....M....T..|
00000160  84 06 58 bb fc d1 d2 d0  eb a7 81 fb 6b 91 1f 7f  |..X.........k...|
00000170  05 e3 e5 c7 df c1 f9 7c  75 c1 ed 7f ae fe 57 0e  |.......|u.....W.|
00000180  95 7f 0d b6 61 37 4b ae  d0 35 ac f9 71 f2 bd ef  |....a7K..5..q...|
00000190  a4 45 07 57 bc f5 7a fb  ef e3 1d 5d d2 d2 cf 5e  |.E.W..z....]...^|
000001a0  f7 6a 4f 2c a7 26 00 00  01 00 02 d2 1f 11 80 00  |.jO,.&..........|
000001b0  00 01 01 0a 3f 32 02 60  13 a0 b0 d0 df ba 00 fe  |....?2.`........|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 28 31 01 00 00  |...........(1...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

```

---

### Post by Quackers on 2011-01-13
It seems that you have 10.10 installed.
Strangely though, you have Windows XP on drive sda, but grub is installed in the mbr of that drive.
Conversely you have 10.10 installed on sdb, but have Windows in that mbr.

Which hard drive is set to boot first in the bios?
Obviously Ubuntu boots, is that via the grub menu? Does Windows appear in that menu, and does that boot too?

---

### Post by Alterah on 2011-01-13
I thought that was strange. That certainly was not my intent when I first installed Ubuntu. Ubuntu is on a 200GB hard drive. Windows in on a partition of a 1TB hard drive. The hard drive Ubuntu is on is the one I have set to boot up first (I am fairly confident if I choose the one Windows is on, it would load directly into Windows). And yes, Windows does show up in the Grub menu. It is at the bottom. I have installed the updates, but haven't restarted yet. Will do that shortly.

Edit:

I rebooted. Grub screen is still low resolution. Anyone know what I need to do to fix this? Also, it used to wait 10 seconds before automatically booting into the top item on the Grub list. Now I have to actually select the item from the list. I went to update manage, I first got a partial upgrade message. I clicked check and now I get this:

```
CD/DVD 'Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)' is required
Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.
```I clicked cancel and it indicates it failed to download repository information. 
```

W:Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/i18n/Translation-en.bz2  
, W:Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/i18n/Translation-en.bz2  
, W:Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/Release  
, E:Some index files failed to download, they have been ignored, or old ones used instead.

```Any thoughts?

---

### Post by Alterah on 2011-01-18
So, I just did an update through Synaptic because my Update Manager wasn't working. The update went well, but after restarting Ubuntu doesn't get past the Ubuntu loading splash screen. The screen appears frozen (the "progress" dots do not change). So, I am fairly certain I will just need to do a clean install of Ubuntu. Before I do that I have booted into Ubuntu with a live CD and am backing up my data. That said, I have a few other things I'd like to save if possible:

Is there anyway to save my Firefox/Chrome settings from the live CD, or can I use the live CD to repair my Ubuntu installation (I don't really care if it works perfectly, as long as it will let me boot into Ubuntu). 

And, is there any way to obtain a list of software I have installed? 

Thank you for any assistance.

---

### Post by Quackers on 2011-01-18
Try this for a list of packages currently installed and a way to re-install them later.

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

Not sure about the FF/Chrome settings.

---

### Post by Alterah on 2011-01-18
I will give that a go. I know there is a utility called MozBackup, but I'd have to be logged on to my normal Ubuntu installation to use that.

Edit: Just tried that, but with the live CD I get this:

bash: installed-software: Permission denied

---

### Post by Laysan_A on 2011-01-18
Hi,

Don't know a thing about chrome, but firefox is easy. Just go to your home folder, select to view hidden files, open the .mozilla folder, then the firefox folder. Find the folder with a name like dxtpldeo.default, and move it somewhere safe. It contains your entire ff profile. On your fresh installation, rename the folder you've kept from your previous installation to match the new one, then delete the new one, replacing it with the old.

As far as backing-up ff, theres a great extension called FEBE you should try (after you're up and running). I allows you to back-up everything individually. This is good for back-up purposes, but it's great for troubleshooting if something goes wrong with your firefox installation some day.

---

### Post by Quackers on 2011-01-18
> **Alterah said:**
> I will give that a go. I know there is a utility called MozBackup, but I'd have to be logged on to my normal Ubuntu installation to use that.

Edit: Just tried that, but with the live CD I get this:

bash: installed-software: Permission denied

Are you trying the command in a terminal?
Thanks for that Laysan_A

---

### Post by Alterah on 2011-01-18
Yes, I went to my home directory on my Ubuntu installation and tried the command. Thanks for the FF info.

---

### Post by Quackers on 2011-01-18
I just ran the command in the terminal and in 2 seconds it created a file in my home folder called "installed-software". I don't know what happened in your case.

---

### Post by Alterah on 2011-01-19
Well, is the problem that I am using a live CD right now? When I look at the partition my Ubuntu installation is on, it doesn't let me alter permissions.

---

### Post by Quackers on 2011-01-19
That could be it :-) You would need to chroot into your installation first.

---

