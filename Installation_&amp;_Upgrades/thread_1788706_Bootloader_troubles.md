---
title: "Bootloader troubles"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Alex455 on 2011-06-23
I'm attempting to install Ubuntu 10.10 on my computer instead of the Windows 7 OS it came with.  Everything went smoothly until I encountered the "Sorry, an error occurred and it was not possible to install the bootloader at the specified location." error.  I've tried to choose all of the three options, but it won't let me click OK.

Excuse me if I've skipped over any of the formalities of requesting for help here; it's my first time trying to do something like this.

Here's the RESULTS.txt:

>                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E}.u......
    Boot sector info:   Syslinux looks at sector 1473688 of /dev/sda1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files:        /etc/fstab

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 2056 MB, 2056257536 bytes
16 heads, 32 sectors/track, 7844 cylinders, total 4016128 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             32     4,016,127     4,016,096   e W95 FAT16 (LBA)


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048   614,623,231   614,621,184  83 Linux
/dev/sdd2         614,625,278   625,141,759    10,516,482   5 Extended
/dev/sdd5         614,625,280   625,141,759    10,516,480  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        6B89-3230                              vfat       TravelDrive
/dev/sdd1        379e2670-1e66-4e96-9d4e-cf2a75f89c32   ext4       
/dev/sdd5        4c274fa5-18ce-424b-a462-a7b683cce739   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

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
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Install Ubuntu" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    set gfxpayload=keep
    linux    /casper/vmlinuz  boot=casper integrity-check quiet splash --
    initrd    /casper/initrd.lz
}
--------------------------------------------------------------------------------

============================== sda1/syslinux.cfg: ==============================

--------------------------------------------------------------------------------
default menu.c32 
prompt 0 
menu title UNetbootin 
timeout 100 
 
label unetbootindefault 
menu label Default 
kernel /ubnkern 
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry0 
menu label ^Help 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry1 
menu label ^Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper  quiet splash -- 
 
label ubnentry2 
menu label ^Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity  quiet splash -- 
 
label ubnentry3 
menu label ^Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check  quiet splash -- 
 
label ubnentry4 
menu label Test ^memory 
kernel /install/mt86plus 
append initrd=/ubninit  
 
label ubnentry5 
menu label ^Boot from first hard disk 
kernel /ubnkern 
append initrd=/ubninit  
 
label ubnentry6 
menu label Try Ubuntu without installing 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- 
 
label ubnentry7 
menu label Install Ubuntu 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity quiet splash -- 
 
label ubnentry8 
menu label Check disc for defects 
kernel /casper/vmlinuz 
append initrd=/casper/initrd.lz boot=casper integrity-check quiet splash -- 
 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/grub.cfg                             1

================= sda1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             menu.c32                                       1
            ?? = ??             syslinux.cfg                                   1

============== sda1: Version of COM32(R) files used by Syslinux: ===============

 menu.c32                           :  COM32R module (v4.xx)

=============================== sdd1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdd1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdd5 during installation
UUID=4c274fa5-18ce-424b-a462-a7b683cce739 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sdd1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

   0.563362122 = 0.604905472    boot/initrd.img-2.6.35-22-generic              1
 142.133285522 = 152.614453248  boot/vmlinuz-2.6.35-22-generic                 1
   0.563362122 = 0.604905472    initrd.img                                     1
 142.133285522 = 152.614453248  vmlinuz                                        1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc 

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected


---

### Post by nzjethro on 2011-06-23
Hi there Alex. Welcome to the forums. Fantastic work with the post, that is exactly what people with a boot problem should do!

The problem is that Grub is installed to the sda, while Ubuntu is installed on sdd.

Try following [this guide]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html") to reinstall Grub to sdd, which should resolve the issue.

:)

---

### Post by Alex455 on 2011-06-23
Thanks for the help, Jethro.  I'll try it out in a second and post a reply if anything else goes wrong.

Also, funny coincidence here, I see you're from Auckland?  I just so happen to be planning on moving somewhere close to that city in about a year's time.

---

### Post by nzjethro on 2011-06-23
Awesome, I'll keep an eye on here for your reply.

And wise choice, Auckland is a fantastic city, although it has a lot of rain this time of year. :)

---

### Post by Alex455 on 2011-06-23
[http://i53.tinypic.com/24lk9hy.png](http://i53.tinypic.com/24lk9hy.png)

I really don't know what to make of this.  Like I said, I'm only moderately familiar with Linux tech jargon. :P

---

### Post by nzjethro on 2011-06-23
Did you reboot from a Live CD, or is this from within your installed Ubuntu?


If yes, try

```
sudo mount /dev/sda1 /mnt
```

If no, reboot to the Live CD, and try the above command.

---

### Post by Alex455 on 2011-06-23
Typo on my part.  It's somewhere around 3 am where I'm at and I've been going back and forth with this for quite a while.

Yes, I'm booting it from a LiveCD that I made on a flash drive using Unetbootin.

This time, I got up to the "sudo chroot/mnt" command and it says THAT is not found.

Everything up to it worked fine, though.

---

### Post by nzjethro on 2011-06-23
> This time, I got up to the "sudo chroot/mnt" command and it says THAT is not found.

Apologies, I think I should have picked up on that error in their guide. They've made typo. Try:

```
sudo chroot /mnt
```

i.e. put in a space between chroot and /mnt.

---

### Post by Quackers on 2011-06-23
There needs to be a space between chroot and /mnt

---

### Post by Alex455 on 2011-06-23
[http://i54.tinypic.com/11tx3xx.png](http://i54.tinypic.com/11tx3xx.png)

It says the directory is nonexistent.

(I swear Jethro, I'm going to buy you a case of your favorite beer if I ever see you on the streets of Auckland. :P)

---

### Post by Quackers on 2011-06-23
I suggest you unmount everything and start again but this time mounting /dev/sdd1 rather than /dev/sda1 as that is your Ubuntu partition.
However, having said that I'm not sure it looks right as it is, as boot files are missing and there is no UUID for a root partition in the /etc/fstab file.

I might be tempted to try the CHROOT section of the guide below to purge grub (though I don't think any of grub is installed yet) then re-install grub, mounting sdd1 and then installing grub to the mbr of sdd (not sdd1).
Of course, /dev/sdd must then be made the first bootable hard drive in your bios.

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by nzjethro on 2011-06-23
Skip the update-grub command for now, and go onto the next step.

In fact, instead of the step they have there, try:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

And before you unmount and stuff, try to run update-grub again. We'll need to get that done, else you could run into major hiccups.

We'll get this problem fixed yet!

@ Quackers, did you see [this?]("http://i53.tinypic.com/24lk9hy.png") In this shot it looks as though sda1 is the Linux partition, hence why I was suggesting sda1. I'm sure you are more knowledgeable about this than I, so could you please explain why Ubuntu is on sdd in bootinfo and sda1 here? Thanks!

---

### Post by Quackers on 2011-06-23
Sorry nzjethro, don't mean to step on toes :-)
I think grub needs to go on sdd, unless I've read things wrong (that's possible :-) )

---

### Post by Alex455 on 2011-06-23
I'll wait for you two to come to a consensus before I move on.  Whichever one of you knows more than the other, you both know more than I do. :P

---

### Post by nzjethro on 2011-06-23
Oh no, not at all. I am genuinely interested, and I'd like to learn more about fixing boot issues, as they seem to come up a lot on here (and a few times when I'm playing around on my own PC too!!). I am still reasonably new to Ubuntu, but I'd like to be able to help others (and myself when I cook the system) out, so if you'd be able to explain the reasoning behind your advice so I know what I'm looking for, I'd appreciate it. Apologies if it came across as me being snarky! Haha.

:)

---

### Post by Quackers on 2011-06-23
Yes, I see what you mean nzjethro, but the sda drive is only 2056MB in size and is almost certainly a flash drive (which in itself can cause problems when it is named as sda, by the system).
The grub files seen in sda are doubtless there because the flash drive is being used to boot the Ubuntu live system.

EDIT not snarky at all! This is how we start helping people - by sharing what we know :-)

---

### Post by nzjethro on 2011-06-23
I saw that too. In [this image]("http://i53.tinypic.com/24lk9hy.png") though ( a screenshot from the fixing), sda is >300GB (primary HDD), while sdb is 2056MB (and thus likely corresponds to the USB at sda on the boot info script). Is there a reason why the system would name them differently like this? And which do you need to install Grub to? I would have thought that on the we would use the naming from the Live CD boot (i.e. sda1 being Linux)?

And sorry for holding up the solution asking all my questions Alex. Haha.

---

### Post by Alex455 on 2011-06-23
Not a problem, Jethro.  I'm taking notes too.

---

### Post by Quackers on 2011-06-23
Yes, I see that, which does give us a problem :-)

Alex455, if you are booted to the live desktop, just to make sure, open gparted (system > Admin > gparted) and the first screen will show /dev/sda.
If that screen gives details of your hard drive (and not a 2056MB drive) use /dev/sda1 in the mount command and install grub to /dev/sda.  If not use /dev/sdd1 and install grub to /dev/sdd.

Sometimes the system can name a flash drive as sda and it can cause problems.

The above method should sort things out, I hope :-)

---

### Post by Alex455 on 2011-06-23
So I should restart the entire process and replace instances of sda with sdd?

---

### Post by Quackers on 2011-06-23
Open gparted first and see which drive it reports as /dev/sda (in its first window). If it reports your actual hard drive in that screen (320GB) use sda1 and install grub to sda.
If that first screen reports sda as being only 2056MB in size, use sdd1 in the mount command and install grub to sdd

---

### Post by nzjethro on 2011-06-23
What is the first drive that comes up in GParted?

It should be up in the top right corner, and have something like /dev/sda or /dev/sdd. It'll have the disk size next to it, so make sure it is your primary HDD (a few hundred GB I assume), rather than the 2GB USB drive.

This primary drive is the drive that you'll want to install Grub to.

***EDIT:*** ^^

---

### Post by Alex455 on 2011-06-23
Beautiful.  No errors whatsoever. (except for the slight human error where I typed 'unmount' instead of 'umount' around five times)

Time to reboot and see if everything's working all right.  I really appreciate the help.


(Also Jethro, from earlier, if you think NZ gets a lot of rain, I live in Louisiana.  I don't suppose you've ever been inside of a hurricane? :P)

---

### Post by Quackers on 2011-06-23
Good luck then :-)

---

### Post by nzjethro on 2011-06-23
Awesome, glad we could help. And no thanks on the hurricanes, rain is bad enough for me!

---

