---
title: "Want to dual-boot Ubuntu 9.10 &amp; XP--advice needed"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by Deer Hunter on 2010-01-29
Hello there,

I have made myself a Ubuntu 9.10 Karmic Koala (32-bit) CD, which I want to dual-boot with my current XP Pro 32-bit on my HP laptop.  But  for some reason HP made two additional partitions on my hard drive (one labeled "HP Tools" and listed as a System partition in the Disk Management, even though it doesn't have anything on it).  I can't see anything (even with "show hidden items" enabled) on either of these extra partitions, at least not that I know about; so I'm wondering if they're system folders that I need to keep, or can I safely delete them?

Another question was, I have read here that you need to make a "Swap Partition" when installing Ubuntu, but I've also read (can't remember for sure, think it was here) that you only need to make the Swap Partition if you're going to be making the machine Hibernate.  Can somebody set me straight here?

My last question was, when I actually install Ubuntu, how do I go about getting some of the drivers for my hardware, so I can actually enable my wireless on Ubuntu to get the updates and software and all that?

Thanks in advance; if I'm not being clear enough, let me know and I'll try again.

Deer Hunter

---

### Post by darkod on 2010-01-29
Usually you would always have swap partition but if you want to hibernate it should be at least 150% of your ram memory. If you have 2GB ram, make 3GB swap. Otherwise, 2GB is more than enough.

You can boot with the cd and select Try Ubuntu option first, that will load live desktop running from the cd. You can check whether your hardware works fine, including internet either wired or wireless. Wireless might need some setting up so you might wanna make sure at least wired is working because you usually need internet to set up any hardware not working by default.

---

### Post by audiomick on 2010-01-29
Hi. I have read about extra partitions, amongst others on HP, but don't know exactly what they do. I believe, amongst other things, recovery partitions. Better wait for some more advice on that.

As far as Swap goes:
some info here
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
From what I have read, it is correct that if you want to hibernate, the swap should be as big as your RAM. If you don't want to hibernate, it can be smaller. If you have lots of RAM, maybe upwards of 1GB, you might only need a Gig or so of Swap. The system will theoretically run without, but it is not recommended.

As far as drivers go, a large percentage are there by default. Try booting from the live CD, the "try without changing" option, to see how much works. Most likely, if there is something that needs a proprietary driver, the hardware driver manager will do it's job and offer it to you.

If you have problems with something specific, post it here.:p

---

### Post by Deer Hunter on 2010-01-29
It seems to me that you could be right about the extra partitions being used for recovery purposes; but my System Restore doesn't work anyway.  I'll just make sure to save all my files.

As far as Swap goes, I didn't think to mention, I'm running a 220 Gb (roughly) hard drive (which is divided up among the partitions) and 3Gb of Ram.  And the one partition (not the "HP Tools" one) is about 1 Gig already, so maybe I could make that the Swap, what do you think?

I've run the Live CD a couple times already, I'll do that again and see if I can make it run my WiFi.  I'll get back to you on that one.

Thanks for the help guys.

Deer Hunter

---

### Post by Deer Hunter on 2010-01-30
Well, as the internet issue goes, it seems we're good to go!  And by that I mean, I'm typing this out of my LiveCD Firefox; just had to set up the connection and password.  I guess maybe I'm to blame for not looking far enough on the system initially, so my apologies for that; but it's working great now.

Anybody have any more advice about the partitions?

Thanks all.

Deer Hunter

---

### Post by VideoRoy on 2010-01-30
I do not have specific info on the partitions but I would suggest using EasyBCD at neosmart.net to setup the dual boot.

I have dual booted and triple booted (Win7, XP, Ubuntu 9.10) using EasyBCD and it is a snap.  Great forum over there as well with good advice.  Use Beta 2.0 build 76 and you should not have any problems.  Lots of folks doing exactly what you are doing.

Also I just got my new HP laptop today with Win7 and I am shrinking the partition now and going to setup a dual boot with Ubuntu.

Good Luck.

---

### Post by Deer Hunter on 2010-01-30
Thanks but when I installed it, it said that I have to have Vista installed.  GParted from the LiveCD should work too, wouldn't it?

---

### Post by VideoRoy on 2010-01-30
> **Deer Hunter said:**
> Thanks but when I installed it, it said that I have to have Vista installed.  GParted from the LiveCD should work too, wouldn't it?

Make sure you register in the Neosmart forums and download version 2.0 build 76 and not the 1.72 version from the main page if you are going to use EasyBCD.

To be clear EasyBCD will just help you with dual boot configurations (managing bootloaders) not partition and installing the OS.  It is also pretty good at recovering mucked up boot loaders for Windows I have found.

Here is a guide if you are interested but it is a little outdated since it references Grub and not Grub2.  If you want to do this look at the forum and you will see how others are doing what you want to do.

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

To your point you could do this from Ubuntu as well.  Just mentioning there are some other alternates especially if you want to truly keep your OSs and bootloaders separate.  I never load the Ubuntu bootloader on the Windows partition, I keep it on the Ubuntu partition and let EasyBCD jump me over there.

Good luck.

---

### Post by Deer Hunter on 2010-02-02
I tried it again but still didn't work.  Thanks anyway.

In the meantime, I have discovered that my machine positively will not boot XP (at least in all the ways I've tried so far) UNLESS the "HP_TOOLS" portion is marked as a boot partition.  Whatever; it's only 1 Gb anyway.  But in any case, I want to install Ubuntu on a third partition, and leave the fourth partition for data to be accessed by both OS's; my understanding is that instead of necessarily making a swap partition, I can make a swap file on the Ubuntu partition.  So my hard drive would have four Partitions: Windows XP, HP_TOOLS, Ubuntu, and then other data.  Does anyone see a problem with doing this?

Thanks all.

---

### Post by darkod on 2010-02-02
> **Deer Hunter said:**
> I tried it again but still didn't work.  Thanks anyway.

In the meantime, I have discovered that my machine positively will not boot XP (at least in all the ways I've tried so far) UNLESS the "HP_TOOLS" portion is marked as a boot partition.  Whatever; it's only 1 Gb anyway.  But in any case, I want to install Ubuntu on a third partition, and leave the fourth partition for data to be accessed by both OS's; my understanding is that instead of necessarily making a swap partition, I can make a swap file on the Ubuntu partition.  So my hard drive would have four Partitions: Windows XP, HP_TOOLS, Ubuntu, and then other data.  Does anyone see a problem with doing this?

Thanks all.

No problem but you don't have to leave out swap. The ubuntu guided install is installing it into an extended partition anyway, so it uses up only one partition. Also, if you are creating root and swap manually just create them as Logical (not Primary) one after the other, and it combines them into one extended I believe. So, you would have:
XP -- HP_TOOLS -- ubuntu extended (inside including root and swap logical) -- Data

You're still within the 4 partitions limit.

---

### Post by Deer Hunter on 2010-02-02
Aha.  I think I understand; the installer makes that extended partition all by itself, right?  So now my next step is to shrink my XP partition down to 50 or 40 Gb, reboot a few times, and install Ubuntu?

Many thanks

---

### Post by darkod on 2010-02-02
> **Deer Hunter said:**
> Aha.  I think I understand; the installer makes that extended partition all by itself, right?  So now my next step is to shrink my XP partition down to 50 or 40 Gb, reboot a few times, and install Ubuntu?

Many thanks

Yes, shrink XP, leave the newly created free space as unallocated, reboot XP few times.
Then simply boot with ubuntu cd and go trough the install process, it installs in extended partition on its own.

---

### Post by Deer Hunter on 2010-02-02
> **darkod said:**
> Yes, shrink XP, leave the newly created free space as unallocated, reboot XP few times.
Then simply boot with ubuntu cd and go trough the install process, it installs in extended partition on its own.

Okay, I understand that part.  But I'm sorry, I'll have to bother you with another question.  When I open GParted, it shows this:

(partition)   (file system)   (label)  (size)          (used)         (unused)     (flags)

/dev/sda1        extended              222.87Gb         ---             ---           lba
    /dev/sda5    ntfs                      222.87Gb    44.40Gb     178.48Gb    


Obviously, I didn't include all the partitions there, and my apologies for the rough chart, but my question is this: I know that the partition that I copied above there has to be my Windows partition, because of the size and how much is used; but how do I know whether to resize "sda1" or "sda5"?  Or does it make a difference?

Thanks for the help, and your patience with me as I try to figure this out.

Deer Hunter

PS. I hope you can understand the rough chart.  It looked alright when I wrote it initially, but some how all the spaces got taken out that would have made it more intelligible.

---

### Post by darkod on 2010-02-02
Uhhh, that is an extended partition itself. I haven't tried shrinking an extended partition, but the logic would be that you first have to shrink /dev/sda5 and then /dev/sda1 to match, because sda5 is inside sda1.
Another option is to delete /dev/sda5, then delete /dev/sda1 and create new primary partition instead but you would have to move all data to another location because that will destroy all data on the partition. After recreating the primary partition you put the data back.
And if you have XP on this partition that would mean reinstalling XP so it's not really an option. Although I think windows wouldn't work installed on extended partition.

---

### Post by Deer Hunter on 2010-02-02
> **darkod said:**
> Uhhh, that is an extended partition itself. I haven't tried shrinking an extended partition, but the logic would be that you first have to shrink /dev/sda5 and then /dev/sda1 to match, because sda5 is inside sda1.

Okay thanks, that makes sense.  I'll try that; it sounds less risky than deleting the partition.

Deer Hunter

---

### Post by cygnus-X1 on 2010-02-03
I've been looking to dual boot 2k & 9.10(32) on one of my older systems (Asus A7V-133/AMD T-bird 850MHz/1.5G Ram/250GB WD HDD). Most of the info has been so convoluted it isn't funny! This thread caught my eye for various reasons and I have followed the advise of Darkod. [*BTW - Huge thanks for the simplicity!*] The good news is that it's the first time the machine has actually rebooted without giving an error. The only problem is, is that it only boots to the 2K partition. The 2K was on the machine first and I used Gparted to add an extended partition for the 9.10 to reside and a primary partition for NTFS shared data storage. Here's what the partitions look like according to Gparted:

sda1 - NTFS - 2K - 15.00GB - BOOT
sda2 - Extended - 15.00GB
sda5 - Ext4
sda6 - Linux-Swap
sda3 - NTFS - Data - 202.89GB

So the real question is: How do I get this to see both 2K and 9.10, AND be able to choose which one to boot to? Please note. I have 3 other machines to do this on! All help will be greatly appreciated!

---

### Post by darkod on 2010-02-03
> **cygnus-X1 said:**
> I've been looking to dual boot 2k & 9.10(32) on one of my older systems (Asus A7V-133/AMD T-bird 850MHz/1.5G Ram/250GB WD HDD). Most of the info has been so convoluted it isn't funny! This thread caught my eye for various reasons and I have followed the advise of Darkod. [*BTW - Huge thanks for the simplicity!*] The good news is that it's the first time the machine has actually rebooted without giving an error. The only problem is, is that it only boots to the 2K partition. The 2K was on the machine first and I used Gparted to add an extended partition for the 9.10 to reside and a primary partition for NTFS shared data storage. Here's what the partitions look like according to Gparted:

sda1 - NTFS - 2K - 15.00GB - BOOT
sda2 - Extended - 15.00GB
sda5 - Ext4
sda6 - Linux-Swap
sda3 - NTFS - Data - 202.89GB

So the real question is: How do I get this to see both 2K and 9.10, AND be able to choose which one to boot to? Please note. I have 3 other machines to do this on! All help will be greatly appreciated!

Are you getting a grub menu or it just boots 2k right away? Do you have only one hdd?

---

### Post by cygnus-X1 on 2010-02-03
No GRUB menu at all. Straight to 2K. Just a single WD 250GB HDD.

---

### Post by darkod on 2010-02-03
If you are sure about the partition layout you wrote above, try reinstalling grub2 to the MBR.
Boot with the 9.10 cd, Try Ubuntu option, in terminal execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

The above should work assuming 9.10 was correctly installed in /dev/sda5 and grub2 config files are actually there. Reboot without the cd and see what happens.

---

### Post by cygnus-X1 on 2010-02-03
Will do. I'll report how it goes, either way. Thanks for the help!

---

### Post by cygnus-X1 on 2010-02-03
I'm ba-ack... ](*,)

Both lines of code entered. Here is what appeared on the screen after the BIOS loaded upon reboot:

GRUB loading.
error: no such partition
grub rescue>

Since I am absolutely clueless when it comes to GRUB... Any ideas?

Big thanks in advance!

---

### Post by darkod on 2010-02-03
OK, it's time for the dumb question: Did you install ubuntu at all?
I know you mentioned you prepared / and swap partition with Gparted, but what about actually installing it?

Also, to avoid assumptions, you can also boot the live desktop again, download the script in my signature, move it on desktop for example and execute it with:
sudo bash ~/Desktop/boot_info_script*.sh

It will create results.txt file with detailed info about your boot process. Copy the content here and wrap it in CODE tags for easier reading (with any text selected hit the # button in the toolbar above while typing the post).

---

### Post by cygnus-X1 on 2010-02-03
Now you're bringing back old memories for when I first started working on computers! ~_o "Is the printer plugged in? No, not just the data cable. The power cable, too." LOL

I double-clicked the icon on the live CD desktop that said Install Ubuntu, answered all of the various questions when prompted, and followed the directions of putting the boot on to the / partition (sda5). 

The interesting thing is that I have already dual-booted 8.04(32) and 9.10(64) on my main system without a hitch, though I had the choice to use GRUB legacy. Also, both the 32 and 64 bit versions tested O.K. when the verify disk program was run. 

Anyhow, here's the text file:

```
============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
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

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
$MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00091dfc

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    31,455,269    31,455,207   7 HPFS/NTFS
/dev/sda2          31,455,270    62,910,539    31,455,270   5 Extended
/dev/sda5          31,455,333    54,910,169    23,454,837  83 Linux
/dev/sda6          54,910,233    62,910,539     8,000,307  82 Linux swap / Solaris
/dev/sda3          62,910,540   488,392,064   425,481,525   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        220B9D09255566CD                       ntfs       2K                            
/dev/sda3        3E4CE1AF4CE1625F                       ntfs       Data                          
/dev/sda5        29a286ae-d2b2-49bb-986d-6f0c9af366fa   ext4       910                           
/dev/sda6        7a1eea4d-fc6f-444d-8916-935962ae1f5c   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINNT

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINNT="Microsoft Windows 2000 Professional" /fastdetect


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
search --no-floppy --fs-uuid --set 29a286ae-d2b2-49bb-986d-6f0c9af366fa
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
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 29a286ae-d2b2-49bb-986d-6f0c9af366fa
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=29a286ae-d2b2-49bb-986d-6f0c9af366fa ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,5)
	search --no-floppy --fs-uuid --set 29a286ae-d2b2-49bb-986d-6f0c9af366fa
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=29a286ae-d2b2-49bb-986d-6f0c9af366fa ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
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
menuentry "Microsoft Windows 2000 Professional (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 220b9d09255566cd
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
UUID=29a286ae-d2b2-49bb-986d-6f0c9af366fa /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7a1eea4d-fc6f-444d-8916-935962ae1f5c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  16.1GB: boot/grub/core.img
  16.1GB: boot/grub/grub.cfg
  16.1GB: boot/initrd.img-2.6.31-14-generic
  16.1GB: boot/vmlinuz-2.6.31-14-generic
  16.1GB: initrd.img
  16.1GB: vmlinuz

```


Meanwhile, while you're looking at that, I'll look over the "Grub 2 Basics" posting on the forum. I'll check back later and Thanks for all of the help!

[COLOR="White"]-[/COLOR]

---

### Post by darkod on 2010-02-03
Hmmm, it looks good except for this under the sda3 description:

Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

It suggests running chkdsk from windows. Not sure if grub2 will break down even if /dev/sda3 has some issues because the ubuntu partition is in fact /dev/sda5, but you might run chkdsk just to make sure all is fine with /dev/sda3.

The easiest way to go back to windows MBR (so you can at least boot 2k again), is booting the live desktop again and doing:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

Ignore any warnings it will report. That should write generic windows MBR to sda and 2k should boot.

Look around at the other ntfs partition, /dev/sda3, and try to check it. After you are satisfied it's looking good, because we returned windows MBR on sda, you have to do those two commands to reinstall grub2 to /dev/sda again. Otherwise 2k will continue booting directly.

PS. You are definitely sure you don't have raid meta data remains on the hdd? Because that error above says can also happen because of Fakeraid settings.

---

### Post by cygnus-X1 on 2010-02-03
LILO, eh? I have even less experience with that. I'll look into changing it as soon as I can. (Supper time.) Out of curiosity, what are the possibilities for GRUB legacy instead of GRUB2, or is that out of the picture?

> PS. You are definitely sure you don't have raid meta data remains on the hdd? Because that error above says can also happen because of Fakeraid settings.

This is a "brand new" refurb drive straight from Western Digital. It went right into that box when it got here and I've been trying to get it running ever since. At one point I even used Gparted to format the who thing as NTFS.

BTW - If you were at a "start from scratch" position with this hardware config, and wanted to run 2K and 9.10 as a dual boot with minimal space, and have the brunt of the drive for shared data storage (NTFS), how would you go about it? That might help me, and anyone else, to get things going.

Big thanks in advance! :guitar:

---

### Post by darkod on 2010-02-03
> **cygnus-X1 said:**
> LILO, eh? I have even less experience with that. I'll look into changing it as soon as I can. (Supper time.) Out of curiosity, what are the possibilities for GRUB legacy instead of GRUB2, or is that out of the picture?



This is a "brand new" refurb drive straight from Western Digital. It went right into that box when it got here and I've been trying to get it running ever since. At one point I even used Gparted to format the who thing as NTFS.

BTW - If you were at a "start from scratch" position with this hardware config, and wanted to run 2K and 9.10 as a dual boot with minimal space, and have the brunt of the drive for shared data storage (NTFS), how would you go about it? That might help me, and anyone else, to get things going.

Big thanks in advance! :guitar:
Those lilo commands are just to install windows generic mbr, you will never see lilo and don't worry about it. It is possible to boot 9.10 with grub1 but I haven't actually tried it.
As for advice about partition sizes, I'm not using linux that long to give relevant information.
I would probably say the obvious here:
1. See how much space 2k takes with all your win software on it.
2. Ubuntu / is happy with 10-15GB, maybe 20GB tops.
3. Swap about 150% of your ram if you plan to hibernate regularly, otherwise 2GB is enough especially if you have lots of ram, swap doesn't even get used.
4. Separate /home partition to make future clean installs of ubuntu very easy, it should be happy with 10-15GB especially if you keep the large files (music, videos, etc) on the shared ntfs.
5. Shared ntfs, all the rest.

For reference, 9.10 default install takes around 2.7GB and it doesn't grow much with software adding. Not as much as windows definitely. So as long as you keep large media files on the shared ntfs, you really don't need huge / and /home.

PS. And "brand new" disk doesn't always mean no raid meta data. I have seen it, but can't explain it. But if you ran those two commands to remove dmraid settings, they would report raid meta data and ask you if you want it removed.

---

### Post by raymondh on 2010-02-03
> **cygnus-X1 said:**
>  Out of curiosity, what are the possibilities for GRUB legacy instead of GRUB2, or is that out of the picture?

[COLOR="Navy"][Number 12 in this how to]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=drs305").  If you really want to revert.[/COLOR]

BTW - If you were at a "start from scratch" position with this hardware config, and wanted to run 2K and 9.10 as a dual boot with minimal space, and have the brunt of the drive for shared data storage (NTFS), how would you go about it? That might help me, and anyone else, to get things going.

[COLOR="Navy"]Install 2K and make sure it's running well.  Use gparted to shrink 2k to create space for data and ubuntu.  Use gparted to create a NTFS, primary partition from the freed-up space.  Boot into 2k and mount the storage parrtition (assign a drive letter) as well as run checkdsk to make sure 2k is well after the resizing.  Use gparted to create the Ubuntu partitions.  I'd make said partition an Extended which would house 3 logical partitions.  Swap at 2Gb.  Root at 20GB using ext3 and the rest for /home, ext3 or ext4.  Then I would install selecting MANUAL and install the appropriate mountpoints unto the prepared partitions ..... that's what I would do.[/COLOR]



[COLOR="Navy"]Raymond[/COLOR]

---

### Post by cygnus-X1 on 2010-02-03
> sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

This worked like a champ! 2K is running again. Am now doing a chkdsk /f on sda3 (E: drive). With just an old T-bird 850, it's gonna take a while to do that 202GB area!

BTW:

> But if you ran those two commands to remove dmraid settings, they would report raid meta data and ask you if you want it removed.

Sorry, I must have missed them. What are they again?

Thanks!

---

### Post by darkod on 2010-02-04
> **cygnus-X1 said:**
> This worked like a champ! 2K is running again. Am now doing a chkdsk /f on sda3 (E: drive). With just an old T-bird 850, it's gonna take a while to do that 202GB area!

BTW:



Sorry, I must have missed them. What are they again?

Thanks!

From live desktop:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

---

### Post by cygnus-X1 on 2010-02-04
Sorry to take so long to get back to you. Today has been a challenge to say the least. Anyhow, here is how things have gone so far...

> sudo dmraid -E -r /dev/sda

Didn't work. It couldn't find a RAID drive.

> sudo apt-get remove dmraid

Worked fine. 

I tried a few other nondescript things, but nothing worked. So since this is technically a fresh install and it doesn't take lots of time to install either 2K (w/o supporting software) or 9.10, I decided to try something novel. I double checked to see if the 9.10 CD was error free, which it is, and threw caution to the wind and loaded the entire 250GB HDD as 9.10(32). No dual boot or anything. Just a vanilla install. After it was finished, I rebooted. And this is what appeared on the screen after the BIOS finish and it was time for GRUB2 to take over:

```
GRUB loading.
error: out of disc
grub rescue>

```

Tried it twice with the same results. (I'ld try 64, but the system doesn't support it.)

I also tried doing an install and told it to use the first 50% +/- of the HDD for 9.10(32) and 50% +/- unallocated. Curiously, the partition editor left a small 57MB partition at the front of the drive and loaded. It essentially gave the same error, only with a long alpha/numeric after it, but it actually went to the GRUB2 screen! 
No celebration yet... When I select Linux to boot to, it said:

```
error: no such device: 80345cc1-56d1-454c-b138-ce7717ca9465
Press any key to continue...
```

So... Any idea where I should go from here? Maybe I should try 9.04 since it has the much more **reliable** GRUB legacy and the upgrade to 10.04 or 10.10 when they come out. Since there is 7 or so hours between us, Eastern US where I'm at, I'll check back in about 13 hours after this gets posted. In the mean time, I'll burn the 9.04 disc...

Thanks again!

[COLOR="White"]-[/COLOR]

BTW - Thanks Raymond, That is pretty much the setup and order I initially started with... And lead to this. I have this gnawing feeling that the 32bit version of 9.10 coupled with GRUB2 might not be playing nice with my system, as old as it is. Asus A7V-133 Mobo / AMD Thunderbird 850MHz / 1.5 GB PC133 SDRAM which may have been pretty hot 8 years ago when I initially built it. But a tad slow by today's standards. Fortunately, this is just the kids system to do their schooling on. I want them to learn how to do things in Linux, but most of the educational software is Winders only. My main/biz system is running a Gigbyte MA78GM-S2HP Mobo / 4GB DDR2 / 95w Phenom II X4 945 Deneb 3.0 QuadCore. With that rating, I'll use a virtual-box for XP. ~_o  The challenge will come when I try to configure Mythbuntu and XP on a third box. I don't know if I'll do a dual boot or virtualize it. It depends on how things work out on this install. 

[COLOR="White"]-[/COLOR]

---

### Post by Deer Hunter on 2010-02-05
It's me here, running from my freshly-installed (read: *not* Live-CD) Ubuntu 9.10.  Everything seems to have gone well, and I have been able to accomplish what I wanted to with the partitioning, so thanks to one and all for the help.

Deer Hunter

PS.  How do I mark this problem as "Solved," or do the moderators take care of that?

---

### Post by darkod on 2010-02-05
> **Deer Hunter said:**
> It's me here, running from my freshly-installed (read: *not* Live-CD) Ubuntu 9.10.  Everything seems to have gone well, and I have been able to accomplish what I wanted to with the partitioning, so thanks to one and all for the help.

Deer Hunter

PS.  How do I mark this problem as "Solved," or do the moderators take care of that?

Glad to know it worked fine for you. You can mark thread as solved in Thread Tools above the first post on any page (if there are more pages with posts in the thread).

---

### Post by darkod on 2010-02-05
> **cygnus-X1 said:**
> Sorry to take so long to get back to you. Today has been a challenge to say the least. Anyhow, here is how things have gone so far...

```
error: no such device: 80345cc1-56d1-454c-b138-ce7717ca9465
Press any key to continue...
```So... Any idea where I should go from here? Maybe I should try 9.04 since it has the much more **reliable** GRUB legacy and the upgrade to 10.04 or 10.10 when they come out. Since there is 7 or so hours between us, Eastern US where I'm at, I'll check back in about 13 hours after this gets posted. In the mean time, I'll burn the 9.04 disc...


Actually I'm puzzled how even a clean install is giving you trouble. As for this error no such device message, I think it happens when grub2 on the MBR is no longer able to find the / partition UUID because it was changed by the reinstall.
I know you tried a few times, but reinstalling grub2 to the MBR should take care of this error. After your last install on 50% of the hdd I'm not sure what is your / partition, it could be /dev/sda5 or /dev/sda1. Boot into live desktop and check the partitions with:
sudo fdisk -l

Then depending which one is your / (Linux) partition, execute:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

In the above commands you might need to replace /dev/sda5 with /dev/sda1 depending on the fdisk results.

---

### Post by cygnus-X1 on 2010-02-05
> Actually I'm puzzled how even a clean install is giving you trouble.

That makes two of us! I went through the steps of wiping the HDD and starting a vanilla install from scratch... Again. It gave the same error message of:

```
GRUB loading.
error: out of disc
grub rescue>
```

After Moving GRUB2 it gave the same message of:

```
error: no such device: 80345cc1-56d1-454c-b138-ce7717ca9465
Press any key to continue...
```

Only with a different UUID.

After 4 days of failures, I think I'll take a breather for now, and do some reading next week to see what is out there, and if anyone has successfully done a 2K/Karmic(32) dual boot without a ton of hassle. Thankfully, this isn't a priority!

One thing I'm curious about is, is there a way to make GRUB legacy the boot-loader? I have this thread bookmarked and will check back after the weekend is over. When I get ready to go at it again, I'll start a new thread.

Many thanks for all your help, darkod

[COLOR="White"]-[/COLOR]

---

### Post by raymondh on 2010-02-05
> **cygnus-X1 said:**
> 
```
GRUB loading.
error: out of disc
grub rescue>
```
]

What is the vintage of your machine and BIOS?  And did you put a new, bigger HD?  But then again, you would be reporting an error18.  Just wondering if GRUB2 is not able to boot far into the HD.

ON how to revert

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Regards,

Raymond

---

### Post by cygnus-X1 on 2010-02-05
> Asus A7V-133 Mobo / AMD Thunderbird 850MHz / 1.5 GB PC133 SDRAM

I believe the Mobo is Rev.1 and the BIOS is 1003 (for now). I started buying the parts to build it 8 years ago this March (2002). It was my first rig and my first build, and I had two brothers and a boat-load of research to make sure things all worked together, and be as forward compatible as possible. I never dreamed it would last this long, but it has surprised me on more than one level. It even took a power surge, while on a UPS w/surge protect, that blew out the a CD-RW drive and a PCI slot. Even the original Voodoo 3 card still works. Though I upgraded that to an ATI AIW-64Mb video card about a year after I built it. Usually, I've had a 20GB HDD in it, but there was an 80GB HDD in there a little while ago.

When I was initially setting things up, Tested to make sure Karmic would run on it in Live mode, and that worked. I check the minimum requirements for it as well, and it passed there, too. I also tried 2K as a vanilla install and things worked just fine. After that, I started following what I had read about installing Winders before Linux, and that's when all of the fun began.

On one of my other boxes, I was already running 8.04(32). Since one of my brothers was trying Ubuntu for the first time and said he was impress with 9.10(64), I thought I'ld run it side-by-side on the 8.04 box. The only problem I had was GRUB2. Fortunately, I was dumb enough to tell it not to blow off GRUB legacy. So it boots just fine to both 8.04 and 9.10, w/o number 2. So far, I ain't impressed with GRUB2 at all! 

Hence, Thank you for the link on how to revert! I may just give it try in the morning to see if it works for the this past install. Wish me luck!

BTW - I'm going to have to finally update the BIOS as I'm picking up a T-Bird 1.4GHz AYHJA CPU to speed things up a bit. ~_o I think one reason the system lasted this long is that I never overclocked it.

**Finally found that mobo dos not support LBA in BIOS. Latest update should take care of it. Then I should be able to make things happen! **
[COLOR="White"]-[/COLOR]

---

### Post by tvrgreg on 2010-09-03
I originally installed Ubuntu 8 as a dual boot with XP. Using the options on the install disk, Ubuntu set up 2 partitions using half of my HDD1 which is set as a slave and annotated 'D' in windows. This works well except for one niggle concerning the grub loader. Booting from cold this is ok and runs up to the system options and will load Ubuntu by default or XP if the option is selected. In order to restart however the system has to be completely shutdown. Rebooting warm gives an error 18 code and the system hangs. This makes updates etc a bit of a pain when restarts are required to complete installation. I have steadily updated Ubuntu and am now on 10.01 but the grub problem has never been resolved. I can't find a setting in the bios that can change anything. Setting HDD1 as first boot brings up more errors. I have searched the faqs but they all seem to refer to single HD systems or instances where error 18 appears every time. Any help would be appreciated.

---

