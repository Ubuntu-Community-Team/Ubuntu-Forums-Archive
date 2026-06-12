---
title: "Yet another dualboot thread (Win7)"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by dedede on 2010-08-23
Hello everybody, I finally managed to install Ubuntu (10.04). But when I did I wasnt able to boot to Windows anymore.
Allow me to post the partitions of my harddrive:

[img]http://a.imageshack.us/img90/618/gparted.jpg[/img]
I have numbered the 'volumes' aka partitions so I'll explain what is for what:

1) Do not ask me where the heck that 200 mb unallocated space came from, I tried to merge it with my Windows ntfs partition and the whole partition became corrupt (black and white in GParted), the windows recovery cd couldn't do anything, so I had to spend several hours recovering my PC to factory state with the Hewlett Packard recovery discs and spends some more 15 minutes reinstalling Ubuntu. Not to mention all the programs I had on both OS's. So yeah, I'm too frustrated to touch that again.

2) This is the Windows 7 partition, the 'C' volume. This is where the OS is and I want to GRUB to load this.

3 - 4 - 5 - 6) Ubuntu partitions inside the (3) extended partition.

7 - 8) This is the part I thought you veterans might not be familiar with, because this was created by the OEM, Hewlett Packard. These 2 are used for restoring the PC to factory state and hardware diagnosis. Probably some bios stuff as well so I dont want to mess with it.

So the problem is that the 7th partition (3rd primary) is added to the GRUB menu instead, as a Vista boothloader, but it is really the 'HP Recovery Environment' - by the look of it its really Windows which only runs the HP programs.

I would also like to mention that there was another primary partition, "System", or Windows7 recovery. So yeah all the 4 primary partitions were taken and it took me alot of headaches to find out which of the partitions can be deleted to make room for another OS. Things like this should be made illegal - you buy a PC and cant install another OS, delete the wrong partition and you void your warranty.

Anyways, I deleted the Windows7 recovery partition, because according to the windows forums, it does the same as the windows recovery discs (which I have made several copies just for safety).

Now how can I tell GRUB to start Windows 7 (on 2nd primary partition) and not the HP REcovery partiton (3rd)?

---

### Post by clrg on 2010-08-23
Frankly I'm too lazy to write a tutorial here,:p so please read this:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by dedede on 2010-08-23
Tutorial detected. Brain shutting down...

I got stuck in the 1st paragraph:
I tried
```

cd /boot/grub/
gedit menu.lst

``` the file seams to be empty.
Help.

---

### Post by dedede on 2010-08-23
Yeah i browsed to the file and its empty. Really weird

---

### Post by clrg on 2010-08-23
That's because of GRUB2 (new version). For some sadistic reason, they decided to redesign the whole configuration.

This is a very good guide for the configuration of GRUB2: [http://linuxers.org/howto/how-configure-grub2-ubuntu-910](http://linuxers.org/howto/how-configure-grub2-ubuntu-910)

---

### Post by dedede on 2010-08-23
I'm sorry if I sound lazy but can you tell me what exactly must I do? Because this is my 1st experience with boothloaders in general.

What do I have to do? Tell it that the C ntfs partition should have its own place in the GRUB menu? Or what?

---

### Post by fil9 on 2010-08-23
Hi dedede,

In a terminal in Ubuntu do

"sudo update-grub" in order to Grub2 to automatically add new bootable partitions to its config file: while it does it, you should see scrolling in the terminal window new partitions being added to the boot menu of Grub2.

See here for all related Grub2 tutorial and configuration:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Excerpt: 
**[COLOR=Navy][SIZE=3]"Adding Entries to Grub 2[/SIZE][/COLOR] **
Menu entries can be added to [COLOR=DarkRed]grub.cfg[/COLOR] automatically or manually.
[LIST]
[*][SIZE=3]**[COLOR=DarkRed]Automatically.[/COLOR]**[/SIZE]
[LIST]
[*]When "[COLOR=Navy]*update-grub*[/COLOR]" or "[COLOR=Navy]*update-grub*[/COLOR]"  is executed, Grub 2 will search for linux kernels and other Operating  Systems. What and where is looks is based on the files contained in  /etc/grub.d folder.
[LIST]
[*][COLOR=DarkRed]10_linux[/COLOR] searches for installed linux kernels on the same partition.
[*][COLOR=DarkRed]30_os-prober[/COLOR] searches for other operating systems."
[/LIST]
 
[/LIST]
 
[/LIST]
Hope this helps.

fil9

---

### Post by dedede on 2010-08-23
That didn't work. Its still only the 'Vista bootloader' only, which starts HP System Restore, which nukes all the partitions except itself and reinstalls Windows 7 (factory state).

Guys I really need to know if there is another way. If Ubuntu killed the Windows 7 boot files then I shouldn't wait any longer. I need Windows for important programs.

---

### Post by dedede on 2010-08-23
Also, the manual: [https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows) Says if youre using 10.04, then \"Sorry, definitely use this guide \":  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) But this page is too general. Yes I can\'t find what I actually need to type/create/add! Same for this \'tutorial\': [http://linuxers.org/howto/how-configure-grub2-ubuntu-910](http://linuxers.org/howto/how-configure-grub2-ubuntu-910) It doesnt tell what I need to type if I want to dualboot with Windows7. How am I supposed to know what do write in the script? I cant believe there isnt any guide for windows 7 users. I thought Ubuntu is supposed to be the most user friendly distro out there. Yes I\'m very tired of this. I had to reformat and reinstall my PC which took several hours because GParted corrupted my C drive and I couldnt restore it, then I reinstall Ubuntu and for 2 days cant figure out how to access Windows. Its just too much...

---

### Post by dedede on 2010-08-23
Also, the manual: [https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows) Says if youre using 10.04, then \"Sorry, definitely use this guide \":  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) But this page is too general. Yes I can\'t find what I actually need to type/create/add! Same for this \'tutorial\': [http://linuxers.org/howto/how-configure-grub2-ubuntu-910](http://linuxers.org/howto/how-configure-grub2-ubuntu-910) It doesnt tell what I need to type if I want to dualboot with Windows7. How am I supposed to know what do write in the script? I cant believe there isnt any guide for windows 7 users. I thought Ubuntu is supposed to be the most user friendly distro out there. Yes I\'m very tired of this. I had to reformat and reinstall my PC which took several hours because GParted corrupted my C drive and I couldnt restore it, then I reinstall Ubuntu and for 2 days cant figure out how to access Windows. Its just too much...

---

### Post by clrg on 2010-08-23
Have you tried running update-grub? It should detect the Faildows installation.

If you desperately need to boot Faildows, insert the Faildows-CD, boot a recovery shell and run fixmbr.

---

### Post by kansasnoob on 2010-08-23
Please post the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Another set of instructions for running the Boot Info Script:

[http://ubuntuforums.org/showpost.php?p=8104352&postcount=1](http://ubuntuforums.org/showpost.php?p=8104352&postcount=1)

---

### Post by dedede on 2010-08-23
Dude, look few posts before? They guy suggested, I tried, reported back that it didnt work.
As for 'faildows' cd, I have even tried that. To my surprise if boothing from cd... it is skipped and grub starts instead!
And no, I dont need 'faildows', I need programs which depend on 'faildows', which arent available on Linux (alternatives are different things, and this is a completely different discussion...). Please lets not talk about this

EDIT: This is not to the post right above me which just appeared.

---

### Post by clrg on 2010-08-23
If your BIOS skips booting from CD you need to change the options or tell it to boot from CD manually.

---

### Post by fil9 on 2010-08-23
Hi,

Don't panic!
Take a look here
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
go to chapter 5.C

In your case, what u want to appear in the booting Grub menu is (also) an entry to boot your W7 partition, i.e., that points to /dev/sda1.

[http://www.dedoimedo.com/images/computers_new_2/grub2-upgrade-windows-entry.jpg](http://www.dedoimedo.com/images/computers_new_2/grub2-upgrade-windows-entry.jpg)

The file "/boot/grub/grub.cfg" has either to be built/updated correctly when u issue the "sudo update-grub" command or u have to edit/correct the entry for W7 (check the article).

Try to re-install grub in the MBR:

"sudo grub-install /dev/sda"

[http://www.dedoimedo.com/computers/grub-2.html#mozTocId232162](http://www.dedoimedo.com/computers/grub-2.html#mozTocId232162)

Good luck,

fil9

---

### Post by dedede on 2010-08-23
> **clrg said:**
> If your BIOS skips booting from CD you need to change the options or tell it to boot from CD manually.
It didnt beofore, and it works for the Ubuntu Live CD, so... Im guessing the ntfs partition really is corrupt...

output of the BOOT INFO SCRIPT:
```

              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       529365896 sectors, but according to the info from 
                       fdisk, it has 336022533 sectors.
    Mounting failed:
Failed to read last sector (529365896): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
Failed to read last sector (529365896): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1             409,600   336,432,133   336,022,534   7 HPFS/NTFS
/dev/sda2         336,433,150   941,938,687   605,505,538   5 Extended
/dev/sda5         336,433,152   918,587,391   582,154,240  83 Linux
/dev/sda6         918,589,440   941,938,687    23,349,248  82 Linux swap / Solaris
/dev/sda3         941,938,688   976,560,127    34,621,440   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7A8A7FE38A7F9A79                       ntfs                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3        BCA0F61CA0F5DCB8                       ntfs       RECOVERY                      
/dev/sda4        EEA0-3218                              vfat       HP_TOOLS                      
/dev/sda5        d8b9a188-f14e-44d0-bb0e-93551ddc6453   ext4                                     
/dev/sda6        047caa1e-e7f1-4ddd-a97e-2a295f04f73f   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=d8b9a188-f14e-44d0-bb0e-93551ddc6453 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=d8b9a188-f14e-44d0-bb0e-93551ddc6453 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d8b9a188-f14e-44d0-bb0e-93551ddc6453 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=d8b9a188-f14e-44d0-bb0e-93551ddc6453 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set d8b9a188-f14e-44d0-bb0e-93551ddc6453
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set bca0f61ca0f5dcb8
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
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=d8b9a188-f14e-44d0-bb0e-93551ddc6453 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=047caa1e-e7f1-4ddd-a97e-2a295f04f73f none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 215.3GB: boot/grub/core.img
 350.7GB: boot/grub/grub.cfg
 215.3GB: boot/initrd.img-2.6.32-21-generic
 215.4GB: boot/initrd.img-2.6.32-24-generic
 215.3GB: boot/vmlinuz-2.6.32-21-generic
 215.3GB: boot/vmlinuz-2.6.32-24-generic
 215.4GB: initrd.img
 215.3GB: initrd.img.old
 215.3GB: vmlinuz
 215.3GB: vmlinuz.old

```

---

### Post by clrg on 2010-08-23
It looks like your NTFS partition is corrupted. I guess that's why you can't boot it anymore..

Did you do backups?

---

### Post by dedede on 2010-08-23
What, this again? Give me a break X0
All I did was delete the recovery partition of windows 7 to free at least 1 primary partition, because the lousy OEM and Micro$oft had filled all 4 of them. I have asked this in at least 2 windows forum if its okay to delete that. That partition is the same as the recovery discs (by content). How could that affect the other partition? maybe the booth files are there? But that would be even more silly, microsoft.

Oh well, another few hours spend on HP Recovery Discs, reinstalling Ubuntu and programs........................

---

### Post by clrg on 2010-08-23
Deleting the recovery partition(s) alone didn't affect the other filesystems. It must be someting else. Did you resize the NTFS partition?

---

### Post by dedede on 2010-08-23
> **clrg said:**
> Deleting the recovery partition(s) alone didn't affect the other filesystems. It must be someting else. Did you resize the NTFS partition?
Well actually I did. How was I supposed to add more space for Linux? Thats what most tutorials suggest. You think GParted messed when I resized it?

---

### Post by kansasnoob on 2010-08-23
I know you're frustrated but please be patient and give me a while to type ;)

If you can still boot into Ubuntu please start by installing "gparted":

```
sudo apt-get install gparted
```

It should then show up in System > Administration > Gparted (Partition Editor). Open it, right click on /dev/sda1 and select "Check". See what the details show, then run the Boot Info Script again.

You needn't post the results but just see if the results are different for /dev/sda1. I have doubts that will help but it's simple and the results may be helpful.

In the meanwhile I need to check out something about "testdisk". That may be useful, but I'm not sure. Do not try to boot anything but Ubuntu until I get another post typed please :D

---

### Post by fil9 on 2010-08-23
Well, if your W7 partition was enough fragmented before u partioned it with GParted (or any other partition tool for that matter) and you didn't defragment it from within W7, it is possible that vital boot files, i.e, **\bootmgr** and/or **\boot\bcd** were damaged/corrupted/erased, making obviously W7 unbootable.

Look here:

[http://www.sevenforums.com/general-discussion/89584-lost-boot-files-boot-into-w7.html](http://www.sevenforums.com/general-discussion/89584-lost-boot-files-boot-into-w7.html)

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html?ltr=B](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html?ltr=B)

---

### Post by dedede on 2010-08-23
There is a warning sign on the ntfs partition. When I try to fix it it fails.

---

### Post by kansasnoob on 2010-08-23
A few additional observations and hints for future knowledge.

1) Never move the beginning (left side) of a Windows OS partition! It hoses things!

2) Never use Gparted to resize a Windows 7 or Vista partition! Use only the Vista/Win 7 utility:

[http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/](http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/)

3) Grub 2 is recognizing /dev/sda3 as a boot partition because of this:

> sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    **[COLOR="Red"]Boot files/dirs:   /bootmgr /boot/bcd[/COLOR]**

OEM Win 7 installs frequently spread the boot files between two partitions!

Not too sure which way we should go with that. If we're able to save that Win 7 OS partition **[COLOR="Red"]trying to boot into sda3 again will result in the exact same thing though![/COLOR]**

Even if you reinstall Windows again as long as grub2 sees sda3 as "boot" you're going to end up with the same thing again so lets get a plan in order before doing anything else, OK?

Next post I'll begin to discuss options!

---

### Post by dedede on 2010-08-23
Thats iiiiiiiiiiiiiiiiiiiiiiiit. Wooohooo

---

### Post by dedede on 2010-08-23
No wait, i just read your post. I had FORGOTTEN to defrag the harddrive. Are you telling me that wasnt the cause?

---

### Post by kansasnoob on 2010-08-23
> **dedede said:**
> Thats iiiiiiiiiiiiiiiiiiiiiiiit. Wooohooo

What's it?

My extra sensory perception isn't working today.

---

### Post by clrg on 2010-08-23
Well yes, that could be the problem. You see, NTFS support in Linux and OSX has been achieved by reverse-engineering NTFS. M$ stubborn unwillingness to share the specifications make it very difficult to implement a stable and reliable NTFS module.

So it is possible, but unlikely gparted corrupted your NTFS partition when reducing it.


Usually people plan their dualboot systems before they install any operating system. I know that most tutorials say you can resize the NTFS partition easily, but I don't recommend that - for obvious reasons. 

I know this is not very helpful to you, but the next time you want to dualboot, plan your partitioning before installing anything.

---

### Post by kansasnoob on 2010-08-23
Well, going back to your first post you said:

> Do not ask me where the heck that 200 mb unallocated space came from

Don't worry about that. That's common with larger discs. Those tiny unpartitioned bits don't harm a thing.

> I tried to merge it with my Windows ntfs partition and the whole partition became corrupt

Yep! Moving the beginning of a Windows partition hoses things!

> I had to spend several hours recovering my PC to factory state with the Hewlett Packard recovery discs

So, you actually did a fresh install with the HP discs? Or a recovery? If it's a fresh install no defragging should have been necessary.

Do you have data in the Windows partition that you need to save? If not I'm actually thinking a fresh install might be best, but that Recovery partition will continue to raise havoc! Since you have the recovery discs why do you need the recovery partition?

If you leave the recovery partition there you'll need to do some editing in grub2 **before trying to boot Windows** whether you somehow recover the Win partition or reinstall!

The editing would go something like this:

1) Add the proper Win 7 entry to "/etc/grub.d/40_custom" something like this:

```
menuentry "Windows 7 (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set **properUUID#**
    chainloader +1
}
```

2) Hide the wrong entry created by os-prober in "/etc/grub.d/30_os-prober" by making it "non-executable" with the command "sudo chmod -x /etc/grub.d/30_os-prober". That of course will also "hide" any additional OS's you may install later!

**[COLOR="Red"]Note: That is only an example![/COLOR]**

I guess I need some of the above questions answered before knowing what to do next. I'm honestly not sure if testdisk would be helpful or not:

[http://www.cgsecurity.org/wiki/Running_TestDisk](http://www.cgsecurity.org/wiki/Running_TestDisk)

I'm hardly proficient with it. I just always read the documentation and muddle my way through.

I may be unavailable for a while, sorry.

---

### Post by dedede on 2010-08-23
> **kansasnoob said:**
> What's it?
I wasnt talking to you. I meant I had forgotten to defrag the harddrive, but youre right. It was a brand new install... so maybe thats not it.

> **clrg said:**
> next time you want to  dualboot, plan your partitioning before installing anything.
Sorry what do you mean by "plan" here?


> Yep! Moving the beginning of a Windows partition hoses things!gee its so great that none of the tutorials mention that ))))

> So, you actually did a fresh install with the HP discs? Or a recovery?  If it's a fresh install no defragging should have been necessary.Yep, fresh install. The 4 'recovery' dvds which you can create from the Recovery partition do exactly the same as that partition. For some reason the discs can be created only once. I dont see any logic in that because you can make a copy of a copy anyways.
Those discs or the Recovery partition nuke all the other partitions and reinstall everything which you could find when you started your PC the 1st time. I would be happy with a single Windows 7 disc.

> 
Do you have data in the Windows partition that you need to save? If not  I'm actually thinking a fresh install might be best, but that Recovery  partition will continue to raise havoc! Since you have the recovery  discs why do you need the recovery partition?
I just did it. I'm on 7 now. Why will the recovery partition do any harm again? What has it done till now other than add another option in GRUB?
I think the problem here Im facing is that I might void my warranty if if I delte HP's partitions. Although I have been told in Windows forums that deleting Window's own recovery partition shouldnt bring any warranty problems, i am not sure about HP's. Another problem is one of the discs can get damaged and then I'm dead.

> 
If you leave the recovery partition there you'll need to do some editing  in grub2 **before trying to boot Windows** whether you somehow  recover the Win partition or reinstall!
I'll need to edit grub2 ONLY ONCE before accessing Windows? Doesnt sound like a big deal...  

> **[COLOR=Red]Note: That is only an example! [/COLOR]**  So i shouldnt use it for safety reasons, right?

> I'm honestly not sure if testdisk would be helpful or not:I already reformatted and reinstalled HP/Windows partitions. Was it for recovery? Too late...

So let me get this straight...
I should
1) delete windows recovery partition again
2) defrag and resize ntfs with Windows tools only
3) install linux on the freed space
4) run grub-update from linux command shell?

Or should I wait till you find out how 'dangerous' the HP Recovery Partition is/ find another solution?

[B][COLOR=Red]
[/COLOR][/B]

---

### Post by dedede on 2010-08-23
Very interesting read:
[http://h30434.www3.hp.com/t5/Operating-systems-and-software/How-am-I-supposed-to-create-dualboot/m-p/311288](http://h30434.www3.hp.com/t5/Operating-systems-and-software/How-am-I-supposed-to-create-dualboot/m-p/311288)
According  to this topic from their forums it will not affect the HP warranty but 'will probably' affect the Windows warranty, whcih doesnt make any sense whatsoever, dont you think?
> It would probably affect warranty support for Windows 7, but will not  affect your hardware warranty.
By warranty I understand future updates. How can a partition created by HP affect it in any way? I know that guy doesnt speak for HP, but seriously? Its their official forum. (bribed by windows?)

---

### Post by 10snoopy1 on 2010-08-23
> **dedede said:**
> Hello everybody, I finally managed to install Ubuntu (10.04). But when I did I wasnt able to boot to Windows anymore.
Allow me to post the partitions of my harddrive:

[img]http://a.imageshack.us/img90/618/gparted.jpg[/img]
I have numbered the 'volumes' aka partitions so I'll explain what is for what:

1) Do not ask me where the heck that 200 mb unallocated space came from, I tried to merge it with my Windows ntfs partition and the whole partition became corrupt (black and white in GParted), the windows recovery cd couldn't do anything, so I had to spend several hours recovering my PC to factory state with the Hewlett Packard recovery discs and spends some more 15 minutes reinstalling Ubuntu. Not to mention all the programs I had on both OS's. So yeah, I'm too frustrated to touch that again.

2) This is the Windows 7 partition, the 'C' volume. This is where the OS is and I want to GRUB to load this.

3 - 4 - 5 - 6) Ubuntu partitions inside the (3) extended partition.

7 - 8) This is the part I thought you veterans might not be familiar with, because this was created by the OEM, Hewlett Packard. These 2 are used for restoring the PC to factory state and hardware diagnosis. Probably some bios stuff as well so I dont want to mess with it.

So the problem is that the 7th partition (3rd primary) is added to the GRUB menu instead, as a Vista boothloader, but it is really the 'HP Recovery Environment' - by the look of it its really Windows which only runs the HP programs.

I would also like to mention that there was another primary partition, "System", or Windows7 recovery. So yeah all the 4 primary partitions were taken and it took me alot of headaches to find out which of the partitions can be deleted to make room for another OS. Things like this should be made illegal - you buy a PC and cant install another OS, delete the wrong partition and you void your warranty.

Anyways, I deleted the Windows7 recovery partition, because according to the windows forums, it does the same as the windows recovery discs (which I have made several copies just for safety).

Now how can I tell GRUB to start Windows 7 (on 2nd primary partition) and not the HP REcovery partiton (3rd)?


The HP recovery stuff shouldn't contain BIOS settings. If it does, you have problems with your computer.

If you tried to get the extra space into Windows, that is a big don't do. This could screw up Windows in such a way that you would have to reinstall. This is what you should do (good thing you made a backup copy of Windows):

1. Erase hard drive
2. Install Windows FIRST
3. Install Ubuntu LAST since it contains GRUB.


You should see something like Windows 7 (loader) when you boot up after reinstalling. 

Hope this helps... 


10snoopy1

Oh yeah, almost forgot: You will destroy ALL data on the hard drive and lose everything you didn't make a backup of.

---

### Post by 10snoopy1 on 2010-08-23
> **dedede said:**
> Very interesting read:
[http://h30434.www3.hp.com/t5/Operating-systems-and-software/How-am-I-supposed-to-create-dualboot/m-p/311288](http://h30434.www3.hp.com/t5/Operating-systems-and-software/How-am-I-supposed-to-create-dualboot/m-p/311288)
According  to this topic from their forums it will not affect the HP warranty but 'will probably' affect the Windows warranty, whcih doesnt make any sense whatsoever, dont you think?

By warranty I understand future updates. How can a partition created by HP affect it in any way? I know that guy doesnt speak for HP, but seriously? Its their official forum. (bribed by windows?)

Not affecting Windows warranty and affecting Windows warranty in my opinion is the difference between opening up that box and installing windows and returning windows back to the store.

---

### Post by dedede on 2010-08-23
I'm sorry if you think this sounds harsh because it was no way intended to be, but your post was ,um, pointless, except this part:
> **10snoopy1 said:**
> The HP recovery stuff shouldn't contain BIOS settings. If it does, you have problems with your computer.

> 
If you tried to get the extra space into Windows, that is a big don't do. This could screw up Windows in such a way that you would have to reinstall.
maybe but I said the complete opposite.

> 
This is what you should do (good thing you made a backup copy of Windows):
1. Erase hard drive
2. Install Windows FIRST
3. Install Ubuntu LAST since it contains GRUB.


You should see something like Windows 7 (loader) when you boot up after reinstalling. 

This is what I tried and it didnt work. The good portion of the topic posts are about why it didnt work and how to add it to the list, which shows you havent read all of them carefully.

> **10snoopy1 said:**
> Not affecting Windows warranty and affecting  Windows warranty in my opinion is the difference between opening up that  box and installing windows and returning windows back to the  store.
Like what is this supposed to mean?

Anyway, I thank you for your time spent on trying to help me, and again, I didnt want to sound harsh, but please, unless you read all the posts do not post something that has already been talked about.

---

### Post by clrg on 2010-08-23
> **dedede said:**
> 
Sorry what do you mean by "plan" here?


I meant plan as in planning. Defining the course of action. Like scheme, devise, think up, construct, make plans, design (I know my English is far from perfect, but come on, that couldn't have been that wrong ;) ).

---

### Post by dedede on 2010-08-23
What you mean I didnt have a plan?
I wanted to
1) make room for another primary partition (for linux), by deleting Windows\'s recovery partition and creating a recovery disc instead,
2) shrink the ntfs with Gparted from Linux live cd
3) install linux on the new, enlarged unallocated space (format it when installing).
4) make dualboot with GRUB
How was I supposed to know GParted would mess up the ntfs drive?
Well I forgot to defragment, but it WAS a fresh install.

So yeah, some things I couldnt ever expect to happen...  Basically right now Im waiting for kansasnoob\'s reply, because if I was sure that the HP Recovery Partition wouldnt bring problems for GRUB I would simply restart the whole process but use Windows\'s partitioning tools and defragmenting this time.

---

### Post by kansasnoob on 2010-08-23
> It was a brand new install

Then defragging (or the lack thereof) had nothing to do with it!

> 
"Originally Posted by clrg View Post
next time you want to dualboot, plan your partitioning before installing anything."

Sorry what do you mean by "plan" here?


Google! A lot! Read on.

> Yep! Moving the beginning of a Windows partition hoses things!

gee its so great that none of the tutorials mention that ))))

Well, actually the official documentation does mention such problems:

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

I don't like the way it's written:

> **Some people think that the Windows partition must be resized only from within  Windows Vista and Windows 7 using the shrink/resize option.** There are several ways you can reduce the size of a Windows 7 or Vista partition and you can choose either the Windows way or one of the Gnu/Linux methods depending on which one you want to put your faith in. It doesn't really matter which one you choose. Linux programs get the job done faster because you don't need to defrag first, but using the Windows Disk Management would be the more conservative option.

Two of the free Gnu-Linux partition editors are the one built into the Ubuntu CDs installer and GParted Partition Editor.

**If you use GParted Partition Editor in the Ubuntu Live CD be careful. You should remember to remove the check mark in the 'round to cylinders' checkbox , otherwise GParted will dutifully move the entire partition to align it with cylinder boundaries. Unfortunately that takes a long time and when it's finished it usually results in booting problems. **This is because the Windows boot loader is not as sophisticated as Linux boot loaders and depends on block addressing to find parts of itself, so when the partition is moved a little, it gets all mixed up and disjointed. Sometimes it can fix itself automatically but other times it requires repairs from the Windows Installation Disc. If you just remember to remove the check mark you will find that GParted will be able to complete the NTFS resize in a fraction of the time it would have taken otherwise and afterwards Windows will boot just fine.

Some hardware vendors (such as Dell) ship with the maximum of four primary partitions occupied. It is simpler to install Ubuntu on at least one primary partition (using Windows bootloader is required for installing on a logical partition). Using GParted may be preferable in this circumstance to utilize the space occupied by the recovery partition or media direct partition.

The Ubuntu installer has its own inbuilt partitioner so there's really no need to partition your disks before hand if you don't want to. The Ubuntu installer's inbuilt partitioner is based on GParted but it works to a different set of rules and it doesn't move the start of the Windows partition so there's no checkbox to worry about if you decide to carry out the partitioning operating during the installation procedure. Windows will run a normal file system check on first boot-up and then it will boot normally.

**[COLOR="Red"]The Windows Disk Management tool is also very good at shrinking Windows, it's very fast and easy, if you don't count the time it takes to defrag first. [/COLOR]**If you want to use the Windows partition editor to resize Windows, here's how you can do that,

Administrative Tools --> Disk Management tool -> Shrink Volume

This may also be located in Windows Vista and Windows 7:

Settings -> Control Panel -> Administrative Tools -> Computer Management -> Storage -> Disk Management -> Shrink Volume

According to one Windows user:

Unlike Windows XP, Vista and Windows 7 does not allow you to move the MFT (Master File Table) that controls the NTFS file structure within Windows. Inexplicably, Microsoft locates this near the middle (or end) of the partition, somewhat limiting the ability to resize (shrink) the partition completely. Although you will be able to gain some hard drive space from the "Shrink Volume" command, it is likely to be limited.

I knew of no partition software that could move the MFT to a different place on the hard drive safely, but this tutorial suggested that Perfect Disk worked for this purpose. I therefore tried the trial version of Perfect Disk, and it seemed to work for me very nicely. I was able to shrink my Vista partition, using the steps in the tutorial (and Perfect Disk), from 300 Gb to 74 Gb. This was perfect for me.

That sounds like an advertisement for a proprietary disk partitioning utility doesn't it? The letters MFT stand for Master File Table, which means the metadata for the NT File System. For more info on NTFS, [http://en.wikipedia.org/wiki/NTFS](http://en.wikipedia.org/wiki/NTFS)

The point of view of someone who is interested in free, open source software is that GParted in the Ubuntu installer has been used quite successfully by thousands of people for years and there's no reason why you can't just use the Ubuntu installer's inbuilt partitioning program. It uses ntfsprogs, URL [http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php) for NTFS support and the people at ntfsprogs keep up with all of the latest developments in the NTFS file system. The goal of the Linux-NTFS project is to write a better, open source NTFS driver than the Windows one. For more info on NTFS and ntfsprogs, [http://www.linux-ntfs.org/doku.php?id=ntfs-en](http://www.linux-ntfs.org/doku.php?id=ntfs-en)

Trust me here, just never resize Vista or Win 7 with anything but it's own tools!!!!!!!!!!

> "So, you actually did a fresh install with the HP discs? Or a recovery? If it's a fresh install no defragging should have been necessary."

Yep, fresh install. The 4 'recovery' dvds which you can create from the Recovery partition do exactly the same as that partition. For some reason the discs can be created only once. I dont see any logic in that because you can make a copy of a copy anyways.
Those discs or the Recovery partition nuke all the other partitions and reinstall everything which you could find when you started your PC the 1st time. I would be happy with a single Windows 7 disc.

No surprise there. Branded discs just do that, they also install a butt-load of crap you'd as soon not have. OTOH the last time I bought an HP branded puter was around 2001. It had Win ME and it rocked for a long, long time! When everyone else was complaining about Win ME I was rockin' on!

I've since bought several "de-branded" HP refurbs and they do fairly well other than power supplies and optical drives.

**More to follow!**

I've been looking at this for hours as I take breaks from checking roof damage on my outbuildings

**[COLOR="Red"]I need to know the current state of the computer![/COLOR]**.

Please post a fresh output of that Boot Info Script. Then hopefully we can get grub 2 to boot Win 7 properly (without hosing things), or maybe we could get you booting with Easy BCD.

Please be patient!

---

### Post by clrg on 2010-08-23
> **dedede said:**
> what you mean i didnt have a plan?


[quote=clrg]the next time you want to dualboot, make a plan before installing **_anything._**
[/quote]`

---

### Post by 10snoopy1 on 2010-08-23
> **dedede said:**
> I'm sorry if you think this sounds harsh because it was no way intended to be, but your post was ,um, pointless, except this part:


maybe but I said the complete opposite.


This is what I tried and it didnt work. The good portion of the topic posts are about why it didnt work and how to add it to the list, which shows you havent read all of them carefully.


Like what is this supposed to mean?

Anyway, I thank you for your time spent on trying to help me, and again, I didnt want to sound harsh, but please, unless you read all the posts do not post something that has already been talked about.

Okay... Sorry... That is supposed to mean that Windows does NOT have any warranty whatsoever.

---

### Post by dedede on 2010-08-24
> Trust me here, just never resize Vista or Win 7 with anything but it's own tools!!!!!!!!!!
Okay, thats what I said I had in my mind.
> 
**[COLOR=Red]I need to know the current state of the computer![/COLOR]**.
I have used the HP Recovery Discs to set my PC to factory state, again. Now there are 4 primary partitions like from the very beginning (look at 1st post). Again I'm going to delete the Windows recovery partition because I have asked in some windows forums and it seams to be perfectly safe, only "I need to set C as the boot partition for windows to start', because the recovery partition is set to 'boot' by default". I will skip this because grub is going to be set to boot anyway.

If you have nothing else to say against HP's own recovery partition, I will start the resizing of my C drive with Windows tools. But I just can't hurry with my Ubuntu installation. I need to be able to boot to Windows as soon as possible. Is it supposed to be like this?: with an uncorrupt ntfs partition GRUB2 should detect Windows automatically? If theres alot to change manually to get it working I'm not going  to rush with the installation...

---

### Post by wilee-nilee on 2010-08-24
Thread starter kansasnoob is one of the highly skilled helpers on the forums. Don't delete that recovery until you post the boot script. The original bootscript showed missing boot files that are probably in that recovery. It is common to see the computers MS portion to boot from the recovery with OEM's, in order to have a system that can recover from a live or booting syatem with a f-key prompt.

---

### Post by dedede on 2010-08-24
> **wilee-nilee said:**
> Thread starter kansasnoob
I'm the thread starter.

Okay, I'm guessing you didnt read all ther posts as well. Its probably  my karma, happens alot.
> 
Don't delete that recovery until you post the boot script. The original  bootscript showed missing boot files that are probably in that  recovery.How am i supposed to do that without installing Ubuntu? Then how am I  supposed to install Ubuntu without deleting a primary partition  (recovery), since all 4 are taken?

Like I said I have asked this before in Windows forum and they said I  can delete that partition, Ill just need to flag the C partition as  'boot' for it to boot (if not installing any other OS). So are you SURE?

Sorry but where did kansasnoob tell me to not delete the Windows  recovery partition? Are you sure you read it carefully?

Others said the output says my ntfs partition is simply corrupt because I  edited it with a non-windows tool. Youre confusing me.

---

### Post by dedede on 2010-08-24
Also, the 'disc managment' tool of Windows 7 isnt able to delete the Windows Recovery Partition ('System'). I cant find a way to change the flag as well. Should I only use it for disc shrinkage?

---

### Post by dedede on 2010-08-24
Just in case if you meant I should run the boot info script from the Live CD, here is the output:
```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda4: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       409,599       407,552   7 HPFS/NTFS
/dev/sda2             409,600   941,938,687   941,529,088   7 HPFS/NTFS
/dev/sda3         941,938,688   976,560,127    34,621,440   7 HPFS/NTFS
/dev/sda4         976,560,128   976,771,119       210,992   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA7C1D887C1D5105                       ntfs       SYSTEM                        
/dev/sda2        3262A69762A65F7B                       ntfs                                     
/dev/sda3        BCA0F61CA0F5DCB8                       ntfs       RECOVERY                      
/dev/sda4        FE66-46E3                              vfat       HP_TOOLS                      
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /media/apt               iso9660    (ro)
/dev/sda1        /media/SYSTEM            fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

```
i had also defragmented the C drive

---

### Post by fil9 on 2010-08-24
It looks like your /dev/sda2 parttion is just a data partition, no system/boot files in there.
This is a typical OEM windows setup at install/recovery (also for HP).
You should be able to delete it + make free space on it's place (= not format it) with the W7 tools as mentioned previously.
After that, with a GParted live disk (boot Ubuntu disk in live mode, for exemple) you can make that free space as an extended partition, first; inside the newly created extended partition, you can create several logical partitions for Ubuntu, such as root part (/), home part (/home) and swap partition (should be slightly more than RAM if RAM>= 2GB, double of RAM if RAM<=2GB, in order to be able to hybernate without problems).

---

### Post by dedede on 2010-08-24
Sorry but sda2 is 'C' drive of Windows, how can Windows possibly work without it?

---

### Post by wilee-nilee on 2010-08-24
> **dedede said:**
> **I'm the thread starter**

Duh; sorry I left out a comma.:(

---

### Post by dedede on 2010-08-24
[SIZE=3]Okay...[/SIZE]
(should I just get a cracked win7 disc? )

---

### Post by fil9 on 2010-08-24
Ok, correction:
It seems that W7 installs in 2 partitions, a small sda1 with boot files, that appears as SYSTEM, and a big sda2 with all the rest of the Windows files, plus data, etc.
This puts you with a problem of the limit of 4 primary partitions without any need (stupid OEM´s, eheh!).
Anyway, you must achieve to convert sda4 "HP_TOOLS" to a logical partition, either with W7 partition tool or a live Linux CD with GParted (like the Ubuntu CD) or another 3rd party partition tool that you can make it work for your Windows partitions (google "free partition manager").
After this is achieved, you can resize from within W7 after booting into it the partition sda2 (shrink it, leaving after it an unpartitioned free space) and then it applies what I said before "After that, with a GParted live disk (boot Ubuntu disk in live mode, for  exemple) you can make that free space as an extended partition, first;  inside the newly created extended partition,...order to be able to hibernate without problems).".

Hope this helps,

fil9

---

### Post by dedede on 2010-08-25
> **fil9 said:**
> Ok, correction:
It seems that W7 installs in 2 partitions, a small sda1 with boot files, that appears as SYSTEM, and a big sda2 with all the rest of the Windows files, plus data, etc.
This puts you with a problem of the limit of 4 primary partitions without any need (stupid OEM´s, eheh!).
I know that, I explained what each partition is in my first post. but whatever.

> Anyway, you must achieve to convert sda4 "HP_TOOLS" to a logical partitionI have limited knowledge here, but dont I need to delete a primary partition to make an extended one, and then create the 'logical' partitions inside it? But then I would still need to delete one of them, right?

Even if, will the HP Recovery manager recognise/find it then?

---

### Post by dedede on 2010-08-25
Seriously, I actually defragged the c drive and only after that shrinked it with Windows's Disc Management tool and when I restart the computer I'm told that windows could not start and taken to 'Startup Repair', where I'm told that 'some of my programs might be deleted' in the process. So I wait another 15 minutes for the 'repair' to finish and start windows. How LAME is that?

---

### Post by entropy1 on 2010-08-25
My new HP also came with 4 regular partitions: SYSTEM (300.00 MiB), OS (215.59 GiB), HP_RECOVERY (15.00 MIB), and HP_TOOLS (2 GIB).  The first one, which seems to be the one you deleted on your machine, is very important - this partition is used for booting Windows - something about EFI (extensible firmware interface) - you can read about it at

[http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf](http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf)

EDIT: EFI has to do with the HP_TOOLS partition, not the SYSTEM partition.

In order to make room for Ubuntu, backup is the first step.  So I made an image of each partition on an external hard drive using partimage from sysrescuecd

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

(sysrescuecd can also be run from a flashdrive if your machine supports booting from a flashdrive; boots faster than a CD.)

Then I deleted the HP_TOOLS partition.  Next, using GParted from a Live CD (GParted is also on sysrescuecd), I resized the OS partition to make it smaller by dragging the right-hand endpoint to the left.  Then I moved HP_RECOVERY to be next to the reduced-size OS partition.  Now, with a lot of unallocated space at the end of the disk, I created an extended partition, inside of which I make a 2.00 GiB logical partition in which I later restored HP_TOOLS from my external hard drive using partimage.  Inside the extended partition, I also created logical partitions for Ubuntu; e.g., swap and / and /home.  Then I restored the HP_TOOLS partition image to the new 2 GiB logical partition and installed Ubuntu into the logical partitions that I created for it.

---

### Post by dedede on 2010-08-25
Looks like youre right. Yesterday I tried again by resizing C (OS) with Windows disc management, but after deleting the System partition it failed to boot again.
This is very weird because I actually asked this in the official HP forums and I was told that one of the options was to delete System after making the windows recovery disc. I can't believe their official forums could give such wrong advice.

Could you please tell me how you did it again? Maybe its my english. Does the HP system recovery locate the HP_TOOLS partition?

---

### Post by clrg on 2010-08-25
(As far as I know, you can't convert a primary partition into a logical one. You'd need to make an image (man dd), delete the partition, make a new one, and restore the data.)

---

### Post by dedede on 2010-08-25
EDIT: OK...

I'll try the method by [entropy1]("http://ubuntuforums.org/member.php?u=778720") as it has already been tested, just waiting for him to reply...

---

### Post by entropy1 on 2010-08-25
dedede,

Can you be more specific about what you did not understand?

In case it might help, below are pictures of my disk drive before and after:

Before:
[IMG]http://ubuntuforums.org/picture.php?albumid=1990&pictureid=6673[/IMG]

After:
[IMG]http://ubuntuforums.org/picture.php?albumid=1990&pictureid=6674[/IMG]

Note the "lba" flag on HP_TOOLS

---

### Post by dedede on 2010-08-25
Okay, I made a sysrescuecd.

First, whats with the warning signs on the ntfs partitions? I had that when my ntfs was corrupt.
And again, does the HP Recovery environment find the stuff it needs from the HP_TOOLS 'logical' partition you create?

For the parts which I dont get:

EDIT: OK I get it now,i must be blind
> 
I also created partitions for Ubuntu.  Then I restored the HP_TOOLS partition to the 2 GiB space and installed Ubuntu.You mean inside the extended partition, right? Do you mean you did it manually or did the Ubuntu CD do it automatically?

---

### Post by entropy1 on 2010-08-25
Dedede,  You can see from the "after" picture that the partitions I created are all inside the extended partition (the names /dev/sda5,6,7,8 and 9 are indented).  I do all my partition changes (create, resize, move, etc.) either by running GParted from an Ubuntu Live CD or from sysrescuecd BEFORE I try to install Ubuntu to the hard drive.  Then, when I install Ubuntu, I choose "manual partitioning", but there is not too much to do - just tell which partition I want to use for / and for /home and if it should be ext3 or ext4.

When I made the "before" picture, I was running GParted from the Live CD.  That's why no partitions are mounted.  After I installed Ubuntu, I ran GParted from the hard drive, and GParted shows several mounted partitions (they have the "key" symbol).  I'm not sure what the "warning" symbol means.

---

### Post by dedede on 2010-08-25
OK, thanks. So about the last question: did you check if the HP Recovery Environment actually recognises the HP_TOOLS?

---

### Post by entropy1 on 2010-08-25
I don't know if the HP Recovery Environment recognizes the HP_TOOLS partition.  I have not tried to do any recovery.
Are you concerned about losing HP_TOOLS if you do a system recovery?

If you have used partimage from sysrescuecd to save an image of the HP_TOOLS partition, then you can restore it.  Recall that I had to restore HP_TOOLS because I deleted it to make /dev/sda4 into an extended partition.  As far as I can tell, running Windows 7 as usual still uses HP_TOOLS in its new location /dev/sda5.  There is information in [http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf]("http://h20000.www2.hp.com/bc/docs/support/SupportManual/c01564727/c01564727.pdf") about how to make a new HP_TOOLS partition if you lose it.  You can also find other info using a search engine.

---

### Post by dedede on 2010-08-25
In fact you do not need to make a system recovery to know if the HP_TOOLS is recognisable.
Simply press F2 at system startup and see if anything happens.
A 'System Diagnosis' window should appear where you can check the health of your hardware. I thing that uses HP_TOOLS. 
Thats the first thing HP Center will tell you to go if you have hardware failure. Do you know what they will respond if youll tell them you erased it? I dont know, in my opinion they will refuse to fix your PC... or they might make you pay for costs if they find out that the hardware is in fact perfectly fine (personal experience with other PCs).

So what was the point in moving 'HP_TOOLS' to the extended partition if youre not sure if it works? You simply add extra steps to yourself, rather than simply deleting it, moving 'Recovery' and telling Ubuntu installer to make the partition on that free space?

Are you even sure if the 'Recovery' partition doesnt depend on it and you can use the 'HP Recovery' at all now and if the 'Recovery' partition isnt useless now?

---

### Post by entropy1 on 2010-08-25
That's good to know about F2.  I'll try it when I get my computer back from HP - I just sent it to them yesterday because the pen and touch screen features stopped working.  They told me to remove the hard drive before I sent the computer to them.  So they'll never know that I did anything with the partitions :)

Interestingly, their tech support never suggested I try F2.

The point in moving HP_TOOLS was that I wanted to keep it around because it might be useful for when I run Windows.

I don't know if HP_RECOVERY would work without HP_TOOLS since I haven't tried it.  If it doesn't, I will use the Windows Installation DVD that I got from tech support a couple of weeks ago.  I would expect HP_RECOVERY to work without HP_TOOLS.  In fact, HP_RECOVERY might even recreate HP_TOOLS.  There are directions for recreating HP_TOOLS in the link in post #52.

By the way, in post #52, I was confused.  EFI is on the FAT 32 HP_TOOLS partition, not the NTFS SYSTEM partition.  Note, however, that the SYSTEM partition has the boot flag set - see images in post #56.  So if you delete the SYSTEM partition, I don't think Windows will boot.

---

### Post by dedede on 2010-08-25
I might sound impatient, but do you mind if I just ask this in the HP forums? I know I sound impatient, but I have spend at least a week trying to install Ubuntu, reformatting the hd several times, so I wasnt able to use my programs for creative work, and it drives me crazy.

PS. Hey, the latest 'System diagnosis' aka 'HP_TOOLS' partition can be downloaded from their site: [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-80840-1&lc=en&dlc=en&cc=us&os=4063&product=4050002&sw_lang=](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=ob-80840-1&lc=en&dlc=en&cc=us&os=4063&product=4050002&sw_lang=)

> - Microsoft .NET 2.0 is required. UEFI and Custom Imaging  ----------------------- The HP System Diagnostics must be run from a FAT  or FAT32 partition with a volume name of "HP_TOOLS". This installer  gives you the option to install to the hard drive (HDD) or to a USB  drive. If you install to the HDD and the HP_TOOLS partition is not  present, the installer prompts you to create the HP_TOOLS partition. If  you install to a USB drive, the installer renames the partition on the  USB drive to HP_TOOLS.

---

### Post by entropy1 on 2010-08-25
No problem for me if you post in the HP forum.  I empathize with your frustration.  I spent a couple of weeks trying to install various linux distros on my HP.  Unfortunately, they boot to a blank screen after install because they cannot handle the graphics processor (details at [http://ubuntuforums.org/showthread.php?t=1550613](http://ubuntuforums.org/showthread.php?t=1550613)).  So I run Windows on that machine; I keep the extra partitions for the future when I hope linux may handle my hardware...

---

### Post by dedede on 2010-08-25
There is a netbook version of ubuntu, isnt there?
Or did you mean the opposite?

---

### Post by entropy1 on 2010-08-25
I always used the Desktop version of Ubuntu.  I never tried the netbook version.  I'll keep that in mind.

---

### Post by horizon.reach02 on 2010-08-25
Use Grub 4 instead

---

### Post by dedede on 2010-08-25
You talking to me?

---

### Post by dedede on 2010-08-26
**My HP forum thread: **[http://h30434.www3.hp.com/t5/Operating-systems-and-software/want-dualboot-4-primary-partitions-taken-what-to-do/m-p/313304#M43453](http://h30434.www3.hp.com/t5/Operating-systems-and-software/want-dualboot-4-primary-partitions-taken-what-to-do/m-p/313304#M43453)

**I MADE UP MY MIND**

On a second thought, Recovery partition might bring other troubles to the  boothloader.
And restoring the PC with that erases EVERYTHING,  even my other OS, the process takes ages, reinstalling programs, the  other OS and other programs for that OS not counted. So I thought:
cant  I just make a backup of the 'System' and 'C' partitions and store them  somewhere else if I'm so concerned of loosing Windows7? I can recreate  them with my partition manager if they get corrupt. I then will need to  simply update GRUB menu to locate booth files from System again.


Isnt  that a better solution, what do you guys think?

---

### Post by entropy1 on 2010-08-26
This sounds like a good idea.  I've made images of all my partitions, including Windows.  However, I've never tried to restore them and see if it worked.  But presumably, I would not have to reinstall any software or updates that were done prior to backing up the partition image.

---

