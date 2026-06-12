---
title: "Dual Boot, Win2K Won't Boot, BSOD: Inaccessible Boot Device Error"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by WildcatRay on 2006-09-23
On a new HDD, I installed Windows 2000 on a 100 GB partition. Next, I installed Ubuntu creating partititions in the remaining 60 GB of unpartitioned disk space. GRUB set up the dual boot. I can boot into Ubuntu. When I try booting into Windows, I get to the splash screen before I get a BSOD listing an "INACCESSIBLE_BOOT_DEVICE" error.

On some, but not all, reboot attempts, my computer would not recognize the HDDs on the main channel.

```
cat /boot/grub/menu.lst
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows 2000 Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

```
sudo fdisk -l
Password:

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       12157    97651071    7  HPFS/NTFS
/dev/hda2           12158       19269    57127140   83  Linux
/dev/hda3           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        2432    19535008+   7  HPFS/NTFS
/dev/hdb2            2433        9729    58613152+   f  W95 Ext'd (LBA)
/dev/hdb5            2433        9729    58613121    7  HPFS/NTFS

Disk /dev/hdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        3825    30724281    7  HPFS/NTFS
/dev/hdd2            3826        9964    49311517+   f  W95 Ext'd (LBA)
/dev/hdd5            3826        7650    30724281    7  HPFS/NTFS
/dev/hdd6            7651        9964    18587173+   7  HPFS/NTFS
```

After I post this I am going to try replacing root with rootnoverify.

---

### Post by WildcatRay on 2006-09-23
I tried replacing root with rootnoverify in the menu.lst file under Windows 2000 Pro listing without any luck. Ubuntu boots without any trouble, though. I am running it now.

Any suggestions on how to troubleshoot this would be greatly appreciated.

---

### Post by maigege on 2006-09-23
You have started your own thread to answer your question, so no need to hijack someone else's thread.

---

### Post by Sef on 2006-09-23
Are you getting any errors when you try and boot into Win2K?

---

### Post by WildcatRay on 2006-09-24
> **Sef said:**
> Are you getting any errors when you try and boot into Win2K?
(In the title) Yes, a BSOD with INACCESSIBLE_BOOT_DEVICE (0x7B, I think). Also (as stated in my OP) on boot, the computer does not always recognize the HDDs on that channel. Enter and then exiting the BIOS setup and then it does recognize them. GRUB comes right up then. Computer boots fine if Ubuntu, but the BSOD if I choose Windows.

---

### Post by BadRambo on 2006-09-24
Hello ---
Been down this exact trail with Win2K before using another distro, but the problem turned out to be that, after installing Win2K on a large HD, I had forgotten to use a disk utility to remove the 137GB maximum size limiation on my partitions BEFORE trying to install Linux....it resulted in a BSOD when trying to boot Win2K after the Linux install because the partion table was simply lost -- just make sure your partitions are fully opened up if you are placing your systems on a large hard drive with Win2K.

Hope it is all that easy for your scenario -- Cheers --- Bob  :eek:

---

### Post by WildcatRay on 2006-09-24
> **BadRambo said:**
> Hello ---
Been down this exact trail with Win2K before using another distro, but the problem turned out to be that, after installing Win2K on a large HD, I had forgotten to use a disk utility to remove the 137GB maximum size limiation on my partitions BEFORE trying to install Linux....it resulted in a BSOD when trying to boot Win2K after the Linux install because the partion table was simply lost -- just make sure your partitions are fully opened up if you are placing your systems on a large hard drive with Win2K.

Hope it is all that easy for your scenario -- Cheers --- Bob  :eek:
That shouldn't be a problem as I started with a new 160 GB disk. For Windows, I set an 100 GB partition and left the rest free for the Ubuntu later on. Windows was fine.

Then, when installing Ubuntu, I directed it to use the free space for all its partitions. The rest you know.

---

### Post by WildcatRay on 2006-09-24
> **maigege said:**
> You have started your own thread to answer your question, so no need to hijack someone else's thread.
With all due respect, what is the purpose of your post here? You seem to be responding to something unrelated to the suggestions/answers I am seeking.

---

### Post by WildcatRay on 2006-09-25
Bump

---

### Post by rockstar on 2006-09-27
I thought the hijacking comment was funny

---

### Post by academician on 2007-02-02
Hello...has anyone figured this problem out?  I am now having the same issue.  I was using Gentoo with grub before (for years) and had no problems.  Yesterday I deleted my Gentoo partitions and installed Ubuntu 6.10 instead.  Now W2K will no longer boot, and I am wishing I had saved a copy of my Gentoo menu.lst!

Any ideas?  Changing "root" to "rootnoverify" did nothing, and Google has failed to save me so far.

Here is my menu.lst:

```
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=b700d6eb-a6ef-44a2-bec1-906b167f7ad5 ro
# kopt_2_6=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows 2000 Server
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
```

And fdisk -l:

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13373   107418591    7  HPFS/NTFS
/dev/hda2           13374       19392    48347617+  83  Linux
/dev/hda3           19393       19457      522112+  82  Linux swap / Solaris
```

---

### Post by reiki on 2007-02-02
Try this:

change rootnoverify back to root
add another line after chainloader   +1 that simply says:

boot

So now your entry would look like:
```

title		Microsoft Windows 2000 Server
root	(hd0,0)
savedefault
makeactive
chainloader	+1
boot

```

I have a similar entry and had to add that boot line to get my WindowsXP to boot.
If you get an error from grub when you try to boot this way, come back and post the error.

---

### Post by academician on 2007-02-02
Er, I don't think that will help.  W2K is actually starting (the loading screen shows up), but it cuts out with an "INACCESSIBLE_BOOT_DEVICE" BSOD.  And the grub '[boot](http://www.gnu.org/software/grub/manual/grub.html#boot)' command is not supposed to be necessary outside of interactive mode.

---

### Post by puredoze on 2007-02-11
Hi there.

I had the same problem with Xubuntu and did the following to boot windows again:

1.) Start from a LiveCD, e.g. Xubuntu or else
2.) Start gparted and remove the linux partitions
3.) Reboot with windows CD
4.) Start the recovery console from the windows setup
5.) Logon to the windows installation (admin password needed)
6.) Type "fixboot" and "fixmbr"
7.) Type "exit" to reboot
8.) Windows should start now.

Sure, it destroys your Ubuntu installation, but you can now boot windows again.
 Before I deleted the linux partitions I tried to repair the window installation the same way with the recovery console and couldn´t even logon to the windows installation. After I did the above mentioned "workaround" I was able to boot windows again.
I think it has to do with the fact, that windows 2000 don´t recognize large harddisks (mine is 160GB).. I remeber to read something about this to fix this issue in windows 2000, so that windows 2000 can handle larger harddisk but I didn´t had the time to try it yet. It is a simple registry entry. 
I think this was it: [http://support.microsoft.com/default.aspx?scid=kb;EN-US;305098](http://support.microsoft.com/default.aspx?scid=kb;EN-US;305098)

Maybe after that fix you`ll be able to dual boot Linux and Windows 2000.
I´ll try it myself the next days with that fix and will post here again.

Greetz doze

---

### Post by puredoze on 2007-02-11
Ok, seems to be working ;)
Simply add the registry key in the above mentioned Microsoft Link and the reinstall (X)Ubuntu.

Works for me ;)

---

### Post by Caysho on 2007-10-01
I know this is six months later, but I want to add another "confirmation" that the fix at [http://support.microsoft.com/kb/305098](http://support.microsoft.com/kb/305098) works.
I came across this when searching on the BSOD error with a dual boot I've just put together (Windows 2000 SP4 and Kubuntu 6.06).

---

### Post by lkraemer on 2007-10-02
Yes, it worked for me today.  I had tried several times before finding this
post.  Thanks.  My procedures follow:


Installing Win2000Prof w/SP4 on a Hard Drive larger than 137 Gig with Ubuntu/Kubuntu as Dual Boot

If your drive has partitions they should be removed before installing.  I use FDISK (Updated) from Win98SE that was upgraded to FDISK64 via Microsoft.

1.  Boot from the Win 98SE floppy and run FDISK to remove any partitions that are left from a previous install.  FDISK will delete FAT, NTFS, and Non DOS Partitions.

2.  Insert the WIN2000 CDR and install Win2000 on the FIRST Partition.  Size the Partition as needed and Format it as NTFS.  I used 78003 for my Windows Partition.

3.  START --> RUN --> CMD   Regedit to edit the Registry to add the following under:
    HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\atapi\Parameters

    EnableBigLba   REG_DWORD  0x1

    Exit Regedit (This allows WIN2000 to work properly with drives
   > 137 Gig. and prevents the boot error when Grub starts Windows
    2000 Prof.) 
    Ref:  [http://support.microsoft.com/default.aspx?scid=kb;EN-US;305098](http://support.microsoft.com/default.aspx?scid=kb;EN-US;305098)

4.  Re-boot Windows 2000, and verify everything works so far.
    
5.  Insert Ubuntu LIVECD and restart.  Run Gnome Partition Editor.
    Make three partitions:  (Don't remove or work with the WIN2000 Partition)
         My Partitions I made:
    /
    /home
    /Linux-swap
                                   My Gnome Partition  
                                   Settings for a 300 Gig                Mount Point
    /DEV/HDA1  NTFS        76.17   78003                        /mnt/windows
    /DEV/HDA2  EXT3        29.29   30000                        /
    /DEV/HDA4  EXT3       192.61   Remainder of Drive  /home
    /DEV/HDA3  Linux-swap   7.84   8                             /swap
    
 
6.  Install Ubuntu to the above Partition (/DEV/HDA2)
     I let Grub write to the MBR (Master Boot Record) of Windows 2000.

7.  Re-boot to see if Windows 2000 loads and runs via Grub.
 
8.  Connect to Internet and update Windows 2000, and IE6.

9.  Update all Drivers, and Update other Software as needed.

10. Re-boot to Ubuntu via Grub.  Update Ubuntu, and load any additional software.

---

### Post by Felix-the-Cat on 2008-01-01
I have also  encountered this problem  when  I installed gusty. I used the windows 2k cd and did a fixboot and fixmbr to get windows to boot again. then i installed drapper(because  i didn't have a edgy or feisty cd) and  windows was fine, I then upgraded to edgy and then to feisty and  then to gusty each time  windows  booted fine. it  was only when i installed from the gusty cd  that windows  wouldn't boot. I don't know  if  this will help anyone solve  the problem but its my $0.02

---

