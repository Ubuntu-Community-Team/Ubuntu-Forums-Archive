---
title: "Saving Private Ubunturion"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by Some_Kittens on 2010-02-22
My sad story:
One happy day, I was enjoying my dual partitioned laptop, one for an installation of Ubuntu 9.04: Pvt. Ubunturion, and one massive one for storage.  All of a sudden, a terrible, evil thought crept into my mind.  One so horrifying as to scare the nonexistent pants of of Sauron himself.

I....  Should install Windows XP.  Struggling with evil thoughts, I tried to tear myself away as backed everything up and inserted the disk that seem to glow with malevolence.  Terrified, I attempted to look away as the install flashed through the text based, and GUI portions!
To no one's surprise, the first attempt at installation failed, thanks to the valiant efforts of many a byte.  Once again, evil forces latched onto my laptop, and this time they overcame the open sources of good.
XP was there, and there to stay.  I had no choice.  My only hope rested in a flanking action, meeting the three-piece suit clad forces of Microsoft at their weakest point: The MBR.
Consulting the oracle that is the Ubuntu Wiki for luck, I plunged ahead with Auto Super Grub Disk!  Tricking the XP bootloader, it added itself in order to install my beloved GRUB.
The ruse was found out, and I was left with a black screen displaying Try hd(0,0) EXT2.
Rearming, I enlisted the forces of UNetBootin, and my considerable army of USB sticks.  I installed ASGD's older, more powerful brother: Super Grub Disk.  Letting out a cry of victory as it successfully booted, I was faced again with utter defeat, as every option to fix or boot Ubuntu led to a frozen screen, with many an fatal message splashing its sad woe across my screen.
XP had won this round.  But this time I came back Harder, Better, Stronger, Faster.  Installing 9.04 to my most loyal USB stick, we plunged ahead.  Watching the Ubuntu logo joyously leap to my screen, I thought I had finally won.  Suddenly, I was interrupted by errors that seem to have been sent by the dark lord Gates himself.  I hung my head in sorrow, as all that was left of a once-proud Ubuntu USB was a sad little terminal prompt.
I turned to the biggest and best of Ubuntu's, 9.10, but he declined to help, stating that his loyalty to GRUB2 superseded any feeling for me in his kernel.
My heart was so desperate for the recovery of Pvt. Ubunturion, that I enlisted the help of an eccentric old wizard, VMWare.  He gaily handed me an image of 9.04 with a twinkle in his eyes.  Booting it, but with little hope, I reached the login screen, and was struck dumb.  The old man claimed he had the password somewhere, but I was not ready to wait around with Ubunturion suffering.
I then decided to request the assistance of the old wise one: 8.04.4.  We geared up, faces grim, but when we finally booted, and he was ready to slay this dragon once and for all, he tripped and fell.  With tears running down my eyes, I watched him plunge down into the abyss, with a hollow echo of "NO....EXT4....SUPPORT"
My heart grieved, and I wore nothing but sackcloth and spread ashes over my head.  My good buddy Ubunturion seemed finally lost.
It all changed when a fair maiden approached me and introduced herself as WUBI.  She had a proposal to win this war from the inside out.  She would sneak behind enemy lines and trick them into installing Ubuntu in their own bootloader!  We then could team up and finally recover poor Pvt. Ubuntu.
Alas, I never saw her again.  One final note after she had completed her mission fell into my hands.  It simply stated: Try hd(0,0) EXT2.

Morose, and having exhausted my considerable allies in this battle, I finally turn to you, good men of Ubuntuforumonia.  The challenge is there.  Are you willing to give what it takes, for the life of Pvt. Ubunturion?

---

### Post by Some_Kittens on 2010-02-22
The tl;dr version
Two partitions, XP, Ubuntu
Installed XP second, can't boot to Ubuntu
Wubi and Auto Super Grub Disk hang on Try hd(0,0) EXT2
USB Ubuntu
8.04.4 doesn't have EXT4 support
9.04 won't boot past a broken terminal prompt, gives lotsa errors.
9.10 uses GRUB2
Super Grub disk gives me lots of menus, but fails every time I try to do something.

---

### Post by DawieS on 2010-02-22
Excellent piece you wrote there, I nearly had to pick a tear at some stage...:smile:

XP (and probably all Windows installations) has a way of wanting to be the ONLY operating system on a hard drive, and goes about changing the numbering sequence (or direction of counting) of partitions in the MBR, if it detects possible other operating systems upon installation. Therefore it is always best to install XP first, if you go for dual booting from the same drive.

> Wubi and Auto Super Grub Disk hang on Try [COLOR=Red]hd(0,0)[/COLOR] EXT2

Assuming you can edit the Grub menu options, try changing to [COLOR=Red]hd(0,1)[/COLOR] or [COLOR=Red]hd(0,2)[/COLOR] etc. This would point the boot loader to the same physical position on the drive that was previously known as [COLOR=Red]hd(0,0)[/COLOR] by reading the MBR.

---

### Post by presence1960 on 2010-02-22
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

**_P.S. Leave the prose behind and cut to the chase!_**

---

### Post by Some_Kittens on 2010-02-23
> **DawieS said:**
> Assuming you can edit the Grub menu options

I can't, Try hd(0,0) EXT2 appears immediately after I select Ubuntu/Auto Super Grub Disk from the XP boot menu.

---

### Post by Some_Kittens on 2010-02-24
My apologies for the prose, I was feeling creative.
results.txt Posted from 9.10 on a USB.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x346028f1

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    23,197,859    23,197,797   5 Extended
Extended  partition  linking to another extended partition
/dev/sda5                 189    21,221,864    21,221,676  83 Linux
/dev/sda2          21,237,930    23,197,859     1,959,930  82 Linux swap / Solaris
/dev/sda3    *     23,197,860   488,392,064   465,194,205   7 HPFS/NTFS

/dev/sda1 overlaps with /dev/sda2

Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 4026 MB, 4026531840 bytes
147 heads, 48 sectors/track, 1114 cylinders, total 7864320 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8adb3ca1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             48     7,864,319     7,864,272   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda2        5ad85b0b-591b-408d-b940-8fc1f28a6a62   swap                                     
/dev/sda3        1E84D02884D003E5                       ntfs                                     
/dev/sda5        90c3a020-dda4-4b22-b13a-f8988be42a54   ext4                                     
/dev/sdb1        ACE1-0D21                              vfat                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb1        /cdrom                   vfat       (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda5/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=90c3a020-dda4-4b22-b13a-f8988be42a54

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
# defoptions=quiet splash

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
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        90c3a020-dda4-4b22-b13a-f8988be42a54
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=90c3a020-dda4-4b22-b13a-f8988be42a54 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5ad85b0b-591b-408d-b940-8fc1f28a6a62 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


   4.9GB: boot/grub/menu.lst
   1.7GB: boot/grub/stage2
   1.1GB: boot/initrd.img-2.6.28-11-generic
   3.3GB: boot/initrd.img-2.6.28-13-generic
   4.8GB: boot/initrd.img-2.6.28-14-generic
   8.2GB: boot/initrd.img-2.6.28-15-generic
    .6GB: boot/vmlinuz-2.6.28-11-generic
   4.0GB: boot/vmlinuz-2.6.28-13-generic
   4.0GB: boot/vmlinuz-2.6.28-14-generic
   7.0GB: boot/vmlinuz-2.6.28-15-generic
   8.2GB: initrd.img
   4.8GB: initrd.img.old
   7.0GB: vmlinuz
   4.0GB: vmlinuz.old

================================ sda3/boot.ini: ================================

[boot loader] 
timeout=15 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\ubnldr.mbr="Auto Super Grub Disk" 
C:\wubildr.mbr = "Ubuntu" 
=======Devices which don't seem to have a corresponding hard drive==============

sdc 
```

---

### Post by presence1960 on 2010-02-24
Boot from the ubuntu 9.04 Live CD. Choose "try ubuntu without any changes." When the desktop loads open a terminal (Applications > Accessories > Terminal) and do this:

```
1. Type sudo grub. Should get text of which last line is grub>
2. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
3. Type "root (hd0,4)"
4. Type "setup (hd0)", to install GRUB to MBR
5. Quit grub by typing "quit".
6. Reboot and remove the bootable CD.

```

Boot into Ubuntu without the Live CD. Open a terminal and run ```
gksu gedit /boot/grub/menu.lst
```That is a lowercase L in .lst

Scroll down to this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1
```

Change it to:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title           Windows XP
rootnoverify    (hd0,2)
chainloader     +1

```

Click Save on top toolbar & close file. reboot and boot into XP. You should now be good to go!

Sorry about the delay, my DSL modem went and I had to wait for a new one to be shipped. Not bad though only waited one day.

---

### Post by Some_Kittens on 2010-02-24
The issue with that is that I can't boot to a graphical desktop in 9.04 at all, I've tried Unetbootin (downloaded .iso, as well as UNB's own fetch), and PenDriveLinux's loader, on both 32 and 64 bit versions.

---

### Post by bruno9779 on 2010-02-24
Have you tried with liveCD?

---

### Post by Some_Kittens on 2010-02-24
Embarrassingly enough, I don't have any CDs.  Would that make a difference?

---

### Post by bruno9779 on 2010-02-24
There are way more things that can go wrong with an usb boot, compared to a CD boot.

And since usb boot is not getting you anywhere, you may as well give the CD a shot.

By the way, I always keep a liveCD of my current distro at hand. I do not use it often at all, but i do use it.

---

### Post by cariboo on 2010-02-24
If you can boot in recovery mode, the instructions in presence1960's post should work. The instructions are for grub-legacy. If you  need instructions for grub2 have a look at [this]("https://wiki.ubuntu.com/Grub2") page. Scroll down to Recover Grub2 via LiveCD.

---

### Post by Some_Kittens on 2010-02-25
Will do, I'll see if someone has a cd I can "borrow".  I'll take that advice about keeping a current cd around.

---

