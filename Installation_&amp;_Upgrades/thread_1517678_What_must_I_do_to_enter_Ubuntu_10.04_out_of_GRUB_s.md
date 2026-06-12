---
title: "What must I do to enter Ubuntu 10.04 out of GRUB screen ?"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by sipak on 2010-06-25
After Installation of Ubuntu 10.04 LTS. I restarted the computer as required. Then I had a GRUB screen:

[CENTER]GNU GRUB version 1.98-1ubuntu5[/CENTER]

Minimal BASH-like line editing is supported. for the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>_





What must I do to get in Ubuntu? are there any commands that enables me to get there ?

Waiting your feedback. Thanks for your time.

---

### Post by Rubi1200 on 2010-06-25
Hi,
what are your computer specifications? RAM, graphics, HDD etc

Do you have a LiveCD handy?

If so, use it and then post the output from:

```
sudo fdisk -l
```

---

### Post by drs305 on 2010-06-25
sipak, 

Welcome to Ubuntu and the Ubuntu forums.  :-)

If you run *meierfra's* boot info script it will give us enough information to help you determine the problem and possibly provide a solution. Post the results within "code" tags, which you can call up by pressing the # icon in the post's top menu bar.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

There are multiple links in my signature line if you want to learn more about Grub 2 on your own.

---

### Post by sipak on 2010-06-25
Intel Core2Duo CPU
E4500@ 2.20GHz
2.21GHz, 2.00GB of RAM

Hard Capacity : 250GB

**Do you have a LiveCD handy?**

I do not know what's it ?

But I installed Ubuntu 10.04LTS from a CD.

Thanks for the fast reply.

---

### Post by sipak on 2010-06-25
> **drs305 said:**
> sipak, 

Welcome to Ubuntu and the Ubuntu forums.  :-)

If you run *meierfra's* boot info script it will give us enough information to help you determine the problem and possibly provide a solution. Post the results within "code" tags, which you can call up by pressing the # icon in the post's top menu bar.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

There are multiple links in my signature line if you want to learn more about Grub 2 on your own.

**meierfra**?
I do not know about it. I've downloaded { boot_info_script055.sh }
What to do next ?

---

### Post by sipak on 2010-06-25
[FONT="Georgia"][SIZE="4"]I have not installed _Wubi_. I made an ext3 drive extension and a swap area, then i installed it. Away from windows.[/SIZE][/FONT]

---

### Post by Rubi1200 on 2010-06-25
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

> **How to use the boot info script**

  
[LIST]
[*] Boot into any Linux based operating system, LiveCD or LiveUSB with an Internet connection.
[*]  [                                                 Download the Boot Info Script ]("http://sourceforge.net/projects/bootinfoscript")
[*] Open a terminal (Applications>Accessories>Terminal in Gnome) and type           sudo bash [path/to/the/download_folder]/boot_info_script*.sh  For example if you downloaded the file to the desktop, use          sudo bash ~/Desktop/boot_info_script*.sh
[*] If your operation system does not use sudo, use              su 
     bash ~/Desktop/boot_info_script*.sh
[*] You will now have the file RESULTS.txt in the same directory as     the script.[SIZE=-1] But if the script is inside a system directory (like     /usr or /etc) RESULTS.txt will be in the home directory.[/SIZE]
[*] If you already have an existing RESULTS.txt, subsequent  files will be called RESULTS1.txt, RESULTS2.txt,...
[*] Open RESULTS.txt in your favorite text editor.
[*] If you came here from a Linux forum, paste the content of RESULTS.txt into your next post. Make sure to use the appropriate formating. For example in the Ubuntu forums click on the code tags (the symbol #) before pasting RESULTS.txt.
[/LIST]


---

### Post by drs305 on 2010-06-25
> **sipak said:**
> **meierfra**?
I do not know about it. I've downloaded { boot_info_script055.sh }
What to do next ?

On the boot info script page from which you downloaded the script there are instructions on how to run it on your computer. In general, if the script downloaded to your Desktop, open a terminal (Applications, Accessories, Terminal) and run:
```
sudo bash ~/Desktop/boot_info_script055.sh
```
You will be asked for your password - type it. You won't see anything as you type. Press ENTER once you have typed it into the terminal window.

It will generate a file called RESULTS.txt, which is what we would like to view.

---

### Post by sipak on 2010-06-25
**In general, if the script downloaded to your Desktop, open a terminal (Applications, Accessories, Terminal) **

How to get into the terminal while the problem is I cannot enter Ubuntu.

---

### Post by Rubi1200 on 2010-06-25
> **sipak said:**
> Intel Core2Duo CPU
E4500@ 2.20GHz
2.21GHz, 2.00GB of RAM

Hard Capacity : 250GB

But I installed Ubuntu 10.04LTS from a CD.

Thanks for the fast reply.

sipak, do you still have the CD you used to install Ubuntu?

If yes, then use it to boot the computer, but this time choose Try Ubuntu only.

Then follow the instructions posted by drs305.

---

### Post by drs305 on 2010-06-25
> **sipak said:**
> **In general, if the script downloaded to your Desktop, open a terminal (Applications, Accessories, Terminal) **

How to get into the terminal while the problem is I cannot enter Ubuntu.

Boot the LiveCD (the one you installed Ubuntu with). When asked, choose to try Ubuntu without installing. That will take you to a LiveCD Desktop. From there you can access the terminal and run the script.

Your computer should boot the CD. If it doesn't, you may have to enter the BIOS and change it so the CD boots before your hard drive. Different computers use different methods to access the BIOS. Usually the user must press one of the Function keys (F1-F12), the DEL key, etc during the boot process to enter the BIOS.

---

### Post by sipak on 2010-06-25
ubuntu@ubuntu:~$ sudo bash ~/media/library/problem/boot_info_script055.shbash: /home/ubuntu/media/library/problem/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ su bash ~/media/library/problem/boot_info_script055.sh
Unknown id: bash
ubuntu@ubuntu:~$ 


That's what I've got..

I do not know where is the results? It's not in the same directory, and not in home folder.

What to do next?

---

### Post by Joe of loath on 2010-06-25
> **sipak said:**
> ubuntu@ubuntu:~$ sudo bash ~/media/library/problem/boot_info_script055.shbash: /home/ubuntu/media/library/problem/boot_info_script055.sh: No such file or directory
ubuntu@ubuntu:~$ su bash ~/media/library/problem/boot_info_script055.sh
Unknown id: bash
ubuntu@ubuntu:~$ 


That's what I've got..

I do not know where is the results? It's not in the same directory, and not in home folder.

What to do next?

There's a line break between 'su' and 'bash'. Type simply: ```
sudo bash /media/library/problem/boot_info_script055.sh
``` instead.

---

### Post by sipak on 2010-06-25
It worked.

The results test file :

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
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
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sdb6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb7: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb8: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb9: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb10: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb11: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,156,224    78,156,162   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    39,070,079    39,070,017   7 HPFS/NTFS
/dev/sdb2          39,070,141   488,392,064   449,321,924   f W95 Ext d (LBA)
/dev/sdb5          39,070,143    59,056,190    19,986,048  83 Linux
/dev/sdb6          61,593,273   136,729,214    75,135,942   7 HPFS/NTFS
/dev/sdb7         136,729,278   234,388,349    97,659,072   7 HPFS/NTFS
/dev/sdb8         234,388,413   332,047,484    97,659,072   7 HPFS/NTFS
/dev/sdb9         332,047,548   429,706,619    97,659,072   7 HPFS/NTFS
/dev/sdb10        429,706,683   488,392,064    58,685,382   7 HPFS/NTFS
/dev/sdb11         59,058,176    61,591,551     2,533,376  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C807-5CFF                              vfat       MOVIES                        
/dev/sda: PTTYPE="dos" 
/dev/sdb10       01C88916EC823060                       ntfs       library                       
/dev/sdb11       48285ecc-0d60-472b-8ac4-7ea11997a473   swap                                     
/dev/sdb1        C4A87AF6A87AE5F8                       ntfs       windows                       
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        bc8b680d-6a47-4e12-9112-bb3db6a9d29e   ext3                                     
/dev/sdb6        15F572CA0692E051                       ntfs       engineering and science       
/dev/sdb7        01C88916E9441C60                       ntfs       miscellaneous                 
/dev/sdb8        01C88916EA50AA60                       ntfs       audio                         
/dev/sdb9        01C88916EB6C7AA0                       ntfs       audio, games, and programs    
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb10       /media/library           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sdb1/boot.ini: ================================

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
C:\wubildr.mbr = "Ubuntu"

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
search --no-floppy --fs-uuid --set bc8b680d-6a47-4e12-9112-bb3db6a9d29e
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
search --no-floppy --fs-uuid --set bc8b680d-6a47-4e12-9112-bb3db6a9d29e
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set bc8b680d-6a47-4e12-9112-bb3db6a9d29e
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=bc8b680d-6a47-4e12-9112-bb3db6a9d29e ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set bc8b680d-6a47-4e12-9112-bb3db6a9d29e
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=bc8b680d-6a47-4e12-9112-bb3db6a9d29e ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set bc8b680d-6a47-4e12-9112-bb3db6a9d29e
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd1,5)'
	search --no-floppy --fs-uuid --set bc8b680d-6a47-4e12-9112-bb3db6a9d29e
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sdb1)" {
	insmod ntfs
	set root='(hd1,1)'
	search --no-floppy --fs-uuid --set c4a87af6a87ae5f8
	drivemap -s (hd0) ${root}
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
UUID=bc8b680d-6a47-4e12-9112-bb3db6a9d29e /               ext3    errors=remount-ro 0       1
# swap was on /dev/sdb11 during installation
UUID=48285ecc-0d60-472b-8ac4-7ea11997a473 none            swap    sw              0       0

=================== sdb5: Location of files loaded by Grub: ===================


  24.9GB: boot/grub/core.img
  24.9GB: boot/grub/grub.cfg
  24.8GB: boot/initrd.img-2.6.32-21-generic
  24.9GB: boot/vmlinuz-2.6.32-21-generic
  24.8GB: initrd.img
  24.9GB: vmlinuz

```

**[FONT="Georgia"][SIZE="4"]What to do next?[/SIZE][/FONT]**

---

### Post by drs305 on 2010-06-25
The problem appears to be that Grub2 is installed on sda and looks for sda5 for the files, but in actuality the files are in sdb5.
> 
=> **Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in partition #5 for /boot/grub.**
=> Windows is installed in the MBR of /dev/sdb


To fix this from the LiveCD, you will need to reinstall Grub2:
```

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

```
This will mount your Linux partition (sdb5) and then install the Grub2 files to that partition. Those files actually already exist, but the command will *also* install Grub 2 to the MBR of sdb.

Once you can boot into Ubuntu, we may need to make a few changes to ensure you don't have a long boot delay and that you can still run Windows.

Note:  I edited your post to add the "code" tags to make the RESULTS.txt more forum-friendly. If you click on the # symbol when you are writing a post, it generates **[COLOR="DarkRed"][noparse]```

```[/noparse][/COLOR]** tags. Pasting or typing text between these codes allows it to display in the format now used in your previous post.

---

### Post by sipak on 2010-06-26
It worked :D

Thanks very much  drs305, Joe of loath, Rubi1200 for your help. I'm really grateful.

Have a good day.

---

### Post by Rubi1200 on 2010-06-26
> **sipak said:**
> It worked :D

Thanks very much  drs305, Joe of loath, Rubi1200 for your help. I'm really grateful.

Have a good day.

Glad things worked out for you!

Use the Thread Tools at the top of the page to mark this as Solved and don't forget to post again if you need help with anything.

---

