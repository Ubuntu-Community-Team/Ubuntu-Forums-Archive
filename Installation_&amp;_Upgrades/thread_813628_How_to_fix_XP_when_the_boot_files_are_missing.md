---
title: "How to fix XP when the boot files are missing"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by meierfra. on 2008-05-31
(For Vista or Windows 7 see [Post 4 ]("http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4"))

This is a follow up on Herman's [post]("http://ubuntuforums.org/showthread.php?p=4701367#post4701367") on how to boot XP from a logical partion. His post is not only relevant if XP is on a logical partition, it also applies whenever the boot files   for XP  are missing. Let me summarize and refine his method

Step 1) Boot into Ubuntu and mount the XP partition.

Step 2) Download the attached file Archive.tar.gz.  Extract the three files boot.ini , NTLDR and NTDETECT.COM to (the root of) the XP partition.

Step 3) Edit "boot.ini". The number in ``partition(1)'' needs to be changed to the correct number for your XP partition. Windows starts counting at 1 and counts partitions in the order of the partition table (so far that's the same way linux counts) BUT skips over extended partitions and empty partitions.


**If XP is on a logical partition:**

Step 4) Do NOT use ``makeactive'' in menu.lst.

Step 5) Use testdisk to rebuild the boot sector.


**Remarks: **
I) In theory one should be able to replace Step 3) by "bootcfg /rebuild" from the Windows Recovery Console. But this did not work out for me. bootcfg did not detect XP, probably since it was on a logical partition. 

II)  Step 5) seems to be unnecessary in some cases.

[B]
[SIZE="4"]Detailed Instructions:[/SIZE][/B]

**Step 1) Mount your windows partition in Linux**


```
sudo mkdir /Win
sudo mount /dev/sda5 /Win    
ls /Win
```
(here /dev/sda5  must be replaced by the device name of your Windows partition. Use "sudo fdisk -l" to determine the device name)

The last command lists all the files in the System directory of your Windows Partition. Look for the files "boot.ini", "NTLDR" and "NTDETECT.COM". If you already have these files, skip Step 2.


**Step 2) Get the boot files and copy them to your Windows partition**


Download this file: [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573](http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573)
and save it to your home folder (/home/your_username). Then 


```
cd /Win
sudo tar -xvzf /home/your_username/Archive.tar.gz
ls /Win
```

Make sure you now have the files "boot.ini", "NTLDR" and "NTDETECT.COM"


**Step 3 Edit boot.ini**

```
sudo nano /Win/boot.ini      (don't use "gedit", since it does
                                    not handle dos files correctly )

```   

Change all "partition(1)" to "partition(3)" (there are two of them) Do not change anything else. Here "3" must be replaced by the correct number for your XP partition. See this [post]("http://ubuntuforums.org/showthread.php?t=829464#24") for some examples.

Save the the file.

[B]
Step 4 Add XP to the Grub menu[/B]

[COLOR="Blue"]If you are using Grub 2[/COLOR]

```
 sudo update-grub
```
(if that does not work, try "sudo grub-mkconfig -o /boot/grub/grub.cfg)

[COLOR="Blue"]If you are using Legacy Grub[/COLOR]

```
gksudo gedit /boot/grub/menu.lst
```

Use 

title XP
rootnoverify (hd0,4)
chainloader +1


Do NOT use "makeactive". 
Of course (hd0,4) needs to be adjusted. The first number is the hard drive and the second number the partition. Grubs starts counting at zero, and counts the hard drives according  to the order in the bios. So the boot drive is always (hd0). The second number is always one less than the number in the device name. So if Windows is /dev/sda5, then  the second number is  4. 
The "hd" is always "hd",  even if the device name contains "sd".
If Windows is  not on the boot drive, you need to add "map" lines:

title XP
rootnoverify (hd3,4)
map (hd0) (hd3)    
map (hd3) (hd0)
chainloader +1



Save the file and reboot. Sometimes this does not work right away and you have to do the fifth step. 

**Step 5:  Rebuild the Boot sector of the Windows partition.**

Install and run "testdisk:

```
sudo apt-get install testdisk

sudo testdisk  /dev/sda  
```

(Replace /dev/sda by device name of the XP partition without the number)

Press "enter" to "proceed"
Press "enter" to select "intel"
Use the "down arrow" and "enter" to select "advanced"
Use the down arrrow to select the "XP" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done:
Use the "right arrow" key and "enter" to select "write". This will write a modified boot sector to the Windows partition.
Press q a few times to quit testdisk.

Reboot.

( You can delete "Archive.tar.gz" at any time, but I would wait until you successfully booted into XP)

**If you do not have a working internet connection in Ubuntu**

In Step 2: Download Archive.tar.gz on a different computer and use a flash drive to transfer it to your Ubuntu home folder.

In Step 5:  Download the [testdisk-6.10.linux26.tar.bz2 package ]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2")   on a different computer and use a flash drive to transfer it to your Ubuntu home folder. Then  in a terminal

```

cd 

tar xvf testdisk-6.10.linux26.tar.bz2

sudo testdisk-6.10/linux/testdisk_static /dev/sda 

```
(Replace /dev/sda by device name of the XP partition without the number)

Press "Enter" to  "proceed" and continue as in Step 5.



**  Windows 2000 **

This tutorial also works for Window 2000 with one modification:

Each occurrence of  "[COLOR="Black"]\[/COLOR]Windows" in  boot.ini  must be replaced by "[COLOR="Black"]\[/COLOR]WINNT" 


**This [thread ]("http://ubuntuforums.org/showthread.php?t=834864")successfully used the method and contains some more information.**

---

### Post by tamoneya on 2008-05-31
that should be it.  Post if it fails other than that you should be all set.
EDIT:  sorry I read the post a little too quickly a little too late at night and took it more as a question.  What was the purpose of splitting the thread?

---

### Post by meierfra. on 2008-06-03
> and took it more as a question.


I rephrased the first sentence to avoid this confusion.


> What was the purpose of splitting the thread?

The original post of Herman appeared hidden in  a long thread about Grub error 17.  But my post has absolutely nothing to do with "Grub error 17"

---

### Post by meierfra. on 2008-09-04
This HowTo shows how to fix the Vista's Boot Loader when the boot file "bootmgr" is  missing.   (the same HowTo works for Windows 7. Just replace Vista by Windows 7 everywhere).

[SIZE="4"]** Step 1)  Edit menu.lst:  ([COLOR="Blue"]Skip this step if you are using Grub 2)[/COLOR]**[/SIZE]

Boot into Ubuntu, open a terminal (Applications->Accessories->Terminal) and type

```

gksudo gedit /boot/grub/menu.lst

```This opens the file boot/grub/menu.lst.
Add this to the very end of the file

title Vista
rootnoverify (hd0,4)
chainloader +1

Do NOT use "makeactive".
Of course (hd0,4) needs to be adjusted. The first number is the hard drive and the second number the partition. Grubs starts counting at zero, and counts the hard drives according to the order in the Bios. So the boot drive is always (hd0). The second number is always one less than the number in the device name (use "sudo fdisk -lu" to determine the device name). So if Vista is on  /dev/sda5, then the second number is 4. The "hd" is always "hd", even if the device name contains "sd".

If Vista is not on the boot drive, you need to add "map" lines:

title Vista
rootnoverify (hd3,4)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1

Save the file.

[SIZE="4"][B]Step 2) Repair the Vista Bootloader.  
[/B][/SIZE]

Boot from  a Vista or Windows 7  CD/DVD. If you do not have one, you can download a  Vista Recovery CD from [ here]("http://www.pcworld.com/downloads/file/fid,71039/description.html") or [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"), and a Windows 7 CD from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

A Vista DVD  can be used for Windows 7 and vice versa. [COLOR="Navy"]Edit 5/3/09:  There is some indication that is  no longer  true for the most recent version of Windows 7.  So I recommend to  use a Windows 7 CD/DVD for Windows 7.[/COLOR]

There are two ways to  repair the Vista Boot Loader: Automatic and Manual. The Automatic repair should work under normal circumstances, but will fail in more complicated situations. 

[SIZE="3"][COLOR="Red"]Automatic Repair of the Vista Boot Loader[/COLOR]
[/SIZE]
At the first screen select your favorite language.
At the second screen choose "Repair your Computer".

If a pop windows appears, offering  to repair a problem with the "Startup options",   click on "Repair and restart".

Otherwise, on the  next screen select  your operating system under "Use recovery tools ..."  and click on "Next".

Choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

This link contains picture of the various screens:  [http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)


[SIZE="3"][COLOR="Red"]Manual  Repair of the Vista Boot Loader[/COLOR][/SIZE]

At the first screen select your favorite language.
At the second screen, select "Install Now"
At the third screen, press  "Shift F10".

This will open a terminal. In the terminal type

```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your Vista partition. In the following I'll assume it is "C:". If the drive letter of your Vista partition is different, you need to replace all "C:" accordingly.  Also determine the drive letter for the CDrom drive, I'll  assume that is "E:".  Type

```
 exit
``` to exit the ``diskpart'' prompt.

Type

```

copy E:\bootmgr C:\

mkdir C:\BOOT

copy E:\BOOT C:\BOOT 

bcdedit /store C:\boot\bcd /set {default} osdevice boot

bcdedit /store C:\boot\bcd /set {default} device boot

bcdedit /store C:\boot\bcd /set {default} path \Windows\system32\winload.exe

bcdedit /store C:\boot\bcd /set {bootmgr} device boot

bcdedit /store C:\boot\bcd /set {memdiag} device boot


```Depending on the DVD you are using you might also  have to type the following three lines

```
bcdedit /store C:\boot\bcd /deletevalue  {default} detecthal 

bcdedit /store C:\boot\bcd /deletevalue  {default} winpe

bcdedit /store C:\boot\bcd /deletevalue  {default} ems

```Just go ahead and type those three  lines. But you might get an "element  not found" warning, which you can ignore.

Then type:

```
bootsect  /nt60  C:
```

If you get a unknown command message try

```
E:\boot\bootsect.exe /nt60  C:
```

instead. Although the actually path for "bootsect.exe" might depend on the CD/DVD you are using.


[COLOR="Blue"][SIZE="3"]If you are using Grub 2:  Reboot into Ubuntu and type "sudo update-grub" in a terminal[/SIZE][/COLOR]


Reboot and select 'Vista' at the grub menu.

Sometimes this does not work right away and you have to do a third step.

[B]
Step 3) Rebuild the Boot Sector of the Vista's  partition.[/B]

Boot into Ubuntu.  (make sure that The Universe Repository is enabled in Systmem->Administration->Software Sources. Then install and run "testdisk via

```

sudo apt-get install testdisk

sudo testdisk /dev/sda

```(Replace /dev/sda by the device name of the Vista partition without the trailing  number)

Press "enter" to "proceed"
Press "enter" to select "intel"
Use the "down arrow" and "enter" to select "advanced"
Use the down error to select the "Vista" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done just follow the instruction on the screen to save the new boot sector and quit testdisk.

Reboot and select Vista at the Grub Menu.

This HowTo has been applied  successfully in many cases, but of course  I cannot guarantee  that it will work under all circumstances.  

For more information on the Vista booting  process see [Vista_Multi_Booting]("http://www.multibooters.co.uk/") and [EasyBCD ]("http://neosmart.net/wiki/display/EBCD/EasyBCD+Documentation+Home")

---

### Post by caljohnsmith on 2008-09-04
Meierfra, is it necessary to use "rootnoverify" instead of "root" in the Grub's menu.lst for the Vista entry? Usually you can use just "root" for Win XP/Vista, which actually I find a bit confusing, because NTFS is not a supported file system with Grub; thus I would think "rootnoverify" would always be necessary.

Also, just a small thing, but is:
> (Replace /dev/sda by device name of the XP partition without the trailing number)
from step 5 a typo? Shouldn't that be Vista instead of XP?

---

### Post by meierfra. on 2008-09-04
> Meierfra, is it necessary to use "rootnoverify" instead of "root" in the Grub's menu.lst for the Vista entry? Usually you can use just "root" for Win XP/Vista, which actually I find a bit confusing, because NTFS is not a supported file system with Grub; thus I would think "rootnoverify" would always be necessary.

In my experience "root" works in most cases, but sometimes it does not. And  "rootnoverify"  seems to always work.  Grub cannot read the files on a  "NTFS" partition, but "root" only mounts a partition without actually reading any of the files.


> Shouldn't that be Vista instead of XP? 

Yes,  I fixed it. Thanks.

---

### Post by Crafty Kisses on 2008-09-05
Nice tutorial, good information in here. :)

---

### Post by caljohnsmith on 2008-09-07
One other question, meierfra: when XP/Vista are in a logical partition, if anything happens to the XP/Vista logical partition and the user needs to do a "Windows repair" or similar from the XP/Vista Install/Recovery CD, is it possible? I was under the impression that XP/Vista will not allow themselves to be installed to a logical partition (you have to manually move them there), and thus they also won't allow themselves to be repaired if they are in a logical partition. Any thoughts about this?

---

### Post by meierfra. on 2008-09-07
> if anything happens to the XP/Vista logical partition and the user needs to do a "Windows repair" or similar from the XP/Vista Install/Recovery CD, is it possible?

Some of the functions of the Recovery CD's seem to work, others do not. I was able to run "fixboot" from the Windows CD, but "bootcfg /rebuild" did not work.  Also "bcdedit" from the Vista CD  did work, but "autorepair" did not. 


> I was under the impression that XP/Vista will not allow themselves to be installed to a logical partition (you have to manually move them there),


This is not quite true. You can install XP/Vista on a logical partition, as long as you have some primary FAT or NTFS partition.  Windows will put the boot files onto this primary partition. Windows calls this partition the System partition. To boot Windows from Grub,  you  have to use "root (hdX,Y)" where "(hdX,Y)" is the System partition. (There are various threads where people are unable to boot Windows, because they do not realize that the boot files are  on some partition, which seem to have nothing to do with the Windows OS)

I have a dedicated primary Grub Partition in FAT32 format. So I'm able  to used the Grub Partition to install XP/Vista on logical partitions.

---

### Post by caljohnsmith on 2008-09-09
> **meierfra. said:**
> You can install XP/Vista on a logical partition, as long as you have some primary FAT or NTFS partition.  Windows will put the boot files onto this primary partition. Windows calls this partition the System partition. To boot Windows from Grub,  you  have to use "root (hdX,Y)" where "(hdX,Y)" is the System partition. (There are various threads where people are unable to boot Windows, because they do not realize that the boot files are  on some partition, which seem to have nothing to do with the Windows OS)

So if the user has all his boot files on a primary partition, but his main Windows install is on a logical partition, is it the boot.ini file that then points to the logical partition? I.e. does "partition(X)" in boot.ini need to be the logical partition I would presume and not the primary partition where the boot.ini is located?

---

### Post by meierfra. on 2008-09-09
> I.e. does "partition(X)" in boot.ini need to be the logical partition 
Yes.

---

### Post by Fleuris on 2008-10-14
Ooops, the link, Vista_Boot_Files.tar.gz doesn't work...:(

---

### Post by meierfra. on 2008-10-14
I fixed the link.

---

### Post by PinkRose on 2008-11-25
Dears, 

Hi , I have followed all the steps in post4 for my vista correction but when i tried to boot into it , i faced the error :
            NTLDR is missing.
            Press Ctrl+Alt+Del to restart

Could you please help me.?
Thanks in Advance
Best Regards

---

### Post by meierfra. on 2008-11-25
PinkRose:


Please post the output of 

```
sudo fdisk -lu
```

and 

```

cat /boot/grub/menu.lst
```

Could you also explain  your situation? Do you know why the Vista boot files were missing?

---

### Post by PinkRose on 2008-11-26
Code:

sudo fdisk -lu

Disk /dev/sda: 58.5 GB, 58506416640 bytes
255 heads, 63 sectors/track, 7113 cylinders, total 114270345 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x313f313f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    30909059    15454498+  83  Linux
/dev/sda2        30909060   114254279    41672610    f  W95 Ext'd (LBA)
/dev/sda5   *    30909123    83345219    26218048+   7  HPFS/NTFS
/dev/sda6        83345283   114254279    15454498+   b  W95 FAT32

and

Code:

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=0be02841-d399-486b-a0d5-3d34f20becd0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0be02841-d399-486b-a0d5-3d34f20becd0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=0be02841-d399-486b-a0d5-3d34f20becd0 ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0be02841-d399-486b-a0d5-3d34f20becd0 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=0be02841-d399-486b-a0d5-3d34f20becd0 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title  Microsoft Windows Vista
root   (hd0,4)
savedefault
#makeactive
chainloader +1

Could you also explain your situation? Do you know why the Vista boot files were missing?

i have the same case , i have installed WinXp on C:/ then Vista on D:/ then decided to switch to linux so i converted the C:/ to ext2 and installed ubuntu on but the Grup did not read Vista and i followed the instructions said in post 4 to the end but i have the error i have written above

Thanks for your help , and hope to hear from you soon 
Best Regrds,

---

### Post by meierfra. on 2008-11-26
Boot from the Vista CD and go to the terminal, just as before.  Use 

```
diskpart

list volume

exit
```

to determine the drive letter for you cdrom drive.


Then type

```
E:\boot\bootsect.exe /nt60  C:
```

(Here E: needs to be drive letter of your CD rom drive and C: the drive letter of the vista partition.

**If this did not solve your  problem:** 

post the output of 

```
bcdedit /store C:\boot\bcd
```
from the Vista Terminal

Also open a Terminal in Ubuntu and post the output of


```

sudo mount /dev/sda5 /mnt
ls -l /mnt
ls -l /mnt/Boot
```

---

### Post by PinkRose on 2008-11-26
> **meierfra. said:**
> Boot from the Vista CD and go to the terminal, just as before.  Use 

```
diskpart

list volume

exit
```

to determine the drive letter for you cdrom drive.


Then type

```
E:\boot\bootsect.exe /nt60  C:
```

(Here E: needs to be drive letter of your CD rom drive and C: the drive letter of the vista partition.

[COLOR="Red"]When i tried to do this , i got the msg:
The System Cannot find the path specified.[/COLOR]

**If this did not solve your  problem:** 

post the output of 

```
bcdedit /store C:\boot\bcd
```
from the Vista Terminal

[COLOR="Red"]please specify how to save it to a file to be read on Linux as it will be hard to copy them on paper and write them here[/COLOR]

Also open a Terminal in Ubuntu and post the output of


```

sudo mount /dev/sda5 /mnt
ls -l /mnt

[COLOR="Red"]total 3433318
-rwxrwxrwx 1 root root         24 2006-09-19 00:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-11-26 23:24 Boot
-rwxrwxrwx 1 root root     443912 2008-01-09 17:22 bootmgr
-rwxrwxrwx 3 root root         10 2006-09-19 00:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 15:02 Documents and Settings
-rwxrwxrwx 1 root root 1600589824 2008-11-20 20:49 hiberfil.sys
drwxrwxrwx 1 root root          0 2008-09-03 20:57 Intel
drwxrwxrwx 1 root root          0 2008-11-15 13:44 LearnKey
drwxrwxrwx 1 root root          0 2008-09-05 21:39 MSOCache
-rwxrwxrwx 1 root root 1914404864 2008-11-20 20:49 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-10-04 14:52 ProgramData
drwxrwxrwx 1 root root      65536 2008-11-17 22:28 Program Files
drwxrwxrwx 1 root root          0 2008-09-02 22:05 $Recycle.Bin
drwxrwxrwx 1 root root       8192 2008-11-20 21:04 System Volume Information
drwxrwxrwx 1 root root       4096 2008-09-02 22:05 Users
drwxrwxrwx 1 root root      16384 2008-11-20 20:49 Windows
-rwxrwxrwx 1 root root        146 2008-09-02 23:50 YServer.txt[/COLOR]

ls -l /mnt/BOOT
```

[COLOR="Red"]ls: cannot access /mnt/BOOT: No such file or directory

but trying  ls -l /mnt/Boot
total 728
-rwxrwxrwx 1 root root 262144 2008-11-27 07:17 BCD.LOG
-rwxrwxrwx 1 root root      0 2006-11-10 23:59 BCD.LOG1
-rwxrwxrwx 1 root root      0 2006-11-10 23:59 BCD.LOG2
-rwxrwxrwx 1 root root  28672 2008-11-27 07:17 BCD,txt
-rwxrwxrwx 1 root root  65536 2006-11-10 23:59 bootstat.dat
drwxrwxrwx 1 root root      0 2008-01-09 23:32 cs-CZ
drwxrwxrwx 1 root root      0 2008-01-09 23:32 da-DK
drwxrwxrwx 1 root root      0 2008-01-09 23:32 de-DE
drwxrwxrwx 1 root root      0 2008-01-09 23:32 el-GR
drwxrwxrwx 1 root root      0 2008-01-09 23:32 en-US
drwxrwxrwx 1 root root      0 2008-01-09 23:32 es-ES
drwxrwxrwx 1 root root      0 2008-01-09 23:32 fi-FI
drwxrwxrwx 1 root root      0 2008-01-09 23:32 Fonts
drwxrwxrwx 1 root root      0 2008-01-09 23:32 fr-FR
drwxrwxrwx 1 root root      0 2008-01-09 23:32 hu-HU
drwxrwxrwx 1 root root      0 2008-01-09 23:32 it-IT
drwxrwxrwx 1 root root      0 2008-01-09 23:32 ja-JP
drwxrwxrwx 1 root root      0 2008-01-09 23:32 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 11:51 memtest.exe
drwxrwxrwx 1 root root      0 2008-01-09 23:32 nb-NO
drwxrwxrwx 1 root root      0 2008-01-09 23:32 nl-NL
drwxrwxrwx 1 root root      0 2008-01-09 23:32 pl-PL
drwxrwxrwx 1 root root      0 2008-01-09 23:32 pt-BR
drwxrwxrwx 1 root root      0 2008-01-09 23:32 pt-PT
drwxrwxrwx 1 root root      0 2008-01-09 23:32 ru-RU
drwxrwxrwx 1 root root      0 2008-01-09 23:32 sv-SE
drwxrwxrwx 1 root root      0 2008-01-09 23:32 tr-TR
drwxrwxrwx 1 root root      0 2008-01-09 23:32 zh-CN
drwxrwxrwx 1 root root      0 2008-01-09 23:32 zh-HK
drwxrwxrwx 1 root root      0 2008-01-09 23:32 zh-TW[/COLOR]

Thanks

---

### Post by meierfra. on 2008-11-26
> 

[QUOTE]```
E:\boot\bootsect.exe /nt60  C:

```

(Here E: needs to be drive letter of your CD rom drive and C: the drive letter of the vista partition.

When i tried to do this , i got the msg:
The System Cannot find the path specified.[/QUOTE]

Strange. What kind of Vista CD are you using? Are you sure that you used the correct drive letter for the CDrom Drive?


If you did use the correct drive letter, try this in Vista CD Terminal 

```
bootrec /fixboot
```

---

### Post by meierfra. on 2008-11-27
> please specify how to save it to a file to be read on Linux as it will be hard to copy them on paper and write them here

Good point.

```
bcdedit /store C:\boot\bcd > C:\bcd.txt
```
This writes the output of "bcdedit" to the file "\bcd.txt" on your Vista partition. You can access this file in ubuntu via

```
sudo mount /dev/sda5 /mnt
cat /mnt/bcd.txt
```

---

### Post by PinkRose on 2008-11-28
Dear meierfra,

Thanks alot the problem is solved and my Vista is back
the problem was thta i wrote : boot\bootsect.exe /nt60  C:
in the terminal without the DVD letter but when i entered it again 
E:\boot\bootsect.exe /nt60  C: 
the problem was fixed 

Again thank you for ur quick replys and ur kind help

Best Regards,

---

### Post by sadiqdude on 2008-11-28
hi thanks for the post its an important pice of infor mation....rock on:):):)

---

### Post by meierfra. on 2008-11-28
> Thanks alot the problem is solved and my Vista is back

Glad to be of help. Have fun with Vista and Ubuntu.

---

### Post by kazemizuhi on 2009-02-03
Can't thank you enough for this post/guide. It's 5:30AM in the morning right now and I've been working on this since midnight. Fell asleep for an hour half-way through... but thanks to this, everything is working again.

Why does Ubuntu default entries in menu.lst to incorrect values (*as that is where my issue lay. I had a backup of XP from which I extracted my boot.ini etc.*)? I mean, it had the values right during the partition stage of install, so why change the values to something that is incorrect? Should this be reported as a bug?

---

### Post by mintar on 2009-02-04
Thank you a thousand times, Meierfra! I just used this method to install the Windows 7 Beta on my Eee PC, and it worked like a charm!

I'll continue using Ubuntu as my primary OS, the rest is just for playing around. But with Xandros, Windows XP, Windows 7, Mac OS X and Ubuntu on the same machine, you quickly run out of primary partitions. And all of them, except Ubuntu, gave me trouble installing them in a way that they don't need a primary partition. Thanks to you (and GRUB ;-) ), I managed to get the last of the bunch onto the machine in a bootable form.

---

### Post by theDaveTheRave on 2009-02-09
Thanks

this was great.

I needed to do a refresh on my XP install (dual boot) and of course I lost my grub menu in the process.

I'm going to tag this one I think, and store it for good measure

David

---

### Post by Hachi-Roku on 2009-02-12
This tutorial was awesome. Thanks.

I used the vista recovery disc i had for the fix vista section and ended up wiping my hdd clean....hmm. Next time ill be obtaining an install disk instead.

Thats one of those 'once only' mistakes! but at least i learned alot about fixing boot sectors!

cheers.

---

### Post by gundam1965 on 2009-03-29
I would like to buy you a drink meierfra. You just saved my Life.

---

### Post by revolver4ever on 2009-04-02
Thank you so much!  Not only did this fix my problem (after installing Ubuntu over a Vista partition, trying to dual boot with Win7, Win7 wasn't coming up in GRUB) but I actually learned a lot about how these things work.

Thanks.

---

### Post by meierfra. on 2009-04-02
> Not only did this fix my problem (after installing Ubuntu over a Vista partition, trying to dual boot with Win7, Win7 wasn't coming up in GRUB)
Glad to be of help.

> but I actually learned a lot about how these things work.
Great. If you still have question about the whole booting process, just asked.

---

### Post by Nixie Pixel on 2009-04-12
This is an extremely informative and useful post, thank you!

---

### Post by dapaintballer331 on 2009-08-05
You fixed my windows 7 installation! Thanks so much, very comprehensive.

---

### Post by ebro173 on 2010-02-01
I'm posting here hoping to get on someone's radar.  I've started another thread describing a problem I'm having trying to boot into Windows in this other thread:

[http://ubuntuforums.org/showthread.php?t=1394394](http://ubuntuforums.org/showthread.php?t=1394394)

When I mount the partition where Windows is installed, it looks to me like I do have the windows boot files so I'm not sure I have the exact same problem being addressed here in this thread.

Thanks for any help.

---

### Post by meierfra. on 2010-02-01
ebro173: I'll respond in your thread.

---

### Post by vivekratnavel on 2010-04-25
Thanks a lot... It saved me a reinstall.... :P U guys rock...

---

### Post by bilboinamerica on 2010-12-11
Hey meierfra,
unfortunately your instructions don't seem to help in my case. The symptoms are the same as above though. I messed up the mbr when deleting a partition and resizing another one with gparted. I can now boot a working Ubuntu installation on a hard drive connected via USB. The same works for the W7 start disk (I copied it onto a hard drive as my computer does not have an optical drive).
When I try using bcdedit it produces this error:
```
 
the boot configuration data store could not be opened
the system cannot find the file specified

```
The problem seems to be that the drive is not set to be active:
[http://neosmart.net/forums/showthread.php?t=767](http://neosmart.net/forums/showthread.php?t=767)
When I try setting it to active using diskpart though it doesn't work:
```
Virtual Disk Service error:
The specified partition type is not valid for this operation
```
 
What am I doing wrong?
Help would be very apreciated as I really need my computer for work over the weekend (and I'm afraid that a re-install might not even help)!

---

### Post by kansasnoob on 2010-12-11
> **bilboinamerica said:**
> Hey meierfra,
unfortunately your instructions don't seem to help in my case. The symptoms are the same as above though. I messed up the mbr when deleting a partition and resizing another one with gparted. I can now boot a working Ubuntu installation on a hard drive connected via USB. The same works for the W7 start disk (I copied it onto a hard drive as my computer does not have an optical drive).
When I try using bcdedit it produces this error:
```
 
the boot configuration data store could not be opened
the system cannot find the file specified

```
The problem seems to be that the drive is not set to be active:
[http://neosmart.net/forums/showthread.php?t=767](http://neosmart.net/forums/showthread.php?t=767)
When I try setting it to active using diskpart though it doesn't work:
```
Virtual Disk Service error:
The specified partition type is not valid for this operation
```
 
What am I doing wrong?
Help would be very apreciated as I really need my computer for work over the weekend (and I'm afraid that a re-install might not even help)!

Please begin by posting the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Alternative instructions;

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by guitarmaniatico on 2011-01-19
The easiest way to do this is just by extracting the tree files from here: [http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573](http://ubuntuforums.org/attachment.php?attachmentid=73056&d=1212690573) (previously mentioned), on the XP partition and thats it. Then just run the Startup-Manager ([https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)) from System> administrator.

If you do not have it just look in the program installer and type Startupmanager.

That applies for GRUB2, thats just the worlds most powerful tool for starting OS.

Thanks to all the good working linux genious!!!

---

### Post by pooyakhp on 2012-08-15
Hey meierfra, seems as if all roads lead to Rome, i.e. your post;). now I've got a question, or two: 


> If Vista is not on the boot drive, you need to add "map" lines:

title Vista
rootnoverify (hd3,4)
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1


how do we know we need to map the drive? And which one is hd0, hd3 and hd4?

---

### Post by oldfred on 2012-08-15
Better to create a new thread as this is now very old. But still useful on some older XP issues, but now there are some newer better ways to solve issues.

The example you post is from grub legacy where we often had to manually edit the limited boot stanza grub legacy would create. hdX are physical drives in a multi-drive configuration - drives 3 & 4 not partitions which Windows calls drives.

Grub2's os-prober almost always finds a Windows install and creates a boot stanza. Sometimes it confuses recovery and full install partition but that is just a label change with Grub Customizer. Grub2's os-prober will also add a mapdevice command if required. mapdevice has replaced the old map commands from grub legacy.

---

