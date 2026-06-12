---
title: "Windows 7 and Ubuntu 10.10 boot issues...."
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by Dfairlite on 2010-12-15
Ok, I have searched the forums and tried many different 'solutions' and I still can't get back to windows. Here's the issue:
I had been happily running 8.10 and windows 7 for quite some time. decided to update to 10.10 via fresh install and now can't boot into windows 7. when I select windows seven on the grub2 menu I get a blank screen with a blinking cursor.
So here is what I have tried:
updating grub2
reinstalling grub2
using windows 7 dvd to repair windows using startup manager (which now fails)
then reinstalling grub2 again
then updating grub2
this thread: [http://ubuntuforums.org/showthread.php?t=1607203](http://ubuntuforums.org/showthread.php?t=1607203)
this thread: [http://askubuntu.com/questions/17493/dual-boot-broken-windows-7-mbr-and-grub](http://askubuntu.com/questions/17493/dual-boot-broken-windows-7-mbr-and-grub)
and some others.

Here is my current info:
3 HDDs,
sda and sdc are for media
sdb is as follows:

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         156     1253038+   7  HPFS/NTFS                --1gb system reserved by windows
/dev/sdb2             157       46104   369077310    7  HPFS/NTFS                --Windows installation
/dev/sdb3           52971       60801    62902477    5  Extended                 --Empty space
/dev/sdb5           52971       60476    60291913+  83  Linux                    --Ubuntu 10.10
/dev/sdb6           60477       60801     2610531   82  Linux swap / Solaris     --Swap 

any ideas would be greatly appreciated!

---

### Post by q999 on 2010-12-15
have you tried to delete all linux partitions?- with any live cd partitioning tools and reinstalling,this is drastic and I'm sure their are other ways but this is what I would do..

---

### Post by Quackers on 2010-12-15
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal and run
```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply) and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by garvinrick4 on 2010-12-15
#You have a Windows system partition: This just might be the problem:

Grub2 was installed with Windows system partition chosen as the root-directory. This causes the folder /boot/grub to be created on the Windows system partition. Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot"
#Solution 
Boot into your Linux OS and delete or rename the folder /boot on the Windows system partition. Make sure that your don't delete the /Boot folder. The /Boot folder contains the file "bcd" which is necessary to boot Windows Vista/7.

---

### Post by Dfairlite on 2010-12-17
Garvinrick, there is only one /Boot folder on the windows partition.the lowercase /boot is on the ubuntu partition. Do I still need to rename it? 
Thanks.

---

### Post by Dfairlite on 2010-12-17
Quackers,
Here are the results:
```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #5 for (,msdos5)/boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /grldr

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sdb3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048 2,930,274,303 2,930,272,256   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     2,506,139     2,506,077   7 HPFS/NTFS
/dev/sdb2           2,506,140   740,660,759   738,154,620   7 HPFS/NTFS
/dev/sdb3         850,963,111   976,768,064   125,804,954   5 Extended
/dev/sdb5         850,963,113   971,546,939   120,583,827  83 Linux
/dev/sdb6         971,547,003   976,768,064     5,221,062  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   976,768,096   976,768,034   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        6674E0B974E08CDD                       ntfs       Video                         
/dev/sda: PTTYPE="dos" 
/dev/sdb1        B280475780472169                       ntfs       System Reserved               
/dev/sdb2        06D04ADAD04AD01B                       ntfs                                     
/dev/sdb3: PTTYPE="dos" 
/dev/sdb5        93134f08-6f2d-4444-a2b6-95ec3f88c698   ext4                                     
/dev/sdb6        01192100-3ca2-469f-8a31-9f36d9e0fa0d   swap                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        AEFEC5E7FEC5A7C3                       ntfs       Music-Video                   
/dev/sdc: PTTYPE="dos" 
error: /dev/sdd: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


=========================== sdb5/boot/grub/grub.cfg: ===========================

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

insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 93134f08-6f2d-4444-a2b6-95ec3f88c698
if loadfont /usr/share/grub/unicode.pf2 ; then
set gfxmode=1280x1024
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd1,msdos5)'
search --no-floppy --fs-uuid --set 93134f08-6f2d-4444-a2b6-95ec3f88c698
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
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 93134f08-6f2d-4444-a2b6-95ec3f88c698
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=93134f08-6f2d-4444-a2b6-95ec3f88c698 ro  splash vga=795  quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 93134f08-6f2d-4444-a2b6-95ec3f88c698
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=93134f08-6f2d-4444-a2b6-95ec3f88c698 ro single  splash vga=795
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 93134f08-6f2d-4444-a2b6-95ec3f88c698
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos5)'
    search --no-floppy --fs-uuid --set 93134f08-6f2d-4444-a2b6-95ec3f88c698
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sdb1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set b280475780472169
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
UUID=93134f08-6f2d-4444-a2b6-95ec3f88c698 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb6 during installation
UUID=01192100-3ca2-469f-8a31-9f36d9e0fa0d none            swap    sw              0       0
UUID=AEFEC5E7FEC5A7C3    /mnt/Music    ntfs    default    0    0

=================== sdb5: Location of files loaded by Grub: ===================


 440.3GB: boot/grub/core.img
 459.7GB: boot/grub/grub.cfg
 436.2GB: boot/initrd.img-2.6.35-22-generic
 440.3GB: boot/vmlinuz-2.6.35-22-generic
 436.2GB: initrd.img
 440.3GB: vmlinuz
=======Devices which don't seem to have a corresponding hard drive==============

sdd 
```

---

### Post by MB0SS on 2010-12-17
Hi

try this 
put windows disk then start 
hit any key for boot for disk

on the first page click install
then click on repair windows
then click on command promot

then type in


diskpart

then

select disk 0

then

select partition 1

then

active

then

exit

and then 

exit

then click on repair your computer or startup repair

goodluk

---

### Post by Quackers on 2010-12-17
Under normal circumstances that would be ok MBOSS, but in this case the Windows OS is on sdb which would be disk 1.
But as that just changes the boot flag - and the boot flag is already on sdb1, there is no need to do it.
The OP also has grldr in with the Windows boot files.
It appears grub legacy has been installed at some time (or attempted). It may be an idea to delete that file and see if Windows then boots.

---

### Post by Herman on 2010-12-17
> #You have a Windows system partition: This just might be the problem:
Grub2 was installed with Windows system partition chosen as the  root-directory. This causes the folder /boot/grub to be created on the  Windows system partition. Since ntfs partitions are case insensitive  this leads to confusions between "/boot" and the already existing folder  "/Boot"

Boot into your Linux OS and delete or rename the folder /boot on the  Windows system partition. Make sure that your don't delete the /Boot  folder. The /Boot folder contains the file "bcd" which is necessary to  boot Windows Vista/7.:twisted: Being the kind of person I am, after seeing this idea I just couldn't resist the temptation to try it out for myself and see if I could find a work-around. 

This is incidental to the thread, and won't help the original poster at all, but I just think it's interesting.
I booted into my Linux OS and renamed the /Boot folder in the Windows system partition to /boot instead, (I just changed 'B' to a lower case 'b').
Then I ran run grub-install again.
```
herman@amd-quad-lynx:~$ sudo grub-install --root-directory=/media/System_Reserved /dev/sda
Installation finished. No error reported.

```That created a new folder named /boot/grub inside the NTFS /boot partition and installed the boot.img and core.img to the first hard disk pointing to the copy of GRUB that I just created inside my Windows 7 /boot partition.

It seems to be booting both Windows 7 and Ubuntu just fine so far.

If any other person decides to try this trick, they need to be aware of the difference between a MBR, (/dev/sda), and a boot sector, (like /dev/sda1). Under no circumstances should GRUB be installed to any Windows boot sector, as that would render Windows unbootable.
I do not actually recommend others to try this trick, as I can't think of any advantages of doing this. It's just interesting that GRUB works as well in NTFS as it does in a Linux file system and it doesn't seem to do Windows any immediate apparent harm.
If I installed GRUB to the Windows boot sector it would harm Windows though, but to MBR is okay. The MBR is at the start of the hard disk drive and is not a part of the Windows file system but the boot sector is at the start of the Windows partition.

ADDITIONAL NOTES: I did have some trouble getting the grub-install command to work when  the Windows /boot partition was labeled 'System Reserved', and I had to  use GParted to re-label it as 'System_Reserved' instead, (with an underscore instead of a whitespace), because I kept  getting the error' /media/System\ Reserved/', is not a directory', or  something like that. 

I can remember trying this same experiment once before, about a year ago and it worked that fine time too. :)

---

### Post by Quackers on 2010-12-17
I must admit that the finer workings of Grub2 and the Windows 7 boot files scare me at times :-) Sometimes Win 7 and its boot files seem so rubust but at others they appear really fragile.

---

### Post by Herman on 2010-12-17
:D Some years ago I read this book, [Zen And The Art Of Motorcycle Maintenance]("http://en.wikipedia.org/wiki/Zen_and_the_Art_of_Motorcycle_Maintenance"), (actually, I read it many times), and although it the author makes no claims about its accuracy regarding motorcycle maintenance, it is nevertheless a very interesting book. 
It seems to be a book that can have different meanings depending on who reads it, or the same person in different situations.

The point for my mention of it here is its relevance to comparing the way different people think about problems.

The 'typical Windows user' would seem to me to fit more into the category of the "Romantic" approach to life while Linux users seem to be more the "classical" type.
Well, that's maybe generalizing a little too much.

Anyhow, I think the fact that you seek knowledge of the finer details of boot loaders shows that you are a "classical" type of thinker and you will succeed in learning all about boot loaders and how they work and lots of other interesting and useful things about computers and operating systems. It's all just a matter of applying scientific principles and using analytical thinking.

I don't know if anyone will be able to understand what I'm talking about just by reading the book review in the link or not, maybe most people will just think I'm some kind of a nut. They might be right. (LOL)  :D

---

### Post by Quackers on 2010-12-17
I suspect that you may be right :-) It is not enough for me to know that something works. I want to know how it works. However, where computers and OSes and boot sectors and mbr's and boot files are concerned, there is only so much info that you can absorb. I find that stages work best for me. I understand something of grub2 and something of Windows booting, but none of the really fine details. I understand that booting an OS involves stages and links in a chain. I am in the dark, though, regarding how each link passes to the next link - other than obviously there is some sort of addressing system in use (which I presume is sectors or blocks) which in turn must be set up by boot files within the OS - I think :-)
As I said, I can only learn so much at one time. I then let it sit a while and let my assumptions prove themselves (or correct themselves) and then I can push on :-)

---

### Post by Dfairlite on 2010-12-18
> **Quackers said:**
> Under normal circumstances that would be ok MBOSS, but in this case the Windows OS is on sdb which would be disk 1.
But as that just changes the boot flag - and the boot flag is already on sdb1, there is no need to do it.
The OP also has grldr in with the Windows boot files.
It appears grub legacy has been installed at some time (or attempted). It may be an idea to delete that file and see if Windows then boots.

Deleted it, no change.

Another thing to add to the list:
I just tried to repair windows startup through startup repair on windows dvd and it fails. tried 4 or 5 times and it failed every time. This all was working fine before I installed 10.10, which leads me to believe maybe I screwed something up during install. I deleted my ubuntu partition (sdb5 I think) and reformatted and installed 10.10, which is probably why grub legacy was still installed (running 8.10 prior).

At this point the only way (I know of, though I am sure there are others) to get back to windows reinstall windows completely since it's boot sequence is super f***ed.

---

### Post by Quackers on 2010-12-18
Did you try startup repair before or after deleting grldr?

---

### Post by Herman on 2010-12-18
Have you tried going for the command prompt in your Windows Repair DVD and running 'bootrec /fixboot'?
```
C:\> bootrec /fixboot
```

---

### Post by theasprint on 2010-12-18
Try this,
 
 Go load a Windows repair disc or installation disc, and use the command prompt in startup repair.
 Be sure to select the Windows partition using diskpart in the command  prompt. ( the post about using diskpart and select earlier )
 After selecting the disk, go and repair your MBR ( Google it for the exact steps )

If fixing MBR fails, maybe you may try 
```
sudo update-grub
```

*Its just trying, Im not sure whether it works. Good luck though!:D

---

### Post by Dfairlite on 2010-12-18
> **Quackers said:**
> Did you try startup repair before or after deleting grldr?

I tried it after deletion, since it failed I restored grldr and it still fails. it worked a couple days ago. but now it fails every time...

Herman: yes I used fixboot in windows recovery command prompt and it said it completed successfully while the startup repair still said there is an issue and fails.

EDIT: START-UP REPAIR IS NOW SAYING THERE IS NO ISSUE AT ALL WITH WINDOWS BOOT CRAP.

---

### Post by Dfairlite on 2010-12-18
> **theasprint said:**
> Try this,
 
 Go load a Windows repair disc or installation disc, and use the command prompt in startup repair.
 Be sure to select the Windows partition using diskpart in the command  prompt. ( the post about using diskpart and select earlier )
 After selecting the disk, go and repair your MBR ( Google it for the exact steps )

If fixing MBR fails, maybe you may try 
```
sudo update-grub
```

*Its just trying, Im not sure whether it works. Good luck though!:D

Just did this, no dice. odd thing is though, it didn't corrupt grub... however it did get startup repair working again. says all is well with windows. But I still have the same issue, blinking cursor, no hdd light activity, no errors. I can access all my info through ubuntu so the hdd should be good. Right now my main concern is to get windows booting again, whether I destroy grub/maverick or not...

---

### Post by Dfairlite on 2010-12-22
One last bump before the dive of reinstalling windows 7.

---

### Post by Herman on 2010-12-22
I tried a few experiments in another thread and I found out that for me, Windows 7 was unable to fix Windows 7 when it was in a non-first hard disk, and bootrec /fixboot wouldn't work either.
I don't know how updating Ubuntu could have affected your Windows 7 in any way, but try removing that first hard disk and making the disk that has Windows 7 / Ubuntu in it your first hard disk.
You might not need to physically unplug any drives, switching the hard drive order in your BIOS might be enough, but physically unplugging all but the drive with Windows in it would ensure your repair DVD tools are finding the right target. :)

---

### Post by Dfairlite on 2010-12-22
> **Herman said:**
> I tried a few experiments in another thread and I found out that for me, Windows 7 was unable to fix Windows 7 when it was in a non-first hard disk, and bootrec /fixboot wouldn't work either.
I don't know how updating Ubuntu could have affected your Windows 7 in any way, but try removing that first hard disk and making the disk that has Windows 7 / Ubuntu in it your first hard disk.
You might not need to physically unplug any drives, switching the hard drive order in your BIOS might be enough, but physically unplugging all but the drive with Windows in it would ensure your repair DVD tools are finding the right target. :)

I've tried all of this except physically unplugging the drives so I'll try that! Thanks for the help!

---

### Post by MrPaperTrain on 2011-01-10
Hi All

I recently had this problem after Dual Booting Ubuntu (10.10) and Windows 7 (Home Premium).

I found that after the GRUB bootloader had shown me the OS's and I try to boot into Win7, it cuts out and repeats the booting sequence, taking me back to the OS list (Ubuntu works perfectly fine). It bugged the hell out of me, so in the end I resorted to putting in my Win7 install disk and booting from that.

However, I don't do anything with it. I allow it to scan and tell me a list of things it could do or tell me this or that, but in the end I just hit 'Finish' when prompted and booted my system up again.

Back to the bootloader I select Win7 and hey presto, it boots no problem, and I've found that if I continue to boot from Win7 it'll be fine, it's only until I select Ubuntu that I have to repeat the process again, and it become a real pain!

One thing to note is that my HP-G60 has been updated to Win7 from Vista, so my Recovery Manager doesn't work, hence why I used the Startup Disks...

Let me know if this works and I'll play around some more to see if I can get any further with this issue!

Not bad for a 16 Year old eh? ;) Shame I haven't made millions... LOL.

---

