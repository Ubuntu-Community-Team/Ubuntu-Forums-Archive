---
title: "Can't See partitions during installations"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by mrcreativity on 2010-10-11
I'm running ubuntu 10.04 with windows 7 in dual boot.

When running the partitioning software during installation of Ubuntu 10.10, i dont see my parition in the partition manager. 

It just shows me /dev/sda, and no partitions.

I have about 5 partitions, 3 for windows and 2 for linux but they dont show up.

Any help would be appreciated.

---

### Post by skyjacker on 2010-10-11
I can't remember the reason, but you can only have four (4) partitions on a hard drive... Maybe do a search in this forum and you can find out why.

---

### Post by mrcreativity on 2010-10-11
I've never had problems before no matter what version of linux i installed. Ubuntu, kubuntu from 6.xx versions.

This is the first time this is happening to me.

---

### Post by Mark Phelps on 2010-10-11
Sorry, all I can suggest is using the Alternate CD.  

I also run multi-boot systems and have had problems in the past where the Desktop PC partitioner could NOT see the partitions, but the Alternate CD partitioner COULD.

And yeah, I KNOW they are supposed to be the same partitioner -- but that's been my experience.

---

### Post by srs5694 on 2010-10-11
See [my Web page on this problem.](http://www.rodsbooks.com/missing-parts/index.html) If you need more help, please post the output of "sudo fdisk -lu /dev/sda", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.

Side note: skyjacker is only partially correct; the Master Boot Record (MBR) partitioning system used on most PCs supports up to four *primary* partitions. It's possible to set aside one of these as an *extended* partition, which can then hold an arbitrary number of *logical* partitions. The end result is that you can have as many partitions as you like. (The theoretical limit is on the order of two billion partitions.) There are also partitioning systems other than MBR that support more partitions in a less convoluted way.

---

### Post by mrcreativity on 2010-10-11
i dont see why i should go through all of the instructions posted above when every ubuntu installation till now worked perfectly.

this is a real bother, and it looks like im going to be stuck with 10.04. 
Not that 10.04 isnt good. its the best ubuntu i've used till date.

thanks for all ur help anyway.

---

### Post by Davor &#268;engija on 2010-10-12
> **mrcreativity said:**
> i dont see why i should go through all of the instructions posted above when every ubuntu installation till now worked perfectly.

this is a real bother, and it looks like im going to be stuck with 10.04. 
Not that 10.04 isnt good. its the best ubuntu i've used till date.

thanks for all ur help anyway.

I went through the above mentioned process since I had some issues with Kubuntu 10.4 and needed upgrade. It is obvious that the described method can be quite dangerous, if you're not careful enough, but still, it's really simple, and works.

I had the same problem as you, and after adjusting my disk partition table, new system installed without any problem.

I suspect that Kubuntu 10.4 installation procedure (partitioning part) messed up my disk, and the above described procedure finally solved those issues.

---

### Post by Davor &#268;engija on 2010-10-12
> **srs5694 said:**
> See [my Web page on this problem.]("http://www.rodsbooks.com/missing-parts/index.html") If you need more help, please post the output of "sudo fdisk -lu /dev/sda", preferably between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility.


Thanks for this webpage, it really solved my disk partitioning issues!

---

### Post by srs5694 on 2010-10-12
> **mrcreativity said:**
> i dont see why i should go through all of the instructions posted above when every ubuntu installation till now worked perfectly.

You shouldn't *have to,* in the sense that it would be unnecessary in an ideal world; but if the problem is what I suspect it is, it's a result of a bug in a partitioning tool along with a bug/limitation in another partitioning tool (namely libparted, upon which the Ubuntu installer relies). When bugs are involved, diagnosis and workarounds are required. This is a nuissance, but if you want the problem solved, it must be done.

FWIW, if the problem is what I suspect it is, you're likely to run into it sooner or later anyhow, since your partition table is damaged. The installer side of the problem existed prior to 10.10, so if you installed 10.04, chances are something has altered your partition table in the meantime, accidentally damaging it. The Linux kernel doesn't care about this particular problem, but some tools obviously do.

---

### Post by mrcreativity on 2010-10-12
You think my partition table is damaged? I'll give the 10.04 installer a try and see where it gets me. If it shows my partitions as it supposed to, I'll try the method mentioned previously.

Thanks for the help.

---

### Post by VMC on 2010-10-12
> **mrcreativity said:**
> You think my partition table is damaged? I'll give the 10.04 installer a try and see where it gets me. If it shows my partitions as it supposed to, I'll try the method mentioned previously.

Thanks for the help.

Boot up using the livecd and type ```
sudo fdisk -l
```

That should give us your partition tables.

---

### Post by srs5694 on 2010-10-12
> **VMC said:**
> Boot up using the livecd and type ```
sudo fdisk -l
```That should give us your partition tables.

It must be "sudo fdisk -lu". Note the "u"; without that, fdisk will report values in cylinders, which are insufficiently precise to spot certain types of problems, including the one I suspect may be in play here.

---

### Post by VMC on 2010-10-12
> **srs5694 said:**
> It must be "sudo fdisk -lu". Note the "u"; without that, fdisk will report values in cylinders, which are insufficiently precise to spot certain types of problems, including the one I suspect may be in play here.

> -l     List the partition tables for the  specified  devices  and  then exit.
       If no devices are given, those mentioned in /proc/partitions (if that exists) are used.


 -u     When listing partition tables, give sizes in sectors instead  of cylinders.

The only difference is U gives sectors instead of cylinders!

---

### Post by srs5694 on 2010-10-12
> **VMC said:**
> The only difference is U gives sectors instead of cylinders!

That's precisely what I said; but contrary to what you seem to think, it's a very important distinction. Check [my Web page on this problem.](http://www.rodsbooks.com/missing-parts/index.html) One common cause is that an extended partition ends beyond the end of the disk. It could end just one sector past the end of the disk and the problem will creep in. A one-sector difference, however, is unlikely to be an obvious problem when you use cylinder notation; since cylinders contain many sectors, the one-sector deviation is likely to be rounded out of the report when you view the partition table using cylinders. Similarly, if partitions don't begin and end on cylinder boundaries (which is increasingly common these days, since Windows Vista and later use 1 MiB partition alignment rather than cylinder partition alignment), one partition can end on the same cylinder as another one begins. This can look like overlap when it's not; or if you ignore one-cylinder overlaps like this, you could be overlooking a real problem if the partitions in fact overlap slightly, but not enough to turn up as more than one cylinder.

---

### Post by VMC on 2010-10-12
> **srs5694 said:**
> That's precisely what I said; but contrary to what you seem to think, it's a very important distinction. Check [url=http://www.rodsbooks.com/missing-parts/index.html]....

Why are you promoting your web page instead of just keeping the problem local. Your assuming that the OP's sectors are mis-aligned, when he hasn't even showed us what they are.

I don't care if it's "-l" or "-lu", I would just like to see his partition table to make further recommendations.

edit: Actually in re-reading this topic, I missed your suggestion of "fdisk -lu", since it was embedded in your comments. Usually its suggested that any command message be within code tags. If it were, I wouln't have responded at all.

That being said the OP, in post#6 felt he didn't need to bother with the instructions. I'm not sure if he was referring to your web page or something else.

I think a better solution would be to use the boot_info_script so we can see his entire boot process. Since the OP (mrcreativity),  hasn't responded anymore, maybe he found his solution.

---

### Post by srs5694 on 2010-10-12
> **VMC said:**
> Why are you promoting your web page instead of just keeping the problem local. Your assuming that the OP's sectors are mis-aligned, when he hasn't even showed us what they are.

The Web page includes an extended description of the source of the problem and possible solutions to it. It saves typing to refer to a ready-made Web page rather than rewrite the whole thing with every message.

I am not *assuming* that the OP's partitions overlap or extend beyond the end of the disk; I asked specifically for the "fdisk -lu" output to diagnose the issue. That said, I'd say that 80-90% of the time when I see a post with these symptoms, the cause turns out to be overlapping or too-large partitions.

Also, this is *not* an issue of partition alignment, except insofar as the difference between cylinder and MiB alignment might be interacting to create the bug and MiB alignment can make it harder to interpret the fdisk output if it's set to display cylinder values.

> I don't care if it's "-l" or "-lu", I would just like to see his partition table to make further recommendations.

My point is that "fdisk -l" *produces imprecise output* -- imprecise enough that it's not likely to be diagnostic. I've seen several cases in the past where somebody has posted that output, which doesn't show any really obvious problems; but when "fdisk -lu" output is posted, the problem becomes obvious. There's no point in the OP posting "fdisk -l" output when "fdisk -lu" is just as easy and will be more precise and more likely to show what's needed for further diagnosis.

FWIW, this problem is very common -- that's why I wrote my Web page about it. There's at least one utility out there that's producing these broken extended partitions left and right. I don't know what utility is doing this, though.

---

### Post by mrcreativity on 2010-10-12
I'm still around and still havent found a solution. The instructions on that web page are kinda scary but i really have no problems following any kind of instructions. 
Thats the exact reason i've been registered on the ubuntu forums for years now, and have followed eveyr kind of instruction to any problem to the dot without ever having to make a post in the forums. I google, read, follow, and stuff just works thanks to the great wikis people have made, that too for free.

Now, as for my problem. fdisk -l outputs this:


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdca88d80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        6834    53357061    7  HPFS/NTFS
/dev/sda3            6835       23470   133628667    7  HPFS/NTFS
/dev/sda4           23471       24322     6836224+   f  W95 Ext'd (LBA)
/dev/sda5           23471       23532      488448   82  Linux swap / Solaris
/dev/sda6           23532       24322     6347776   83  Linux

Disk /dev/sdb: 4089 MB, 4089445376 bytes
126 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 7812 * 512 = 3999744 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed9df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1022     3991901    b  W95 FAT32



and fdisk -lu outputs this:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdca88d80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *     3074088   109788209    53357061    7  HPFS/NTFS
/dev/sda3       109788216   377045549   133628667    7  HPFS/NTFS
/dev/sda4       377049087   390721535     6836224+   f  W95 Ext'd (LBA)
/dev/sda5       377049088   378025983      488448   82  Linux swap / Solaris
/dev/sda6       378025984   390721535     6347776   83  Linux

Disk /dev/sdb: 4089 MB, 4089445376 bytes
126 heads, 62 sectors/track, 1022 cylinders, total 7987198 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ed9df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7983863     3991901    b  W95 FAT32


thanks once again.

---

### Post by VMC on 2010-10-13
mrcreativity, The above looks fine. Now if you don't mind, can you download [[COLOR="Blue"]**Boot_Info_Script**[/COLOR]]("http://sourceforge.net/projects/bootinfoscript/") . And run the script.

 Then output the RESULTS.txt file back here within CODES please. 
That will give us a better picture of how your system boots and where your MBR resides.

---

### Post by mrcreativity on 2010-10-13
what exactly do u mean by within Codes? do i attach the text file? or copy and paste the content within quotes?

---

### Post by mrcreativity on 2010-10-13
>                 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,088   109,788,209   106,714,122   7 HPFS/NTFS
/dev/sda3         109,788,216   377,045,549   267,257,334   7 HPFS/NTFS
/dev/sda4         377,049,087   390,721,535    13,672,449   f W95 Ext d (LBA)
/dev/sda5         377,049,088   378,025,983       976,896  82 Linux swap / Solaris
/dev/sda6         378,025,984   390,721,535    12,695,552  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        2E30C99030C96007                       ntfs       WinRE                         
/dev/sda2        DE32B30832B2E4A5                       ntfs       Seven                         
/dev/sda3        3634CE7834CE3A9F                       ntfs       Backup                        
/dev/sda4: PTTYPE="dos" 
/dev/sda5        8a524e4b-9fa5-49ca-bb4b-1fda32fe5a6e   swap                                     
/dev/sda6        ed3331df-8a1b-472a-becf-516eea6354d2   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)
/dev/sda3        /media/Backup            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
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
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=ed3331df-8a1b-472a-becf-516eea6354d2 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=ed3331df-8a1b-472a-becf-516eea6354d2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
	insmod ntfs
	set root='(hd0,2)'
	search --no-floppy --fs-uuid --set 284a1b264a1aeff4
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ed3331df-8a1b-472a-becf-516eea6354d2 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=8a524e4b-9fa5-49ca-bb4b-1fda32fe5a6e none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


 198.2GB: boot/grub/core.img
 196.3GB: boot/grub/grub.cfg
 198.7GB: boot/initrd.img-2.6.32-25-generic
 198.6GB: boot/vmlinuz-2.6.32-25-generic
 198.7GB: initrd.img
 198.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda4

00000000  5a ab 4c b3 1e b9 e7 8c  87 33 e8 d3 07 70 3c 40  |Z.L......3...p<@|
00000010  43 31 cc 70 ef b4 02 81  46 fc fd 3b 09 42 ae ee  |C1.p....F..;.B..|
00000020  8c 81 fb e8 c1 da 1d df  1d ba 66 a4 65 c8 a6 39  |..........f.e..9|
00000030  e8 c2 12 5d a0 38 9a 30  cd b3 0e 92 5a 20 e5 1e  |...].8.0....Z ..|
00000040  82 e0 a0 15 18 a0 15 0a  00 ae 80 51 20 df 9f a0  |...........Q ...|
00000050  7e ba 57 66 6c bb 1d 91  8d 95 67 aa be ad 1d bb  |~.Wfl.....g.....|
00000060  bb 4f bf 30 93 15 a3 2e  41 14 9b 6b 35 fc 9b 77  |.O.0....A..k5..w|
00000070  34 e4 c2 49 ca b5 76 73  ca b0 39 52 4d 1c 87 50  |4..I..vs..9RM..P|
00000080  0a dd 88 0a 85 1e 94 6c  50 ca 20 21 6f d5 1d b6  |.......lP. !o...|
00000090  d9 10 a4 be 76 4a 0a 45  93 f5 2d c7 f8 8b d4 2b  |....vJ.E..-....+|
000000a0  65 7e 90 f5 2b 25 69 30  1e 09 67 83 76 bf d0 99  |e~..+%i0..g.v...|
000000b0  6f eb 3b cf f0 d8 ad bd  15 d4 78 37 82 8a 1f 16  |o.;.......x7....|
000000c0  90 fb 43 5b 21 e4 3f bb  ff 00 ae 5b 0c 34 43 69  |..C[!.?....[.4Ci|
000000d0  2a d9 14 da 24 79 86 68  1d 29 b9 91 3a 27 40 4c  |*...$y.h.)..:'@L|
000000e0  64 2e bc d6 a7 37 4c 19  af 9c a1 f2 f5 06 de 6b  |d....7L........k|
000000f0  e7 6a 2f 5f 10 ec 98 81  38 d6 8d f4 5b 1b e4 27  |.j/_....8...[..'|
00000100  66 d9 52 5f 25 25 11 88  22 92 5e ad 6a 3a 5d a1  |f.R_%%..".^.j:].|
00000110  10 66 03 36 cc 82 59 b9  c3 89 45 b8 8e 42 a8 ea  |.f.6..Y...E..B..|
00000120  6c c5 54 7b ed 4a 60 50  a2 01 ff 00 e6 06 bb 4b  |l.T{.J`P.......K|
00000130  c7 6a 2a 54 1d 92 2c a7  e8 99 7b 9b 47 6f dd 84  |.j*T..,...{.Go..|
00000140  a0 76 e9 10 78 f3 2e 6a  79 0c f3 88 87 8e 79 94  |.v..x..jy.....y.|
00000150  8c cb 40 06 3e 7a c8 2d  23 20 7d 5b 0f 00 1c 24  |..@.>z.-# }[...$|
00000160  ac 71 ba da df 38 5b e5  c7 b4 97 6a 36 cf 64 68  |.q...8[....j6.dh|
00000170  3e cd 61 fb bb 9b f4 c9  4a cb cf 3a ea c3 0c c3  |>.a.....J..:....|
00000180  3e b1 0a 21 34 cf bb 93  97 39 8d d5 f4 4c 14 42  |>..!4....9...L.B|
00000190  50 0a a1 83 a6 d4 a6 13  85 83 f6 c3 e9 b3 ec d4  |P...............|
000001a0  03 c1 d9 9c 29 cf 54 b4  29 fb b2 bd 9c f6 e9 92  |....).T.).......|
000001b0  d6 69 cc 2e 75 d7 e6 c4  a3 32 cc 0e d0 46 00 fe  |.i..u....2...F..|
000001c0  ff ff 82 fe ff ff 01 00  00 00 00 e8 0e 00 00 fe  |................|
000001d0  ff ff 05 fe ff ff c2 e7  0e 00 3f b8 c1 00 00 00  |..........?.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


This is what the text file looks like.I hope it's helpful.

---

### Post by VMC on 2010-10-13
mrcreativity, In the future use CODE tags, not QUOTE tags. Look below to see the difference. Much smaller inside comments.

Now boot up again using livecd, and this time select Manual Partitioning just to see if it recognizes your SDA partitions. You can then back out of it.

===CODE TAGS===
```
Boot Info Script 0.55 dated February 15th, 2010 

============================= Boot Info Summary: ==============================

=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
partition #6 for /boot/grub.

sda1: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

sda2: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: Windows 7
Boot files/dirs: /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________ _______________________

File system: ntfs
Boot sector type: Windows Vista/7
Boot sector info: No errors found in the Boot Parameter Block.
Operating System: 
Boot files/dirs: 

sda4: __________________________________________________ _______________________

File system: Extended Partition
Boot sector type: Unknown
Boot sector info: 

sda5: __________________________________________________ _______________________

File system: swap
Boot sector type: -
Boot sector info: 

sda6: __________________________________________________ _______________________

File system: ext4
Boot sector type: -
Boot sector info: 
Operating System: Ubuntu 10.04.1 LTS
Boot files/dirs: /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________ ___

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition Boot Start End Size Id System

/dev/sda1 2,048 3,074,047 3,072,000 27 Hidden HPFS/NTFS
/dev/sda2 * 3,074,088 109,788,209 106,714,122 7 HPFS/NTFS
/dev/sda3 109,788,216 377,045,549 267,257,334 7 HPFS/NTFS
/dev/sda4 377,049,087 390,721,535 13,672,449 f W95 Ext d (LBA)
/dev/sda5 377,049,088 378,025,983 976,896 82 Linux swap / Solaris
/dev/sda6 378,025,984 390,721,535 12,695,552 83 Linux


blkid -c /dev/null: __________________________________________________ __________

Device UUID TYPE LABEL 

/dev/sda1 2E30C99030C96007 ntfs WinRE 
/dev/sda2 DE32B30832B2E4A5 ntfs Seven 
/dev/sda3 3634CE7834CE3A9F ntfs Backup 
/dev/sda4: PTTYPE="dos" 
/dev/sda5 8a524e4b-9fa5-49ca-bb4b-1fda32fe5a6e swap 
/dev/sda6 ed3331df-8a1b-472a-becf-516eea6354d2 ext4 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev output: ===========================

Device Mount_Point Type Options

/dev/sda6 / ext4 (rw,errors=remount-ro)
/dev/sda3 /media/Backup fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="4"
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
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
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
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
set locale_dir=($root)/boot/grub/locale
set lang=
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=ed3331df-8a1b-472a-becf-516eea6354d2 ro quiet splash
initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
echo	'Loading Linux 2.6.32-25-generic ...'
linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=ed3331df-8a1b-472a-becf-516eea6354d2 ro single 
echo	'Loading initial ramdisk ...'
initrd	/boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set ed3331df-8a1b-472a-becf-516eea6354d2
linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda2)" {
insmod ntfs
set root='(hd0,2)'
search --no-floppy --fs-uuid --set 284a1b264a1aeff4
chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=ed3331df-8a1b-472a-becf-516eea6354d2 / ext4 errors=remount-ro 0 1
# swap was on /dev/sda6 during installation
UUID=8a524e4b-9fa5-49ca-bb4b-1fda32fe5a6e none swap sw 0 0

=================== sda6: Location of files loaded by Grub: ===================


198.2GB: boot/grub/core.img
196.3GB: boot/grub/grub.cfg
198.7GB: boot/initrd.img-2.6.32-25-generic
198.6GB: boot/vmlinuz-2.6.32-25-generic
198.7GB: initrd.img
198.6GB: vmlinuz
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader on sda4

00000000 5a ab 4c b3 1e b9 e7 8c 87 33 e8 d3 07 70 3c 40 |Z.L......3...p<@|
00000010 43 31 cc 70 ef b4 02 81 46 fc fd 3b 09 42 ae ee |C1.p....F..;.B..|
00000020 8c 81 fb e8 c1 da 1d df 1d ba 66 a4 65 c8 a6 39 |..........f.e..9|
00000030 e8 c2 12 5d a0 38 9a 30 cd b3 0e 92 5a 20 e5 1e |...].8.0....Z ..|
00000040 82 e0 a0 15 18 a0 15 0a 00 ae 80 51 20 df 9f a0 |...........Q ...|
00000050 7e ba 57 66 6c bb 1d 91 8d 95 67 aa be ad 1d bb |~.Wfl.....g.....|
00000060 bb 4f bf 30 93 15 a3 2e 41 14 9b 6b 35 fc 9b 77 |.O.0....A..k5..w|
00000070 34 e4 c2 49 ca b5 76 73 ca b0 39 52 4d 1c 87 50 |4..I..vs..9RM..P|
00000080 0a dd 88 0a 85 1e 94 6c 50 ca 20 21 6f d5 1d b6 |.......lP. !o...|
00000090 d9 10 a4 be 76 4a 0a 45 93 f5 2d c7 f8 8b d4 2b |....vJ.E..-....+|
000000a0 65 7e 90 f5 2b 25 69 30 1e 09 67 83 76 bf d0 99 |e~..+%i0..g.v...|
000000b0 6f eb 3b cf f0 d8 ad bd 15 d4 78 37 82 8a 1f 16 |o.;.......x7....|
000000c0 90 fb 43 5b 21 e4 3f bb ff 00 ae 5b 0c 34 43 69 |..C[!.?....[.4Ci|
000000d0 2a d9 14 da 24 79 86 68 1d 29 b9 91 3a 27 40 4c |*...$y.h.)..:'@L|
000000e0 64 2e bc d6 a7 37 4c 19 af 9c a1 f2 f5 06 de 6b |d....7L........k|
000000f0 e7 6a 2f 5f 10 ec 98 81 38 d6 8d f4 5b 1b e4 27 |.j/_....8...[..'|
00000100 66 d9 52 5f 25 25 11 88 22 92 5e ad 6a 3a 5d a1 |f.R_%%..".^.j:].|
00000110 10 66 03 36 cc 82 59 b9 c3 89 45 b8 8e 42 a8 ea |.f.6..Y...E..B..|
00000120 6c c5 54 7b ed 4a 60 50 a2 01 ff 00 e6 06 bb 4b |l.T{.J`P.......K|
00000130 c7 6a 2a 54 1d 92 2c a7 e8 99 7b 9b 47 6f dd 84 |.j*T..,...{.Go..|
00000140 a0 76 e9 10 78 f3 2e 6a 79 0c f3 88 87 8e 79 94 |.v..x..jy.....y.|
00000150 8c cb 40 06 3e 7a c8 2d 23 20 7d 5b 0f 00 1c 24 |..@.>z.-# }[...$|
00000160 ac 71 ba da df 38 5b e5 c7 b4 97 6a 36 cf 64 68 |.q...8[....j6.dh|
00000170 3e cd 61 fb bb 9b f4 c9 4a cb cf 3a ea c3 0c c3 |>.a.....J..:....|
00000180 3e b1 0a 21 34 cf bb 93 97 39 8d d5 f4 4c 14 42 |>..!4....9...L.B|
00000190 50 0a a1 83 a6 d4 a6 13 85 83 f6 c3 e9 b3 ec d4 |P...............|
000001a0 03 c1 d9 9c 29 cf 54 b4 29 fb b2 bd 9c f6 e9 92 |....).T.).......|
000001b0 d6 69 cc 2e 75 d7 e6 c4 a3 32 cc 0e d0 46 00 fe |.i..u....2...F..|
000001c0 ff ff 82 fe ff ff 01 00 00 00 00 e8 0e 00 00 fe |................|
000001d0 ff ff 05 fe ff ff c2 e7 0e 00 3f b8 c1 00 00 00 |..........?.....|
000001e0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 |................|
000001f0 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 aa |..............U.|
00000200
```

---

### Post by lingenfr on 2010-10-13
I'm having a similar problem. I installed Windows 7 and then installed Ubuntu 10.10 x64. During the install Ubu saw my Windows 7 partitions (60GB and 100MB) as one block of unallocated space. I went ahead and installed. Now I have no Grub and can't get to Windows. Not a big deal, but I am not sure what to do to get a dual boot system set up. I read the web page but 'sudo fdisk -lu' and the script gave me the following and I am not sure where to go next. From reading the webpage, it appears that GPT is not compatible with Windows. I am not sure how I ended up with GPT unless that is now the default. To be clear, I am booting from a USB thumbdrive with 10.10 x64 Live. Help!

```

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x56b83fba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   500118191   250059095+  ee  GPT


                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks at sector 185789186 
    of the same hard drive for core.img, but core.img can not be found at this 
    location.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 256.1 GB, 256060514304 bytes
255 heads, 63 sectors/track, 31130 cylinders, total 500118192 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                   1   500,118,191   500,118,191  ee GPT


GUID Partition Table detected.

Partition           Start           End          Size System
/dev/sda1     122,882,048   126,788,297     3,906,250 Linux Swap
/dev/sda2     126,788,298   500,118,158   373,329,861 Linux or Data

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1007 MB, 1007157248 bytes
31 heads, 62 sectors/track, 1023 cylinders, total 1967104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             62     1,966,205     1,966,144   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        ef9cf0f5-5241-4de4-aacf-ded5abc1d1ce   swap                                     
/dev/sda2        14d55efa-2c77-4672-be65-a9e2a2eed0f9   ext4                                     
/dev/sda: PTTYPE="gpt" 
/dev/sdb1        2257-62B9                              vfat                                     
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
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

insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 14d55efa-2c77-4672-be65-a9e2a2eed0f9
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_gpt
insmod ext2
set root='(hd0,gpt2)'
search --no-floppy --fs-uuid --set 14d55efa-2c77-4672-be65-a9e2a2eed0f9
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
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 14d55efa-2c77-4672-be65-a9e2a2eed0f9
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=14d55efa-2c77-4672-be65-a9e2a2eed0f9 ro   quiet splash
	initrd	/boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 14d55efa-2c77-4672-be65-a9e2a2eed0f9
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=14d55efa-2c77-4672-be65-a9e2a2eed0f9 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 14d55efa-2c77-4672-be65-a9e2a2eed0f9
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_gpt
	insmod ext2
	set root='(hd0,gpt2)'
	search --no-floppy --fs-uuid --set 14d55efa-2c77-4672-be65-a9e2a2eed0f9
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
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
UUID=14d55efa-2c77-4672-be65-a9e2a2eed0f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda1 during installation
UUID=ef9cf0f5-5241-4de4-aacf-ded5abc1d1ce none            swap    sw              0       0

=================== sda2: Location of files loaded by Grub: ===================


  95.1GB: boot/grub/core.img
  95.1GB: boot/grub/grub.cfg
  65.4GB: boot/initrd.img-2.6.35-22-generic
  95.1GB: boot/vmlinuz-2.6.35-22-generic
  65.4GB: initrd.img
  95.1GB: vmlinuz

=========================== sdb1/boot/grub/grub.cfg: ===========================


if loadfont /boot/grub/font.pf2 ; then
	set gfxmode=auto
	insmod efi_gop
	insmod efi_uga
	insmod gfxterm
	terminal_output gfxterm
fi

set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

menuentry "Try Ubuntu without installing" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Install Ubuntu" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
	initrd	/casper/initrd.lz
}
menuentry "Check disc for defects" {
	set gfxpayload=keep
	linux	/casper/vmlinuz  boot=casper integrity-check quiet splash --
	initrd	/casper/initrd.lz
}

=================== sdb1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/grub.cfg

```

---

### Post by srs5694 on 2010-10-13
lingenfr, I strongly suggest that you post your problem in a new thread. In my experience, trying to deal with two peoples' problems in one thread gets very confusing very fast.

One point: Windows *will* install to GPT *if* the computer uses EFI rather than a conventional BIOS. It's conceivable that you've got such a system, which could be why the system now uses GPT. If you've got a conventional BIOS-based system, though, it appears that you've somehow accidentally converted from MBR to GPT and lost your existing partitions in the process. Deleting the new partitions and using [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) may be your only hope of recovering old data, and that might not work very well (or even at all). I hope you've got good backups, or at least don't care about your old data.

---

### Post by lingenfr on 2010-10-13
I posted here as it seems to be the same or at least a similar problem. I read the entire thread and your webpage before I posted and attempted the listed solutions. I don't have any valuable data in any of the partitions, so I am willing to wipe everything and start over as long as I don't keep chasing my tail. My computer is an Alienware M11x (R1) with a 256GB SSD drive. I am not familiar with GPT or EFI. I guess I might have gotten confused from reading your webpage where it said "The biggest stumbling block is Windows, which can't boot from GPT disks on BIOS-based computers." I didn't see any caveat about BIOS/EFI. My bad. I've probably done 50 installs of Ubuntu over the last several years. I did nothing different this time. Disk manager in 32-bit Ubu 10.10 (or maybe .04) saw the Windows partitions just fine. Please take a look at what I submitted and provide feedback. VMC where are you? Thanks.

---

### Post by mrcreativity on 2010-10-14
sorry about the quotes/codes thing. looks like im dafter than i think i am.

i've tried booting from the live cd numerous times, and have always used the manual partition option.everytime shows me the same thing. just /dev/sda.

Why hasnt this happened with any other linux distribution i've used? even ubuntu 10.04 installs flawlessly.

I booted into a live session, and started gparted. It shows my complete hard drive as unallocated space. Now i tried the disk utility that comes with ubuntu. It shows all the partitions but does not let me mount any one of them. Keeps giving me an error message that says daemon is inhibited.

---

### Post by srs5694 on 2010-10-14
Mrcreativity, this is sounding more and more like a new bug in 10.10. Unless I've overlooked something, your partition table looks fine, and if 10.04 and other libparted-based tools can see it, it's not likely to be a libparted bug I know about. (I'd like to be clear, though: If 10.04 installed fine *in the past,* that doesn't mean that the disk is fine *today.* Partition tables can and do change when you run various utilities, and it's easy to forget or not realize that you've run something that will alter the partition table. If you haven't done so, it might be worth verifying that 10.04 sees the disk OK as it is now.)

I'd be willing to look into this a bit further myself, but I'll need two files from you, which you can create as follows:

```

sudo dd if=/dev/sda of=backup.mbr bs=512 count=1
sudo sfdisk -d /dev/sda > backup.txt

```

Send me both the backup.mbr and backup.txt files and I'll look into this further; but I can't guarantee to do so in a timely manner. You can e-mail them to me at the e-mail address on my [personal Web pages.](http://www.rodsbooks.com) Also, please tell me precisely which version of Ubuntu you're attempting to install (32-bit, 64-bit, desktop, server, etc.).

I vaguely recall hearing something about a problem that can make a disk "disappear" depending on BIOS settings related to AHCI; however, my recollection is that this would make the whole disk disappear, not just the partitions it contains. Nonetheless, you could try fiddling with your BIOS options related to the disk. I don't hold out much hope that this will help.

One other idea, which I don't recommend unless you're willing to experiment with something that's rather flaky, is to convert the disk to GPT form, using a hybrid MBR to enable Windows to boot. Hybrid MBRs are flaky and dangerous, though, and there's no guarantee that this would work at all, so you should only try this if you're desperate and/or are willing to sacrifice all your data in the interest of experimentation. If so, install [GPT fdisk (gdisk),](http://www.rodsbooks.com/gdisk/) launch it on /dev/sda, type "n" to create a new partition (give it a type code of EF02 and let it fill the largest available space, which will be fairly small), type "r" to go to the recovery & transformation menu, type "p" to view the current partitions, type "h" to create a hybrid MBR containing partitions 1, 2, and 3 (you'll be prompted for type codes and whatnot; the defaults or suggested values should work fine), and then type "w" to save the changes. Then boot the 10.10 installer and hope it works. If it doesn't, you'll have to either use [Super GRUB Disk](http://www.supergrubdisk.org) or some other method to boot and re-install GRUB or you'll need to convert back from GPT to MBR by deleting the EF02 partition you created and then using the "g" option on the recovery & transformation menu of gdisk. As you can see, this is moderately involved and carries significant risks.

---

### Post by mrcreativity on 2010-10-14
I've generated the files you have asked for and am emailing them now. I'm also creating an Ubuntu 10.04 live usb and will try starting the partitioning process and installation over again.

I dont think ill try the options u have listed since the 10.04 i've installed works perfectly. In fact, im using windows 7 less and less since this version of ubuntu is so darned good.

Thanks for the help.

Alright, there's definately something wrong with my partition table. The 10.04 installation shows the same thing. just /dev/sda.

The last thing i remember doing was restoring grub after i resized the partitions through windows. I'm going to try and fix the partition table through windows startup repair and then installing grub again.

---

### Post by dino99 on 2010-10-14
[http://ubuntuforums.org/showpost.php?p=9971263&postcount=4](http://ubuntuforums.org/showpost.php?p=9971263&postcount=4)

---

### Post by VMC on 2010-10-14
>  ...BIOS settings related to AHCI...

I think this is exactly the problem. Someone else in another forum was able to change from AHCI to IDE and the boot process was able to continue. Doesn't make much sense sine its SATA, but ACHI has come up several times as problematic.

---

### Post by srs5694 on 2010-10-14
> **mrcreativity said:**
> I've generated the files you have asked for and am emailing them now.

I've received your e-mail. I'll look this over when time permits. (I plan to duplicate your partitions on a virtual machine to try to recreate your problem.)

> Alright, there's definately something wrong with my partition table. The 10.04 installation shows the same thing. just /dev/sda.

The last thing i remember doing was restoring grub after i resized the partitions through windows. I'm going to try and fix the partition table through windows startup repair and then installing grub again.

Given this, my suspicion is that the Windows partitioner has done something very subtle that libparted doesn't like. If I had to guess, it would be something related to the partition alignment (cylinder vs. MiB), although I've never seen libparted flake out like this over such issues. In any event, I wouldn't recommend using Windows to try to fix the problem; my concern is that it will just make matters worse.

Try this for more diagnostic information:

```

sudo parted /dev/sda

```

When you get the "(parted)" prompt, type "exit" to quit. Look for any warnings or error messages; they may provide a clue about what libparted doesn't like about the disk. Such messages don't appear when you launch GParted via a desktop menu or the installer's partitioner, since these messages are directed only to a text-mode output stream.

[quote=VMC]Someone else in another forum was able to change from AHCI to IDE and the boot process was able to continue. Doesn't make much sense sine its SATA, but ACHI has come up several times as problematic.[/quote]

Unless I'm misunderstanding, this isn't a boot problem. The computer boots fine; it's just that libparted is reporting that the partition table is empty when in fact it isn't. As I wrote, it's still worth checking, since there's definitely weirdness to be had with AHCI, but IMHO it's a long shot.

---

### Post by mrcreativity on 2010-10-14
oh snap...i went ahead and restored the mbr with windows 7 repair, and deleted the ubuntu partitions. i was thinking of starting over.

i'm gonna give it a shot see how it goes. 

any suggestions on how i should go about installing ubuntu now?

---

### Post by mrcreativity on 2010-10-14
that did the trick. i reinstalled ubuntu 10.10 and now everything works as it should. 
this is what i did

started windows 7 repair...did bootrec /fixmbr from the command prompt and then just booted with the linux usb.

it worked...updating as we speak.
thanks for all the help.

---

### Post by srs5694 on 2010-10-14
I'm glad it's working for you now. I'll still look over your files sooner or later, since I'd like to figure this out myself, and maybe mention it on my Web page on the topic.

---

### Post by lingenfr on 2010-10-14
> **srs5694 said:**
> One point: Windows *will* install to GPT *if* the computer uses EFI rather than a conventional BIOS. It's conceivable that you've got such a system, which could be why the system now uses GPT. If you've got a conventional BIOS-based system, though, it appears that you've somehow accidentally converted from MBR to GPT and lost your existing partitions in the process. 

Windows 7 64-bit WILL NOT install to GPT on my system. The partitioner comes up with an error message saying it will not install to GPT. Maybe because it does not support EFI. Don't know. I downloaded the parted disc and used gdisk to convert GPT to MBR. Of course grub no longer knew what to do and Windows would not boot. I first tried mrcreativity's idea to use fdisk to repair the MBR. Unfortunately my restore disk won't get me to a prompt and I did not want to fool around downloading and burning other disks. I reinstalled Win 7. Next I will try and reinstall grub to see if my linux installation still functions. If not I will reinstall using x64 10.04 to see if it munges my disk similarly. As I said, I've done many installs and many dual boots. Never a mess like this, so I assume it is some new 'feature' of 10.10. Not that I am getting any assistance, but I will report back with results if successful.

---

### Post by lingenfr on 2010-10-16
I imagine that my and the OPs problem were the same, but can't confirm. As mentioned in another thread, either the partitioner or the installer (or both) with 10.10 are hosed. I imagine you can either try and roll your own (use the 10.4 partitioner/installer/both with 10.10) or do what I did and install 10.04 and then dist-upgrade to 10.10. As mentioned previously, I am using an Alienware M11x (R1). If like me, you are doing a clean install of Win 7 and Ubuntu for dual boot, I recommend you do the following:

1) Install Win 7 leaving sufficient disk space for your swap and system (however many you intend to use) partitions.
2) Install Ubuntu 10.04. (I used the 64-bit versions of Win 7 and Ubu)
3) Change your settings in Updater to allow you to see new distributions.
4) Dist-upgrade to Ubuntu 10.10

I started my dist-upgrade before leaving for work. When I returned the upgrade was hung in the installation process. I had to power off and restart. It would not boot Ubu, so I did a recovery boot and selected dpkg to fix broken packages. A few bumps along the way, but I kept current config files and defaults and completed the upgrade. Seems to be working fine and as mentioned in another thread, sound works without installing the Realtek driver. If you are interested in the details of what I did to recover, I will share, but my instructions above will prevent the problem from occurring. My recovery method did not save any data, so I doubt it is useful to others. Good luck.

---

