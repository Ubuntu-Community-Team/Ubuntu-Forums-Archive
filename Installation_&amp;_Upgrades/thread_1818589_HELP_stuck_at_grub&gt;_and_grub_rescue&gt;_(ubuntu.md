---
title: "HELP: stuck at grub&gt; and grub rescue&gt; (ubuntu 11.04 with windows xp)"
date: 2011-08-05
forum: Installation &amp; Upgrades
---

### Post by jimkenstein on 2011-08-05
please help. i have been stuck for a day now..

i have just installed ubuntu 11.04 off usb stick and it worked fine  until i tried to 'erase and reinstall ubuntu' because the  login-keyring-dont-match thingy. but then when i reboot the command  screen "error: unknown filesystem. grub rescue>" came up and i was  stuck at that. then i read some posts and booted off usb stick and chose  "run ubuntu bla bla" went to the terminal and typed a couple commands  (i cant remember the commands) and reboot.. now all i have is:

1. if i try to boot my pc on WITHOUT ubuntu usb stick i get,
"[B]error: unknown filesystem.
grub rescue[/B]"

2. if i try to boot WITH (from) ubuntu usb stick i get below command screen,
"[B]GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.

grub>[/B] "

please help a s a p, i need my pc for my studies TOMORROW and on!

PC: Dell Mini 10v (Windows XP)

---

### Post by garvinrick4 on 2011-08-05
You have to have something that will boot to fix grub. So in your case without a Optical drive you need a USB flash drive that is bootable.

---

### Post by jimkenstein on 2011-08-05
i know what your meaning to say. as i have mentioned, i will get the "**error: unknown filesystem. grub rescue>**" if i boot from my **main hard drive**. otherwise, booting from my USB stick which has **ubuntu11.04 .iso files in it** although i have changed my **BIOS setup to boot from USB flash drive** in the first place  will give the "**GNU GRUB version bla bla..**" command screen. what do i do now?

---

### Post by apollothethird on 2011-08-05
> **jimkenstein said:**
> please help. i have been stuck for a day now..

i have just installed ubuntu 11.04 off usb stick and it worked fine  until i tried to 'erase and reinstall ubuntu' because the  login-keyring-dont-match thingy. but then when i reboot the command  screen "error: unknown filesystem. grub rescue>" came up and i was  stuck at that. then i read some posts and booted off usb stick and chose  "run ubuntu bla bla" went to the terminal and typed a couple commands  (i cant remember the commands) and reboot.. now all i have is:

1. if i try to boot my pc on WITHOUT ubuntu usb stick i get,
"[B]error: unknown filesystem.
grub rescue[/B]"

2. if i try to boot WITH (from) ubuntu usb stick i get below command screen,
"[B]GNU GRUB version 1.99~rc1-13ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB  lists possible command completions. Anywhere else TAB lists possible  device or file completions.

grub>[/B] "

please help a s a p, i need my pc for my studies TOMORROW and on!

PC: Dell Mini 10v (Windows XP)

Use these two sections of the Ubuntu Documentation:

Command Lie and Rescue Mode / Editing the Grub2 Menu During Boot:
[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

Boot a Specific Kernel Manually:
[https://help.ubuntu.com/community/Grub2#Boot%20a%20Specific%20Kernel%20Manually](https://help.ubuntu.com/community/Grub2#Boot%20a%20Specific%20Kernel%20Manually)

Namely use:

set: to display the current Grub2 settings
ls: to list the partitions
ls: (hdx,y)/ to see where your vmlinuz and initrd.img is installed
ls (hdx,y)/boot to see which kernal and intrd.img files
ls (hdx,y)/boot/grub to see the grub.cfg files

Set or edit what you want then:

boot your computer:

```
https://help.ubuntu.com/community/Grub2#Boot%20a%20Specific%20Kernel%20Manually
```Once you have booted into the system use the "grub-install" command to specify the boot drive.

Example:
```
sudo grub-install --root-directory=/mnt /dev/sdX
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by garvinrick4 on 2011-08-05
Make a new USB flash drive that works. You have made an error and messed up grub on
both HDD and Usb flash drive. If you google there are articles on how to boot from grub prompt
but they will be difficult to understand. 
 Nobody will no what condition your boot is in until it can be looked at with a Live USB (install USB using Try Ubuntu)

---

### Post by jimkenstein on 2011-08-05
okay now im downloading ubuntu's .iso on this other pc. it takes hours to complete downloading as the service sucks in Brunei Darussalam. i'll get back to you later for what to do next, so please please reply to me later. thank you. i would like you to be specific as im a newbie to Ubuntu, seriously (:

---

### Post by garvinrick4 on 2011-08-05
> **jimkenstein said:**
> okay now im downloading ubuntu's .iso on this other pc. it takes hours to complete downloading as the service sucks in Brunei Darussalam. i'll get back to you later for what to do next, so please please reply to me later. thank you. i would like you to be specific as im a newbie to Ubuntu, seriously (:
I will be around to help you out to bad about your internet speeds would drive me nuts.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> I will be around to help you out to bad about your internet speeds would drive me nuts.

it would have taken years to complete download. but luckily i could download it by torrent, well at least it was faster. so what do i do now? now im posting using firefox from ubuntu running by USB stick. basically currently im booting off USB flash drive.

---

### Post by jimkenstein on 2011-08-06
could some other expert whos online right  now help me out...?

---

### Post by garvinrick4 on 2011-08-06
OK download this script to DESKTOP or put on Desktop after downloading it:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Right click on it and open with Archive manager then click on exract and  will put a
a file on desktop that says boot_info-script.sh now do as the next line:
Then open a terminal and copy and paste this line below.
```
 sudo bash ~/Desktop/boot_info_script.sh
```You will now have a file called RESULTS on your desktop open it and
copy and paste it to this Thread. If you can after you copy and paste
it to this thread highlight whole thing and hit the # sign upper right
of message box will make it easier to read for me.

---

### Post by x-D on 2011-08-06
_**THE METHOD I'M ABOUT TO SHOW YOU CAN BE DONE FROM:**_

. A LIVE DISK/CD/DVD
. A LIVE USB
. ANY OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU

The absolute EASIEST WAY, to (re)install GRUB is to use a little program   called Boot-Repair. It does all that work to do with commands in the   Terminal to reinstall GRUB for you, and it's really noob friendly, with a   simple GUI, that you merely have to indicate which OS you want as your   main Operating System etc, IF YOU WANT TO! This is all under advanced   options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Now, run the program (search for it in Unity, or go to: System   ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode   in 11.04 Natty Narwhal)

Then, once the program is done reinstalling GRUB (should take at max 2 minutes), do this:

```

sudo update-grub

```This is probably not necessary, but it will just eradicate the potential for any errors, whatsoever!

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:

---

### Post by apollothethird on 2011-08-06
> **jimkenstein said:**
> could some other expert whos online right  now help me out...?

I'll be glad to help.  Look at my reply in this thread (reply #4) and perform the steps or specify which part you don't understand.  It should get you up and running without having to download anything particular.  Just us the prompt you described in your topic subject where you're stuck.

It works.  I've used it many times myself.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> OK download this script to DESKTOP or put on Desktop after downloading it:
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Right click on it and open with Archive manager then click on exract and  will put a
a file on desktop that says boot_info-script.sh now do as the next line:
Then open a terminal and copy and paste this line below.
```
 sudo bash ~/Desktop/boot_info_script.sh
```You will now have a file called RESULTS on your desktop open it and
copy and paste it to this Thread. If you can after you copy and paste
it to this thread highlight whole thing and hit the # sign upper right
of message box will make it easier to read for me.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /boot/bcd /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Recovery: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304   292,099,751   292,001,448   7 NTFS / exFAT / HPFS
/dev/sda3         292,109,895   302,575,217    10,465,323  db CP/M / CTOS / ...
/dev/sda4         302,575,614   312,580,095    10,004,482   5 Extended
/dev/sda5         310,507,520   312,580,095     2,072,576  82 Linux swap / Solaris
/dev/sda6         308,432,896   310,503,423     2,070,528  82 Linux swap / Solaris
/dev/sda7         302,575,616   306,356,223     3,780,608  83 Linux
/dev/sda8         306,358,272   308,430,847     2,072,576  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,892,991     7,892,929   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        C62A267D2A266B1F                       ntfs       Jim Yusof
/dev/sda3        9E04-6055                              vfat       DELLRESTORE
/dev/sda5        4d7eb8c8-1a12-4dd0-b539-f08bd733d83d   swap       
/dev/sda6        ccd994c9-b07c-4770-85aa-b34e7a16bf46   swap       
/dev/sda7        662cca8b-0e10-4203-804e-a65a6973f643   ext4       
/dev/sda8        957f8497-e28a-4e49-bda4-ea518835f375   swap       
/dev/sdb1        E057-BD11                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=957f8497-e28a-4e49-bda4-ea518835f375 none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 08  79 00 00 a0 1f 00 00 fe  |........y.......|
000001d0  ff ff 05 fe ff ff 41 5c  59 00 c1 9b 1f 00 00 00  |......A\Y.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

---

### Post by x-D on 2011-08-06
> **jimkenstein said:**
> ```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /boot/bcd /ntldr /NTDETECT.COM 
                       /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Recovery: FAT32
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /etc/fstab

sda8: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:   Syslinux looks at sector 16392 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. No errors 
                       found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux/syslinux.cfg /ldlinux.sys

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63        96,389        96,327  de Dell Utility
/dev/sda2    *         98,304   292,099,751   292,001,448   7 NTFS / exFAT / HPFS
/dev/sda3         292,109,895   302,575,217    10,465,323  db CP/M / CTOS / ...
/dev/sda4         302,575,614   312,580,095    10,004,482   5 Extended
/dev/sda5         310,507,520   312,580,095     2,072,576  82 Linux swap / Solaris
/dev/sda6         308,432,896   310,503,423     2,070,528  82 Linux swap / Solaris
/dev/sda7         302,575,616   306,356,223     3,780,608  83 Linux
/dev/sda8         306,358,272   308,430,847     2,072,576  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4041 MB, 4041211904 bytes
128 heads, 63 sectors/track, 978 cylinders, total 7892992 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63     7,892,991     7,892,929   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        3030-3030                              vfat       DellUtility
/dev/sda2        C62A267D2A266B1F                       ntfs       Jim Yusof
/dev/sda3        9E04-6055                              vfat       DELLRESTORE
/dev/sda5        4d7eb8c8-1a12-4dd0-b539-f08bd733d83d   swap       
/dev/sda6        ccd994c9-b07c-4770-85aa-b34e7a16bf46   swap       
/dev/sda7        662cca8b-0e10-4203-804e-a65a6973f643   ext4       
/dev/sda8        957f8497-e28a-4e49-bda4-ea518835f375   swap       
/dev/sdb1        E057-BD11                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


================================ sda2/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=============================== sda7/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda7       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=957f8497-e28a-4e49-bda4-ea518835f375 none            swap    sw              0       0
--------------------------------------------------------------------------------

========================= sdb1/syslinux/syslinux.cfg: ==========================

--------------------------------------------------------------------------------
# D-I config version 2.0
include menu.cfg
default vesamenu.c32
prompt 0
timeout 50

# If you would like to use the new menu and be presented with the option to install or run from USB at startup, remove # from the following line. This line was commented out (by request of many) to allow the old menu to be presented and to enable booting straight into the Live Environment! 
# ui gfxboot bootlogo
--------------------------------------------------------------------------------

================= sdb1: Location of files loaded by Syslinux: ==================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             ldlinux.sys                                    1
            ?? = ??             syslinux/gfxboot.c32                           1
            ?? = ??             syslinux/syslinux.cfg                          1
            ?? = ??             syslinux/vesamenu.c32                          1

============== sdb1: Version of COM32(R) files used by Syslinux: ===============

 syslinux/gfxboot.c32               :  COM32R module (v4.xx)
 syslinux/vesamenu.c32              :  COM32R module (v4.xx)

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff ff ff  |................|
*
000001b0  ff ff ff ff ff ff ff ff  ff ff ff ff ff ff 00 fe  |................|
000001c0  ff ff 82 fe ff ff 02 08  79 00 00 a0 1f 00 00 fe  |........y.......|
000001d0  ff ff 05 fe ff ff 41 5c  59 00 c1 9b 1f 00 00 00  |......A\Y.......|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


========= Devices which don't seem to have a corresponding hard drive: =========

sdc 

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/ubuntu/Desktop/boot_info_script.sh: line 1579: [: 2.73495e+09: integer expression expected

```

Surely just using my GUI method to reinstall GRUB will be far easier for him/her? They said they can now boot into a Live USB Version of Ubuntu, so they can do as I said, and I have used it many times, within 2 minutes GRUB is reinstalled :)

x-D :guitar:

---

### Post by apollothethird on 2011-08-06
> **x-D said:**
> Surely just using my GUI method to reinstall GRUB will be far easier for him/her? They said they can now boot into a Live USB Version of Ubuntu, so they can do as I said, and I have used it many times, within 2 minutes GRUB is reinstalled :)

x-D :guitar:
x-D.  I believe his problem is download speed.  He's probably anxious to bet his system up.

I'm sure your boot utilities are the best way.  I'll be testing it today.  It'll take me about an hour to download the iso also.  But I'll certainly keep it in my toolbox for the future.

Since he appears to be typing to us from one computer and trying to fix the other, there's a chance he might already have your recommendation in his download queue with the transfer in progress.  The method I suggested can be done in minutes also, but of course the commands have to be typed in correctly.

Garvinirick4 can probably have him up and running in minutes also, after studying the boot_info_scribe.sh output file.  Of course the commands Garvinrick4 would give him would have to typed in correctly also.

There's a good chance that Garvinrick4 would be giving him basically the same commands I have given him in my message/reply #4.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by madjr on 2011-08-06
> **x-D said:**
> _**THE METHOD I'M ABOUT TO SHOW YOU CAN BE DONE FROM:**_

. A LIVE DISK/CD/DVD
. A LIVE USB
. ANY OTHER LIVE MEDIA
. AN INSTALLED VERSION OF UBUNTU

The absolute EASIEST WAY, to (re)install GRUB is to use a little program   called Boot-Repair. It does all that work to do with commands in the   Terminal to reinstall GRUB for you, and it's really noob friendly, with a   simple GUI, that you merely have to indicate which OS you want as your   main Operating System etc, IF YOU WANT TO! This is all under advanced   options, but really, it's not so advanced, anyway to get Boot-Repair:[U][B]

Do this in the Terminal:[/B][/U]

```

sudo add-apt-repository ppa:yannubuntu/boot-repair

sudo apt-get update && sudo apt-get install -y boot-repair-ubuntu

```Now, run the program (search for it in Unity, or go to: System   ----> Administration ----> Boot Repair, in Gnome 2/ Classic Mode   in 11.04 Natty Narwhal)

Then, once the program is done reinstalling GRUB (should take at max 2 minutes), do this:

```

sudo update-grub

```This is probably not necessary, but it will just eradicate the potential for any errors, whatsoever!

_**Inf****o for this can be found by:**_

a) going to: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
b) messaging me here.

Hope this helped...

x-D :guitar:

+1 for boot-repair.

this should be included by default in the disk.

more info also:
[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)
[http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html](http://www.ubuntugeek.com/boot-repair-simple-tool-to-repair-frequent-boot-problems.html)

---

### Post by garvinrick4 on 2011-08-06
You have had Wubi install at one time and there is no grub files at all in sda7 where ubuntu lives right now and Grub is looking for boot files in sda6 a swap partition.
So lets put grub2 back into right place. Copy and paste these one at a time. We have to
install grub into sda7 and then put it in sda so she will boot. Make sure you have
internet working in live USB. Now copy and paste these one at a time:
   ```

    sudo mount /dev/sda7 /mnt
    for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
    sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
    sudo chroot /mnt
    apt-get update
    apt-get install grub-common grub-pc

     apt-get grub-install /dev/sda

    update-grub
    exit
    for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
    sudo umount /mnt
    sudo reboot
   
  

```Now should boot into Ubuntu or Windows your choice, let me know has a boot file
for wubi ubuntu in windows we might have to get out. Keep me informed.
##If asks you where to install grub when installing say sda and use tab key to toggle with. The second apt-get grub-install is redundant but want to make sure in sda.

---

### Post by garvinrick4 on 2011-08-06
> Surely just using my GUI method to reinstall GRUB will be far easier for  him/her? They said they can now boot into a Live USB Version of Ubuntu,  so they can do as I said, and I have used it many times, within 2  minutes GRUB is reinstalledx-D, applothethird, madjr
 I wanted to take a look at bootscript and OP has no boot files at all and was using WUBI
at one time and has left over boot files called "wubildr" left in XP install. Want to install
boot files before can do anything. I am sure ppa is fine but need to know what is wrong before I can see a solution. No what I mean, going in blind is really tough to do.

---

### Post by garvinrick4 on 2011-08-06
@appoloththird

[FONT=monospace]#Since grub-pc version 1.99 in Natty the line of code is now.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
instead of 1.98 at:
sudo grub-install --root-directory=/mnt /dev/sda

# Just found out about that myself reading an oldfred post or a
  drs305 I cannot remember which but have tried and works in grub
  version 1.99 
[/FONT]

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> You have had Wubi install at one time and there is no grub files at all in sda7 where ubuntu lives right now and Grub is looking for boot files in sda6 a swap partition.
So lets put grub2 back into right place. Copy and paste these one at a time. We have to
install grub into sda7 and then put it in sda so she will boot. Make sure you have
internet working in live USB. Now copy and paste these one at a time:
   ```

    sudo mount /dev/sda7 /mnt
    for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done 
    sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
    sudo chroot /mnt
    apt-get update
    apt-get install grub-common grub-pc

     apt-get grub-install /dev/sda

    update-grub
    exit
    for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
    sudo umount /mnt
    sudo reboot
   
  

```Now should boot into Ubuntu or Windows your choice, let me know has a boot file
for wubi ubuntu in windows we might have to get out. Keep me informed.
##If asks you where to install grub when installing say sda and use tab key to toggle with. The second apt-get grub-install is redundant but want to make sure in sda.

when i pasted the third line "sudo cp /etc/resolv.conf /mnf/etc/resolv.conf" it says:
[B]cp: cannot create regular file '/mnt/etc/resolv.conf': No space left on device
ubuntu@ubuntu:~$[/B]

---

### Post by garvinrick4 on 2011-08-06
> when i pasted the third line "sudo cp /etc/resolv.conf /mnf/etc/resolv.conf" it says:
[B]cp: cannot create regular file '/mnt/etc/resolv.conf': No space left on device
ubuntu@ubuntu:~$[/B]Is it a small usb device? See if this makes room. Then rerun line. Have you unmounted /dev/sda7? If so start over.
sudo apt-get clean

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> Is it a small usb device? See if this makes room. Then rerun line. Have you unmounted /dev/sda7? If so start over.
sudo apt-get clean

yeah its a small 4G USB stick but with Ubuntu in it it only fills the stick 685mb meaning a lot as 3gb left free. okay i will try "sudo apt-get clean" now start over and get back to you after.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> Is it a small usb device? See if this makes room. Then rerun line. Have you unmounted /dev/sda7? If so start over.
sudo apt-get clean

this is what i get when i tried to mount. i thought the command apt-get clean unmounts?
```
ubuntu@ubuntu:~$ sudo apt-get clean
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ubuntu@ubuntu:~$
```

seriously, i really need my pc for my studies. can i just easily uninstall ubuntu and reinstall it? ):

---

### Post by garvinrick4 on 2011-08-06
> yeah its a small 4G USB stick
Plenty big enough.

---

### Post by garvinrick4 on 2011-08-06
That just means sda7 is still mounted thats ok.
run all the lines after that just to make sure they are all mounted.
We want them mounted.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> That just means sda7 is still mounted thats ok.
run all the lines after that just to make sure they are all mounted.
We want them mounted.

this is what i did in the terminal, one at a time:
```
ubuntu@ubuntu:~$ sudo apt-get clean
ubuntu@ubuntu:~$ sudo mount /dev/sda7 /mnt
mount: /dev/sda7 already mounted or /mnt busy
mount: according to mtab, /dev/sda7 is already mounted on /mnt
ubuntu@ubuntu:~$ for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: cannot create regular file `/mnt/etc/resolv.conf': No space left on device
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# apt-get update
E: List directory /var/lib/apt/lists/partial is missing. - Acquire (2: No such file or directory)
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/# apt-get install grub-common grub-pc
E: Could not open lock file /var/lib/dpkg/lock - open (2: No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
root@ubuntu:/# apt-get grub-install /dev/sda
E: Invalid operation grub-install
root@ubuntu:/# update-grub
/usr/sbin/grub-mkconfig: 253: cannot create /boot/grub/grub.cfg.new: No space left on device
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; doneubuntu@ubuntu:~$ sudo umount /mnt
umount: /mnt: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
ubuntu@ubuntu:~$ sudo reboot
```

but still "error: unknown filesystem. grub rescue> screen comes up. so i have to boot off USB and "try ubuntu" everytime.

---

### Post by garvinrick4 on 2011-08-06
The sda7 where you attempted to install ubuntu looks as if it is to small to put
an operating system on. It is not much bigger than your swap partition. When
installed did not have room to put all of the operating system. You have 3 swaps
so I imagine you tried to install a few times and kept making swap partitions.
Open the app called "gparted" and see how much room you have between sda7
and 2 of the swaps. Lets see if have enough to make a full install. If you can make
a screenshot of gparted and post here we can look to see what you have to do.
Do not get frustrated you just got off to a rocky start. We can get this straitened out.

/dev/sda5         310,507,520   312,580,095     2,072,576  82 Linux swap / Solaris
/dev/sda6         308,432,896   310,503,423     2,070,528  82 Linux swap / Solaris 
/dev/sda7         302,575,616   306,356,223     3,780,608  83 Linux 
/dev/sda8         306,358,272   308,430,847     2,072,576  82 Linux swap / Solaris

---

### Post by garvinrick4 on 2011-08-06
sudo parted -l (lower case L)
will tell you the size of the partition also.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> The sda7 where you attempted to install ubuntu looks as if it is to small to put
an operating system on. It is not much bigger than your swap partition. When
installed did not have room to put all of the operating system. You have 3 swaps
so I imagine you tried to install a few times and kept making swap partitions.
Open the app called "gparted" and see how much room you have between sda7
and 2 of the swaps. Lets see if have enough to make a full install. If you can make
a screenshot of gparted and post here we can look to see what you have to do.
Do not get frustrated you just got off to a rocky start. We can get this straitened out.

/dev/sda5         310,507,520   312,580,095     2,072,576  82 Linux swap / Solaris
/dev/sda6         308,432,896   310,503,423     2,070,528  82 Linux swap / Solaris 
/dev/sda7         302,575,616   306,356,223     3,780,608  83 Linux 
/dev/sda8         306,358,272   308,430,847     2,072,576  82 Linux swap / Solaris

my gparted screenshot:
[ATTACH]199377[/ATTACH]

---

### Post by garvinrick4 on 2011-08-06
Well you had a partition of only 1.8 gig for file system sda7 and 3 swaps at 1 gig each.
Total of 5 gigs which is not enough room for a install. You have to take some room
out of Windows if you want to continue with a Linux install. Will need a minimum or 8
gig plus swap of twice the size of your RAM installed in your machine. And that is minimum.
Let me know. Unmount what we mounted to start with.
                         ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
```    ```
sudo umount /mnt
```
Now let me know what you want to do. 

How much room do you have on Windows side?
If you want to boot into Windows here is site if you have a disk: Only 2 commands.

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
   
  
#This is if you do not have a windows disk to boot Windows, use Ubuntu Live Usb.
```
sudo apt-get install lilo
``````
sudo lilo -M /dev/sda mbr
```May show error messages about the rest of lilo missing, ignore, we just want MBR
reboot.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> Well you had a partition of only 1.8 gig for file system sda7 and 3 swaps at 1 gig each.
Total of 5 gigs which is not enough room for a install. You have to take some room
out of Windows if you want to continue with a Linux install. Will need a minimum or 8
gig plus swap of twice the size of your RAM installed in your machine. And that is minimum.
Let me know. Unmount what we mounted to start with.
                         ```
for i in /dev/pts /dev /proc /sys; do sudo umount /mnt$i ; done
```    ```
sudo umount /mnt
```Now let me know what you want to do. 

How much room do you have on Windows side?
If you want to boot into Windows here is site if you have a disk: Only 2 commands.

[ATTACH]199384[/ATTACH]
should i continue with command "apt-get install lilo" now?

---

### Post by garvinrick4 on 2011-08-06
Reboot your Live USb and run lilo anytime from Live USB. Sorry you had a bad experience with Linux, you just had to small of a partition. Will be here if you need anything.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> Reboot your Live USb and run lilo anytime from Live USB. Sorry you had a bad experience with Linux, you just had to small of a partition. Will be here if you need anything.

YAYY! i just got booted to my windows xp :D does this mean that my ubuntu got uninstalled? i would really like to have it back install it like i never had ubuntu installed before.

---

### Post by garvinrick4 on 2011-08-06
No we have to make a partition bigger to put it in first. How much room do you have
on your Windows drive. Open computer and it will say how big and how much is used.
> does this mean that my ubuntu got uninstalled?
Your ubuntu install is not a complete install it is no good. Have to redo it in bigger partition.

---

### Post by Karthik6 on 2011-08-06
Hi

I have also got the same problem [grub rescue> (ubuntu 11.04 with windows xp)]("http://ubuntuforums.org/showthread.php?t=1818589")

This is the result from the Boot info how did you get the Windows XP back i need it back badly stuck with it for the past 2 days

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> No we have to make a partition bigger to put it in first. How much room do you have
on your Windows drive. Open computer and it will say how big and how much is used.

Your ubuntu install is not a complete install it is no good. Have to redo it in bigger partition.

Used: 103Gb
Free: 35.7Gb

i thats roughly 140Gb totaled. should be 160Gb.

---

### Post by jimkenstein on 2011-08-06
> **Karthik6 said:**
> Hi

I have also got the same problem [grub rescue> (ubuntu 11.04 with windows xp)]("http://ubuntuforums.org/showthread.php?t=1818589")

This is the result from the Boot info how did you get the Windows XP back i need it back badly stuck with it for the past 2 days

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```

the last thing i did was opened terminal and typed in:
```
sudo apt-get install lilo
```then
```
sudo lilo -M /dev/sda mbr
```then reboot then i got my XP back (:

but btw u should make ur own thread so things dont get mixed up for helpers. no offense.

---

### Post by garvinrick4 on 2011-08-06
> Used: 103Gb
Free: 35.7Gb

i thats roughly 140Gb totaled. should be 160Gb.
Ok I am going to eat dinner will be back in about 1/2 hour to use gparted to
remove old linux partition and swaps and make new ones and install Ubuntu.
Will not take long. See you in a 1/2 hour.

---

### Post by jimkenstein on 2011-08-06
> **garvinrick4 said:**
> Ok I am going to eat dinner will be back in about 1/2 hour to use gparted to
remove old linux partition and swaps and make new ones and install Ubuntu.
Will not take long. See you in a 1/2 hour.

i'll wait. sorry to burden u.

---

### Post by Karthik6 on 2011-08-06
> **jimkenstein said:**
> the last thing i did was opened terminal and typed in:
```
sudo apt-get install lilo
```then
```
sudo lilo -M /dev/sda mbr
```then reboot then i got my XP back (:

but btw u should make ur own thread so things dont get mixed up for helpers. no offense.

Thank you. Will Try that. I'm really sorry. Since you said you got your windows back. i just asked the question.

---

### Post by garvinrick4 on 2011-08-06
> **Karthik6 said:**
> Hi

I have also got the same problem [grub rescue> (ubuntu 11.04 with windows xp)]("http://ubuntuforums.org/showthread.php?t=1818589")

This is the result from the Boot info how did you get the Windows XP back i need it back badly stuck with it for the past 2 days

```
 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos6)/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:   Grub2 (v1.99) is installed in the boot sector of sda5 
                       and looks at sector 282589992 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files:        /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /grub/core.img 
                       /boot/grub/core.img

sda7: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    83,891,429    83,891,367   7 NTFS / exFAT / HPFS
/dev/sda2          83,891,491   312,580,095   228,688,605   5 Extended
/dev/sda5          83,891,493   269,498,531   185,607,039   7 NTFS / exFAT / HPFS
/dev/sda6         269,500,416   308,389,887    38,889,472  83 Linux
/dev/sda7         308,391,936   312,580,095     4,188,160  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        9CBC3981BC3956CC                       ntfs       
/dev/sda5        26CCA422CCA3E9EF                       ntfs       Data
/dev/sda6        1fdb86c8-f2c2-462e-9945-8161e9ac4c4a   ext4       
/dev/sda7        524e8ca8-59dd-4952-b4d6-ee3ed52a480a   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda6        /media/1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ext4       (rw,nosuid,nodev,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=================== sda5: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

            ?? = ??             boot/grub/core.img                             1

=========================== sda6/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
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
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(/dev/sda,msdos6)'
search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
set locale_dir=($root)/boot/grub/locale
set lang=en_GB
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
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-2.6.38-8-generic
}
menuentry 'Ubuntu, with Linux 2.6.38-8-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    echo    'Loading Linux 2.6.38-8-generic ...'
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.38-8-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos6)'
    search --no-floppy --fs-uuid --set=root 1fdb86c8-f2c2-462e-9945-8161e9ac4c4a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root 9CBC3981BC3956CC
    drivemap -s (hd0) ${root}
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
--------------------------------------------------------------------------------

=============================== sda6/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=1fdb86c8-f2c2-462e-9945-8161e9ac4c4a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=524e8ca8-59dd-4952-b4d6-ee3ed52a480a none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 140.682376862 = 151.056551936  boot/grub/core.img                             1
 136.801460266 = 146.889449472  boot/grub/grub.cfg                             1
 131.059776306 = 140.724363264  boot/initrd.img-2.6.38-8-generic               2
 140.679912567 = 151.053905920  boot/vmlinuz-2.6.38-8-generic                  1
 140.682872772 = 151.057084416  grub/core.img                                  1
 131.059776306 = 140.724363264  initrd.img                                     2
 140.679912567 = 151.053905920  vmlinuz                                        1

=============================== StdErr Messages: ===============================

unlzma: Decoder error

```
Hi start a another thread and Title it Grub problem and put your bootscript there.
Will get more assistance. I get confused trying to do two at once. You will get a lot 
of help some good grub users out there.

---

### Post by garvinrick4 on 2011-08-06
Looking at your partition table between the end of your drive (5 gig total not enough)sda5,sda6,sda7,sda8 and your dell recovery about 5 gig (sda3) and then your windows C: drive (sda2) and then another dell utilitys (sda1)
sda4 is an extended drive which holds all your logical drives sda5 thru sda8.
This is reading from back to front of your HDD.

I do not see a way to get around the dell recovery to get more room for Linux without
removing sda3 and using it for Linux but that puts your Windows at risk because you
do not have xp install disks. If something ever go's wrong with Windows you cannot repair or replace.

Up to you whatever you want to do. 
Some say you can move the Dell recovery partition to another partition without damage I have never tried. 

Or if you want to try to put Ubuntu in the 5 gig and not put anything in your /home folder
and keep the Applications down. We can give her a go.
There is a install called Lubuntu which I like to use which uses less resources but have to download and make
a new USB stick or LiveCd to install. I am using Lubuntu right now. Just a thought.

---

### Post by jimkenstein on 2011-08-07
> **garvinrick4 said:**
> Looking at your partition table between the end of your drive (5 gig total not enough)sda5,sda6,sda7,sda8 and your dell recovery about 5 gig (sda3) and then your windows C: drive (sda2) and then another dell utilitys (sda1)
sda4 is an extended drive which holds all your logical drives sda5 thru sda8.
This is reading from back to front of your HDD.

I do not see a way to get around the dell recovery to get more room for Linux without
removing sda3 and using it for Linux but that puts your Windows at risk because you
do not have xp install disks. If something ever go's wrong with Windows you cannot repair or replace.

Up to you whatever you want to do. 
Some say you can move the Dell recovery partition to another partition without damage I have never tried. 

Or if you want to try to put Ubuntu in the 5 gig and not put anything in your /home folder
and keep the Applications down. We can give her a go.
There is a install called Lubuntu which I like to use which uses less resources but have to download and make
a new USB stick or LiveCd to install. I am using Lubuntu right now. Just a thought.


i think we've forgotten something here. this all started because i tried to "erase ubuntu and reinstall it" from ubuntu installation options because i hated the login-keyring-dont-match thingy kept on appearing after many attempts to login my account with wrong passwords, which finally i succeeded logged in though. so basically it all was fine and ubuntu was **finely installed** and was running great. many times i switched on pc used xp then used ubuntu then used xp back then used ubuntu, all that without any problems until i tried to erase and reinstall. so anyways, during the erase and reinstall processing, it was a failure and it said that bla bla something like memory wasnt enough and bla bla the options "go back to partition table" or "continue reinstallation" came up. so i cancelled reinstallation and rebooted pc and thats when the 'grub rescue>' screen started.

so anyway, whats the best thing u recommend me doing right now?

---

### Post by garvinrick4 on 2011-08-07
> so anyway, whats the best thing u recommend me doing right now?
You got your Windows booting now so you have an operating system and it seems
like your main system since you only had 5 gig for Ubuntu total. You do not have
[COLOR=Red]install disks for Windows and maybe not any backups[/COLOR]. I do not want to make any
suggestions for you, if you make a mistake which I cannot control you will have
no system at all. If you want to use gparted and delete sda5 thru sda8 and reinstall
Ubuntu in that original 5gig is totally up to you. 

> i think we've forgotten something here. this all started because i tried to "erase ubuntu and reinstall it"
Here is the link from Ubuntu on "how to" , I wish you well. 
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")

---

### Post by jimkenstein on 2011-08-07
> **garvinrick4 said:**
> You got your Windows booting now so you have an operating system and it seems
like your main system since you only had 5 gig for Ubuntu total. You do not have
[COLOR=Red]install disks for Windows and maybe not any backups[/COLOR]. I do not want to make any
suggestions for you, if you make a mistake which I cannot control you will have
no system at all. If you want to use gparted and delete sda5 thru sda8 and reinstall
Ubuntu in that original 5gig is totally up to you.

so basically right now is my ubuntu **completely unistalled** and **all its components removed** from my pc or what? and secondly, i think im gonna give Lubuntu a try since u said it uses less resources (i take that it uses less memory, isnt it?). but before installing Lubuntu i would like to clear my sda5 and sda8 first (is it okay?), so how am i gonna do that?

---

### Post by apollothethird on 2011-08-07
Hi, Jimkenstein.  I casually looked at some of the other versions of Ubuntu and personally feel more conformable with Ubuntu over all the other versions.  I don't see a reason of your dilemma for a need to ditch Ubuntu as a resolution.  You have enough resources to run any version.  If I were you I wouldn't try to find a way to strip it down.  I don't know Lubuntu (I'm sure a Lubuntu fan would suggest that you go that direction), but if it's striped down, I'd say no.  My suggestion would be for you to have the opportunity to experience Ubuntu at it fullest since you have much more resources than necessary.

I have installed and run Ubuntu on 2 gigs without any problems.  I also installed Ubuntu on 4 gigs without any problems.  I eventually staring installing lots of things such as movie players and games and started to run out of space on the 4 gig installation.  I moved up to 8 gigs and went a long time before I started running out of space.  I was running out of space on my 8 gig installation because I created a number of virtual machines for running test and soon didn't have enough space for the virtual machines.

I believe 8 gigs would be plenty of space for most people, but I'd recommend having at least 20 gigs no matter which version of Ubuntu you decide to run so that you won't be cramped when you decide to download something from the Internet.

You can clear (delete) those small partitions you mention, (sd5, sd8, etc) with Gpartd or Disk Utility.  You can find them on the Live CD.  When you first start Disk Utility it'll immediately show you a list of all the drives on your computer.  Click on one of the drives and it'll show you all the partitions on that drive.  Select a partition and it'll show you lots of details about each partition.  You can pick your most important partition (your Windows partition) to be sure to skip (keep intact).

My suggestion is for you to remove the other partitions so that you can create one big partitions for Ubuntu.  Actually it'd be better to create two partitions for Ubuntu, one for your Ubuntu OS and one for swap.  I would recommend that you have twice the space of your RAM for your swap partition.  I usually try to have twice the space of the amount of RAM I'd expect to have in the computer in the next year, in case I might upgrade the memory.

I suggest that you keep two partitions for your Windows.  Keep the original partition which has your default restore that was shipped.  Thats usually a few hundred megs and your Windows installation partition.

I'd also suggest that you backup your important Windows Data if you can.  You can use Gparted or Disk Utility to resize and Move your Windows installation so that you can have more space for Ubuntu.  If you don't have at least 20 Gigs of continuous space for Ubuntu, I'd suggest that you use the resize and move feature to provide for this.  Then create an ext4 partition for your Ubuntu installation.

I have a lot of confidence that resizing and moving your Windows partition won't corrupt it.  But backing up your most important data is still a good security precaution.  Data is your important information which you've created such as your docs and pictures.  It's not the applications such as the Office Installation files or the OS installation files which can be brought back with the Install disks.

By the way, I strongly recommend your creating and using a Live USB/CD that includes the Boot Repair program.  I have tested it and it works well.  This would have recovered your Windows boot issue within minutes.  You can also use this same Live USB/CD to install Ubuntu or perform other maintenance tasks.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Having the Boot-Repair USB/CD is the way to go!  Spend some hours downloading this to avoid hours in the future, while you plan the course you'll take!

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by pritam_par on 2011-08-07
See the steps here to install the Grub 

[http://ubuntuforums.org/showthread.php?p=11124764#post11124764](http://ubuntuforums.org/showthread.php?p=11124764#post11124764)

---

### Post by apollothethird on 2011-08-07
> **pritam_par said:**
> See the steps here to install the Grub 

[http://ubuntuforums.org/showthread.php?p=11124764#post11124764](http://ubuntuforums.org/showthread.php?p=11124764#post11124764)

Hi, pritam_par.  The steps in your link will work.  It took me a while to understand the steps.  But I understand them.  They include exploring your disk to find the partition where your OS is.  It makes reference to looking for the boot files and other technical things about the installation.

If it were all we had, it'd be something we'd have to do.  But I recently learned a single click resolution that the most novice user can use.  Take a look at x-D's contribution to this topic.  The boot-repair utility is probably the best method.  It certainly would be for this novice user who is still learning what a partition is.

Take a look at:

Installing Grub or repairing boot problems at it simplest (From x-D):
[http://ubuntuforums.org/showthread.php?t=1818589&page=2](http://ubuntuforums.org/showthread.php?t=1818589&page=2) 

(which is already in this thread).  You might consider saving the link for future reference to others who are having boot problems.  I tested it.  It works amazingly simple and well.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Blasphemist on 2011-08-07
> **jimkenstein said:**
> so basically right now is my ubuntu **completely unistalled** and **all its components removed** from my pc or what? and secondly, i think im gonna give Lubuntu a try since u said it uses less resources (i take that it uses less memory, isnt it?). but before installing Lubuntu i would like to clear my sda5 and sda8 first (is it okay?), so how am i gonna do that?

Unless you have deleted partitions sda5, sda6, sda7 and sda8, no, you still have a mess installed. What it all comes down to is that you DO NOT have a large enough extended partition created, sda4. 4.77 GB is not enough. Technically you could install ubuntu of any flavor but you don't have enough space to add much software nor have a swap partition. The base installation of ubuntu, xubuntu, lubuntu, whatever, will take nearly 4GB even without a swap.

You also can't create a larger extended partition without doing something about the Dell restore partition. You could shrink it as it has 2.25GB free but that still doesn't give you much more space. My question is would you ever be happy with a restoration of the hard drive to the state it was in when you purchased the machine? Windows and all software would be back to where it was when you made the purchase, before you pressed a key. I think that would be a nearly worthless state. Anything added since then would be gone.

The main point of that is that I don't think the restore partition is of much value. If it came down to that option, I'd choose instead to wipe everything and install only ubuntu and free software. As always, you should ensure that you are doing something to make sure that your documents, pictures, data of any kind that is important is backed up regularly. 

So if I was you, I'd delete sda3, sda4, sda5, sda6, sda7 and sda8. That will remove all of the mess. You should still have a good windows installation with all of that gone. Before doing that you should make the windows recovery disk and have a plan for being able to fix the mbr of the drive should you need to. 

Then use windows tools to try and get as defragged as possible and get windows shrunk as much as it will let you. How much it lets you will decide how to proceed. I don't see just how much space is available on the windows partition. How much is? You're still going to be quite space limited for ubuntu unless you are able to get some space from the windows partition. 

Please comment on this and indicate how you'd like to proceed.

---

### Post by jimkenstein on 2011-08-09
> **Blasphemist said:**
> Please comment on this and indicate how you'd like to proceed.

i have decided to **completely** remove XP and use **Ubuntu only**. so from here _do i need to clear up certain sda(s)?_ or *_do i just boot from Ubuntu USB and simply click on "erase XP and install Ubuntu"?_* of course i will have all my documents backed up first before proceeding.

but before that, does Ubuntu support **C++, Notepad++, Microsoft Office**, and Counter-Strike 1.6? (: i have just started a major in Programming so obviously i will need the first three softwares.

---

### Post by apollothethird on 2011-08-09
> **jimkenstein said:**
> i have decided to **completely** remove XP and use **Ubuntu only**. so from here _do i need to clear up certain sda(s)?_ or *_do i just boot from Ubuntu USB and simply click on "erase XP and install Ubuntu"?_* of course i will have all my documents backed up first before proceeding.

but before that, does Ubuntu support **C++, Notepad++, Microsoft Office**, and Counter-Strike 1.6? (: i have just started a major in Programming so obviously i will need the first three softwares.

You can run Windows applications in a VirtualBox OS.  The Games will work be would be extremely slow.

You have access to C++ in Linux.  You can use gedit as a text editor.  Libreoffice beats Microsoft Office in everything except Grammar checking.  You can even import and export Microsoft Office documents into LibreOffice.

Many people go through school and work with programming without Microsoft.  Some of them use a Mac.  Some of them uses Linux.  But if you're really set on using Microsoft you might consider a dual boot while you wean yourself off it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by Hakunka-Matata on 2011-08-09
Since jimkenstein has decided that he is ready, willing, & able to completely remove XP and go with Ubuntu, an additional approach is now made available.  @jimkenstein, you could attempt a dual boot installation with XP and Ubuntu now and not worry about the consequences if you happen to Break XP in the process.  If XP breaks, OK, install Ubuntu as a single boot OS.  If you want to experiment and learn though, why not:

delete sda3 ....> sda8  (you might even want to attempt keeping sda3 Restore partition and move in left, next after shrinking ntfs OS partition sda2)
Boot to XP if possible,
defragement drive twice
shrink XP partition sda2
reboot machine to XP, to test and let it fix itself (first boot after resizing)
boot to Ubuntu live CD, run ```
 sudo fdisk -lu 
``` to see what partitioning looks like at this time
Create sda3 as EXTENDED Partition
Install Ubuntu after this if you want to let it create it's own partitions, OR
Create new Logical partiton sda5 for Ubuntu root "/"
Create new Logical parition sda6 Swap ~ same size as your RAM (2GiB)? or twice RAM size if you want to hibernate your machine

creating a separate /home partition is another option you may want to consider

---

### Post by jimkenstein on 2011-08-09
> **apollothethird said:**
> You can run Windows applications in a VirtualBox OS.  The Games will work be would be extremely slow.

You have access to C++ in Linux.  You can use gedit as a text editor.  Libreoffice beats Microsoft Office in everything except Grammar checking.  You can even import and export Microsoft Office documents into LibreOffice.

Many people go through school and work with programming without Microsoft.  Some of them use a Mac.  Some of them uses Linux.  But if you're really set on using Microsoft you might consider a dual boot while you wean yourself off it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

could you please clarify to me, at the moment **is my Ubuntu completely uninstalled, along with its components?** if not then i would like to completely uninstall and remove all its components and start all over again. and if theres particular steps to do just that **please tell me how**. i might even replace ubuntu after i read this ([COLOR=Blue]http://ubuntuforums.org/showthread.php?t=1821838[/COLOR]) just now.

---

### Post by jimkenstein on 2011-08-09
> **Hakunka-Matata said:**
> Since jimkenstein has decided that he is ready, willing, & able to completely remove XP and go with Ubuntu, an additional approach is now made available.  @jimkenstein, you could attempt a dual boot installation with XP and Ubuntu now and not worry about the consequences if you happen to Break XP in the process.  If XP breaks, OK, install Ubuntu as a single boot OS.  If you want to experiment and learn though, why not:

delete sda3 ....> sda8
Boot to XP if possible,
defragement drive twice
shrink XP partition sda2
reboot machine to XP, to test and let it fix itself (first boot after resizing)
boot to Ubuntu live CD, run ```
 sudo fdisk -lu 
``` to see what partitioning looks like at this time
Create sda3 as EXTENDED Partition
Install Ubuntu after this if you want to let it create it's own partitions, OR
Create new Logical partiton sda5 for Ubuntu root "/"
Create new Logical parition sda6 Swap ~ same size as your RAM (2GiB)? or twice RAM size if you want to hibernate your machine

creating a separate /home partition is another option you may want to consider

i had a dual-boot recently (XP and Ubuntu) but i had problems. so i think im gonna remove my XP. but i dont know if my previous installed-Ubuntu is completely uninstalled or not? if so then i just boot from Ubuntu USB and choose "erase XP and install Ubuntu". otherwise, i would like to 100% uninstall Ubuntu and all of its components first then after that i'll proceed.

---

### Post by Hakunka-Matata on 2011-08-09
Yes, I read all the posts in this thread before throwing in my 2cents worth.  I just thought this is a great time to experiment with installing a somewhat messed up dual boot system.
If you want Ubuntu as a single OS system, the quickest, simplest way is to install it and choose use the whole disk, you don't have to prepare anything beforehand if you do it that way.

---

### Post by YannBuntu on 2011-08-10
Hello

> **jimkenstein said:**
> could you please clarify to me, at the moment **is my Ubuntu completely uninstalled, along with its components?**

No. To completely remove it, you just need to:
1) boot on a Ubuntu CD
2) launch Gparted and delete partitions sda4, sda5, sda6, sda7 and sda8.

As you are new here, I **strongly** recommand you to keep Windows in dual-boot, until you are sure you don't need it any more. This is very easy:

3) Boot on XP, delete unused files (movies, music..), then defrag it.
4) Boot on Ubuntu CD (better if it is [Ubuntu Secured CD]("https://help.ubuntu.com/community/UbuntuSecuredRemix") :guitar: ), launch Gparted, and reduce sda2 until sda2 =110Go
5) Launch the Ubuntu installer, when you are at the "Allocate Drive Space" window, **choose "Something else"**:
[[img]http://pix.toile-libre.org/upload/thumb/1312973605.png[/img]](http://pix.toile-libre.org/?img=1312973605.png)
6) A new window will appear, create a new partition between sda2 and sda4 with the following parameters:
- filesystem: EXT4
- mount point: /
- size : as much as you can (should be around 24Go)
[[img]http://pix.toile-libre.org/upload/thumb/1312974048.jpg[/img]](http://pix.toile-libre.org/?img=1312974048.jpg)
7) Validate, and continue the installation. Reboot, and you should get the choice to start Ubuntu or Windows. :)

---

### Post by jimkenstein on 2011-08-13
> **YannBuntu said:**
> 
As you are new here, I **strongly** recommand you to keep Windows in dual-boot, until you are sure you don't need it any more.

im certain to remove XP, ive been using it my whole life so i wanna start living thru Ubuntu now :D im not so sure what to do, do i just go to gparted and right click on those sda(s) and choose delete? or if this might be the easier way, i choose "erase XP and install Ubuntu"? im scared that if i simply choose "erase XP and install Ubuntu" the grubs screen would come back, wouldnt they?

so again, i am very sure i wanna remove XP. besides its not like i cant reinstall it in the future. but XP is so out of date anyways, well at least for me.

---

### Post by apollothethird on 2011-08-13
> **jimkenstein said:**
> im certain to remove XP, ive been using it my whole life so i wanna start living thru Ubuntu now :D im not so sure what to do, do i just go to gparted and right click on those sda(s) and choose delete? or if this might be the easier way, i choose "erase XP and install Ubuntu"? im scared that if i simply choose "erase XP and install Ubuntu" the grubs screen would come back, wouldnt they?

so again, i am very sure i wanna remove XP. besides its not like i cant reinstall it in the future. but XP is so out of date anyways, well at least for me.

The install will include freshly installing grub.  It isn't a question what you do with XP.  XP doesn't matter, whether it's there or whether it's not.  The Grub will be freshly install as part of the Ubuntu install process.

Gparted is very easy to use.  You just remove resize or remove any partition.  In this case, just make space for Ubuntu, then use the Ubuntu install CD to install it.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

