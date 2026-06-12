---
title: "grub 0.97~beta4  vs. chkdsk on XP"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Innigo on 2010-05-03
Hi all,
Synaptic offered the above upgrade to grub and I said OK.  Then I see some comments by "ranch hand" suggesting there may be problems with this version.  When I tried the newly offered option to boot into the old XP it said chkdsk had found a problem and proceeded without so much as a by your leave, failing to respond even to ctrl-alt-del  This I found quite alarming as chkdsk has never fixed anything for me, only broken them.  I was so alarmed I powered off the machine mid-scandisk.  Perhaps I'm too nervous with these things or is there perhaps something akin to the old browser wars going on here?

I'm prepared to wipe the old XP install as it has been completely backed up before I installed Linux.  The upshot of a thread I followed from ranch hand seemed to be:

[INDENT]*Open Synaptic, search for Grub and Grub2, COMPLETELY remove all the grub packages, then do a file search and make sure files and folders like /etc/default/grub, /etc/grub.d and /boot/grub are gone .... basically nuke Grub as completely as you can.*
*...*
*as complete a scrub of Grub as possible, including all files and folders, then fix windows MBR, boot windows, then *** because fixing the MBR from the windows repair disk will really kill grub in the MBR  ***, reinstall Grub2.*
[/INDENT]
This sounds intuitively the simplest and safest way. Unfortunartely I didn't make a windows repair disk :(  So I'm thinking I should just edit the grub menu to remove the boot to XP option and then just never look back.

But am I worrying about nothing?  Is scandisk/chkdsk the going to "fix" my MBR and try to make my disk a Windows disk again?  Will Synaptic at some later point offer me Grub2 or should I start again while it's still a fairly new install?

---

### Post by Innigo on 2010-06-28
Hmmmm, no response whatsoever :-( 
mebe somint wrong wit my netiquette? 

Maybe I should repost in Installation/Upgrades re. Grub2 upgrade and 9.10 to 10.04LTS Upgrade

In answer to my own question, there's this link:
[Grub2 Upgrade]("https://help.ubuntu.com/community/Grub2#Upgrading") 
I thought the instructions looked relatively clear, simple, straightforward. Yay! But it won't go
I tried Synaptic. Mirror no find repo index so set to use main server. Went to 
System > Administration > Update Manager
Set that file to say prompt=normal (also tried prompt=lts)
Hit [Check] but it doesn't offer me any upgrades.

Ok, so I try manual way. See log below. It's very helpfully removed my JDK :lolflag:
What's going on? Anyone, please?

me@mine:~$ grub-install -v
grub-install (GNU GRUB 1.97~beta4)

me@mine:~$ sudo aptitude install grub-pc
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  ca-certificates-java{u} icedtea-6-jre-cacao{u} java-common{u} 
  libaccess-bridge-java{u} libaccess-bridge-java-jni{u} libice-dev{u} 
  libjline-java{u} libpthread-stubs0{u} libpthread-stubs0-dev{u} 
  libsm-dev{u} libx11-dev{u} libxau-dev{u} libxcb1-dev{u} libxdmcp-dev{u} 
  libxt-dev{u} openjdk-6-jdk{u} openjdk-6-jre{u} openjdk-6-jre-headless{u} 
  openjdk-6-jre-lib{u} rhino{u} x11proto-core-dev{u} x11proto-input-dev{u} 
  x11proto-kb-dev{u} xtrans-dev{u} 
0 packages upgraded, 0 newly installed, 24 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 132MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 203424 files and directories currently installed.)
Removing openjdk-6-jdk ...
Removing openjdk-6-jre ...
Removing icedtea-6-jre-cacao ...
Removing libaccess-bridge-java-jni ...
Removing libaccess-bridge-java ...
Removing libxt-dev ...
Removing libsm-dev ...
Removing libice-dev ...
Removing libx11-dev ...
Removing libxcb1-dev ...
Removing libpthread-stubs0-dev ...
Removing libpthread-stubs0 ...
Removing libxau-dev ...
Removing libxdmcp-dev ...
Removing x11proto-core-dev ...
Removing x11proto-input-dev ...
Removing x11proto-kb-dev ...
Removing xtrans-dev ...
Removing ca-certificates-java ...
Removing rhino ...
Removing libjline-java ...
Removing openjdk-6-jre-headless ...
Removing openjdk-6-jre-lib ...
Removing java-common ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 2 removed doc-base file(s)...
Registering documents with scrollkeeper...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done

---

### Post by wilee-nilee on 2010-06-28
**Could you be more concise as to what the problem is**.

So your original thread was here, did you fix XP?
[http://ubuntuforums.org/showthread.php?p=9523778#post9523778](http://ubuntuforums.org/showthread.php?p=9523778#post9523778)

The description here has no mention of XP is it still on your computer?
The description here is also very convoluted with to much information.

**Post the bootscript in my signature in code tags as described.**

---

### Post by cariboo on 2010-06-28
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Innigo on 2010-06-29
Ok, 1 thread, 2 problems:
1.) Got Grub1.97~beta4 over XP MBR and wanted Grub2 
    I ran  "sudo aptitude install grub-pc" but got openjdk-6 et. al. uninstalled and no Grub2.
2.) Wanted to upgrade to 10.04LTS but Synaptic offered no upgrade after [Check]
    I was interested in the option where 10.04 upgrade would try out a chainloaded Grub2.

Yes, XP is still there, lurking at the bottom of the grub boot menu, waiting to "fix" my Linux with chkdsk. The XP partition is all backed up and this is a developer machine. I've run bootscriptinfo.sh and RESULTS.TXT is here:

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3d4c6192

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   112,197,959   112,197,897   7 HPFS/NTFS
/dev/sda2         112,197,960   156,296,384    44,098,425   5 Extended
/dev/sda5         112,198,023   154,368,584    42,170,562  83 Linux
/dev/sda6         154,368,648   156,296,384     1,927,737  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7613AAB7242BDC06                       ntfs       SYSTEM                        
/dev/sda5        e558305e-ec67-4bbd-bf73-dc8392392c9b   ext4                                     
/dev/sda6        28f23be2-dd8a-408c-b226-072d5bc3cbbc   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\="Microsoft Windows"  

=========================== sda5/boot/grub/grub.cfg: ===========================

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
insmod ext2
set root=(hd0,5)
search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
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
menuentry "Ubuntu, Linux 2.6.31-22-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-22-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-22-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro single 
    initrd    /boot/initrd.img-2.6.31-22-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-21-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-21-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro single 
    initrd    /boot/initrd.img-2.6.31-21-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set e558305e-ec67-4bbd-bf73-dc8392392c9b
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 7613aab7242bdc06
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=e558305e-ec67-4bbd-bf73-dc8392392c9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=28f23be2-dd8a-408c-b226-072d5bc3cbbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  57.7GB: boot/grub/core.img
  58.9GB: boot/grub/grub.cfg
  59.0GB: boot/initrd.img-2.6.31-14-generic
  60.9GB: boot/initrd.img-2.6.31-20-generic
  61.1GB: boot/initrd.img-2.6.31-21-generic
  62.5GB: boot/initrd.img-2.6.31-22-generic
  59.1GB: boot/vmlinuz-2.6.31-14-generic
  60.5GB: boot/vmlinuz-2.6.31-20-generic
  64.1GB: boot/vmlinuz-2.6.31-21-generic
  61.6GB: boot/vmlinuz-2.6.31-22-generic
  62.5GB: initrd.img
  61.1GB: initrd.img.old
  61.6GB: vmlinuz
  64.1GB: vmlinuz.old

```

---

### Post by dino99 on 2010-06-29
sorry guy but what a mess in your head :confused: (you repair windoz with windoz tool; and linux with linux tools)

maybe its time to do something cleaner

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Innigo on 2010-06-29
Thanks for your response wilee-nilee. As for dino99's comments, it looks more like there's something wrong with your head. I'm not trying to repair XP. If you can't be bothered reading my post why bother replying. Perhaps you should re-read the Forum DO'S and DON'T's I was so recently referred to.

I suppose the real question I have is this:
Why would  "sudo aptitude install grub-pc" remove my openjdk and then do nothing else that it was expected to based on the Upgrading to GRUB2 guide at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
What would be the cleanest way to repair my _Linux_ install? 

If I were to run   sudo grub-mkconfig && update-grub  would this complete the abortion of an install of grub-pc and reinstall my openjdk?

---

### Post by Innigo on 2010-07-06
Ok, so once again in answer to my own questions:

update-grub   would have written my changes to disk but as I didn't do this no changes were made (except the mysterious uninstall of my openjdk which I simply reinstalled with Synaptic thus repairing my Eclipse.)

grub-mkconfig is another way(soon to be deprecated) to update grub according to ranch hand.
([http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211))


In summary:
No, I wasn't worried about nothing and yes, chkdsk was intent on destruction of my new Linux system. Windows _will_ overwrite my MBR the first chance it gets as it currently stands so yes, maybe it is something akin to the old browser wars.

Grub1.97~beta4 is halfway between Grub legacy and Grub2 as far as I can make out. Some links I've found(eg. [http://members.iinet.net/~herman546/p20.html]("http://members.iinet.net/%7Eherman546/p20.html")) refer to it as Grub2 yet it seems to behave the same as Grub Legacy is said to.

Unless you're prepared to read a lot of doco, don't even think about it if you're new to Grub. I would have liked to go straight to 10.04LTS with Grub2 and not have to worry about Grub legacy but it seems I came in just at the wrong time.

Yes, an upgrade to Grub2 will be provided but at the moment it's still a bit new and unstable. Avoid 9.10 and 10.04 Desktop Install CD's if you want chainloading and/or a boot partition(as I did.) If you're nervous about losing access to an important dual boot system, I'd hold off a while or just use the BIOS to boot to entirely different hard disks.

---

