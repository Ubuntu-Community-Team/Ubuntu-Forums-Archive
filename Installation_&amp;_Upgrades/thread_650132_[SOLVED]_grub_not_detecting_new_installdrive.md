---
title: "[SOLVED] grub not detecting new install/drive"
date: 2007-12-25
forum: Installation &amp; Upgrades
---

### Post by klemencic on 2007-12-25
I originally installed Ubuntu on a separate 4GB drive, with my main drive being a 80gb Windows drive
I have now decided to keep using Linux and have installed a 40gb drive for this, so now I have a 4gb, 40gb and 80gb
I have loaded Ubuntu onto the 40gb but am unable to boot to it, GRUB has only detected the original Ubuntu on the 4gb drive
I have run the live CD again and the partitioning information has given me the following details
40gb drive HDB
80gb drive HDC
4gb drive HDD

I have spent a couple of hours on /grub/menu.lst but have been unable to get the new drive to boot. if I try root as (HD2,0) I am told that this drive does not exist

I thought the problem was in /boot/grub/device.map which says hd0 /dev/hdc
When I went sudo gedit /boot/grub/device.map to change hd0 to /dev/hdb I get the following
(hd0) /dev/sda
(hd1) /dev/sdb

The partitions I want are
80gb drive leave as a bootable Windows
40gb drive to be a bootable Ubuntu
4gb drive to be a Linux data drive

Grub will load but not give me the option of the new drive and installation

following is the output of fdisk -l 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x063a986e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4689    37664361   83  Linux
/dev/sda2            4690        4865     1413720    5  Extended
/dev/sda5            4690        4865     1413688+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
81 heads, 63 sectors/track, 30629 cylinders
Units = cylinders of 5103 * 512 = 2612736 bytes
Disk identifier: 0xfc25fc25

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          42       14890    37887192    7  HPFS/NTFS
/dev/sdb2           14891       14930      102060   83  Linux
/dev/sdb3              14          41       71410+  16  Hidden FAT16
/dev/sdb4           14931       30629    40055998+   f  W95 Ext'd (LBA)
/dev/sdb5           14931       30629    40055967   8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/sdc: 4311 MB, 4311982080 bytes
255 heads, 63 sectors/track, 524 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe74fe74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         494     3968023+  83  Linux
/dev/sdc2             495         524      240975    5  Extended
/dev/sdc5             495         524      240943+  82  Linux swap / Solaris


My /boot/grub/menu.lst file is as follows

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
default		4

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
# kopt=root=UUID=92f2ee5e-59f6-4bc1-b59c-2d7d6e734018 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=92f2ee5e-59f6-4bc1-b59c-2d7d6e734018 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=92f2ee5e-59f6-4bc1-b59c-2d7d6e734018 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows 2000 Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by meierfra on 2007-12-26
Sorry, I didn't realized that it would take so long for your new thread to  appear. 

root (hd2,0) seems to  be the correct choice.

But let's  see whether you can access  the menu.lst from  your new ubuntu:

Post the output of 


```
mkdir new
sudo  mount -t ext3  /dev/sda1 new
cat  new/boot/grub/menu.lst
```

Also post the output of

```
sudo grub 
```

and at the "grub>" prompt

 ```
find /boot/grub/stage1
```
(the last letter is the number one)

Also reboot and see what happens if you change the boot order in the bios. You might try all six possibilities.

Just to make sure: You are  able to boot to  Windows from the Grub Menu?

---

### Post by klemencic on 2007-12-26
following is the output as requested

klem@Klem-Linux:~$ mkdir new
klem@Klem-Linux:~$ sudo mount -t ext3 /dev/sda1 new
[sudo] password for klem:
klem@Klem-Linux:~$ cat new/boot/grub/menu.lst
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
# kopt=root=UUID=1126069b-053f-44f5-b3fc-87fecce5a23b ro

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

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1126069b-053f-44f5-b3fc-87fecce5a23b ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=1126069b-053f-44f5-b3fc-87fecce5a23b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdc1
title           Microsoft Windows 2000 Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hdd1)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=92f2ee5e-59f6-4bc1-b59c-2d7d6e734018 ro quiet splash 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hdd1)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=92f2ee5e-59f6-4bc1-b59c-2d7d6e734018 ro single 
initrd          /boot/initrd.img-2.6.22-14-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hdd1.
title           Ubuntu 7.10, memtest86+ (on /dev/hdd1)
root            (hd2,0)
kernel          /boot/memtest86+.bin  
savedefault
boot

klem@Klem-Linux:~$ 

grub> find /boot/grub/stage1
 (hd0,0)
 (hd2,0)

grub>

---

### Post by meierfra on 2007-12-26
Did you try changing  the boot order in the bios? 

If that did not help: In a terminal in the old ubuntu:

```
sudo grub
root (hd2,0)
setup (hd2)
quit
```

reboot  from the 40GBdrive.

---

### Post by klemencic on 2007-12-27
In the BIOS the only options I have are booting from primay and secondary masters which are the 80gb drive and CD
I entered the last code into grub and that come up with a sucess message
I have also edited menu.lst to change Ubuntu to partition (0,0) and receive the a error message unable to mount whilst (2,0) gives the message file not found

---

### Post by klemencic on 2007-12-27
In the BIOS the only options I have are booting from primay and secondary masters which are the 80gb drive and CD
I entered the last code into grub and that come up with a sucess message
I have also edited menu.lst to change Ubuntu to partition (0,0) and receive the a error message unable to mount whilst (2,0) gives the message file not found

---

### Post by klemencic on 2007-12-27
Plan B
what is involved in installing LILO - would this detect all of the installed OS's??

---

### Post by meierfra on 2007-12-27
Edit: Ignore this for now. Go to post 10.

> In the BIOS the only options I have are booting from primay and secondary masters which are the 80gb drive and CD

Maybe your  40 GB drive is not detected by the  bios.
To confirm that:

At the grub menu at boot up, press "c". You will get a "grub>" prompt.

Type 

find /boot/grub/menu.lst

I bet the output will be just (hd1,0). (It won't detect the menu.lst on (hd2,0))

(Press "esc" to get back to the grub menu)

Maybe there is a way to  to change the setting in the  bios so that the 40GB drive is detected, but I have no experience with such things. You might start on a new thread  for that.

Couple of of suggestions:

1)  Could you physically swap your 40GB and  4GB drives, so that the 40 GB drive is detected by the bios?

2) You could create a /boot partition  for your new  Ubuntu on either the 80GB drive or your 4GB drive.

---

### Post by meierfra on 2007-12-27
> Plan B
what is involved in installing LILO - would this detect all of the installed OS's??

Hadn't seen that before my last post. Installing Lilo is fairly easy, but I doubt that it will work if your bios don't detect your 40GB drive.
__________________

---

### Post by meierfra on 2007-12-27
> whilst (2,0) gives the message file not found

Actually this is a  good  sign. Seems I'm wrong about the bios not detecting  the 40 GB drive.  (Otherwise it would have said "drive not found". "file not  found" would be expected if you just change "(hd1,0)" to "(hd2,0)".  

Do this: Boot into your old ubuntu and reinstall grub:

```
sudo grub
```

and at the grub prompt:

```
root (hd2,0)
setup (hd0)
quit
```
Mount  you new ubuntu as before and open the new menu.lst

```
mkdir new
sudo  mount -t ext3  /dev/sda1 new
gksudo gedit  new/boot/grub/menu.lst

```

Change 

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)

to

title Ubuntu, kernel 2.6.20-15-generic
root (hd2,0)

Save the file and reboot.

(If this gets you into the new ubuntu, we'll have to do some more editing later)

---

### Post by klemencic on 2007-12-27
OK I think I will create the boot partition on one of the other drives
Just to confirm that I have an idea of waht I'm doing
When I run install, I manually partition the drives
I require a /swap partition of 128mb min
What size does the /boot partition has to be?

thanks for your help

---

### Post by meierfra on 2007-12-27
Did you try  my instructions from post 10? I really think it should work and would be much easier than creating a separate boot partition.
(Even if you do create a boot partition there  is a very high change that you  still  have to edit menu.lst)

---

### Post by klemencic on 2007-12-27
sorry just trying to cover all bases so i can spend another couple of hours on it but i will try all of your other suggestions first

---

### Post by meierfra on 2007-12-27
Please only do  the instruction from post 10 right now. If you carry out any of the other suggestion at the same time, the instruction will fail, since the underlying assumptions will have changed.

---

### Post by klemencic on 2007-12-27
ok I followed post 10 
I assume that you meant 
sudo grub
root (hd2,0) 
because roof(0,20 gave the error no such partition

I then tried both setup (hd0) and (hd2) but both times when i went to boot Utumbu i received file not found error

---

### Post by meierfra on 2007-12-27
> I assume that you meant
sudo grub
root (hd2,0) 

Of course. Thanks for noticing that.

I might have found my mistake in post 10 but I'm still confused.
 
after setup (hd0): Did the grub menu appear at boot up? If yes which  one, the old from from  6GB partition or the new one from the 40 GB partiton.

after setup (hd2) : Same questions

---

### Post by meierfra on 2007-12-27
Sorry, I really messed up in post 10.  I already new  that grub was using the  wrong device map, but didn't take it into account.
You are probably sick of me by  now, put I promise you that this is my last suggestion.
Also this solution is based on the following assumption which I have been making for some reason and I'm no longer sure that is true:
The grub menu which appears at boot up, is the grub menu from the 6GB harddrive.(That is the one which is has  Windows at the end, not in the middle)

Mount your new ubuntu as before and open the new menu.lst
```

mkdir new
sudo  mount -t ext3  /dev/sda1 new
gksudo gedit  new/boot/grub/menu.lst
```

Change

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)

to

title Ubuntu, kernel 2.6.20-15-generic
root (hd2,0)


```
 gksudo gedit new/boot/grub/device.map
```

Change the file so that it reads:

(hd0) /dev/sdb
(hd1) /dev/sdc
(hd2) /dev/sda



```
sudo grub  --device-map=new/boot/grub/device.map
root (hd2,0)
setup (hd0)
quit
```

---

### Post by klemencic on 2007-12-29
Bingo
All is good now
Thank you for the help

---

### Post by meierfra on 2007-12-29
> All is good now


But you still need to edit your new menu.lst, so that you don't run into problems after the next kernel update:


Boot into the new ubuntu on the 40 gb hard drive. Open  menu.lst via

```
gksudo  gedit /boot/grub/menu.lst 
```

Change "#groot (hd0,0)" to "#groot(hd2,0)"

(this needs to be done, since otherwise "root (hd2,0)" will be changed  back to  "root (hd0,0)" during the next kernel update )

And if you haven't  done  so  yet, change

title Microsoft Windows 2000 Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

to 

title Microsoft Windows 2000 Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

Save the file. In a terminal

```
sudo update-grub
```
(this makes sure you can   boot into recover mode and use the memtest)

---

