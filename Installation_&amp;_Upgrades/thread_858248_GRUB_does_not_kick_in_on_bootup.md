---
title: "GRUB does not kick in on bootup"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by Johanustom on 2008-07-13
Please help a newby who deperately wishes to free himself from the tyrany of Microsoft.

I am running XP Sp3 on the "C" drive of my machine.
I resized the windows partition and then installed Ubuntu on a logical partition of that drive and as far as I can tell everything went according to plan.
However when the instalation instruction asked me to reboot i went straight into Windows without seeing the GRUB screen.
I can however get into Ubuntu from the live DVD.
My initial assumption was that perhaps the GRUB files had corrupted and followed the forum instructions to restore GRUB.
I therefore ran in terminal:-
"sudo grub" followed by
"find  /boot/grub/stage1"  (which returned "hd1,6")
I then entered "root (hd1.6)" and then
"setup (hd0)"
Perhaps I am misunderstanding the instructions as I am still booting straight into Windows.
Does anyone have any idea as to what might be amiss or what I have got wrong?

---

### Post by Pumalite on 2008-07-13
Boot your Live CD. Post:
sudo fdisk -lu

---

### Post by Johanustom on 2008-07-14
Thank you for your prompt reply. Here is the output from sudo fdisk -lu:-

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5870a964

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       16065   465595829   232789882+   f  W95 Ext'd (LBA)
/dev/sda5           16128    65545199    32764536    b  W95 FAT32
/dev/sda6        65545263   131074334    32764536    b  W95 FAT32
/dev/sda7       131074398   196603469    32764536    b  W95 FAT32
/dev/sda8       196603533   262132604    32764536    b  W95 FAT32
/dev/sda9       262132668   327661739    32764536    b  W95 FAT32
/dev/sda10      327661803   393190874    32764536    b  W95 FAT32
/dev/sda11      393190938   438253199    22531131    b  W95 FAT32


Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xdc9edc9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    30025484    15012711    7  HPFS/NTFS
/dev/sdb2        30025485    61545014    15759765    f  W95 Ext'd (LBA)
/dev/sdb3        61545015    82027889    10241437+   7  HPFS/NTFS
/dev/sdb4        82027890   312576704   115274407+   7  HPFS/NTFS
/dev/sdb5        61271973    61545014      136521    7  HPFS/NTFS
/dev/sdb6        30025611    37833074     3903732   82  Linux swap / Solaris
/dev/sdb7        37833138    57368114     9767488+  83  Linux

Partition table entries are not in disk order

P.S. I don't know if this helps but I do get the GRUB sceen when booting from the dvd..

---

### Post by Pumalite on 2008-07-14
sudo mkdir /media/sdb7
sudo mount -t ext3 /dev/sdb7 /media/sdb7
Post:
cat /media/sdb7/boot/grub/menu.lst

---

### Post by Johanustom on 2008-07-14
Thanks again
The 3 commands return the following:-

john@john-desktop:~$ sudo mkdir/media/sdb7
sudo: mkdir/media/sdb7: command not found
john@john-desktop:~$ sudo mount -t ext3/dev/sdb7/media/sdb7
john@john-desktop:~$ cat/media/sdb7/boot/grub/menu.1st
bash: cat/media/sdb7/boot/grub/menu.1st: No such file or directory
john@john-desktop:~$

---

### Post by Pumalite on 2008-07-14
You have to respect the spaces. Copy and paste the commands in the Terminal.

---

### Post by Johanustom on 2008-07-14
Sorry, I thought my typing was accurate - here is the result:-

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
timeout		15

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=b5a651b6-220a-4ba2-bd27-762613c3ab10 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,6)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5a651b6-220a-4ba2-bd27-762613c3ab10 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b5a651b6-220a-4ba2-bd27-762613c3ab10 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b5a651b6-220a-4ba2-bd27-762613c3ab10 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=b5a651b6-220a-4ba2-bd27-762613c3ab10 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by Valsodar on 2008-07-14
> **Johanustom said:**
> 
"sudo grub" followed by
"find  /boot/grub/stage1"  (which returned "hd1,6")
I then entered "root (hd1.6)" and then
"setup (hd0)"

Did you enter root (hd1,6)? or root (hd1.6)?
and what were the output of the grub command?

---

### Post by Johanustom on 2008-07-14
Hi Valsadar,

My typing again, I used a comma, not a full point i.e. root  (hd1,6).
The output was as follows:-

 [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find  /boot/grub/stage1
 (hd1,6)

grub> root  (hd1,6)

grub> setup  (hd0)

---

### Post by Pumalite on 2008-07-14
At Grub; try editing your boot line: hit 'e' and 'e' again. Then try different drives/partitions. 'b' to boot. If successful; edit menu.lst and make change permanent.

---

### Post by Johanustom on 2008-07-17
Hello again, Pumalite,

I appologise for the delay in coming back to you.  This was due to me having to be away from my computer and also spending time on forums etc. trying to establish exactly what you mean by a “boot line”. I am still not sure but here is what I have done.  Please correct me if I am misunderstanding your instruction.  :-

I booted up from the live DVD and selected the option “boot from Hard drive”.
This produced the Grub menu which is as follows:-
Ubuntu 8.04.1, kernel 2.6.24-19-generic
Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04.1, kernel 2.6.24-16-generic
Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04.1, memtest 86+
Other Operating Systems
Microsoft Windows XP Professional

I then selected the first item “Ubuntu 8.04.1, kernel 2.6.24-19-generic”, which is what I believe you refer to as the “boot line”, and hit e to edit.  This produced the following display :-
root  (hd1,6)
kernel  /boot/vmlinuz-2.6.24-19-generic root=UUID=b5a651b6-22a-4ba2- &#8594;
initrd  /boot/initrd.img-2.6.24-19-generic
quiet

I then edited “(hd1,6)” with every drive/partition.  In all cases the return was :-
Error 17: Cannot mount selected partition

I then tried the same procedure with item 3 in the Grub menu “Ubuntu 8.04.1, kernel 2.6.24-16-generic” with exactly the same result.  I would have thought, however that I should only have one Ubuntu boot option and do not understand why I have two options to boot up from.  Is this correct or is this a problem? 

In summary the only option which I have found to boot is “(hd1,6)”.
 I hope I have interpreted your instructions correctly and the above information is helpful.

---

### Post by Pumalite on 2008-07-17
I imagine you are booting Ubuntu by now.

---

### Post by Johanustom on 2008-07-18
Hi again Pumalite,
No, as I said in my previous post, I tried editing the boot line (did I identify it correctly?)and in every case except(hd1,6)the return was "Error 17: Cannot mount selected partition.
I can still only boot (and get the grub operating systems screen) when my live dvd is in its drive. 
If I don't have my live dvd in its drive my computer does not show the grub screen and boots straight into Windows.
I have not really altered anything as grub is recognised only when I boot up into my hard drive with the aid of the dvd and only on (hd1,6).  This, of course was my original problem. Any other thoughts?

---

### Post by libe on 2008-07-18
Do you have more than one hd,if the answer is yes just change the boot squence from your bios and you're fine!
I have posted the same thing yesterday and it worked!

---

### Post by kartiksinghal on 2008-07-18
I am also getting this "error 17: Cannot mount selected partition" whenever I try to boot into Ubuntu.

I freshly installed windows xp and as usual the MBR was overwritten by xp. I reinstalled grub and got the grub screen back but i am unable to boot into ubuntu with this error cropping up:
error 17: Cannot mount selected partition

Please help

---

### Post by libe on 2008-07-18
sorry can't help more i'm inexperienced.

---

### Post by Johanustom on 2008-07-20
Success!!!!!
I have changed my BIOS boot order to look at my hard drive first and disk drive second, as Libe suggested, and Grub now works fine.
Thank you Libe for putting me on the right track and Pumalite for the time spent looking at my problem.
I do not understand why this has worked as previously the BIOS would have instructed my computer to look at my disk drive first, and having found nothing there, defaulted to look at the hard drive, so all I have done is to instruct it to look at my hard drive first.  I really can not see why this should make a difference.
If anyone can throw light on this it would be appreciated.
Once again thanks for all your help

---

### Post by tom1234 on 2008-07-20
I am having a very similar problem to this.  Could you explain to me what you did to make the BIOS to look at your hard drive?  Thanks.

---

### Post by stenjo on 2008-07-20
> **tom1234 said:**
> I am having a very similar problem to this.  Could you explain to me what you did to make the BIOS to look at your hard drive?  Thanks.

When booting your machine you have the option (for a short while) to enter the BIOS option settings either by pressing F2 (on my Fujitsu Siemens E-Series Lifebook) og any other key or key combination. From this new menu system you will be able to edit the boot sequence.

---

