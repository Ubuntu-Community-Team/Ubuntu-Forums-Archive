---
title: "[SOLVED] No dual-boot screen after reinstalling xp"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by darkwood67 on 2008-10-26
I had ubuntu installed along with xp on the same disk. I reinstalled xp and from that point there is no dual-boot option. I tried to reinstall ubuntu on the same partition it was previously installed but the partition did not show up in the installation process. After booting with the live cd I could see and access the ubuntu partition. Is there a way to make things work again.
P.S. don't talk too technical because I won't understand a thing!

---

### Post by bulldog on 2008-10-26
You need to reinstall GRUB again with the live cd.
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.


Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

---

### Post by darkwood67 on 2008-10-26
> **bulldog said:**
> You need to reinstall GRUB again with the live cd.
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.


Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
This will get you a grub> prompt 
```
sudo grub
```
This will return a location which you have to use in the next command.
```
find /boot/grub/stage1
```
Enter the location given by the previous command in the next command. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

before I start this, do I have to open the terminal in any specific folder? and can I change the default os to xp, because the family uses the pc too and has no idea what ubuntu is...

---

### Post by darkwood67 on 2008-10-26
thank you for the quick reply and the accurate solution!

---

### Post by bulldog on 2008-10-26
Yes,you can boot XP by default.
Count your entry's in your menu.lst starting with zero.
You need to count them all including recovery and memtest.
The number which would be your windows entry you have to change in your menu.lst.
```
# default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0 
```
This is zero by default,but if your windows would be 5 change the zero into five.

To enter your menu.lst,
```
gksu gedit /boot/grub/menu.lst
```
When done save the file and exit,and on next reboot windows will start up.

---

### Post by Felipejane on 2008-10-26
I think this might be a related problem with a similar solution, but I want to verify it. 

I used to have a dual boot setup, with the luxury of Ubuntu installed on a second internal hard drive. That drive failed, and in the process of fiddling around trying to get an Ubuntu workaround using a USB flash drive, I somehow managed to mess up the MBR on my primary (Windows XP) drive.

I ended up buying an external 160GB hard drive that connects by USB, and successfully installed Ubuntu onto it. I can still see the files on my Windows drive, and can read and write to that drive while running Ubuntu from the external drive. What I can no longer do is boot Windows XP. I assume that the MBR was relocated from that Windows internal hard drive to the new external hard drive. When I pick Windows XP from the GRUB menu, I see a message that a file (HAL.DLL or something like that) is missing.

My plan is to disconnect the external (Ubuntu) hard drive, then use the reinstall disk for the PC (a Dell), specifically the FixMBR program on it, which should let me boot once again straight into Windows. My question is, once I've done that, can I then plug the external drive back in and get its copy of GRUB to recognize the Windows drive so that I can boot Windows if I need to? I'm guessing the solution is some variation on Bulldog's answer to the original poster of this thread; I'd just like to have that confirmed.

P.S.: I'm happy to say that after several weeks without Windows, I'm increasingly happy to work exclusively in Ubuntu, but there are a few things that still go better in Windows. And there are some files I need to process with their original applications so that I can get them over to the external drive; I'm beginning to have some success installing Windows apps under Wine.

---

### Post by rajeev123 on 2009-03-18
hi  recently i reinstalled my xp. and i got the same problem as darkwood67
i did all the  tricks mention in this post, but  it doesn't work .. i am still not able to start my ubuntu .. is there any other alternative to get my ubuntu work ..

---

### Post by meierfra. on 2009-03-19
In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by rajeev123 on 2009-03-19
hi @ **meierfra.**, below is the copy of my result.text

```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 290376045 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /boot/grub/menu.lst.
    Operating System:  Ubuntu 8.04.2
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x795f795f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    78,140,159    78,140,097   7 HPFS/NTFS
/dev/sda2          78,140,160   120,083,199    41,943,040   7 HPFS/NTFS
/dev/sda3         120,085,875   142,625,069    22,539,195   c W95 FAT32 (LBA)
/dev/sda4         142,625,070   312,576,704   169,951,635   5 Extended
/dev/sda5         142,625,133   306,600,524   163,975,392  83 Linux
/dev/sda6         306,600,588   312,576,704     5,976,117  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="60B48EC0B48E97E4" TYPE="ntfs" 
/dev/sda2: UUID="6484897A84894F8A" TYPE="ntfs" 
/dev/sda3: UUID="42FF-4302" TYPE="vfat" 
/dev/sda5: UUID="3a10135a-d05a-43a6-8cac-cafc5d5f859c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f3f1c5ce-9e75-4f46-8313-0c47f5262832" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


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
# kopt=root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro quiet splash
initrd		/boot/initrd.img-2.6.24-22-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-22-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro single
initrd		/boot/initrd.img-2.6.24-22-generic

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro quiet splash
initrd		/boot/initrd.img-2.6.24-21-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-21-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro single
initrd		/boot/initrd.img-2.6.24-21-generic

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.2, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.2, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3a10135a-d05a-43a6-8cac-cafc5d5f859c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=f3f1c5ce-9e75-4f46-8313-0c47f5262832 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 148.6GB: boot/grub/menu.lst
 148.6GB: boot/grub/stage2
 148.6GB: boot/initrd.img-2.6.24-16-generic
 148.6GB: boot/initrd.img-2.6.24-16-generic.bak
 148.6GB: boot/initrd.img-2.6.24-19-generic
 148.6GB: boot/initrd.img-2.6.24-19-generic.bak
 148.6GB: boot/initrd.img-2.6.24-21-generic
 148.7GB: boot/initrd.img-2.6.24-21-generic.bak
 148.7GB: boot/initrd.img-2.6.24-22-generic
 148.7GB: boot/initrd.img-2.6.24-22-generic.bak
 148.7GB: boot/initrd.img-2.6.24-23-generic
 148.7GB: boot/initrd.img-2.6.24-23-generic.bak
 148.7GB: boot/vmlinuz-2.6.24-16-generic
 148.5GB: boot/vmlinuz-2.6.24-19-generic
 148.7GB: boot/vmlinuz-2.6.24-21-generic
 148.6GB: boot/vmlinuz-2.6.24-22-generic
 148.7GB: boot/vmlinuz-2.6.24-23-generic
 148.7GB: initrd.img
 148.7GB: initrd.img.old
 148.7GB: vmlinuz
 148.6GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  eb 58 90 4d 53 57 49 4e  34 2e 31 00 02 20 5c 00  |.X.MSWIN4.1.. \.|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 73 5d 28 07  |........?...s](.|
00000020  bb eb 57 01 7e 15 00 00  00 00 00 00 02 00 00 00  |..W.~...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 02 43 ff 42 4e  4f 20 4e 41 4d 45 20 20  |..).C.BNO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 8c c8 8e d0 bc ff  |  FAT32   ......|
00000060  7b fb 8e d8 8e c0 fc bf  20 00 33 c0 b9 15 00 af  |{....... .3.....|
00000070  75 05 af 75 04 e2 f8 47  47 81 7d fe 00 c0 72 0a  |u..u...GG.}...r.|
00000080  e2 ed 81 3e 02 01 00 c0  73 0f be 88 7d e8 3f 00  |...>....s...}.?.|
00000090  33 c0 cd 16 3d 00 3b 75  f7 be a7 7c bf a7 7e b9  |3...=.;u...|..~.|
000000a0  71 00 f3 a5 e9 00 02 bb  00 7c b9 01 00 be e1 7e  |q........|.....~|
000000b0  e8 1c 00 33 c0 cd 16 b8  01 02 33 d2 50 cd 13 58  |...3......3.P..X|
000000c0  cd 13 72 e3 81 3e fe 7d  55 aa 75 db e9 31 fd 50  |..r..>.}U.u..1.P|
000000d0  53 51 ac 3c 00 75 04 59  5b 58 c3 b4 0e cd 10 eb  |SQ.<.u.Y[X......|
000000e0  f1 0a 0d 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
000000f0  73 6b 20 6f 72 20 64 69  73 6b 20 65 72 72 6f 72  |sk or disk error|
00000100  0a 0d 49 6e 73 65 72 74  20 44 4f 53 20 64 69 73  |..Insert DOS dis|
00000110  6b 65 74 74 65 20 61 6e  64 20 70 72 65 73 73 20  |kette and press |
00000120  61 6e 79 20 6b 65 79 20  2e 2e 2e 0a 0d 00 00 00  |any key ........|
00000130  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000180  00 00 00 00 00 00 00 00  0a 0d 50 6f 73 73 69 62  |..........Possib|
00000190  6c 65 20 62 6f 6f 74 20  56 49 52 55 53 20 64 65  |le boot VIRUS de|
000001a0  74 65 63 74 65 64 21 0a  0d 50 72 65 73 73 20 3c  |tected!..Press <|
000001b0  46 31 3e 20 74 6f 20 63  6f 6e 74 69 6e 75 65 00  |F1> to continue.|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

umount: /tmp/BootInfo/sda3: device is busy
umount: /tmp/BootInfo/sda3: device is busy
```

---

### Post by meierfra. on 2009-03-19
You installed grub to the boot sector of the ubuntu partition, instead to the MBR. To fix uour problem, boot from the Ubuntu Live CD, open a terminal and then


```
sudo grub
root (hd0,4)
setup (hd0)
quit
```

Reboot and you should get the Grub menu.

---

### Post by rajeev123 on 2009-03-20
hi , i did with above said  commands again .. but the result is same .. i am not able to start ubuntu .. there is no option for selecting OS

---

### Post by meierfra. on 2009-03-20
> .. i am not able to start ubuntu .. there is no option for selecting OS

Do you still boot directly into XP?

Please try my instruction again.  Make sure that you use "setup (hd0)" and not "setup (hd0,4)". Also before typing "quit" at the grub prompt, copy the  content of the terminal and post it here.

After you  typed "quit" and run the boot info script again and post the RESULT.txt

---

