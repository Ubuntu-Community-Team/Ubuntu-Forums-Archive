---
title: "Cannot boot Ubuntu 10.04"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by ezzy96 on 2010-06-06
I am new to linux scene. Trying out Ubuntu 10.04 from a live CD. Initially, It had the purple screen on and came up with "unrecoverable error" will load Live CD. I tried installing Lynx and everything went on fine until I tried to reboot at end of installation.

After POST screen the following showed on screen

error: out of disk
grub rescue>

I am not able to go back to live CD as earlier when I could use it to check the web.

What is grub rescue?

---

### Post by Mikko8 on 2010-06-06
I have the same problem. I cannot boot from hard disk anymore. But if you want to run the LiveCD you can do that by changing some settings in BIOS.

---

### Post by darkod on 2010-06-06
If there was an error or message when trying to run live mode, that is usually a warning not to install before you figure out what's wrong.

If you can boot into live mode, you could run the boot info script as explained here and post the content of your results file:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

As for booting into live mode, you should always be able to do it, regardless what you have on your hdd. Even without a hdd in the system.

---

### Post by enduroktm300 on 2010-06-06
Hi there, I'm having the same problems as the other posters above:  error on install -->run from Live CD....
Attempt to boot from HDD give the same "grub rescue" error message.

I DL'd your script and when I executed the sudo bash command i received  a no such file or directory error.

I am completely new to Linux so it may be a simple user error on my part.
Any ideas?

---

### Post by darkod on 2010-06-06
> **enduroktm300 said:**
> Hi there, I'm having the same problems as the other posters above:  error on install -->run from Live CD....
Attempt to boot from HDD give the same "grub rescue" error message.

I DL'd your script and when I executed the sudo bash command i received  a no such file or directory error.

I am completely new to Linux so it may be a simple user error on my part.
Any ideas?

Depending where the script is after download, you need to adjust the command, or simply move the script on the Desktop and in terminal do:

sudo bash ~/Desktop/boot_info_script*.sh

If it is in your Home folder, it would be only:

sudo bash ~/filename

If in Downloads folder:

sudo bash ~/Downloads/filename

You get the point. Another thing to note is that linux ALWAYS makes difference between small and capital letters, even in file and folder names (while in windows you can type any way you want).

In linux the folder desktop is not the same as Desktop.

---

### Post by enduroktm300 on 2010-06-06
Thanks Darkrod, 
This is my first taste of success  :)
I have confirmed the boot_info_script*.sh file  is in the Downloads directory.  The RESULTS.txt file is there as well.

I did a quick search on the web but I was unable to find how to display/post the contents of the RESULTS.txt file in order to copy for a post.

***EDIT I figured out that bash will do this.  The results were posted under the Original link for Darkrod's post

---

### Post by darkod on 2010-06-06
> **enduroktm300 said:**
> Thanks Darkrod, 
This is my first taste of success  :)
I have confirmed the boot_info_script*.sh file  is in the Downloads directory.  The RESULTS.txt file is there as well.

I did a quick search on the web but I was unable to find how to display/post the contents of the RESULTS.txt file in order to copy for a post.

The easiest way is just double-click it to open it (it's text file), select the whole text just like in a document, and select Copy from the Edit menu (or simply Ctrl + C).

Then open new post here, and just Ctrl+V to Paste. After Paste the whole text should stay selected and it's good to hit the # button in the toolbar above when creating the post to put CODE tags at start and end of the text. It makes it easier to read, although this last step is not necessary. But it's preferred. :)

---

### Post by enduroktm300 on 2010-06-06
> **darkod said:**
> The easiest way is just double-click it to open it (it's text file), select the whole text just like in a document, and select Copy from the Edit menu (or simply Ctrl + C).

Then open new post here, and just Ctrl+V to Paste. After Paste the whole text should stay selected and it's good to hit the # button in the toolbar above when creating the post to put CODE tags at start and end of the text. It makes it easier to read, although this last step is not necessary. But it's preferred. :)

I think I finally have this right...

```
/dev/sda2: PTTYPE="dos" 
/dev/sda5        NUlTTv-100X-x4G3-HLSp-BHXb-ONQs-yO7uzb LVM2_member                               
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr1         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


============================= sda1/grub/grub.cfg: =============================

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
insmod lvm
insmod ext2
set root='(ubuntutheserver-root)'
search --no-floppy --fs-uuid --set e913e614-8710-405f-b449-656ae0a0f977
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
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
set locale_dir=($root)/grub/locale
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    linux    /vmlinuz-2.6.32-21-generic-pae root=/dev/mapper/ubuntutheserver-root ro   quiet
    initrd    /initrd.img-2.6.32-21-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    echo    'Loading Linux 2.6.32-21-generic-pae ...'
    linux    /vmlinuz-2.6.32-21-generic-pae root=/dev/mapper/ubuntutheserver-root ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /initrd.img-2.6.32-21-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0b6aadc3-b4ef-411f-8738-bb25378d06df
    linux16    /memtest86+.bin console=ttyS0,115200n8
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

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: grub/core.img
    .0GB: grub/grub.cfg
    .0GB: initrd.img-2.6.32-21-generic-pae
    .0GB: vmlinuz-2.6.32-21-generic-pae
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda2

00000000  14 8b 00 85 c0 74 6b 8b  8f 50 12 00 00 51 8d 8c  |.....tk..P...Q..|
00000010  24 74 03 00 00 51 8d 8c  24 a8 00 00 00 51 8b 8f  |$t...Q..$....Q..|
00000020  a8 0f 00 00 51 8b 8f d4  0e 00 00 03 cb 51 8b 4c  |....Q........Q.L|
00000030  24 50 51 8b 8f a4 0f 00  00 51 8d 8f 38 11 00 00  |$PQ......Q..8...|
00000040  51 8b 4c 24 38 51 8b 8f  00 05 00 00 03 cb 51 8b  |Q.L$8Q........Q.|
00000050  4c 24 38 51 68 f4 dd 6f  68 8b ca 68 cc dd 6f 68  |L$8Qh..oh..h..oh|
00000060  ba a4 dd 6f 68 e8 b6 41  ff ff 83 c4 34 e9 84 00  |...oh..A....4...|
00000070  00 00 8b 87 50 12 00 00  50 8d 8c 24 74 03 00 00  |....P...P..$t...|
00000080  51 8b 8f a8 0f 00 00 8d  84 24 a8 00 00 00 50 8b  |Q........$....P.|
00000090  87 d4 0e 00 00 51 8b 4c  24 4c 03 c3 50 8b 87 a4  |.....Q.L$L..P...|
000000a0  0f 00 00 51 50 8b 44 24  34 8d 8c 24 88 00 00 00  |...QP.D$4..$....|
000000b0  51 8b 8f 00 05 00 00 50  8b 44 24 34 03 cb 51 50  |Q......P.D$4..QP|
000000c0  68 f4 dd 6f 68 8b ca 68  cc dd 6f 68 ba a4 dd 6f  |h..oh..h..oh...o|
000000d0  68 33 c0 e8 48 41 ff ff  83 c4 34 83 7c 24 38 00  |h3..HA....4.|$8.|
000000e0  74 14 8b b7 a8 0f 00 00  b9 28 00 00 00 8d bc 24  |t........(.....$|
000000f0  00 06 00 00 f3 a5 b9 28  00 00 00 8d b4 24 70 03  |.......(.....$p.|
00000100  00 00 8d bc 24 c0 04 00  00 f3 a5 8b 75 08 8b 7d  |....$.......u..}|
00000110  14 8d 4c 24 68 51 8d 55  10 52 8d 84 24 9c 00 00  |..L$hQ.U.R..$...|
00000120  00 50 8d 4c 24 40 51 8d  54 24 60 52 8d 44 24 40  |.P.L$@Q.T$`R.D$@|
00000130  50 8b 44 24 60 8d 8c 24  a8 01 00 00 51 8d 94 24  |P.D$`..$....Q..$|
00000140  7c 05 00 00 52 50 8b 86  d4 0e 00 00 8d 8c 24 c4  ||...RP........$.|
00000150  00 00 00 51 8b 8e a8 0f  00 00 8d 94 24 e8 04 00  |...Q........$...|
00000160  00 52 03 c3 50 8b 44 24  44 51 8b 0f 8d 94 24 8c  |.R..P.D$DQ....$.|
00000170  00 00 00 52 8b 96 00 11  00 00 50 8b 86 f4 10 00  |...R......P.....|
00000180  00 51 8b 08 52 51 e8 45  51 ff ff 8b 4c 24 68 83  |.Q..RQ.EQ...L$h.|
00000190  c4 48 66 85 c9 75 19 d9  ee d8 9e e4 09 00 00 df  |.Hf..u..........|
000001a0  e0 f6 c4 05 7a 0a 8b 54  24 2c 89 96 d4 09 00 00  |....z..T$,......|
000001b0  66 83 f9 03 75 19 d9 ee  d8 9e e8 09 00 00 00 3b  |f...u..........;|
000001c0  1d 1f 8e fe ff ff 02 00  00 00 00 f0 99 12 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

---

### Post by darkod on 2010-06-06
I replied on the other thread because I saw the file attached there first. Decide on which thread you want to post, don't do it twice.
In fact, it might be better to open your own thread since it seems you have specific setup (LVM). As I said in my reply to the other thread, your results file looks incomplete, at least the part you posted. Was that all in the file?

---

### Post by enduroktm300 on 2010-06-06
I did not realize the response went to another thread.
I did as you suggested and began a new thread:
[http://ubuntuforums.org/showthread.php?p=9420657#post9420657](http://ubuntuforums.org/showthread.php?p=9420657#post9420657)

---

### Post by oldfred on 2010-06-06
Back to ezzy96's out of disk error, this may be a workaround:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:write)

---

### Post by ezzy96 on 2010-06-15
I think I made an error. I could not find this initial post and after a week I did a second post (thread 1509205). Er, any way of deleting that post?


```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary:  ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same  drive in 
    partition #1 for /boot/grub.

sda1: __________________________________________________   _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab  /boot/grub/core.img

sda2: __________________________________________________   _______________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________   _______________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info:  =============================

Drive: sda ___________________  __________________________________________________  ___

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   310,360,063   310,358,016  83 Linux
/dev/sda2         310,362,110   312,580,095     2,217,986   5 Extended
/dev/sda5         310,362,112   312,580,095     2,217,984  82 Linux swap  / Solaris


blkid -c /dev/null: __________________________________________________   __________

Device           UUID                                   TYPE       LABEL                          

/dev/loop0                                              squashfs                                  
/dev/ramzswap0                                          swap                                      
/dev/sda1        b040e032-0901-4304-a940-0d047583dd30   ext4                                      
/dev/sda2: PTTYPE="dos" 
/dev/sda5        d65f4543-b00b-4e05-ac16-72cd166b70d0   swap                                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output:  ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sda1/boot/grub/grub.cfg:  ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using  templates
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
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env  recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b040e032-0901-4304-a940-0d047583dd30
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that  don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set b040e032-0901-4304-a940-0d047583dd30
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class  gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set  b040e032-0901-4304-a940-0d047583dd30
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=b040e032-0901-4304-a940-0d047583dd30 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class  ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set  b040e032-0901-4304-a940-0d047583dd30
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic  root=UUID=b040e032-0901-4304-a940-0d047583dd30 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set  b040e032-0901-4304-a940-0d047583dd30
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set  b040e032-0901-4304-a940-0d047583dd30
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
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
# This file provides an easy way to add custom menu entries.  Simply  type the
# menu entries you want to add after this comment.  Be careful not to  change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab:  ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique  identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>   <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=b040e032-0901-4304-a940-0d047583dd30 /               ext4     errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d65f4543-b00b-4e05-ac16-72cd166b70d0 none            swap    sw               0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0        0

=================== sda1: Location of files loaded by Grub:  ===================


  79.6GB: boot/grub/core.img
 129.0GB: boot/grub/grub.cfg
  79.6GB: boot/initrd.img-2.6.32-21-generic
  79.5GB: boot/vmlinuz-2.6.32-21-generic
  79.6GB: initrd.img
  79.5GB: vmlinuz


:confused:
```

Hope this helps. I have read and tried to implement the workaround by sourceforge. did not work. Maybe I keyed something wrong. Will try again.

---

### Post by ezzy96 on 2010-06-15
Oldfred, I just use live CD and opened a terminal. Using the commands given in the page by sourceforge, could not find the specified entries in /etc/grub.d/10_linux.

---

### Post by oldfred on 2010-06-15
Your are correct, it is in my Karmic but not in my Lucid 10_linux. Then I do not know what causes that error in Lucid.

---

### Post by ezzy96 on 2010-06-16
Thanks anyway Oldfred. I thought using the distros would be easier for me to install ubuntu or any flavour of linux. Looks like I might have to learn to build. I came across the LFS site and it looks interesting. Only I do not know if at half a century old would be able to grasp the programming language.

---

### Post by ezzy96 on 2010-06-16
Still wondering why it cannot boot. Used live Cd and examined the structure of my setup. This is what I discovered

1. Using Gparted

there is a unallocated portion about 1MiB size. Why is this so?

2. Using File Browser

three files have X on them, root, vmlinuz and initrd.img.
when I tried to access both vmlinuz and inrd.img, it states the link is broken and if I want to delete the file.
as for boot, no authority to access it.

Could it be that the links for both vmlinuz nd intrd.img is pointing to the unallocated partition?

---

### Post by oldfred on 2010-06-16
Those are linked files to your most current kernel. If they are broken it sounds like an update did not complete.

I would then try chrooting into your system and run some updates.

kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition - He has sda5 and yours is sda1. I changed this copy:
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Commands once in chroot:
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
grub-install /dev/sda
grub-install --recheck /dev/sda

sudo dpkg-reconfigure grub-pc

---

### Post by ezzy96 on 2010-06-17
Oldfred, tried and got this message

ubuntu@ubuntu:~$ sudo mount /dev/sda1/mnt && sudo mount -bind /dev /mnt/dev && sudo mount -bind /proc /mnt/proc && sudo mount -bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
mount: can't find /dev/sda1/mnt in /etc/fstab or /etc/mtab

what next?

---

### Post by oldfred on 2010-06-17
You need to see why to mount command is not working. Your install is on sda1 per the script unless you have moved something.

See Kansasnoob's links and you can run each command one at a time to make sure each works and adjust if not correct.

---

### Post by ezzy96 on 2010-06-18
Thanks Oldfred. You gave me some things to work on and I have attached a part of the process captured from the terminal. Once I boot up most probably will lose this information. Will be booting up and let you know if it works.

---

### Post by oldfred on 2010-06-18
It looks like it processed a lot of updates normally except the dbus error. I do not know about that, whether it is critical or not.

---

### Post by ezzy96 on 2010-06-19
After all the updates and on rebooting, the same error: out of disk.
I guess this means my hardware has a problem. May junk this hardware and get another to try out linux.

---

### Post by oldfred on 2010-06-19
Can you check BIOS settings.
 I saw this in another thread.

I saw a suggestion on a forum to "set the drive up in LBA mode in the BIOS. So I went under "primary IDE master" and found LBA mode control was set to Disable, so I enabled it and now I can load and run Xubuntu from my hard drive, where I could not before and was getting grub errors.

---

### Post by ezzy96 on 2010-06-22
Okay, I have reset the bios to LBA mode and installed again but on booting up the same error {out of disk appeared again. Could a sector in the hard disk that is not allocated cause any problems? I read somewhere that if I had a separate boot partition it may solve this problem. How do I go about doing it?

---

### Post by oldfred on 2010-06-22
Separate boot partition is only required if you have a really old PC where the BIOS can only read smaller hard drives and you have upgraded to a newer drive that is larger than the BIOS can see.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
See #15 and try booting per the instructions.

---

### Post by ezzy96 on 2010-06-25
command ls works, it showed hd0,  hd0,1   fd0

the search command was not recognised.
I tried set and it worked????

grub rescue have very limited commands that work.so far onlt ls and set works the rest from the list given in the Grub2 manual wiki does not work.

Did I key in wrongly?

---

### Post by oldfred on 2010-06-25
If it shows hd0,1 that should be sda1

Manual boot:
#show you the available partitions
ls
#look for boot files on the partitions
ls (hd0,1)/boot
# continue until you see vmlinuz-2.6.xxxx
#then boot that linux replacing hd0,1 with your partition
insmod ext2
set root=(hd0,1)
# in the next command sda1 represents (hd0,1), sdb2 would be for (hd1,2)
linux /vmlinuz root=/dev/sda1 ro quiet splash
initrd /initrd.img
boot
Install grub to MBR:
sudo grub-install /dev/sda
sudo update-grub

---

### Post by ezzy96 on 2010-06-27
Okay, I was so desperate that I reformatted the harddrive and reinstalled from  live CD. Now everything loads and I end up with the grub>      

What next?

---

### Post by ezzy96 on 2010-06-27
Finally!!! Got Ubuntu running. Thank you Oldfred for your patience. After reformatting and reinstalling from Live CD, I used the manual boot instructions that you gave and my linux setup booted correctly.

:p

---

### Post by ezzy96 on 2010-06-27
Ha! Ha!  I was so happy to get the Ubuntu going but got a surprise. When I cold booted it after switching off, I got back the grub>.

Am able to restart  it with the same manual boot instructions am updating the files now. Will try shut down and cold boot to see if the updates work.

Ed

---

### Post by ezzy96 on 2010-06-27
Yes!!!!! Yes!!! Yes!!!  It worked!! After updating the files, it booted okay!!

---

