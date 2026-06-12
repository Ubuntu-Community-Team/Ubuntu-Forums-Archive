---
title: "help need for multiboot for win xp, vista, and linux"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by quovadis on 2010-06-01
Guys, I am new to Linux.  I want to have a multiboot with two installations of XP in different partitions, a Vista, and Ubuntu or Ubuntu Studio as the fourth OS.  How do I go about it? Triple boot with XP, Vista, and Ubuntu seems not too complicated from what I have read, but this extra install of XP seems a bit of a doubt to me.  I have 320GB HD and another 500GB HD.  I plan to use the 320GB for all the four OS installs and the 500 GB for storage and backup.  All the experts and masters, please help me out.

---

### Post by darkod on 2010-06-01
Sit down and decide how to split the 320GB for the 4 OSs. Because windows needs to be on primary partition, you should create 3 primary partitions for each windows, and extended partition to hold your ubuntu (root + swap, or root + swap + /home if you wish).

The main thing when installing more than one windows, and if you plan to load them directly from grub2, is this: before install you have to move the boot flag around.

Windows puts its boot files where the boot flag is, and for multiple versions that will mean combining the boot files. After that grub2 can't split them, and you will have to boot any windows as two stage process, first to select Windows General in grub2, and then the specific windows version.

But if you do this:
- use ubuntu live mode and Gparted to create the 3 primary ntfs partitions. Put the boot flag on the first.
- install windows (which ever version) on part #1
- run ubuntu live mode again and with Gparted move the boot flag to part #2. install another windows there
- do the same for part #3
- install ubuntu into the remaining unallocated space by guided method or manual partitioning

Because you were moving the boot flag, all windows installs should be independent in windows eyes. Grub2 will locate the boot files from all 3, because they now have them on their own partition each, and your grub boot menu should look like:

Ubuntu
XP 1
XP 2
Vista

IMHO, that's your best option.

---

### Post by quovadis on 2010-06-02
Darko

Thanks for the suggestion.  You guys are amazing. I could see your reply within 5 mins of posting my message.  Wish some of the others also would add to that if there is anything to be added to.  Have to wait till I get some free time so I can install this setup.  Thanks again, Darko.

Quovadis

---

### Post by oldfred on 2010-06-02
+1 on Darko's suggestions.

If you really want to know more about how windows combines its boot loaders. (Lots of info but even pictures help explain it).

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by quovadis on 2010-06-04
Guys, thanks again for all the help.  I just have one thing bothering me a bit.  Suppose things go wrong and things dont boot or boot wrong, how do I fix it?

Regarding the options that Darko gave, in the first option, where I dont move the flags, install one after that other, in this case, how do I fix it if I have to repair the boot process? Should I use the recovery CD from XP and vista to repair every install in the order I installed them in the first place?

Second option of Darko, where I move the flags around, in this case, how do I fix it? I dont have any idea about this, so please help.

I am just being wary of things so I know what to do when something goes wrong or if I need to reinstall just one of those OS's.

Thirdly, when i install things moving the flag around, after I install all the OS's, should I again move the flag to the first partition? or leave it at the linux partition?

All help greatly appreciated.  Thanks again Fred and Darko.

Guess I am not too off-topic here.

---

### Post by darkod on 2010-06-04
I'll start from number 3. If you use grub2 on the MBR to boot all OSs, don't worry about where the boot flag remains. Grub2 doesn't use it.

It is only important when booting windows with windows bootloader because all windows bootloader on the MBR does, is continue loading the partition where the boot flag is. In that case, which windows version boots will depend on where the flag is. Grub2 works differently and within the entry you select in the menu, there is information which partition to boot. So the flag is irrelevant.

Which brings question number 2 up. If you install them moving the flag around, then before repair you should put the flag on the partition with the windows version you want to repair. Then use the repair process.

If you install without moving the flag and the boot files get combined, I have no idea if it makes a difference in which order you repair the windows versions. I never had two versions of windows on the same machine. I wouldn't know about that.

Most probably things will never boot wrong, regardless which method you use to install. But of course, with technology, things go wrong sometimes. We can't talk about fixing things before they even go wrong, we don't know what the symptoms would be.

In general, I think moving the flag around is best for multiple windows installs. And that everything will work out OK for you.

---

### Post by quovadis on 2010-06-05
Guys, I need your help here.  As suggested I installed two separate XP setups and a Vista using gparted to move the flags around.  Till I finished installing Vista, everything was going like clockwork.  But when I installed Ubuntu Studio, grub detected all my Windows OS's and when it was time for reboot, it would not boot into anything, not any of the Windows OS's nor Ubuntu Studio.  The error I got was something that said "Intel Boot Agent Failure" and asked me to check the cable, whatever that means.  I tried to rescue the installs in rescue mode with the Ubuntu Studio disk, but couldn't do anything with it.  When I tried to reinstall Grub in the first partition where I suppose MBR is, it said fatal error and said could not install.

Now, I had to use gparted to move the boot flag again to the first partition so I can boot int XP, from which I am posting this.

Any idea about what has gone wrong?  As I said earlier I am rookie in linux/ubuntu, so I dont know what to do.  I will try to google it out while I wait for you guys to pull me out of this.:(:confused::(:confused:

---

### Post by darkod on 2010-06-05
Run the boot info script and post the content of the results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

That should show us more.

---

### Post by oldfred on 2010-06-05
Intel Boot Agent Failure sounds like you have an Intel motherboard and a BIOS that is checking things before grub or windows. 

I do not understand why windows would work and Ubuntu/grub would not. You should review BIOS settings and what the BIOS may be checking for. If it says cable is something not plugged in that BIOS expects?

---

### Post by quovadis on 2010-06-05
Darko, I did like you told me.  Before you look in to the script results, I would like to clarify certain things which may or may not be of help here.  I had two HDs already installed -- a 160GB in SATA port 0 (sda) and another 320GB in SATA port 3 (sdb).  So I wiped out the 160GB HD and installed all the OS's in the 320GB in the order and manner you said I should do.  I thought since the sda HD was nonpartitioned, nothing would be installed there, and since the all the OS's are installed in sdb I expected grub to be installed in the MBR of sdb.  Moreover, I had changed the boot device order preference in BIOS so that sdb was before sda, but it now seems like grub got installed in sda whereas all my OS's are in sdb.  The "SHAREPART" fat32 partition you see in sda was not there when I installed everything.  I just created it so I could easily share the script between XP and linux as I am unable to connect to the net through Ubuntu.

Here come the script result. Thanks for everything Darko.
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 597454829 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /ntdetect.com

sdb3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63     5,381,774     5,381,712   b W95 FAT32


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   204,796,619   204,796,557   7 HPFS/NTFS
/dev/sdb2         204,796,620   358,394,084   153,597,465   7 HPFS/NTFS
/dev/sdb3         358,394,085   511,991,549   153,597,465   7 HPFS/NTFS
/dev/sdb4         511,991,611   625,137,344   113,145,734   5 Extended
/dev/sdb5         511,991,613   604,654,469    92,662,857  83 Linux
/dev/sdb6         604,654,533   616,944,194    12,289,662  83 Linux
/dev/sdb7         616,944,258   625,137,344     8,193,087  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        203D-E8F4                              vfat       SHAREPART                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        BA101DA3101D6821                       ntfs                                     
/dev/sdb2        720033B9003382E1                       ntfs                                     
/dev/sdb3        F6B0B837B0B80063                       ntfs       Local Drive                   
/dev/sdb4: PTTYPE="dos" 
/dev/sdb5        6ddbcb88-2e37-4533-8184-e64f49806107   ext3                                     
/dev/sdb6        95528d2b-9130-4ffc-bda0-9bd817757fd4   ext3                                     
/dev/sdb7        505eff82-26f7-44c6-9388-c0f55f121f9c   swap                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/SHAREPART         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="MS WinXP Ins 1 GenPurpose" /fastdetect /noexecute=optin

================================ sdb2/boot.ini: ================================

[boot loader]
timeout=20
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="MSWinXPTest" /fastdetect /noexecute=optin

=========================== sdb5/boot/grub/grub.cfg: ===========================

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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6ddbcb88-2e37-4533-8184-e64f49806107
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
set root='(hd1,5)'
search --no-floppy --fs-uuid --set 6ddbcb88-2e37-4533-8184-e64f49806107
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6ddbcb88-2e37-4533-8184-e64f49806107
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6ddbcb88-2e37-4533-8184-e64f49806107 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6ddbcb88-2e37-4533-8184-e64f49806107
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=6ddbcb88-2e37-4533-8184-e64f49806107 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6ddbcb88-2e37-4533-8184-e64f49806107
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd1,5)'
    search --no-floppy --fs-uuid --set 6ddbcb88-2e37-4533-8184-e64f49806107
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "MS WinXP Ins 1 GenPurpose (on /dev/sdb1)" {
    insmod ntfs
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set ba101da3101d6821
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "MSWinXPTest (on /dev/sdb2)" {
    insmod ntfs
    set root='(hd1,2)'
    search --no-floppy --fs-uuid --set 720033b9003382e1
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sdb3)" {
    insmod ntfs
    set root='(hd1,3)'
    search --no-floppy --fs-uuid --set f6b0b837b0b80063
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb5 during installation
UUID=6ddbcb88-2e37-4533-8184-e64f49806107 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sdb6 during installation
UUID=95528d2b-9130-4ffc-bda0-9bd817757fd4 /home           ext3    defaults        0       2
# swap was on /dev/sdb7 during installation
UUID=505eff82-26f7-44c6-9388-c0f55f121f9c none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


 305.9GB: boot/grub/core.img
 305.9GB: boot/grub/grub.cfg
 305.9GB: boot/initrd.img-2.6.32-21-generic
 305.9GB: boot/vmlinuz-2.6.32-21-generic
 305.9GB: initrd.img
 305.9GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb4

00000000  5b 2e 1a 4f ad 72 33 38  eb 5a 9c c4 6e ff 72 a5  |[..O.r38.Z..n.r.|
00000010  e5 3f f4 38 c9 21 1f 6f  5f e5 42 c1 ea e5 68 50  |.?.8.!.o_.B...hP|
00000020  20 c7 d2 95 de 9f b1 3e  f6 07 c7 55 ee 64 e5 89  | ......>...U.d..|
00000030  a3 ec 62 b4 85 d7 ac ec  32 9f 48 c9 de 70 8b fb  |..b.....2.H..p..|
00000040  be 92 16 68 b9 3c 9a cc  7a 36 c9 e9 02 2d f4 30  |...h.<..z6...-.0|
00000050  e0 c5 3c 5c 11 02 30 b2  a2 21 23 d7 e9 c7 86 2f  |..<\..0..!#..../|
00000060  44 f5 71 31 8a e4 9d a6  1f 71 e8 5d 3a 20 10 a2  |D.q1.....q.]: ..|
00000070  c0 7d 27 7a 1e 09 8f 4f  a4 62 66 df 71 e4 47 35  |.}'z...O.bf.q.G5|
00000080  e9 07 22 ef f3 2c f7 32  cb 23 14 9d 4d e6 a4 4c  |.."..,.2.#..M..L|
00000090  65 38 47 ff cb 63 78 fa  49 6e cb dc 1d 83 1a 29  |e8G..cx.In.....)|
000000a0  32 9c d5 e1 aa 7a ca 4a  a2 d4 bd 09 53 46 5f b6  |2....z.J....SF_.|
000000b0  4b 64 b2 b0 99 7a 42 63  92 f6 ea 3d 7d c8 b4 a4  |Kd...zBc...=}...|
000000c0  09 df f2 93 5b ac ce 11  55 18 7f f6 bc 8d bd 2d  |....[...U......-|
000000d0  5f b8 38 27 57 fb b9 f5  a4 8f b6 c5 8f e7 35 8b  |_.8'W.........5.|
000000e0  f9 22 6e 53 eb 76 e1 97  69 ed 64 a9 85 ad 37 42  |."nS.v..i.d...7B|
000000f0  75 b7 a1 a6 fe cd cd 3a  85 75 b4 02 87 a4 9b e9  |u......:.u......|
00000100  fa 79 85 af 23 ef 62 7b  c5 9c 93 85 ac 4d 6a 57  |.y..#.b{.....MjW|
00000110  91 aa bd 06 1f a2 9b 61  5f 2c ad ea cb 92 ed ba  |.......a_,......|
00000120  dd 4e 68 8f f5 b7 58 ef  17 35 72 ad 26 8c 15 bf  |.Nh...X..5r.&...|
00000130  e1 22 7f d3 a6 eb b8 17  d1 82 bb 4c a7 fd a6 8e  |.".........L....|
00000140  54 b1 76 db 24 08 be 9b  fb 21 2a 7d 23 b2 a9 6a  |T.v.$....!*}#..j|
00000150  db dc ca ea be cb 32 b3  23 a9 6c 5f 28 46 9a fc  |......2.#.l_(F..|
00000160  ca ee 41 c0 a7 32 9b 4f  b3 b3 8e a5 30 81 5d cd  |..A..2.O....0.].|
00000170  2a b0 f7 e5 8d 7d 6c cd  cb 1e 9f 76 db 10 61 3b  |*....}l....v..a;|
00000180  eb 36 4d c0 e0 cd cd 66  70 db 00 00 01 b6 97 bf  |.6M....fp.......|
00000190  2c 1c 9c 50 7b e9 75 72  a5 e9 f4 e9 fa 7d 3f d3  |,..P{.ur.....}?.|
000001a0  d5 37 ff e9 7e 9d 2a 97  54 d5 3a 57 49 d3 ff f4  |.7..~.*.T.:WI...|
000001b0  ad 3f d3 f4 af 4e b8 e9  55 4d 4c 19 e4 f9 00 fe  |.?...N..UML.....|
000001c0  ff ff 83 fe ff ff 02 00  00 00 49 ec 85 05 00 fe  |..........I.....|
000001d0  ff ff 05 fe ff ff 4b ec  85 05 bd 86 bb 00 00 00  |......K.........|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200



```

---

### Post by darkod on 2010-06-05
I am not sure what Intel Boot Agent is complaining about.

Otherwise, it looks OK in the script results apart from grub2 being on the other disk as you noticed.

You can try reinstalling it on /dev/sdb. Leave in BIOS /dev/sdb as first option to boot from. Then boot with the cd in live mode and do:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Otherwise all is as planned. The boot files are independent on their own partitions. See if this makes grub2 boot, because the grub2 on /dev/sda not only that it's on different disk, but it also can't find the necessary files to continue booting. So it's useless.

---

### Post by quovadis on 2010-06-05
Fred, mine is an Intel proccy on an Intel mboard.  What I found out while googling is that this Intel Boot Agent is for the Intel network adapter, which I have onboard and many people have had success with disabling the net adapter and/or the booting from LAN option in BIOS.  I disable both.  When I restarted, while I expected grub to take over, it booted into XP, as I had moved the boot flag into the XP partition, which from what Darko said does not matter to grub anyway.  Now it boots into XP, so it is not a hardware problem I guess.  From the script results I have posted above, grub got installed in sda whereas it should have been in sdb where my installs are.

Waiting for Darko or you or some saint to hear my prayers.:):).

It has definitely been a learning experience for a rookie like me.

---

### Post by darkod on 2010-06-05
> **quovadis said:**
> F  When I restarted, while I expected grub to take over, it booted into XP, as I had moved the boot flag into the XP partition, which from what Darko said does not matter to grub anyway. 

It booted XP directly because /dev/sdb is the first option to boot from (at it should be), but as you saw from the script results grub2 got installed on /dev/sda (which shoudn't have happened).

There is no problem as far as I can see. Do as in my previous post, and all should be fine.

Grub2 doesn't care about the boot flag but when you are booting with grub2. Right now you are booting with windows bootloader on /dev/sdb and it does boot the partition where the boot flag is. Hence booting XP from /dev/sdb1 directly.

---

### Post by quovadis on 2010-06-05
Darko, thanks for the fast reply.  Just one question, I installed Ubuntu Studio which as you already know is not a live disk and not Ubuntu.  So how do I run those commands in Ubuntu Studio? Should I opt for the text mode in the beginning? I am not sure of doing that with 100% certainty as I dont know anything in linux.  I am afraid I might goof up somewhere.  I also have a Ubuntu disk,  which I guess are both essentially the same.  So would I be able to reinstall grub like you told with that?

---

### Post by oldfred on 2010-06-05
If you booted into XP then you are booting from sdb. You could try booting from sda, but I am not sure it would work (script with grub2 now has not always been correct on drive order). Darko's suggestion on reinstalling grub2 to sdb is the best solution. I always prefer to have the boot loader on the same drive as the system. But I also like to separate drives for windows and Ubuntu when more than one drive is available.

I see /grldr which is from grub4dos in your sdb3 Vista partition. I would remove that. Also the Vista stanza in grub.cfg does not have the drivemap command that the XP stanza's have. I thought all windows required it. If Vista does not boot thru grub we will have to manually add an entry.

---

### Post by darkod on 2010-06-05
> **quovadis said:**
> Darko, thanks for the fast reply.  Just one question, I installed Ubuntu Studio which as you already know is not a live disk and not Ubuntu.  So how do I run those commands in Ubuntu Studio? Should I opt for the text mode in the beginning? I am not sure of doing that with 100% certainty as I dont know anything in linux.  I am afraid I might goof up somewhere.  I also have a Ubuntu disk,  which I guess are both essentially the same.  So would I be able to reinstall grub like you told with that?

I think grub2 is the same, so I would do it using the ubuntu standard cd in live mode. It will use the current grub2 config files anyway, with those two commands you are just installing grub2 to the MBR of /dev/sdb where it should be.

Unless oldfred has a better idea to reinstall grub2 using the studio cd? But I think it's safe to do the above.

---

### Post by oldfred on 2010-06-05
It was my understanding that the install of grub is from the system not the CD. You use the CD to boot. So any liveCD should work but I prefer to use the same version if possible.

---

### Post by quovadis on 2010-06-05
Fred/Darko, reinstalling grub with those commands worked like a charm.   Grub caught all the installs.  I tested by booting into all OS's without any trouble.  So now booting trouble is over.  Thanks again Fred/Darko, your time and effort greatly appreciated.  Just have a few more loose ends to tie with regard to some drivers and net connection.  Would it be appropriate to continue to post in this thread? or shall I start a new thread?

Anyways guys, thanks a lot.

P.S.:  I used the Ubuntu live cd to boot and to execute those commands, but as Fred said it is from the system I guess.

---

### Post by darkod on 2010-06-05
You are welcome. I missed earlier to mention to pay attention during the install grub2 to go to the same disk. Sorry. :)

Reinstalling grub2 would have been avoided if that went OK.

For your net connection questions the Networking subforum might be best place because there are more experts about that there I guess.
Myself for example, can't really help with installing a network adapter unless it's something really simple.

---

