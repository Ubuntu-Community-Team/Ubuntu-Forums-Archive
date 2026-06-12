---
title: "No disc space!?"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by buddah1620 on 2009-12-01
Having some serous problems... Was going to do a fresh install, moving to new HDD, and nothing will install.  Was going to do a Dual boot with Win XP pro (32bit) and Ubuntu 9.10 (64bit).  This setup worked fine on my previous HDD WD 320 GB SATA.  But now that I am trying on a new HDD WD 500 GB SATA, nothing works.  Windows installer says I don't have any hard drives connected.  Ubuntu says I have no hard drive space.  Ubuntu live wont let me look at my hard drives, it says i don't have authorized access.  It makes no since to me.  I have used the WD 500 GB for quite some time as a storage hard drive for movies and music.  I am so Grrrr right now.  ](*,)

for the record:
Asus m2n32 sli delux
AMD Athlon x2 4200+
Western Digital HDD 320 GB x2
Western Digital HDD 500 GB
Hitachi 1 TB 

All hdd are sata, and never had read / write problem before. Occasionally, windows would not unmount upon shut down and i would have to re-boot windows because Ubuntu would not mount it.  but this was far and few between.  And when that was the case, it told me that was the problem.

P.S.  I also dont get that BIOS recognizes my hard drives.  So does Acronis suite.  The disc director sees all of them. It will for mat, create partitions ect...

---

### Post by oldfred on 2009-12-01
Was this drive ever in a Raid configuration? New grub2 finds old raid settings that have to be removed.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by buddah1620 on 2009-12-02
No I never set up a raid.  Just didn't seem practical for me.  

For some unknown reason, my computer started reading and booting into my old 320 GB which has a dual boot on it.  I thought maybe I should flash my BIOS.  Which killed all ability for me you use a mouse or keyboard in windows, but Ubuntu still worked.... (*scratches head). Downgraded bios twice and everything worked as it should.  Disconnected my 320 GB and reconnected the 500 GB and booted in windows installer which worked! :D (My goal in all this was to install a dual boot on the 500GB, and have the 2, 320GB drives as storage.) Windows installed.  Was updating windows, SP3, all the updates, restarted after installing IE 8, and won't restart into windows.  Wont start normally, in safe mode, with last known config., nothing.  Can't boot into windows installer, it freezes or reboots itself.  Can't boot into Acronis, it freezes before loading.  I'm almost ready to through this thing through a window.  Something about a missing kernel nto file.

Oh yea, when I try to boot into Ubuntu 9.1 live cd it freezes on the language selection, or the computer re-boots.](*,)](*,)](*,)

---

### Post by oldfred on 2009-12-02
I cannot tell you how many times I have gone into my system to plug or unplug something and I bump something else that then is just loose enought to cause problems. Check every connection, memory card seated, and anything else that might be an issue hardware wise first. 

Beyond that down grading BIOS never seems right but may be? I have found BIOS settings for USB vs ports for keyboard and mouse either work or not in some systems. I had to switch connections several times to get one install to work, after that for some reason  (updates?) everything just worked.

---

### Post by buddah1620 on 2009-12-03
thank you for your reply's oldfred.  Having read many posts on this forum and others, I've heard alot of people flashing their bios and things miraculously working.  And miraculously failing. When the latter happend, stepping it down to the next version or two seemed to do the trick for them.  So I though I'd give it a try.  Also, after installing ubuntu 9.10 after grub, but before splash screen it gave me a message... something about k8... and I would work with latest bios... i didn't get a full read of it as it was very fast. 

After reading your post I think you are right.  I re-connected my 320 with the dual boot on it to find ubuntu still working like a champ and windows to have no mouse or keyboard again. This time I connected the sata cable from that drive to the 500 gb (that is I connected the sata cable from sata port 1 on mother board to the 500 gb, instead of it being connected to sata port 4 on the mother board where it had always been.) Well, windows is re-installing on the 500 gb.  After re-install I will try your suggestion.  I have a feeling you are on the money because weird things like this seem to happen all the time to me, and it is usually really simple things i just over look. :smile:

---

### Post by buddah1620 on 2009-12-03
Now no matter what drive i boot into, i get a mbr error.  So giving up for now.

---

### Post by buddah1620 on 2009-12-03
I've tried installing windows and Ubuntu on both drives.  When i boot after install, I get an MBR error message no matter which drive it is.  Sigh.....  thoughts...? opinions...?

---

### Post by oldfred on 2009-12-03
Lets take a look at your detailed boot configuration, you can download and run from the liveCD:

Boot Info Script 0.37 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions
  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 [http://ubuntuforums.org/showthread.php?p=8279056#1](http://ubuntuforums.org/showthread.php?p=8279056#1)
  caljohnsmith
 [http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3) 
cd to directory saved to: 
chmod 755 boot_info_script037.sh 
sudo ./boot_info_script037.sh 
or as example if on desktop from liveCD download 
sudo bash ~/Desktop/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by buddah1620 on 2009-12-04
Again thanks much for your help oldfred. Weird thing is it says I have weird stuff going on with boot loaders... But I distinctly remember the bubble being ticked to install the boot loader on (0,0) (default setting) the last time I installed karmic.  Do you think I should procure a 3rd party boot loader like Acronis's or I'm sure their are others as well.

*note the hard drives I had 3 HDD connected. 1: 500GB that I wanted the dual boot install on, 1: 320GB storage, and 1: 1TB storage.  I know it would not allow me to access the 320 GB.  It needed a password but I'm on a live CD, so their is no sudo password, so no access. Wish I knew how to disable that.

```
============================= Boot Info Summary: ==============================

 => Grub1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
 => No known boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu karmic (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdc2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdc5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sdc5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x11cdffbd

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   964,719,314   964,719,252  83 Linux
/dev/sda2         964,719,315   976,768,064    12,048,750   5 Extended
/dev/sda5         964,719,378   976,768,064    12,048,687  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x67a208da

Partition  Boot         Start           End          Size  Id System

/dev/sdb2    *         16,065   625,137,344   625,121,280   5 Extended
/dev/sdb5              16,128   625,137,344   625,121,217   7 HPFS/NTFS


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x262397ce

Partition  Boot         Start           End          Size  Id System

/dev/sdc2    *         16,065 1,953,520,064 1,953,504,000   5 Extended
/dev/sdc5              16,128 1,953,520,064 1,953,503,937   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="2e1844b1-9fb8-43ea-a64e-707a67a63d58" TYPE="ext4" 
/dev/sda5: UUID="1489435d-a1c3-4d03-8b1b-cf8f8f3d0cc2" TYPE="swap" 
/dev/sdb5: UUID="16AFB6C6AA7B0A30" LABEL="Hades" TYPE="ntfs" 
/dev/sdc5: UUID="62FAC67EFAC64E4B" LABEL="Titans" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /sys/kernel/security type securityfs (rw)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 2e1844b1-9fb8-43ea-a64e-707a67a63d58
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
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
        recordfail=1
        save_env recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2e1844b1-9fb8-43ea-a64e-707a67a63d58
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=2e1844b1-9fb8-43ea-a64e-707a67a63d58 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
        recordfail=1
        save_env recordfail
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2e1844b1-9fb8-43ea-a64e-707a67a63d58
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=2e1844b1-9fb8-43ea-a64e-707a67a63d58 ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=2e1844b1-9fb8-43ea-a64e-707a67a63d58 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1489435d-a1c3-4d03-8b1b-cf8f8f3d0cc2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-11-generic
    .0GB: boot/vmlinuz-2.6.31-11-generic
    .0GB: initrd.img
    .0GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdc

00000000  e8 12 01 b9 f0 01 be 10  7c bf 10 06 57 f3 a4 c3  |........|...W...|
00000010  8b 4e 14 83 f9 0e 75 08  8d 5e 07 43 02 07 e2 fb  |.N....u..^.C....|
00000020  8c 56 0c 8c 56 0e 75 69  8a 56 10 84 d2 79 62 e8  |.V..V.ui.V...yb.|
00000030  f6 00 bb aa 55 cd 13 72  6f 3b 5e 5c 75 6a d1 e9  |....U..ro;^\uj..|
00000040  73 66 b4 42 c6 46 02 01  eb 66 89 b6 f6 fe 8a 44  |sf.B.F...f.....D|
00000050  04 84 c0 74 0f 3c 05 74  0b 3c 0f 74 07 8a 14 80  |...t.<.t.<.t....|
00000060  e2 80 75 cb 83 c6 10 06  c4 5c 08 89 5e 08 8c 46  |..u......\..^..F|
00000070  0a 07 fe 8e f9 fe 75 d2  b0 31 c6 46 d7 50 88 46  |......u..1.F.P.F|
00000080  d4 be 6a 07 ac 84 c0 74  08 b4 0e b3 07 cd 10 eb  |..j....t........|
00000090  f3 e8 81 00 88 46 11 be  ae 07 3c 05 75 c6 cd 16  |.....F....<.u...|
000000a0  33 d2 89 56 08 89 56 0a  e8 7d 00 72 1b b8 01 02  |3..V..V..}.r....|
000000b0  bf 05 00 8b dc 56 50 50  32 e4 cd 13 58 8b f5 cd  |.....VPP2...X...|
000000c0  13 58 5e 73 03 4f 75 eb  b0 32 72 b2 40 8a 66 11  |.X^s.Ou..2r.@.f.|
000000d0  9e 7b 04 c6 47 02 0e 72  35 75 0c 88 57 40 c4 4e  |.{..G..r5u..W@.N|
000000e0  08 89 4f 1c 8c 47 1e 79  06 8a 4e 12 88 4f 25 80  |..O..G.y..N..O%.|
000000f0  c7 02 81 7f fe 55 aa 75  85 81 7f fa cd 19 75 09  |.....U.u......u.|
00000100  c6 47 fa e9 c7 47 fb 94  88 e8 1c 00 ff e4 74 ce  |.G...G........t.|
00000110  88 57 24 eb c9 5d 33 c0  8e d8 8e c0 8e d0 bc 00  |.W$..]3.........|
00000120  7c 55 bd a2 07 fc fb c3  b4 08 52 06 cd 13 07 72  ||U........R....r|
00000130  33 33 db 8a de 8b 46 0a  33 d2 83 e1 3f f7 f1 91  |33....F.3...?...|
00000140  97 8b 46 08 f7 f7 42 87  ca 3b da 72 17 43 f7 f3  |..F...B..;.r.C..|
00000150  8a f2 86 c5 d1 e8 d1 e8  0a c8 d0 cc d0 cc 0a f4  |................|
00000160  84 e4 74 02 b4 41 5b 8a  d3 c3 0d 0a 4d 42 52 20  |..t..A[.....MBR |
00000170  45 72 72 6f 72 20 00 0d  0a 00 72 65 73 73 20 61  |Error ....ress a|
00000180  6e 79 20 6b 65 79 20 74  6f 20 62 6f 6f 74 20 66  |ny key to boot f|
00000190  72 6f 6d 20 66 6c 6f 70  70 79 2e 2e 2e 00 00 00  |rom floppy......|
000001a0  00 00 10 00 01 00 00 7c  00 00 00 00 00 00 00 00  |.......|........|
000001b0  00 00 00 00 00 00 00 00  ce 97 23 26 00 00 00 00  |..........#&....|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 80 00  |................|
000001d0  01 01 05 fe ff ff c1 3e  00 00 00 1b 70 74 00 00  |.......>....pt..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```

---

### Post by oldfred on 2009-12-04
Your windows installs do not look correct. For windows to boot it has to be on a primary partition. You also have the boot flag on the extended partition which is just a container for the logical partitions in the extended partition.

check that your 500GB drive sda in listing is the first drive in BIOS as the first is the one used for booting. If either of the other two drives are first that is why you cannot boot. It looks like the 500GB drive should boot. It has grub2 and looks to the correct partition with the rest of the boot files.

---

### Post by buddah1620 on 2009-12-04
well sir what is your recommendation? make sure the 500 is plugged in sata port 1. Reformat as a primary partition with acronis. Fresh install of windows or ubuntu and go from there?  Am I missing anything, or do you have a better / different idea?

---

### Post by oldfred on 2009-12-05
the 500gb does not have to be sata port1. Just in BIOS select it as the boot drive and see if ubuntu boots. If that works then we can look at windows.

I think you will have to reinstall windows as the installs are in extended partitions and do not look complete. I suggest making a new primary partition formated NTFS to a size you want for windows and set the boot flag on in that partition. Then install windows. You may want to make that drive the first in BIOS so windows installs its boot loader to that drive rather than overwriting Grub and making you reinstall grub. Make sure it boots on its own. Then switch drives back so the 500 is first again , boot ubuntu, and do an update-grub which should then find the windows install and set it up for you.

---

### Post by buddah1620 on 2009-12-05
Not sure how to set a boot flag:?:.  BIOS does see the 500 gb as the first drive as it is in sata port 1.  I got home last night before i saw your reply and I used acronis to wipe the drive last night, so nothing is on the drive.  I just created an active partition at the front of the drive for installing XP.  I put XP SP2 disc in and I'll let you know how the install goes. You don't think it would have to do that I was installing windows on primary partition instead of active do you?

---

### Post by buddah1620 on 2009-12-05
Installed XP.  Started Installing drivers from my motherboard cd.  Restarted computer, and got "MBR error 1" on screen.  for *****$ and giggles I tried re-starting with windows disc in tray (and not hitting any key to enter set up, just let it run through to windows), and it boots up fine.  IDK.  *scratches head.  I'm at a loss.  I have to go to work in a bit.  I'll finish installing drivers when i get home and install ubuntu later i guess. It doesn't make any sence as to why it is not working.

---

### Post by oldfred on 2009-12-05
It sounds like it did not install windows boot to the MBR or did it put it in the other drive? Windows, grub, ubuntu and BIOS do not always identify the first drive the same which confuses me and everyone else. 

I find with grub2 and the lastest Ubuntu that my default drive order sda, sdb, sdc matches the order physically plugged into the motherboard. Even when I changed sdc to be the boot drive, the drive order did not change, but it boots from sdc.

---

### Post by buddah1620 on 2009-12-06
here's the thing though, I saw it (windows installer) say it was installing the boot loader to the correct drive's MBR when I let it format he partition.  

I think i need to be educated in the ways of ubuntu's terminology.  I read a write up about what the sda, sdb, sdc means (i know they are hdd), but i forget. What would you do if you were me?

---

### Post by buddah1620 on 2009-12-07
I tried using acronis Boot loader.  First i used the analizer utility which gave me this report:


```
*****************************
Disk Administrator hard disks
*****************************

Disk 1
Standard properties:
  BIOS Number:       080h
  Sectors per Track: 63
  Heads:             255
  MS-DOS Cylinders:  1023
  PTS-DOS Cylinders: 1024
  Total Cylinders:   60801
  MS-DOS Size:       7.9G
  PTS-DOS Size:      7.9G
  Total Size:        465.8G
  DA_API uses BIOS Extension above 7.9G
HDPT properties:
  Cylinders:                16643
  Heads:                    255
  Sectors per Track:        63
  Phys. Cylinders:          16383
  Phys. Heads:              16
  Phys. Sectors per Track:  63
  Precompensation Cylinder: 0
  Landing Cylinder:         65534
  Reserved:                 000h
  Defect Map Present:       No
  Disabled ECC Retry:       No
  Disabled Access Retry:    No
Extended properties:
  Extension Version:   2.1
  Functions Supported: Ext. EDD
  Transparent DMA:     No
  CHS Information:     None
  Removable Drive:     No
  Write with Verify:   No
  Change-line:         No
  Lockable Drive:      No
  Cylinders:           16383
  Heads:               16
  Sectors per Track:   63
  Total Sectors:       976773168
  Sector Size:         512
EDD properties:
  Base Port:     009F0h Master
  Control Port:  00BF2h
  LBA Enabled:   Yes
  Proprietary:   000h
  Multi-Sectors: 1
  PIO:           IRQ5 Mode 4 Fast
  DMA:           DRQ2 Mode 0 Fast
  Translation:   LBA Phoenix
  Removable:     No
  ATAPI Device:  No
  32-bit:        Yes
  Reserved:      00006h
  EDD Revision:  1.1

Disk 2
Standard properties:
  BIOS Number:       081h
  Sectors per Track: 63
  Heads:             255
  MS-DOS Cylinders:  1023
  PTS-DOS Cylinders: 1024
  Total Cylinders:   38913
  MS-DOS Size:       7.9G
  PTS-DOS Size:      7.9G
  Total Size:        298.1G
  DA_API uses BIOS Extension above 7.9G
HDPT properties:
  Cylinders:                16643
  Heads:                    255
  Sectors per Track:        63
  Phys. Cylinders:          16383
  Phys. Heads:              16
  Phys. Sectors per Track:  63
  Precompensation Cylinder: 0
  Landing Cylinder:         65534
  Reserved:                 000h
  Defect Map Present:       No
  Disabled ECC Retry:       No
  Disabled Access Retry:    No
Extended properties:
  Extension Version:   2.1
  Functions Supported: Ext. EDD
  Transparent DMA:     No
  CHS Information:     None
  Removable Drive:     No
  Write with Verify:   No
  Change-line:         No
  Lockable Drive:      No
  Cylinders:           16383
  Heads:               16
  Sectors per Track:   63
  Total Sectors:       625142448
  Sector Size:         512
EDD properties:
  Base Port:     00970h Master
  Control Port:  00B72h
  LBA Enabled:   Yes
  Proprietary:   000h
  Multi-Sectors: 1
  PIO:           IRQ5 Mode 4 Fast
  DMA:           DRQ2 Mode 0 Fast
  Translation:   LBA Phoenix
  Removable:     No
  ATAPI Device:  No
  32-bit:        Yes
  Reserved:      00006h
  EDD Revision:  1.1

Disk 3
Standard properties:
  BIOS Number:       082h
  Sectors per Track: 63
  Heads:             255
  MS-DOS Cylinders:  1023
  PTS-DOS Cylinders: 1023
  Total Cylinders:   121601
  MS-DOS Size:       7.9G
  PTS-DOS Size:      7.9G
  Total Size:        931.6G
  DA_API uses BIOS Extension above 7.9G
Extended properties:
  Extension Version:   2.1
  Functions Supported: Ext. EDD
  Transparent DMA:     No
  CHS Information:     None
  Removable Drive:     No
  Write with Verify:   No
  Change-line:         No
  Lockable Drive:      No
  Cylinders:           16383
  Heads:               16
  Sectors per Track:   63
  Total Sectors:       1953525168
  Sector Size:         512
EDD properties:
  Base Port:     00960h Master
  Control Port:  00B62h
  LBA Enabled:   Yes
  Proprietary:   000h
  Multi-Sectors: 1
  PIO:           IRQ5 Mode 4 Fast
  DMA:           DRQ2 Mode 0 Fast
  Translation:   LBA Phoenix
  Removable:     No
  ATAPI Device:  No
  32-bit:        Yes
  Reserved:      00006h
  EDD Revision:  1.1

*******************************
Disk Administrator sector dumps
*******************************

Disk 1 sector 15723B3D (CHS 0000577D, 00, 01):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................

Disk 1 sector 15521EB9 (CHS 000056FA, 01, 01):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................

Disk 1 sector 15521E7A (CHS 000056FA, 00, 01):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 F2 0E 00 00 00 00 00 00 00 00 01  .....ò..........
01C0  C1 FF 82 FE FF FF 3F 00 00 00 84 1C 20 00 00 00  Áÿ‚þÿÿ?...„. ...
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA  ..............Uª

Disk 1 sector 0000003F (CHS 00000000, 01, 01):
0000  EB 52 90 4E 54 46 53 20 20 20 20 00 02 08 00 00  ëRNTFS    .....
0010  00 00 00 00 00 F8 00 00 3F 00 FF 00 3F 00 00 00  .....ø..?.ÿ.?...
0020  00 00 00 00 80 00 80 00 3A 1E 52 15 00 00 00 00  ....€.€.:.R.....
0030  00 00 0C 00 00 00 00 00 E3 21 55 01 00 00 00 00  ........ã!U.....
0040  F6 00 00 00 01 00 00 00 12 CD 54 7C DA 54 7C 80  ö........ÍT|ÚT|€
0050  00 00 00 00 FA 33 C0 8E D0 BC 00 7C FB B8 C0 07  ....ú3ÀŽÐ¼.|û¸À.
0060  8E D8 E8 16 00 B8 00 0D 8E C0 33 DB C6 06 0E 00  ŽØè..¸..ŽÀ3ÛÆ...
0070  10 E8 53 00 68 00 0D 68 6A 02 CB 8A 16 24 00 B4  .èS.h..hj.ËŠ.$.´
0080  08 CD 13 73 05 B9 FF FF 8A F1 66 0F B6 C6 40 66  .Í.s.¹ÿÿŠñf.¶Æ@f
0090  0F B6 D1 80 E2 3F F7 E2 86 CD C0 ED 06 41 66 0F  .¶Ñ€â?÷â†ÍÀí.Af.
00A0  B7 C9 66 F7 E1 66 A3 20 00 C3 B4 41 BB AA 55 8A  ·Éf÷áf£ .Ã´A»ªUŠ
00B0  16 24 00 CD 13 72 0F 81 FB 55 AA 75 09 F6 C1 01  .$.Í.r.ûUªu.öÁ.
00C0  74 04 FE 06 14 00 C3 66 60 1E 06 66 A1 10 00 66  t.þ...Ãf`..f¡..f
00D0  03 06 1C 00 66 3B 06 20 00 0F 82 3A 00 1E 66 6A  ....f;. ..‚:..fj
00E0  00 66 50 06 53 66 68 10 00 01 00 80 3E 14 00 00  .fP.Sfh....€>...
00F0  0F 85 0C 00 E8 B3 FF 80 3E 14 00 00 0F 84 61 00  .…..è³ÿ€>....„a.
0100  B4 42 8A 16 24 00 16 1F 8B F4 CD 13 66 58 5B 07  ´BŠ.$...‹ôÍ.fX[.
0110  66 58 66 58 1F EB 2D 66 33 D2 66 0F B7 0E 18 00  fXfX.ë-f3Òf.·...
0120  66 F7 F1 FE C2 8A CA 66 8B D0 66 C1 EA 10 F7 36  f÷ñþÂŠÊf‹ÐfÁê.÷6
0130  1A 00 86 D6 8A 16 24 00 8A E8 C0 E4 06 0A CC B8  ..†ÖŠ.$.ŠèÀä..Ì¸
0140  01 02 CD 13 0F 82 19 00 8C C0 05 20 00 8E C0 66  ..Í..‚..ŒÀ. .ŽÀf
0150  FF 06 10 00 FF 0E 0E 00 0F 85 6F FF 07 1F 66 61  ÿ...ÿ....…oÿ..fa
0160  C3 A0 F8 01 E8 09 00 A0 FB 01 E8 03 00 FB EB FE  Ã*ø.è..*û.è..ûëþ
0170  B4 01 8B F0 AC 3C 00 74 09 B4 0E BB 07 00 CD 10  ´.‹ð¬<.t.´.»..Í.
0180  EB F2 C3 0D 0A 41 20 64 69 73 6B 20 72 65 61 64  ëòÃ..A disk read
0190  20 65 72 72 6F 72 20 6F 63 63 75 72 72 65 64 00   error occurred.
01A0  0D 0A 4E 54 4C 44 52 20 69 73 20 6D 69 73 73 69  ..NTLDR is missi
01B0  6E 67 00 0D 0A 4E 54 4C 44 52 20 69 73 20 63 6F  ng...NTLDR is co
01C0  6D 70 72 65 73 73 65 64 00 0D 0A 50 72 65 73 73  mpressed...Press
01D0  20 43 74 72 6C 2B 41 6C 74 2B 44 65 6C 20 74 6F   Ctrl+Alt+Del to
01E0  20 72 65 73 74 61 72 74 0D 0A 00 00 00 00 00 00   restart........
01F0  00 00 00 00 00 00 00 00 83 A0 B3 C9 00 00 55 AA  ........ƒ*³É..Uª

Disk 1 sector 00000000 (CHS 00000000, 00, 01):
0000  33 C0 8E D0 BC 00 7C FB 50 07 50 1F FC BE 1B 7C  3ÀŽÐ¼.|ûP.P.ü¾.|
0010  BF 1B 06 50 57 B9 E5 01 F3 A4 CB BD BE 07 B1 04  ¿..PW¹å.ó¤Ë½¾.±.
0020  38 6E 00 7C 09 75 13 83 C5 10 E2 F4 CD 18 8B F5  8n.|.u.ƒÅ.âôÍ.‹õ
0030  83 C6 10 49 74 19 38 2C 74 F6 A0 B5 07 B4 07 8B  ƒÆ.It.8,tö*µ.´.‹
0040  F0 AC 3C 00 74 FC BB 07 00 B4 0E CD 10 EB F2 88  ð¬<.tü»..´.Í.ëòˆ
0050  4E 10 E8 46 00 73 2A FE 46 10 80 7E 04 0B 74 0B  N.èF.s*þF.€~..t.
0060  80 7E 04 0C 74 05 A0 B6 07 75 D2 80 46 02 06 83  €~..t.*¶.uÒ€F..ƒ
0070  46 08 06 83 56 0A 00 E8 21 00 73 05 A0 B6 07 EB  F..ƒV..è!.s.*¶.ë
0080  BC 81 3E FE 7D 55 AA 74 0B 80 7E 10 00 74 C8 A0  ¼>þ}Uªt.€~..tÈ*
0090  B7 07 EB A9 8B FC 1E 57 8B F5 CB BF 05 00 8A 56  ·.ë©‹ü.W‹õË¿..ŠV
00A0  00 B4 08 CD 13 72 23 8A C1 24 3F 98 8A DE 8A FC  .´.Í.r#ŠÁ$?˜ŠÞŠü
00B0  43 F7 E3 8B D1 86 D6 B1 06 D2 EE 42 F7 E2 39 56  C÷ã‹Ñ†Ö±.ÒîB÷â9V
00C0  0A 77 23 72 05 39 46 08 73 1C B8 01 02 BB 00 7C  .w#r.9F.s.¸..».|
00D0  8B 4E 02 8B 56 00 CD 13 73 51 4F 74 4E 32 E4 8A  ‹N.‹V.Í.sQOtN2äŠ
00E0  56 00 CD 13 EB E4 8A 56 00 60 BB AA 55 B4 41 CD  V.Í.ëäŠV.`»ªU´AÍ
00F0  13 72 36 81 FB 55 AA 75 30 F6 C1 01 74 2B 61 60  .r6ûUªu0öÁ.t+a`
0100  6A 00 6A 00 FF 76 0A FF 76 08 6A 00 68 00 7C 6A  j.j.ÿv.ÿv.j.h.|j
0110  01 6A 10 B4 42 8B F4 CD 13 61 61 73 0E 4F 74 0B  .j.´B‹ôÍ.aas.Ot.
0120  32 E4 8A 56 00 CD 13 EB D6 61 F9 C3 49 6E 76 61  2äŠV.Í.ëÖaùÃInva
0130  6C 69 64 20 70 61 72 74 69 74 69 6F 6E 20 74 61  lid partition ta
0140  62 6C 65 00 45 72 72 6F 72 20 6C 6F 61 64 69 6E  ble.Error loadin
0150  67 20 6F 70 65 72 61 74 69 6E 67 20 73 79 73 74  g operating syst
0160  65 6D 00 4D 69 73 73 69 6E 67 20 6F 70 65 72 61  em.Missing opera
0170  74 69 6E 67 20 73 79 73 74 65 6D 00 00 00 00 00  ting system.....
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 2C 44 63 BD FF CD 11 00 00 80 01  .....,Dc½ÿÍ...€.
01C0  01 00 07 FE FF FF 3F 00 00 00 3B 1E 52 15 00 00  ...þÿÿ?...;.R...
01D0  C1 FF 05 FE FF FF 7A 1E 52 15 C3 1C 20 00 00 00  Áÿ.þÿÿz.R.Ã. ...
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA  ..............Uª

Disk 2 sector 00003F00 (CHS 00000001, 01, 01):
0000  EB 52 90 4E 54 46 53 20 20 20 20 00 02 08 00 00  ëRNTFS    .....
0010  00 00 00 00 00 F8 00 00 3F 00 FF 00 3F 00 00 00  .....ø..?.ÿ.?...
0020  00 00 00 00 80 00 80 00 C0 97 42 25 00 00 00 00  ....€.€.À—B%....
0030  02 00 00 00 00 00 00 00 30 00 00 00 00 00 00 00  ........0.......
0040  F6 00 00 00 01 00 00 00 30 0A 7B AA C6 B6 AF 16  ö.......0.{ªÆ¶¯.
0050  00 00 00 00 FA 33 C0 8E D0 BC 00 7C FB B8 C0 07  ....ú3ÀŽÐ¼.|û¸À.
0060  8E D8 E8 16 00 B8 00 0D 8E C0 33 DB C6 06 0E 00  ŽØè..¸..ŽÀ3ÛÆ...
0070  10 E8 53 00 68 00 0D 68 6A 02 CB 8A 16 24 00 B4  .èS.h..hj.ËŠ.$.´
0080  08 CD 13 73 05 B9 FF FF 8A F1 66 0F B6 C6 40 66  .Í.s.¹ÿÿŠñf.¶Æ@f
0090  0F B6 D1 80 E2 3F F7 E2 86 CD C0 ED 06 41 66 0F  .¶Ñ€â?÷â†ÍÀí.Af.
00A0  B7 C9 66 F7 E1 66 A3 20 00 C3 B4 41 BB AA 55 8A  ·Éf÷áf£ .Ã´A»ªUŠ
00B0  16 24 00 CD 13 72 0F 81 FB 55 AA 75 09 F6 C1 01  .$.Í.r.ûUªu.öÁ.
00C0  74 04 FE 06 14 00 C3 66 60 1E 06 66 A1 10 00 66  t.þ...Ãf`..f¡..f
00D0  03 06 1C 00 66 3B 06 20 00 0F 82 3A 00 1E 66 6A  ....f;. ..‚:..fj
00E0  00 66 50 06 53 66 68 10 00 01 00 80 3E 14 00 00  .fP.Sfh....€>...
00F0  0F 85 0C 00 E8 B3 FF 80 3E 14 00 00 0F 84 61 00  .…..è³ÿ€>....„a.
0100  B4 42 8A 16 24 00 16 1F 8B F4 CD 13 66 58 5B 07  ´BŠ.$...‹ôÍ.fX[.
0110  66 58 66 58 1F EB 2D 66 33 D2 66 0F B7 0E 18 00  fXfX.ë-f3Òf.·...
0120  66 F7 F1 FE C2 8A CA 66 8B D0 66 C1 EA 10 F7 36  f÷ñþÂŠÊf‹ÐfÁê.÷6
0130  1A 00 86 D6 8A 16 24 00 8A E8 C0 E4 06 0A CC B8  ..†ÖŠ.$.ŠèÀä..Ì¸
0140  01 02 CD 13 0F 82 19 00 8C C0 05 20 00 8E C0 66  ..Í..‚..ŒÀ. .ŽÀf
0150  FF 06 10 00 FF 0E 0E 00 0F 85 6F FF 07 1F 66 61  ÿ...ÿ....…oÿ..fa
0160  C3 A0 F8 01 E8 09 00 A0 FB 01 E8 03 00 FB EB FE  Ã*ø.è..*û.è..ûëþ
0170  B4 01 8B F0 AC 3C 00 74 09 B4 0E BB 07 00 CD 10  ´.‹ð¬<.t.´.»..Í.
0180  EB F2 C3 0D 0A 41 20 64 69 73 6B 20 72 65 61 64  ëòÃ..A disk read
0190  20 65 72 72 6F 72 20 6F 63 63 75 72 72 65 64 00   error occurred.
01A0  0D 0A 4E 54 4C 44 52 20 69 73 20 6D 69 73 73 69  ..NTLDR is missi
01B0  6E 67 00 0D 0A 4E 54 4C 44 52 20 69 73 20 63 6F  ng...NTLDR is co
01C0  6D 70 72 65 73 73 65 64 00 0D 0A 50 72 65 73 73  mpressed...Press
01D0  20 43 74 72 6C 2B 41 6C 74 2B 44 65 6C 20 74 6F   Ctrl+Alt+Del to
01E0  20 72 65 73 74 61 72 74 0D 0A 00 00 00 00 00 00   restart........
01F0  00 00 00 00 00 00 00 00 83 A0 B3 C9 00 00 55 AA  ........ƒ*³É..Uª

Disk 2 sector 00003EC1 (CHS 00000001, 00, 01):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 01  ................
01C0  01 01 07 FE FF FF 3F 00 00 00 C1 97 42 25 00 00  ...þÿÿ?...Á—B%..
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA  ..............Uª

Disk 2 sector 00000001 (CHS 00000000, 00, 02):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................

Disk 2 sector 00000000 (CHS 00000000, 00, 01):
0000  33 C0 8E D0 BC 00 7C FB 50 07 50 1F FC BE 1B 7C  3ÀŽÐ¼.|ûP.P.ü¾.|
0010  BF 1B 06 50 57 B9 E5 01 F3 A4 CB BD BE 07 B1 04  ¿..PW¹å.ó¤Ë½¾.±.
0020  38 6E 00 7C 09 75 13 83 C5 10 E2 F4 CD 18 8B F5  8n.|.u.ƒÅ.âôÍ.‹õ
0030  83 C6 10 49 74 19 38 2C 74 F6 A0 B5 07 B4 07 8B  ƒÆ.It.8,tö*µ.´.‹
0040  F0 AC 3C 00 74 FC BB 07 00 B4 0E CD 10 EB F2 88  ð¬<.tü»..´.Í.ëòˆ
0050  4E 10 E8 46 00 73 2A FE 46 10 80 7E 04 0B 74 0B  N.èF.s*þF.€~..t.
0060  80 7E 04 0C 74 05 A0 B6 07 75 D2 80 46 02 06 83  €~..t.*¶.uÒ€F..ƒ
0070  46 08 06 83 56 0A 00 E8 21 00 73 05 A0 B6 07 EB  F..ƒV..è!.s.*¶.ë
0080  BC 81 3E FE 7D 55 AA 74 0B 80 7E 10 00 74 C8 A0  ¼>þ}Uªt.€~..tÈ*
0090  B7 07 EB A9 8B FC 1E 57 8B F5 CB BF 05 00 8A 56  ·.ë©‹ü.W‹õË¿..ŠV
00A0  00 B4 08 CD 13 72 23 8A C1 24 3F 98 8A DE 8A FC  .´.Í.r#ŠÁ$?˜ŠÞŠü
00B0  43 F7 E3 8B D1 86 D6 B1 06 D2 EE 42 F7 E2 39 56  C÷ã‹Ñ†Ö±.ÒîB÷â9V
00C0  0A 77 23 72 05 39 46 08 73 1C B8 01 02 BB 00 7C  .w#r.9F.s.¸..».|
00D0  8B 4E 02 8B 56 00 CD 13 73 51 4F 74 4E 32 E4 8A  ‹N.‹V.Í.sQOtN2äŠ
00E0  56 00 CD 13 EB E4 8A 56 00 60 BB AA 55 B4 41 CD  V.Í.ëäŠV.`»ªU´AÍ
00F0  13 72 36 81 FB 55 AA 75 30 F6 C1 01 74 2B 61 60  .r6ûUªu0öÁ.t+a`
0100  6A 00 6A 00 FF 76 0A FF 76 08 6A 00 68 00 7C 6A  j.j.ÿv.ÿv.j.h.|j
0110  01 6A 10 B4 42 8B F4 CD 13 61 61 73 0E 4F 74 0B  .j.´B‹ôÍ.aas.Ot.
0120  32 E4 8A 56 00 CD 13 EB D6 61 F9 C3 49 6E 76 61  2äŠV.Í.ëÖaùÃInva
0130  6C 69 64 20 70 61 72 74 69 74 69 6F 6E 20 74 61  lid partition ta
0140  62 6C 65 00 45 72 72 6F 72 20 6C 6F 61 64 69 6E  ble.Error loadin
0150  67 20 6F 70 65 72 61 74 69 6E 67 20 73 79 73 74  g operating syst
0160  65 6D 00 4D 69 73 73 69 6E 67 20 6F 70 65 72 61  em.Missing opera
0170  74 69 6E 67 20 73 79 73 74 65 6D 00 00 00 00 00  ting system.....
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 2C 44 63 DA 08 A2 67 00 00 00 00  .....,DcÚ.¢g....
01C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 80 00  ..............€.
01D0  01 01 05 FE FF FF C1 3E 00 00 00 98 42 25 00 00  ...þÿÿÁ>...˜B%..
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA  ..............Uª

Disk 3 sector 00003F00 (CHS 00000001, 01, 01):
0000  EB 52 90 4E 54 46 53 20 20 20 20 00 02 08 00 00  ëRNTFS    .....
0010  00 00 00 00 00 F8 00 00 3F 00 FF 00 3F 00 00 00  .....ø..?.ÿ.?...
0020  00 00 00 00 80 00 80 00 C0 1A 70 74 00 00 00 00  ....€.€.À.pt....
0030  00 00 0C 00 00 00 00 00 AC 01 47 07 00 00 00 00  ........¬.G.....
0040  F6 00 00 00 01 00 00 00 4B 4E C6 FA 7E C6 FA 62  ö.......KNÆú~Æúb
0050  00 00 00 00 FA 33 C0 8E D0 BC 00 7C FB 68 C0 07  ....ú3ÀŽÐ¼.|ûhÀ.
0060  1F 1E 68 66 00 CB 88 16 0E 00 66 81 3E 03 00 4E  ..hf.Ëˆ...f>..N
0070  54 46 53 75 15 B4 41 BB AA 55 CD 13 72 0C 81 FB  TFSu.´A»ªUÍ.r.û
0080  55 AA 75 06 F7 C1 01 00 75 03 E9 D2 00 1E 83 EC  Uªu.÷Á..u.éÒ..ƒì
0090  18 68 1A 00 B4 48 8A 16 0E 00 8B F4 16 1F CD 13  .h..´HŠ...‹ô..Í.
00A0  9F 83 C4 18 9E 58 1F 72 E1 3B 06 0B 00 75 DB A3  ŸƒÄ.žX.rá;...uÛ£
00B0  0F 00 C1 2E 0F 00 04 1E 5A 33 DB B9 00 20 2B C8  ..Á.....Z3Û¹. +È
00C0  66 FF 06 11 00 03 16 0F 00 8E C2 FF 06 16 00 E8  fÿ.......ŽÂÿ...è
00D0  40 00 2B C8 77 EF B8 00 BB CD 1A 66 23 C0 75 2D  @.+Èwï¸.»Í.f#Àu-
00E0  66 81 FB 54 43 50 41 75 24 81 F9 02 01 72 1E 16  fûTCPAu$ù..r..
00F0  68 07 BB 16 68 70 0E 16 68 09 00 66 53 66 53 66  h.».hp..h..fSfSf
0100  55 16 16 16 68 B8 01 66 61 0E 07 CD 1A E9 6A 01  U...h¸.fa..Í.éj.
0110  90 90 66 60 1E 06 66 A1 11 00 66 03 06 1C 00 1E  f`..f¡..f.....
0120  66 68 00 00 00 00 66 50 06 53 68 01 00 68 10 00  fh....fP.Sh..h..
0130  B4 42 8A 16 0E 00 16 1F 8B F4 CD 13 66 59 5B 5A  ´BŠ.....‹ôÍ.fY[Z
0140  66 59 66 59 1F 0F 82 16 00 66 FF 06 11 00 03 16  fYfY..‚..fÿ.....
0150  0F 00 8E C2 FF 0E 16 00 75 BC 07 1F 66 61 C3 A0  ..ŽÂÿ...u¼..faÃ*
0160  F8 01 E8 08 00 A0 FB 01 E8 02 00 EB FE B4 01 8B  ø.è..*û.è..ëþ´.‹
0170  F0 AC 3C 00 74 09 B4 0E BB 07 00 CD 10 EB F2 C3  ð¬<.t.´.»..Í.ëòÃ
0180  0D 0A 41 20 64 69 73 6B 20 72 65 61 64 20 65 72  ..A disk read er
0190  72 6F 72 20 6F 63 63 75 72 72 65 64 00 0D 0A 42  ror occurred...B
01A0  4F 4F 54 4D 47 52 20 69 73 20 6D 69 73 73 69 6E  OOTMGR is missin
01B0  67 00 0D 0A 42 4F 4F 54 4D 47 52 20 69 73 20 63  g...BOOTMGR is c
01C0  6F 6D 70 72 65 73 73 65 64 00 0D 0A 50 72 65 73  ompressed...Pres
01D0  73 20 43 74 72 6C 2B 41 6C 74 2B 44 65 6C 20 74  s Ctrl+Alt+Del t
01E0  6F 20 72 65 73 74 61 72 74 0D 0A 00 00 00 00 00  o restart.......
01F0  00 00 00 00 00 00 00 00 80 9D B2 CA 00 00 55 AA  ........€²Ê..Uª

Disk 3 sector 00003EC1 (CHS 00000001, 00, 01):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 F2 0E 00 00 00 00 00 00 00 00 01  .....ò..........
01C0  01 01 07 FE FF FF 3F 00 00 00 C1 1A 70 74 00 00  ...þÿÿ?...Á.pt..
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA  ..............Uª

Disk 3 sector 00000001 (CHS 00000000, 00, 02):
0000  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0010  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0020  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0030  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0040  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0050  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0060  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0070  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0080  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0090  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
00F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0100  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0110  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0120  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0130  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0140  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0150  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0160  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0170  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0180  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
0190  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01A0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01B0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01D0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................

Disk 3 sector 00000000 (CHS 00000000, 00, 01):
0000  E8 12 01 B9 F0 01 BE 10 7C BF 10 06 57 F3 A4 C3  è..¹ð.¾.|¿..Wó¤Ã
0010  8B 4E 14 83 F9 0E 75 08 8D 5E 07 43 02 07 E2 FB  ‹N.ƒù.u.^.C..âû
0020  8C 56 0C 8C 56 0E 75 69 8A 56 10 84 D2 79 62 E8  ŒV.ŒV.uiŠV.„Òybè
0030  F6 00 BB AA 55 CD 13 72 6F 3B 5E 5C 75 6A D1 E9  ö.»ªUÍ.ro;^\ujÑé
0040  73 66 B4 42 C6 46 02 01 EB 66 89 B6 F6 FE 8A 44  sf´BÆF..ëf‰¶öþŠD
0050  04 84 C0 74 0F 3C 05 74 0B 3C 0F 74 07 8A 14 80  .„Àt.<.t.<.t.Š.€
0060  E2 80 75 CB 83 C6 10 06 C4 5C 08 89 5E 08 8C 46  â€uËƒÆ..Ä\.‰^.ŒF
0070  0A 07 FE 8E F9 FE 75 D2 B0 31 C6 46 D7 50 88 46  ..þŽùþuÒ°1ÆF×PˆF
0080  D4 BE 6A 07 AC 84 C0 74 08 B4 0E B3 07 CD 10 EB  Ô¾j.¬„Àt.´.³.Í.ë
0090  F3 E8 81 00 88 46 11 BE AE 07 3C 05 75 C6 CD 16  óè.ˆF.¾®.<.uÆÍ.
00A0  33 D2 89 56 08 89 56 0A E8 7D 00 72 1B B8 01 02  3Ò‰V.‰V.è}.r.¸..
00B0  BF 05 00 8B DC 56 50 50 32 E4 CD 13 58 8B F5 CD  ¿..‹ÜVPP2äÍ.X‹õÍ
00C0  13 58 5E 73 03 4F 75 EB B0 32 72 B2 40 8A 66 11  .X^s.Ouë°2r²@Šf.
00D0  9E 7B 04 C6 47 02 0E 72 35 75 0C 88 57 40 C4 4E  ž{.ÆG..r5u.ˆW@ÄN
00E0  08 89 4F 1C 8C 47 1E 79 06 8A 4E 12 88 4F 25 80  .‰O.ŒG.y.ŠN.ˆO%€
00F0  C7 02 81 7F FE 55 AA 75 85 81 7F FA CD 19 75 09  Ç.þUªu…úÍ.u.
0100  C6 47 FA E9 C7 47 FB 94 88 E8 1C 00 FF E4 74 CE  ÆGúéÇGû”ˆè..ÿätÎ
0110  88 57 24 EB C9 5D 33 C0 8E D8 8E C0 8E D0 BC 00  ˆW$ëÉ]3ÀŽØŽÀŽÐ¼.
0120  7C 55 BD A2 07 FC FB C3 B4 08 52 06 CD 13 07 72  |U½¢.üûÃ´.R.Í..r
0130  33 33 DB 8A DE 8B 46 0A 33 D2 83 E1 3F F7 F1 91  33ÛŠÞ‹F.3Òƒá?÷ñ‘
0140  97 8B 46 08 F7 F7 42 87 CA 3B DA 72 17 43 F7 F3  —‹F.÷÷B‡Ê;Úr.C÷ó
0150  8A F2 86 C5 D1 E8 D1 E8 0A C8 D0 CC D0 CC 0A F4  Šò†ÅÑèÑè.ÈÐÌÐÌ.ô
0160  84 E4 74 02 B4 41 5B 8A D3 C3 0D 0A 4D 42 52 20  „ät.´A[ŠÓÃ..MBR 
0170  45 72 72 6F 72 20 00 0D 0A 00 72 65 73 73 20 61  Error ....ress a
0180  6E 79 20 6B 65 79 20 74 6F 20 62 6F 6F 74 20 66  ny key to boot f
0190  72 6F 6D 20 66 6C 6F 70 70 79 2E 2E 2E 00 00 00  rom floppy......
01A0  00 00 10 00 01 00 00 7C 00 00 00 00 00 00 00 00  .......|........
01B0  00 00 00 00 00 00 00 00 CE 97 23 26 00 00 00 00  ........Î—#&....
01C0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 80 00  ..............€.
01D0  01 01 05 FE FF FF C1 3E 00 00 00 1B 70 74 00 00  ...þÿÿÁ>....pt..
01E0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00  ................
01F0  00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA  ..............Uª

*****************************************
Disk Administrator tables and bootsectors
*****************************************

Disk 1  Free space of size 294.2G:
  First physical sector:   359807805 (cyl. 22397, head 0, sec. 1)
  Last physical sector:    976768064 (cyl. 60800, head 254, sec. 63)
  Total physical sectors:  616960260


Disk 1  Partition 5 of type 082h (Linux swap, Solaris) and size 1.0G:
  First physical sector:   357703353 (cyl. 22266, head 1, sec. 1)
  Last physical sector:    359807804 (cyl. 22396, head 254, sec. 63)
  Total physical sectors:    2104452


Disk 1  Nested partition table:
  First physical sector:   357703290 (cyl. 22266, head 0, sec. 1)
  Last physical sector:    357703290 (cyl. 22266, head 0, sec. 1)
  Total physical sectors:          1

Table structure:
  Extended boot sector:       0
  Extended hidden partitions: 000h (Unused)
                              000h (Unused)
                              000h (Unused)
                              000h (Unused)
  Extended boot disk:         000h
  Extended patch flags:       FAT16(-) MS-DOS7+(-) FAT32(-) OS/2(-)
  Extended OS/2 patch:        000h
  Extended checksum (0F2h):   0F2h
  Extended size (14):         14
  NT serial number:           000000000h
  Extended serial number:     00000h
I Flag      Begin CHS           End CHS        Begin       Size Type
- - ------------------ ------------------ ---------- ---------- -------------
0 -       1023   1   1       1023 254  63         63    2104452 082h (Linux swap, Solaris)
  -       1023   1   1       1023 254  63         63    2104452 082h (Linux swap, Solaris)
  -      22266   1   1      22396 254  63  357703353    2104452
- - ------------------ ------------------ ---------- ---------- -------------
1 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
2 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
3 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
  Boot sign (0AA55h):         0AA55h

Disk 1  Partition 1 of type 007h (NTFS, HPFS) and size 170.6G:
  First physical sector:          63 (cyl. 0, head 1, sec. 1)
  Last physical sector:    357703289 (cyl. 22265, head 254, sec. 63)
  Total physical sectors:  357703227

NTFS bootsector structure:
  Jump code:               0EBh 052h 090h
  File system name:        NTFS    
  Sector size (512):       512
  Sectors per cluster:     8
  Reserved sectors (0):    0
  FAT copies (0):          0
  Root folder items (0):   0
  Total sectors (0):       0
  Media ID:                0F8h
  FAT size (0):            0
  Sectors per track:       63
  Number of heads:         255
  Hidden sectors:          63
  Big total sectors (0):   0
  Hard disk:               080h
  Reserved:                000h 080h
  Big total sectors:       357703226
  MFT cluster:             786432
  MFTmirr cluster:         22356451
  MFT record size:         -10
  Index buffer size:       1
  Serial number:           0807Ch-054DAh-07C54h-0CD12h
  Boot signature (0AA55h): 0AA55h

Disk 1  MBR (Master Boot Record):
  First physical sector:           0 (cyl. 0, head 0, sec. 1)
  Last physical sector:            0 (cyl. 0, head 0, sec. 1)
  Total physical sectors:          1

Table structure:
  Extended boot sector:       0
  Extended hidden partitions: 000h (Unused)
                              000h (Unused)
                              000h (Unused)
                              000h (Unused)
  Extended boot disk:         000h
  Extended patch flags:       FAT16(-) MS-DOS7+(-) FAT32(-) OS/2(-)
  Extended OS/2 patch:        000h
  Extended checksum (059h):   02Ch
  Extended size (14):         25412
  NT serial number:           011CDFFBDh
  Extended serial number:     00000h
I Flag      Begin CHS           End CHS        Begin       Size Type
- - ------------------ ------------------ ---------- ---------- -------------
0 A          0   1   1       1023 254  63         63  357703227 007h (NTFS, HPFS)
  A          0   1   1       1023 254  63         63  357703227 007h (NTFS, HPFS)
  -          0   1   1      22265 254  63         63  357703227
- - ------------------ ------------------ ---------- ---------- -------------
1 -       1023   0   1       1023 254  63  357703290    2104515 005h (Extended)
  -       1023   0   1       1023 254  63  357703290    2104515 005h (Extended)
  -      22266   0   1      22396 254  63  357703290          1
- - ------------------ ------------------ ---------- ---------- -------------
2 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
3 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
  Boot sign (0AA55h):         0AA55h

Disk 2  Partition 5 of type 007h (NTFS, HPFS) and size 298.1G:
  First physical sector:       16128 (cyl. 1, head 1, sec. 1)
  Last physical sector:    625137344 (cyl. 38912, head 254, sec. 63)
  Total physical sectors:  625121217

NTFS bootsector structure:
  Jump code:               0EBh 052h 090h
  File system name:        NTFS    
  Sector size (512):       512
  Sectors per cluster:     8
  Reserved sectors (0):    0
  FAT copies (0):          0
  Root folder items (0):   0
  Total sectors (0):       0
  Media ID:                0F8h
  FAT size (0):            0
  Sectors per track:       63
  Number of heads:         255
  Hidden sectors:          63
  Big total sectors (0):   0
  Hard disk:               080h
  Reserved:                000h 080h
  Big total sectors:       625121216
  MFT cluster:             2
  MFTmirr cluster:         48
  MFT record size:         -10
  Index buffer size:       1
  Serial number:           016AFh-0B6C6h-0AA7Bh-00A30h
  Boot signature (0AA55h): 0AA55h

Disk 2  Nested partition table:
  First physical sector:       16065 (cyl. 1, head 0, sec. 1)
  Last physical sector:        16065 (cyl. 1, head 0, sec. 1)
  Total physical sectors:          1

Table structure:
  Extended boot sector:       0
  Extended hidden partitions: 000h (Unused)
                              000h (Unused)
                              000h (Unused)
                              000h (Unused)
  Extended boot disk:         000h
  Extended patch flags:       FAT16(-) MS-DOS7+(-) FAT32(-) OS/2(-)
  Extended OS/2 patch:        000h
  Extended checksum (000h):   000h
  Extended size (14):         0
  NT serial number:           000000000h
  Extended serial number:     00000h
I Flag      Begin CHS           End CHS        Begin       Size Type
- - ------------------ ------------------ ---------- ---------- -------------
0 -          1   1   1       1023 254  63         63  625121217 007h (NTFS, HPFS)
  -          1   1   1       1023 254  63         63  625121217 007h (NTFS, HPFS)
  -          1   1   1      38912 254  63      16128  625121217
- - ------------------ ------------------ ---------- ---------- -------------
1 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
2 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
3 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
  Boot sign (0AA55h):         0AA55h

Disk 2  Free space of size 7.8M:
  First physical sector:           1 (cyl. 0, head 0, sec. 2)
  Last physical sector:        16064 (cyl. 0, head 254, sec. 63)
  Total physical sectors:      16064


Disk 2  MBR (Master Boot Record):
  First physical sector:           0 (cyl. 0, head 0, sec. 1)
  Last physical sector:            0 (cyl. 0, head 0, sec. 1)
  Total physical sectors:          1

Table structure:
  Extended boot sector:       0
  Extended hidden partitions: 000h (Unused)
                              000h (Unused)
                              000h (Unused)
                              000h (Unused)
  Extended boot disk:         000h
  Extended patch flags:       FAT16(-) MS-DOS7+(-) FAT32(-) OS/2(-)
  Extended OS/2 patch:        000h
  Extended checksum (059h):   02Ch
  Extended size (14):         25412
  NT serial number:           067A208DAh
  Extended serial number:     00000h
I Flag      Begin CHS           End CHS        Begin       Size Type
- - ------------------ ------------------ ---------- ---------- -------------
0 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
1 A          1   0   1       1023 254  63      16065  625121280 005h (Extended)
  A          1   0   1       1023 254  63      16065  625121280 005h (Extended)
  -          1   0   1      38912 254  63      16065          1
- - ------------------ ------------------ ---------- ---------- -------------
2 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
3 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
  Boot sign (0AA55h):         0AA55h

Disk 3  Partition 5 of type 007h (NTFS, HPFS) and size 931.5G:
  First physical sector:       16128 (cyl. 1, head 1, sec. 1)
  Last physical sector:   1953520064 (cyl. 121600, head 254, sec. 63)
  Total physical sectors: 1953503937

NTFS bootsector structure:
  Jump code:               0EBh 052h 090h
  File system name:        NTFS    
  Sector size (512):       512
  Sectors per cluster:     8
  Reserved sectors (0):    0
  FAT copies (0):          0
  Root folder items (0):   0
  Total sectors (0):       0
  Media ID:                0F8h
  FAT size (0):            0
  Sectors per track:       63
  Number of heads:         255
  Hidden sectors:          63
  Big total sectors (0):   0
  Hard disk:               080h
  Reserved:                000h 080h
  Big total sectors:       1953503936
  MFT cluster:             786432
  MFTmirr cluster:         122093996
  MFT record size:         -10
  Index buffer size:       1
  Serial number:           062FAh-0C67Eh-0FAC6h-04E4Bh
  Boot signature (0AA55h): 0AA55h

Disk 3  Nested partition table:
  First physical sector:       16065 (cyl. 1, head 0, sec. 1)
  Last physical sector:        16065 (cyl. 1, head 0, sec. 1)
  Total physical sectors:          1

Table structure:
  Extended boot sector:       0
  Extended hidden partitions: 000h (Unused)
                              000h (Unused)
                              000h (Unused)
                              000h (Unused)
  Extended boot disk:         000h
  Extended patch flags:       FAT16(-) MS-DOS7+(-) FAT32(-) OS/2(-)
  Extended OS/2 patch:        000h
  Extended checksum (0F2h):   0F2h
  Extended size (14):         14
  NT serial number:           000000000h
  Extended serial number:     00000h
I Flag      Begin CHS           End CHS        Begin       Size Type
- - ------------------ ------------------ ---------- ---------- -------------
0 -          1   1   1       1023 254  63         63 1953503937 007h (NTFS, HPFS)
  -          1   1   1       1023 254  63         63 1953503937 007h (NTFS, HPFS)
  -          1   1   1     121600 254  63      16128 1953503937
- - ------------------ ------------------ ---------- ---------- -------------
1 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
2 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
3 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
  Boot sign (0AA55h):         0AA55h

Disk 3  Free space of size 7.8M:
  First physical sector:           1 (cyl. 0, head 0, sec. 2)
  Last physical sector:        16064 (cyl. 0, head 254, sec. 63)
  Total physical sectors:      16064


Disk 3  MBR (Master Boot Record):
  First physical sector:           0 (cyl. 0, head 0, sec. 1)
  Last physical sector:            0 (cyl. 0, head 0, sec. 1)
  Total physical sectors:          1

Table structure:
  Extended boot sector:       0
  Extended hidden partitions: 000h (Unused)
                              000h (Unused)
                              000h (Unused)
                              000h (Unused)
  Extended boot disk:         000h
  Extended patch flags:       FAT16(-) MS-DOS7+(-) FAT32(-) OS/2(-)
  Extended OS/2 patch:        000h
  Extended checksum (000h):   000h
  Extended size (14):         0
  NT serial number:           0262397CEh
  Extended serial number:     00000h
I Flag      Begin CHS           End CHS        Begin       Size Type
- - ------------------ ------------------ ---------- ---------- -------------
0 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
1 A          1   0   1       1023 254  63      16065 1953504000 005h (Extended)
  A          1   0   1       1023 254  63      16065 1953504000 005h (Extended)
  -          1   0   1     121600 254  63      16065          1
- - ------------------ ------------------ ---------- ---------- -------------
2 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
- - ------------------ ------------------ ---------- ---------- -------------
3 -          0   0   0          0   0   0          0          0 000h (Unused)
  -          0   0   0          0   0   0          0          0 000h (Unused)
  Boot sign (0AA55h):         0AA55h

*******************************
Disk Administrator file systems
*******************************

Partition #1-5
General:
  File system:        Linux Swap
  Size:               1.0G (2104448 sectors)
  Useful information: 0 (0 bytes)
Blocks:
  Size:             4.0K
  Total:            1.0G (263056)

Partition #1-1
General:
  File system:        NTFS
  Volume label:       
  Serial number:      807C-54DA-7C54-CD12
  Size:               170.6G (357703225 sectors)
  Useful information: 9.0G (9688197442 bytes)
Special:
  Reserved (boot record): 8.0K (16 sectors)
  Journal size:           64.0M (131072 sectors)
Clusters:
  Size:             4.0K
  Total:            170.6G (44712903)
  Free:             162.1G (42498779)
File records:
  Size:             1024 bytes
  Total:            36.6M (37440)
  Free:             13.0K (13)
Statistics:
  Files:             34660
  Folders:           2692
  Hard links:        0

Partition #2-5
General:
  File system:        NTFS
  Volume label:       Hades
  Serial number:      16AF-B6C6-AA7B-0A30
  Size:               298.1G (625121217 sectors)
  Useful information: 253.4G (272062282581 bytes)
Special:
  Reserved (boot record): 4.0K (8 sectors)
  Journal size:           64.0M (131072 sectors)
Clusters:
  Size:             4.0K
  Total:            298.1G (78140152)
  Free:             44.6G (11687396)
File records:
  Size:             1024 bytes
  Total:            21.1M (21616)
  Free:             7.2M (7394)
Statistics:
  Files:             12770
  Folders:           1111
  Hard links:        0

Partition #3-5
General:
  File system:        NTFS
  Volume label:       Titans
  Serial number:      62FA-C67E-FAC6-4E4B
  Size:               931.5G (1953503937 sectors)
  Useful information: 841.7G (903716459372 bytes)
Special:
  Reserved (boot record): 8.0K (16 sectors)
  Journal size:           64.0M (131072 sectors)
Clusters:
  Size:             4.0K
  Total:            931.5G (244187992)
  Free:             89.7G (23514468)
File records:
  Size:             1024 bytes
  Total:            18.5M (18960)
  Free:             13.0K (13)
Statistics:
  Files:             17961
  Folders:           966
  Hard links:        0

************************

```

I also tried to install the OS Selector. Upon boot up, i was given this error:

> Cannot get exclusice access to hard disk drives.  Please make sure that Windows Computer managment Console, or other software that locks the hard disk drives, are not running.

This was before Windows started... I don't see how windows could be "locking" the hard drive.

---

### Post by buddah1620 on 2009-12-10
This whole time I've been assuming that my problem was a write error. While that may be true, and play into it. I believe my problem is read.  I tried to reinstall xp again to find my dvd drive scratched / etched rings into the disc.  If only i could boot off of a thumb drive. I could still run Ubuntu, and I wouldn't have any problems short of games and select other programs. But; alas, my board will not boot off of usb. When I get a drive I will post back. But I am a poor college student, and Christmas is around the corner.

---

### Post by oldfred on 2009-12-10
I have not had to do it but you can use a floppy to boot into your USB with supergrub. You also should be able to add boot entries to grub to use your USB install to boot, it just is not directly booting the USB.

This is one way except you will have to have the grub entries on your hard drive refering to the USB:
[B][FONT=Arial][SIZE=1]HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2  
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)[/SIZE][/FONT]
[/B]

---

### Post by buddah1620 on 2009-12-16
So I was talking to a customer of mine last week about my problems.  And he was kind enough to donate an old dvd drive to me. I installed it, and was going through the motions of installing Ubuntu.  And when I got to the final steps I noticed that the boot loader was by default installing to (hd0). Should I change the boot loader install to the drive I am installing the OS? Which is /dev/sda. Or should I install to the partition of the Ubuntu install which is /dev/sda1.

---

### Post by oldfred on 2009-12-16
Hd0 is sda. You want to install to the MBR of the drive that boots first in BIOS which may not be sda or hd0. You do not want to install to sda1 the partition unless you plan on chainbooting where you have many operating systems and want each to have its own boot menu (advanced users).

Grub2 has a minor bug where it boots slow if grub is in one drive and Ubuntu is in another drive. I had Ubuntu in sdc and grub in sda and it took an extra 20-30 secs to get the grub menu. So I installed grub2 to sdc and in BIOS set it first, now grub is much faster. But my drive order of sda, sdb, & sdc has not changed.

---

### Post by buddah1620 on 2009-12-16
When I am at the disk manager / partitioner portion of the install, and it asks me where i want to install ubuntu, their is not hd0 option. Their is: sda, sdb, and sdc. sda is where I am installing ubuntu, so shouldn't the boot loader / grub be installed to sda?

---

### Post by buddah1620 on 2009-12-19
can one bump one's own thread? Should I install Grub onto sda or not?

---

### Post by oldfred on 2009-12-19
If in BIOS you have selected sda to be the boot drive then you want to install grub to sda so it will boot. 

On my machine I installed to sdc (my640GB) and in BIOS changed the boot drive to be the 640GB drive. I also have 2 160GB drives and I cannot tell which is which in BIOS. So if I want to boot from one of the 160GB drives, I try one if it works great if not try the other.

---

### Post by buddah1620 on 2009-12-19
I have not seen the option in my bios menu to select a drive to boot from. I'll try to contact asus

---

### Post by buddah1620 on 2009-12-29
My wife was in a near fatal accident almost a week ago.  I haven't touched my computer since, and probably wont for some time.  I will reply back when I get pertinent information about my computer. Thanks to all.

---

### Post by buddah1620 on 2010-01-17
So It has been a crazy holidays for me to say the least.  I finally got my computer to stably boot into Ubuntu 9.10 I think my biggest error in this ordeal was not throughly Google-ing. The "MBR  error 1" seems to be common in Acronis users (This is probably because Acronis users move images around different hard drives and thus have a more common occurrence of similar errors.).  Acronis has MBR error fix software available as an ISO image which can be downloaded and documentation for it (but I didn't see it).  What was easier for me was to use an old xp home disc I don't have rights to.  I unplugged all my sata drives except the 500 GB (the one I want to be the system disc).  Boot into the XP disc and instead of installing, go into the recovery console.  When the command prompt comes up type "fixmbr". It will give you a warning about it. I typed "y" and hit enter. Less than a second and it says MBR fixed and I type "exit".  The compute Re-boots. I Boot into Ubuntu and re-install everything.  Boot loader installs to hd(0,0).  Yea! just need to update Ubuntu now.  One question now though... This is the first computer that I have ever had that only boots into Ubuntu and not a dual boot into window$ and Ubuntu. So should I not be suprised that the grub options window does not pop up while booting?  The screed I am referring to in the black and white screen that asks you if you want windows, Ubuntu, memtest, ect.

---

### Post by oldfred on 2010-01-17
It seems to be something new with Karmic/grub2 that if it sees only one operating system it boots without showing the menu. If you need to menu to boot an older kernel or test memory you can hold down the shift key right after the BIOS.

If you add drives after installing to just one, you will probably have to do some updates to grub2 to get it to update the device.map to see the additional drives.

I hope your wife is recovering well. And good luck with Ubuntu.

---

### Post by buddah1620 on 2010-01-20
Thank you sir.  I am still running Karmic stable.  I had shut down and added the other drives.  No update was necessary on grubs part.  It bootup fine with no problems.  Now I just need a way to get my old data from my old partitions.  I cant boot into acronis, I don't know to what fault that is.  My plan now is to use Virtual box and emulate windows(I was going to do this anyways for windows only programs).  Install Acronis to virtual windows and restore images temporary to a temporary partition.  Transfer data. Delete temporary partitions. Sound feasible?

---

### Post by buddah1620 on 2010-01-22
The reason I couldn't boot into acronis is because of an antiquated optical drive that was donated to me.  I was able o salvage another drive from a computer that was put out of it's misery years ago.  Now I need to save up for a modern dvd drive so I can install M$ if it is needed in the future in virtual box.

My idea for restoring the image was successful.  I restored it to a logical partition, took what I needed, and am in the process of formatting that drive and re-naming it.  Since I my problems that caused me to post have been resolved I am labeling this post as solved.  Long story short: if you get a "MBR ERROR 1" after bios post; your mbr is screwed.  You need: either the Arconis software to fix it, or to run microsoft recovery console and type "fixmbr". 
Will you have to re-install your OS? I don't know. But since you are screwed if you don't you don't have much of a choice.

---

