---
title: "'grub_xputs' not found after upgrade"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by Holman on 2010-10-14
So today I decided I would upgrade my computer to 10.10 from 10.04. Everything was going great until after the restart. As the title suggests, when booting I get the message "error: the symbol 'grub_xputs' not found." and a grub rescue shell.

From this shell, is there anyway that I can load Ubuntu so I can reinstall grub, or do whatever needs to be done? Unfortunately booting to a livecd does not seem to be much of an option. Any help would be greatly appreciated, thanks!

EDIT: After not finding anything I eventually gave up and took a dvd-rom drive out of another computer to get into the live cd and was able to solve the problem through there using kansasnoob's linked solution, so I guess my problem is solved, but only by changing the conditions of the problem.

---

### Post by kansasnoob on 2010-10-14
I think this should get you straightened out:

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Holman on 2010-10-14
Thanks, but unfortunately the steps I see there are using the live CD. If you know of a way to boot into ubuntu with only the grub recovery shell, that is really what I need.

---

### Post by mikebravo on 2010-10-14
Yeah, me too. 64 bit 10.4 was doing fine but when I upgraded to 10.10 it pooched the grub. Might have something to do with having a raid0 setup on 10.4 with manually defined partitions and me being too much of a noob to know what to do now. It said
error: fd0 read error
error: the symbol 'grub_xputs' not found
grub rescue>_ 

Any way, after a few hours of futzing around I got a bad attitude about the whole thing. I am going to do a clean install of 32bit 10.10 and make it just plain vanilla as I possibly can.  What do you want to bet the next upgrade will find something brand new to screw up?

---

### Post by Holman on 2010-10-15
So I've found a little more information, but I still am stuck, and all the posts I find about this issue run into the same brick wall as me in the grub rescue shell.
That is to follow this procedure:
set root=(hd0,5)
set prefix=(hd0,5)/boot/grub
insmod linux
but that is where it fails and it throw up the 'grub_xputs' not found error again and I am not sure how to precede or even where or what that symbol is.

It seems that most of the time people have the ability to use a live CD, but if not do I have any chance at recovery?

---

### Post by mikebravo on 2010-10-15
I went to bootinfoscript.sourceforge.net and ran it. I am posting results.txt below, not to get help but to show those who know more than I do how badly a simple thing can get screwed up. 

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #4 for /boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks for (md0)/boot/grub.

sda1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb2: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  Unknown
    Boot sector info:  

sdb3: _________________________________________________________________________

    File system:       linux_raid_member
    Boot sector type:  -
    Boot sector info:  

sdb4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1          97,707,330   156,296,384    58,589,055  fd Linux raid autodetect
/dev/sda2          87,939,810    97,707,329     9,767,520  fd Linux raid autodetect
/dev/sda3           3,951,990    87,939,809    83,987,820  fd Linux raid autodetect
/dev/sda4    *             63     3,951,989     3,951,927  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *     97,707,330   156,296,384    58,589,055  fd Linux raid autodetect
/dev/sdb2          87,939,810    97,707,329     9,767,520  fd Linux raid autodetect
/dev/sdb3           3,951,990    87,939,809    83,987,820  fd Linux raid autodetect
/dev/sdb4                  63     3,951,989     3,951,927  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        c11dca9e-3a5d-86de-0efa-063447264cb6   linux_raid_member                               
/dev/sda2        ec0bce47-be3f-cb43-6697-cc1132d3f8d5   linux_raid_member                               
/dev/sda3        a2cdc655-b0d5-bea7-5102-83ea10aa19da   linux_raid_member                               
/dev/sda4        e5370981-4018-474f-bbdc-0839f23b6f44   ext4                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        c11dca9e-3a5d-86de-0efa-063447264cb6   linux_raid_member                               
/dev/sdb2        ec0bce47-be3f-cb43-6697-cc1132d3f8d5   linux_raid_member                               
/dev/sdb3        a2cdc655-b0d5-bea7-5102-83ea10aa19da   linux_raid_member                               
/dev/sdb4        d7f22d1a-419f-4e35-8f7a-c70cd97b3348   ext4                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/mapper/no: No such file or directory
error: raid: No such file or directory
error: sets: No such file or directory

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda4/grub/grub.cfg: =============================

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
insmod raid
insmod mdraid
insmod ext2
set root=(md0)
search --no-floppy --fs-uuid --set 286d289c-913f-4447-825a-cb9741283a9e
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
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set e5370981-4018-474f-bbdc-0839f23b6f44
	linux	/vmlinuz-2.6.31-14-generic root=UUID=286d289c-913f-4447-825a-cb9741283a9e ro   quiet splash
	initrd	/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,4)
	search --no-floppy --fs-uuid --set e5370981-4018-474f-bbdc-0839f23b6f44
	linux	/vmlinuz-2.6.31-14-generic root=UUID=286d289c-913f-4447-825a-cb9741283a9e ro single 
	initrd	/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/memtest86+.bin console=ttyS0,115200n8
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

=================== sda4: Location of files loaded by Grub: ===================


    .1GB: boot/grub/core.img
    .1GB: grub/core.img
    .1GB: grub/grub.cfg
    .1GB: initrd.img-2.6.31-14-generic
    .1GB: vmlinuz-2.6.31-14-generic
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb2

00000000  9e 9f 9b 91 58 7f 00 00  ae 9f 9b 91 58 7f 00 00  |....X.......X...|
00000010  be 9f 9b 91 58 7f 00 00  ce 9f 9b 91 58 7f 00 00  |....X.......X...|
00000020  de 9f 9b 91 58 7f 00 00  ee 9f 9b 91 58 7f 00 00  |....X.......X...|
00000030  fe 9f 9b 91 58 7f 00 00  0e a0 9b 91 58 7f 00 00  |....X.......X...|
00000040  1e a0 9b 91 58 7f 00 00  2e a0 9b 91 58 7f 00 00  |....X.......X...|
00000050  3e a0 9b 91 58 7f 00 00  4e a0 9b 91 58 7f 00 00  |>...X...N...X...|
00000060  5e a0 9b 91 58 7f 00 00  6e a0 9b 91 58 7f 00 00  |^...X...n...X...|
00000070  7e a0 9b 91 58 7f 00 00  8e a0 9b 91 58 7f 00 00  |~...X.......X...|
00000080  9e a0 9b 91 58 7f 00 00  ae a0 9b 91 58 7f 00 00  |....X.......X...|
00000090  be a0 9b 91 58 7f 00 00  ce a0 9b 91 58 7f 00 00  |....X.......X...|
000000a0  de a0 9b 91 58 7f 00 00  ee a0 9b 91 58 7f 00 00  |....X.......X...|
000000b0  fe a0 9b 91 58 7f 00 00  0e a1 9b 91 58 7f 00 00  |....X.......X...|
000000c0  1e a1 9b 91 58 7f 00 00  2e a1 9b 91 58 7f 00 00  |....X.......X...|
000000d0  00 06 52 91 58 7f 00 00  4e a1 9b 91 58 7f 00 00  |..R.X...N...X...|
000000e0  5e a1 9b 91 58 7f 00 00  6e a1 9b 91 58 7f 00 00  |^...X...n...X...|
000000f0  00 5d 4d 91 58 7f 00 00  8e a1 9b 91 58 7f 00 00  |.]M.X.......X...|
00000100  9e a1 9b 91 58 7f 00 00  ae a1 9b 91 58 7f 00 00  |....X.......X...|
00000110  be a1 9b 91 58 7f 00 00  ce a1 9b 91 58 7f 00 00  |....X.......X...|
00000120  de a1 9b 91 58 7f 00 00  50 36 24 92 58 7f 00 00  |....X...P6$.X...|
00000130  fe a1 9b 91 58 7f 00 00  0e a2 9b 91 58 7f 00 00  |....X.......X...|
00000140  1e a2 9b 91 58 7f 00 00  2e a2 9b 91 58 7f 00 00  |....X.......X...|
00000150  3e a2 9b 91 58 7f 00 00  4e a2 9b 91 58 7f 00 00  |>...X...N...X...|
00000160  5e a2 9b 91 58 7f 00 00  6e a2 9b 91 58 7f 00 00  |^...X...n...X...|
00000170  7e a2 9b 91 58 7f 00 00  8e a2 9b 91 58 7f 00 00  |~...X.......X...|
00000180  c0 43 4d 91 58 7f 00 00  ae a2 9b 91 58 7f 00 00  |.CM.X.......X...|
00000190  be a2 9b 91 58 7f 00 00  ce a2 9b 91 58 7f 00 00  |....X.......X...|
000001a0  90 f4 54 91 58 7f 00 00  ee a2 9b 91 58 7f 00 00  |..T.X.......X...|
000001b0  fe a2 9b 91 58 7f 00 00  0e a3 9b 91 58 7f 00 00  |....X.......X...|
000001c0  1e a3 9b 91 58 7f 00 00  30 7b 50 91 58 7f 00 00  |....X...0{P.X...|
000001d0  3e a3 9b 91 58 7f 00 00  4e a3 9b 91 58 7f 00 00  |>...X...N...X...|
000001e0  5e a3 9b 91 58 7f 00 00  6e a3 9b 91 58 7f 00 00  |^...X...n...X...|
000001f0  7e a3 9b 91 58 7f 00 00  8e a3 9b 91 58 7f 00 00  |~...X.......X...|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

no raid sets 
=============================== StdErr Messages: ===============================

ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "sil_afaeeiafagcb"
ERROR: no RAID set found
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "sil_afaeeiafagcb"
ERROR: only one argument allowed for this option
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "sil_afaeeiafagcb"
ERROR: no RAID set found
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "sil_afaeeiafagcb"
ERROR: no RAID set found
ERROR: sil: only 3/4 metadata areas found on /dev/sda, electing...
ERROR: sil: RAID type 253 not supported
ERROR: adding /dev/sda to RAID set "sil_afaeeiafagcb"
ERROR: only one argument allowed for this option

```
------------------------------------------------------
Pretty bad huh? It had been perfect before update.

Did things like suggested at [www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)  and things suggested on these forums. Problem is most of the suggestions were slanted toward simple systems or dual booters. I think this time I will just throw in a 10.10 32bit CD and let it do its thing. It won't be the system I want, but it will be a system that works.

---

### Post by drs305 on 2010-10-15
Talking with the devs about this - they say the 'xputs' error is the result of an incomplete grub installation and that a reinstall of Grub is necessary.

If you can't use a Live CD but have a way to get a copy of the ISO image on a drive that the computer can see I may have an answer. 

I spent about 4 hours today playing with Grub and the rescue mode and finally got the right set of commands to boot the ISO from a rescue prompt. (I'm pretty slow).

If you tell me the designation of the partition with the ISO and the ISO filename we can test it out. I've got the guide mostly written but need some users to test it.

---

