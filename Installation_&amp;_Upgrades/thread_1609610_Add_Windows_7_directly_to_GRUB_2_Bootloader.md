---
title: "Add Windows 7 directly to GRUB 2 Bootloader?"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by molotov256 on 2010-10-30
Hey all, great forum here... been lurking and learning a lot of stuff on here - much obliged!

Anyhow, I'm a n00b to the Linux world, so I installed it on my Windows 7 desktop to dual boot.  Current configuration is as such:

160GB HDD with 3 partitions:  Ubuntu Studio 10.10 on one, Win 7 on another, and the third is for storage.
1TB HDD for extra storage.

So far, all is well, but I'm not pleased with the default GRUB options and layout.  It gives me 4 options to choose:

-Ubuntu Studio
-Memtest
-Memtest Debug Mode (or something to that effect)
-Windows 7 (Bootloader)

When I select the Windows 7 option from GRUB, it launches my old Windows 7 bootloader from which I have to choose Windows 7 again (other options include a nonexistent former Win XP install and Recovery Console).  Granted, it boots successfully, so it's not a major issue, but it's redundant and bothers me.  

My Goals:
-Make Win 7 to appear in GRUB and launch the OS directly when selected.
-Remove the Memtest options from GRUB

I've read lots of articles about editing *menu.lst* but that's not applicable to the GRUB version that came with UbuntuStudio 10.10 as I understand it.  I've also scanned through some other articles about editing GRUB2 specifically, but it's a lot of info to digest and I think much of it is over my head.

Any help is much appreciated!  Thank you!

---

### Post by mikewhatever on 2010-10-30
It looks like you really need to edit the Windows bootloader which seems to have too many options. Can you post the output of **sudo fdisk -l** from Ubuntu.

---

### Post by molotov256 on 2010-10-30
Ty for quick response, Mike!  You may well be onto something with my windows bootloader.  I'll look into that more now.  (See how us Windows users are?  Immediately blaming Ubuntu, lol..)

In the meantime, here's my **sudo fdisk -l** output:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa8aba8ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3854    30957223+   7  HPFS/NTFS
/dev/sda2            3855       18133   114696037    f  W95 Ext'd (LBA)
/dev/sda3           18134       19458    10636288   83  Linux
/dev/sda5            3855       18133   114696036    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9f9ef0c8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS


If you find what you're looking for in there, would you be so kind as to tell me what you're looking for in that output?  Trying to learn as I go with this stuff...

---

### Post by Jetso on 2010-10-30
To remove memtest, do this:

```
sudo chmod -x /etc/grub.d/20_memtest86+
```
To make memtest appear, do:

```
sudo chmod +x /etc/grub.d/20_memtest86+
```
Then run ```
sudo update-grub
```

And BAM! it's gone

---

### Post by mikewhatever on 2010-10-30
> **Jetso said:**
> To remove memtest, do this:

[....
And BAM! it's gone

Who said the OP wants to remove memtest?

---

### Post by Jetso on 2010-10-30
> **molotov256 said:**
> 
My Goals:
-Make Win 7 to appear in GRUB and launch the OS directly when selected.
**_-Remove the Memtest options from GRUB_**



The OP says :P

---

### Post by drs305 on 2010-10-30
I believe what *mikewhatever* suggested is the course you have to take. You'll probably have to adjust the W7 boot files. 

When two versions of Windows are installed the second adds it's info to the existing bootloader, which I think is why you have a two step process once you get into Windows.

If you post the contents of the boot info script Windows guys will be able to tell you how to fix it. When ready to paste the RESULTS.txt, press the # icon in the post's menubar to generate 'code' tags and paste between them.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by molotov256 on 2010-10-30
Sweet... the response times on this forum are nearly overwhelming, but that's a good thing.  Thanks!

@Jetso -  Thank you - that did the trick!  The CLI in Linux is great when people tell me what to type :rolleyes:.  I can't help but wonder why Memtest is a default boot option; it's a useful tool to have in one's diagnostic arsenal, but how often am I going to want to test the RAM on the same machine?

@Mike & DRS305 - I'm working with my BOOTMGR now, but I'm having a hell of a time getting recovery console off of it.  I got rid of the Win XP entry, though, so I'm on the right track.

Here's the requested RESULTS of the Boot Info Script.  Should I start a new thread for the Windows related boot issues?

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #3 for (,msdos3)/boot/grub.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,914,509    61,914,447   7 HPFS/NTFS
/dev/sda2          61,914,571   291,306,644   229,392,074   f W95 Ext d (LBA)
/dev/sda5          61,914,573   291,306,644   229,392,072   7 HPFS/NTFS
/dev/sda3         291,307,520   312,580,095    21,272,576  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63 1,953,520,064 1,953,520,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        A4BC5DFBBC5DC906                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        13599496-fc16-4a18-a86f-54cbfb65be2f   ext4                                     
/dev/sda5        D01A64EE1A64D2D0                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        F220362E2035F9E5                       ntfs       Images                        
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda3        /                        ext4       (rw,errors=remount-ro,commit=0)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=2 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

=========================== sda3/boot/grub/grub.cfg: ===========================

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
set default="4"
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

insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 13599496-fc16-4a18-a86f-54cbfb65be2f
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos3)'
search --no-floppy --fs-uuid --set 13599496-fc16-4a18-a86f-54cbfb65be2f
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=15
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 13599496-fc16-4a18-a86f-54cbfb65be2f
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=13599496-fc16-4a18-a86f-54cbfb65be2f ro  splash  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set 13599496-fc16-4a18-a86f-54cbfb65be2f
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=13599496-fc16-4a18-a86f-54cbfb65be2f ro single  splash
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set a4bc5dfbbc5dc906
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

=============================== sda3/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=13599496-fc16-4a18-a86f-54cbfb65be2f /               ext4    errors=remount-ro 0       1

=================== sda3: Location of files loaded by Grub: ===================


 149.3GB: boot/grub/core.img
 153.7GB: boot/grub/grub.cfg
 150.1GB: boot/initrd.img-2.6.35-22-generic
 149.3GB: boot/vmlinuz-2.6.35-22-generic
 150.1GB: initrd.img
 149.3GB: vmlinuz
```

---

### Post by mikewhatever on 2010-10-30
> **Jetso said:**
> The OP says :P

Indeed, thanks for noticing.

---

### Post by drs305 on 2010-10-30
> **molotov256 said:**
> 
@Mike & DRS305 - I'm working with my BOOTMGR now, but I'm having a hell of a time getting recovery console off of it.  I got rid of the Win XP entry, though, so I'm on the right track.

Here's the requested RESULTS of the Boot Info Script.  Should I start a new thread for the Windows related boot issues?


Since your original thread title references W7 I think you should be good keeping things in this thread. If you stop getting responses then you might reconsider...

I edited your post slightly, changing the 'QUOTE' tags to "CODE" tags just to take up less window space.

If you can get one of the Grub menu entries to boot directly to your Win7 OS you have won the battle. Hiding or renaming the Recovery mode option is fairly straightforward.  (Really geeky, but straightforward.)

Here's a thread I created for tweaking the Grub entriy titles. Section 4 is probably what you want. If it's too confusing, just ask for help.

[Grub 2 Title Tweaks Thread]("http://ubuntuforums.org/showthread.php?t=1287602")

---

### Post by molotov256 on 2010-10-30
@DRS:  I checked out that link and looked at #4, and I don't know if we're talking about the same thing... I'm not trying to hide the partition from the boot menu - just the option of booting to Recovery Console.  I believe RC is installed on the same partition as W7 is, so I'd like to avoid hiding the whole partition lest GRUB lose track of Windows in it's entirety.

Ironically, the whole reason I have Recovery Console installed on a W7 machine is from using ComboFix to remove rootkits which I wouldn't have gotten if I'd just been using Ubuntu in the first place.

---

### Post by drs305 on 2010-10-30
It could be one of the other menu tweaks that you might want - the idea being that you have 2 Windows entries on your Grub menu and you don't want to see one of them. You can hide it from the menu by excluding the partition, excluding by the title, or several other methods. Of course, you may want to see a second option.

Some users had automatically-created Windows menu options that would boot to a restore mode rather than the normal install. Other users found they had to select the "Recovery" option to boot into their normal Windows install and didn't like the name. That's why I put them in the tweaks thread.

If you end up with a menu entry you don't want to see, or want one renamed, it can be done within the Grub2 scripts; or you can create a custom menu just for Windows and just turn off the 'search' script that looks for Windows and other OS entries. If you want something like that, we can do it.

---

### Post by molotov256 on 2010-10-30
Got it!!!  Woot!

Turns out I still had a boot.ini file hidden on my C:\ Drive, and that's what was giving the option to boot to Recovery Console.

Since I am no longer using Win XP, I just deleted the antiquated boot.ini file, and now when I select Windows 7 (loader) from GRUB, there are no other superfluous options, so it loads Win 7 without delay.

For anybody who's still actively using WinXP and wants to remove the recovery console option from their startup, all you need to do is edit your boot.ini file (don't delete it though!).  Good directions from Microsoft available in the knowledge base:

[http://support.microsoft.com/kb/555032](http://support.microsoft.com/kb/555032)

This whole situation had thrown me for a loop because I previously had this computer set up to dual boot XP and W7.  Since I had formatted my XP partition to make way for Ubuntu, I was surprised to see options for the XP related Recovery Console popping up still.  Silly ComboFix installed the antiquated boot options to my W7 partition!  I was just looking in the wrong places.

Still, all's well that ends well... great success!  Thanks to all for the uber fast responses.  Ubuntu is leaving a nice taste in my mouth already.  I've got plenty more n00b tasks to tackle what with printers and MIDI interfaces and all, so I'm sure you haven't seen the last of me yet.   Thanks again!

@DRS - Do I change the tag on this thread to SOLVED or does an admin do that?

---

### Post by drs305 on 2010-10-30
Glad you have it sorted out.

When a user has no more questions in the particular thread, it's helpful if you mark it SOLVED. That allows others seeking threads with solutions to find them, and lets the 'helpers' concentrate on unresolved problems.

You mark it SOLVED via the 'Thread Tools' link near the top right of the first post. (It's also reversible).

Happy Ubuntu-ing !

---

