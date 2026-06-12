---
title: "GRUB Windows 7 option restarts computer"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by Mygly on 2010-04-24
I'm having a problem with GRUB.

I had an installation of Windows 7 and then today decided I wanted to turn my machine into a dual booter again. So I installed the latest Debian stable release (5.0.2), creating a new partition on my second hard drive and installing it there. Naturally I installed GRUB as well and rebooted. I can boot into Debian from GRUB fine, but if I chose the Windows 7 option (title Windows Vista/Longhorn (loader)) the screen goes black and the machine reboots. I have tried booting with the Windows 7 disc and then going to recovery and using command line with:

bootrec /mbr - success
bootrec /fixboot - fails (can't remember the exact message)

bootsect /nt60 c: /mbr - success

fdisk -l
```

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x203c203b

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2              13       19269   154674176    7  HPFS/NTFS
/dev/hda3           19270       19457     1510110    5  Extended

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa93c10ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       74174   595802623+   7  HPFS/NTFS
/dev/sda2           74175       77669    28073587+  83  Linux
/dev/sda3           77670       77825     1253070    5  Extended
/dev/sda5           77670       77825     1253038+  82  Linux swap / Solaris

```

I ran the boot info script and this is what I got:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/hda and looks on boot drive #2 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sda

hda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

hda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

hda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Debian GNU/Linux 5.0
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: hda ___________________ _____________________________________________________

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x203c203b

Partition  Boot         Start           End          Size  Id System

/dev/hda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/hda2             206,848   309,555,199   309,348,352   7 HPFS/NTFS
/dev/hda3         309,556,485   312,576,704     3,020,220   5 Extended
Empty Partition


Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa93c10ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63 1,191,605,309 1,191,605,247   7 HPFS/NTFS
/dev/sda2       1,191,605,310 1,247,752,484    56,147,175  83 Linux
/dev/sda3       1,247,752,485 1,250,258,624     2,506,140   5 Extended
/dev/sda5       1,247,752,548 1,250,258,624     2,506,077  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hda1        7E5824A1582459E3                       ntfs       System Reserved               
/dev/hda2        16B82ED5B82EB2E3                       ntfs                                     
/dev/sda1        CA64F48364F47413                       ntfs       Local Disk                    
/dev/sda2        71afc9da-b86c-48b9-9662-9fe80b4c47ec   ext3                                     
/dev/sda5                                               swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext3       (rw,errors=remount-ro)


=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-legacy-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.26-2-686
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda2 ro quiet
initrd		/boot/initrd.img-2.6.26-2-686

title		Debian GNU/Linux, kernel 2.6.26-2-686 (single-user mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.26-2-686 root=/dev/sda2 ro single
initrd		/boot/initrd.img-2.6.26-2-686

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda2       /               ext3    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

=================== sda2: Location of files loaded by Grub: ===================


 613.9GB: boot/grub/menu.lst
 613.9GB: boot/grub/stage2
 613.8GB: boot/initrd.img-2.6.26-2-686
 613.9GB: boot/initrd.img-2.6.26-2-686.bak
 613.9GB: boot/vmlinuz-2.6.26-2-686
 613.8GB: initrd.img
 613.9GB: vmlinuz
```

I know this is Ubuntu forums and I'm using Debian, but frankly this is the best Linux community around and Ubuntu is built on Debian so they are very similar. I find myself alternating between the two. Anyways, I really appreciate any help I might be able to get, this is killing me. :confused:

*edit: please ignore the wubi in the title, I did not use the windows installer since I actually installed Debian, not Ubuntu*

---

### Post by bcbc on 2010-04-24
You have a mix of /boot and /Boot and /BOOT files on the windows partition. This confuses Windows (not case-sensitive). So mount it from debian and delete (which ones I can't say). Anyway - try that...

---

### Post by Mygly on 2010-04-24
After doing
```
sudo mount /dev/hda1 /mnt/win7boot
```
and then changing to the directory and
```
ls -A
```
all I see is ```
Boot bootmgr BOOTSECT.BAK System Volume Information
```

I don't see any duplicates of anything.

---

### Post by bcbc on 2010-04-24
OK... 

One thing that puzzles me is how small hda1 is. Most likely Windows7 is on hda2. But hda1 has the boot flag set...

I'm not the best person to help you with this. But [this site]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD") has helped others get Win7 booting again.

---

### Post by Mygly on 2010-04-24
I think the reason hda1 is so small is it's just the windows boot loader and possibly some recovery functionality. The actual Windows 7 OS is on hda2. This is what I think is the case.

What's puzzling to me is that if I do
```
bootrec /fixmbr
```
this should overwrite GRUB, right? However it seems that none of the attempted windows mbr fixes has any effect on GRUB... So is it the case that GRUB is on my second hard drive (we'll call HD2), the windows boot loader is on my first hard drive (HD1) and therefore no bootrec commands overwrite GRUB because it's not in the same place as the windows boot loader? This is a theory I thought of right now, but I don't know.

---

### Post by bcbc on 2010-04-24
> **Mygly said:**
> 
What's puzzling to me is that if I do
```
bootrec /mbr
```
this should overwrite GRUB, right? However it seems that none of the attempted windows mbr fixes has any effect on GRUB... So is it the case that GRUB is on my second hard drive (we'll call HD2), the windows boot loader is on my first hard drive (HD1) and therefore no bootrec commands overwrite GRUB because it's not in the same place as the windows boot loader? This is a theory I thought of right now, but I don't know.

I think it should be
```
bootrec /fixmbr
```

But if windows still doesn't boot, then you'll have no working OS so make sure you have a live CD at hand.

According to the boot info script, grub is in the MBR of the first drive.

---

### Post by oldfred on 2010-04-24
I do not understand why the script shows multiple entries but you do not see them??  I wonder if the fixboot did not work because of the extra files? Did you look in sda1 not sda2?

The fixMBR just rewrote the sda MBR but the OP must be booting from sdb (fortunately or he would have overwritten grub).

New installs of win7 create a separate 100mb boot partition. Installs over Vista or into an existing NTFS partition do not create a boot partition.

---

### Post by Mygly on 2010-04-24
hda1 contains:
Boot bootmgr BOOTSECT.BAK System Volume Information,
so this seems to be the windows boot partition

hda2 contains:
the actual Windows 7 OS

sda1 contains:
All the files from my secondary hard drive (I use this just for file storage in windows, but also installed Debian here)

sda2 contains:
this is Debian

I can't even overwrite GRUB if I wanted to, I'm stumped where to go from here.

---

### Post by bcbc on 2010-04-24
> **oldfred said:**
> I do not understand why the script shows multiple entries but you do not see them??  I wonder if the fixboot did not work because of the extra files? Did you look in sda1 not sda2?

The fixMBR just rewrote the sda MBR but the OP must be booting from sdb (fortunately or he would have overwritten grub).

New installs of win7 create a separate 100mb boot partition. Installs over Vista or into an existing NTFS partition do not create a boot partition.

I'm puzzled, but from the commands posted it looks like hda1 was mounted correctly and therefore ls -A should have picked up duplicates. Also bootinfoscript didn't show /boot files on any other partition, so unlikely to have mounted the wrong partition.

---

### Post by BlackMaxPhoto on 2010-04-24
There IS an issue with Win7 GRUB2 dual boot, a few weeks ago I read that there was a drive enumeration issue in GRUB2 that is the actual cause.

See the link below for a list of solutions that don't work:

[HTML]http://ubuntuforums.org/showthread.php?t=1459441[/HTML]

BC
:popcorn:

---

### Post by oldfred on 2010-04-24
If in BIOS you directly boot your windows drive (160GB) does it boot directly into windows or give error messages. Grub will only boot a working windows install.

It is interesting that sda is hda and sdb is sdb. Does Debian see a difference between PATA & SATA?

---

### Post by bcbc on 2010-04-24
I was wondering whether booting from the DVD delivered a different drive order than booting from hard drive. That's a stab in the dark, but otherwise why would replacing the MBR fail.

Personally, if I couldn't sort it out - I'd unplug the second drive to remove any ambiguity, and try and get windows sorted. Of course you'd need to boot the recovery dvd - otherwise you'd have grub as your MBR and it'd fail miserably. That at least would be better than reinstalling, as Blackmax had to do :(

If normal recovery doesn't work, try the 'nuclear holocaust' section at the bottom of that link I supplied earlier.

---

### Post by Mygly on 2010-04-24
Alright, So I have windows running again without GRUB. Here's what has happened so far, from the beginning.

Originally I only had Windows 7 installed. It was installed on a 160GB drive, HD1, and I had another drive, HD2 (640GB), that I used to store files in windows.

I then decided I would like a Linux distro again that I could boot into for doing various tasks (I've alternated between Debian and Ubuntu in the past). This time I figured I'd go with Debian, for no other reason than it's what I've used the most.

Installed Debian 5.0.4 (Lenny) using the GUI install, went smooth, I chose to install Debian on HD2, the drive I use for file storage in windows. So I had to resize the NTFS partition I was using for storing files to make room for Debian. That went fine and then I installed all of Debian onto one partition (excluding swap of course). It detected Windows 7, so I said go ahead and install GRUB.

Debian installed successfully, and booted when I chose it from GRUB's options, but if I chose Windows 7, it would show the boot command, then go to a black screen (blank) and then after a few seconds reboot the computer and then I'd be back to GRUB again.

I then tried to get Windows 7 to boot from GRUB for a bit with no luck. Then I decided I just wanted to be able to boot back into Windows 7 again. So I restarted with the Windows 7 DVD in the drive, let it boot to the screen where you choose language, etc. and then hit next and chose Repair. **No windows installation was shown in the list.**

Startup repair did not work, and I tried
```

bootrec /fixmbr

```
with sucess
```

bootrec /fixboot

```
this failed, although I don't remember the exact error message

I also tried
```

bootsect /nt60 c: /mbr

```
which was successful

After all of that I restarted the computer. However, it still went to GRUB, which I found odd since the MBR should have been overwritten. I then noticed GRUB and the windows boot loader were not on the same drive. The windows boot loader must have been on HD1 and GRUB on HD2.

At this point I decided to try switching the hard drive boot order in BIOS, but that just led to nothing booting. Then I opened up my case and unplugged HD2 (file storage) because every restart GRUB was loading up and I couldn't figure out another way to stop that. Upon booting up with only HD1 (Windows 7) plugged in it still attempted to load GRUB, but with an error because it could not find GRUB. So I again restarted the computer with the Windows 7 DVD in the drive and went to recovery. **This time there was a Windows 7 installation in the list**. Startup recovery didn't work, again (still got the GRUB error after this). So I once again tried opening a command prompt to recover manually.

```
bootrec /fixmbr
```
success again.
```
bootrec /fixboot
```
success this time!

After exiting the command prompt in recovery, I selected restart. After booting this time it successfully booted into my Windows 7 installation. I then shut down the computer and plugged HD2 back in and started up. Everything went fine, an automatic CHKDSK test ran on HD2, but all was fine and it booted into Windows 7 normally.

So now I'm back to where I was before installing Debian. I would ideally like to be able to dual boot a system with either Debian or Ubuntu as my Linux distro, but I'm not sure I want to try to get GRUB working with both, as you can see I've had bad luck with it so far. How is the Ubuntu Wubi installer? I would then be using the windows boot loader to boot into either Ubuntu or Windows, correct?

---

### Post by oldfred on 2010-04-24
You should be able to reinstall grub to the 640GB drive. Then set BIOS to boot from the 640GB drive. If you ever had drive issue you can still directly boot windows from the 160GB drive.

What still seems confusing is that is sda-640GB  when windows is hda-160GB? In Ubuntu one would be sdb.

---

### Post by bcbc on 2010-04-24
Great you've recovered...

I used wubi for a bit. It works ok although you won't find many people here recommending it.

Oldfred's idea is good if it's convenient to do that.

Good luck.

---

### Post by Mygly on 2010-04-24
Yea, I didn't know Wubi was just like running Ubuntu as a Windows application, definitely not what I'm after. I think I'm actually going to install Ubuntu 9.10 and if I get to the point where Win7 won't boot again I should be able to fix it if things get too out of hand. I will keep posting until I get it working.

---

### Post by bcbc on 2010-04-24
> **Mygly said:**
> Yea, I didn't know Wubi was just like running Ubuntu as a Windows application, definitely not what I'm after. I think I'm actually going to install Ubuntu 9.10 and if I get to the point where Win7 won't boot again I should be able to fix it if things get too out of hand. I will keep posting until I get it working.

It's not exactly like 'running ubuntu as a Windows application'. It's more the install and uninstall is like any Windows application - in fact the ubuntu os is contained within a file on your windows file system, but the file contains it's own file system (ext4 for 9.10) with ubuntu on it, and this is loop mounted and booted. At this point you are really running ubuntu, not windows. It's a neat way of trying ubuntu without having to deal with the dual boot hell that you found yourself in :) 

Anyway, now that you're an expert - go for the dual boot option.

---

### Post by Mygly on 2010-04-24
Well, I went ahead and axed Debian so I could install Ubuntu 9.10. I went and tried to go with the option of using EasyBCD to use the windows boot loader first and foremost instead of GRUB. Followed the directions at [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) but I get an error about windows failing to start when I chose the new Ubuntu option from the windows boot loader. However, I found out that was because I was using EasyBCD 1.7 which didn't support GRUB2. So I've installed the latest build of EasyBCD 2.0 and configured it similarly to that article except instead of GRUB I've selected GRUB2 and now when I choose Ubuntu from my windows boot loader menu I am sent to GRUB and then I can boot Ubuntu.

Interestingly, once I get to GRUB from the windows boot loader, if I select Windows 7 from the GRUB menu it does the same thing it did before with the blank screen and then restarting and I still have no idea why. I think I'm just going to stick with the EasyBCD method for now. What's the downside to having GRUB installed on the same partition as Ubuntu as opposed to having GRUB installed in the MBR?

---

### Post by oldfred on 2010-04-25
The install of grub2 to a partition worked for me (at least for a while) as I chainbooted to it. Grub spits out all sorts of warnings about using blocklists (whatever they are) and as I understand if certain key files for grub in the grub folder get relocated it may not boot. You would then have to reinstall grub to the partition.

---

### Post by Mygly on 2010-04-25
Yeah, I figured it would only be a big deal if I didn't have another boot loader. Since I'm chain booting to GRUB2 from the Windows boot loader it doesn't seem like there should be any issues... Although I'm not very well versed in boot loaders so I don't know for sure.

---

