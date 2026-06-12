---
title: "Grub doesn't start. What did I do wrong?"
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by vampire666eng on 2007-09-13
Hi to you all!

I'm a complete n00b of uBuntu and of all the Linux wold (I am a Windows XP users and always used Windows systems).

I installed uBuntu on a system with Windows XP already installed (double boot)
After I installed ubuntu (with the graphic interface on the live cd) and rebooted the system, I can't choose what system to run and windows xp is always executed (I can't see any boot loader). 

I installed ubuntu after freeing 20GB on a 80GB hard disk with another partition (used to store windows XP programs (drive 1 (F:\) as shown in the image attached)).

These are the steps that I used to install uBuntu:
-runned the live CD, clicked on the "Install" icon on the desktop, and in the partition options I've put in the "Manual" settings:
total 20GB:
-"/" ext3 5GB primary
-"swap" 3GB (I have 2GB of Ram) logic
-"/usr" 12GB logic

The Grub boot loader should start at that point right (after concluding the installation and reboot the pc)? What should I do? Did I do something wrong with the partitions?

I also tried the Super Grub Disk ([http://sgd.howto-linux.de/](http://sgd.howto-linux.de/)) and reinstalled grub in the MBR but the problem persists. What should I do?

Thanks for the help.

Maybe this can help:
[[IMG]http://img513.imageshack.us/img513/9353/partitionsam3.th.jpg[/img]](http://img513.imageshack.us/my.php?image=partitionsam3.jpg)

---

### Post by vampire666eng on 2007-09-13
I tried also running the cd live of uBuntu and then in the terminal I typed:
sudo grub

grub> find /boot/grub/stage1
(hd0,1)

grub> root (hd0,1)

grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded.
succeeded
Running "install /boot/grub/stage1 (hd0)  (hd0)1+17 p (hd0,1)/boot/grub/stage2/boot/grub/menu.lst" ... succeeded
Done.

But nothing changes.

---

### Post by wolfger on 2007-09-13
At a guess, your grub is installed on Disk 1, but you're booting from C: (Disk 3). A quick test of your BIOS settings should tell you which boot order you have. If you put Disk 1 as primary boot device (or second behind CD-ROM), Grub should load. If this is already the case, then I'm obviously wrong. :-)

---

### Post by vampire666eng on 2007-09-13
Geez! You are right!:cool:
I feel stupid...I just changed the boot order and the grub boot loader runs fine. :)

But I don't get one thing...Why can't I run windows XP with the grub boot loader now?
If I select the Windows XP entry I receive the following message:

"Error 12: invalid device requested"

It's a little bit annoying to change the boot order in the Bios every time I want to start the other system.

Thanks again!

---

### Post by logos34 on 2007-09-13
Just curious: is disk 1 (linux) an IDE/PATA drive?  What about the other two?

---

### Post by vampire666eng on 2007-09-13
Hi. :)
Disk 1 is IDE/PATA (linux)
Disk 2 and disk 3 (windows) are IDE/SATA

---

### Post by logos34 on 2007-09-13
> **vampire666eng said:**
> Why can't I run windows XP with the grub boot loader now?
If I select the Windows XP entry I receive the following message:

"Error 12: invalid device requested"

Edit your windows entry in /boot/grub/menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

---

### Post by Pumalite on 2007-09-13
Maybe all you need is to map the Windows entry in your menu.lst. For that, post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by vampire666eng on 2007-09-13
> **logos34 said:**
> Edit your windows entry in /boot/grub/menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Yes, it is the same as the first image of the link you posted.

> **Pumalite said:**
> Maybe all you need is to map the Windows entry in your menu.lst. For that, post:
sudo fdisk -lu
cat /boot/grub/menu.lst
I'll give it a try. Thanks.:)

---

### Post by logos34 on 2007-09-13
> **vampire666eng said:**
> Hi. :)
Disk 1 is IDE/PATA
Disk 2 and 3 are IDA/SATA

Just as I thought...Even though your windows disk (#3) is first in the Bios hard disk boot order, the grub 'find' command still returns '(hd0,1)' for root (disk 1) because it privileges IDE ahead of SATA.  I sure hope Grub2 addresses this issue.

---

### Post by vampire666eng on 2007-09-13
> **Pumalite said:**
> Maybe all you need is to map the Windows entry in your menu.lst. For that, post:
sudo fdisk -lu
cat /boot/grub/menu.lst

Ok I did that and this is what I get. I really don't know what all this is about (the comands you made me to insert and the result:oops:). 

```
alain@VAMPIRE666:~$ sudo fdisk -lu
Password:

Disk /dev/hdb: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders, total 156355584 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63   115378829    57689383+   7  HPFS/NTFS
/dev/hdb2       115378830   127042019     5831595   83  Linux
/dev/hdb3       127042020   156344579    14651280    f  W95 Ext'd (LBA)
/dev/hdb5       127042083   132905744     2931831   82  Linux swap / Solaris
/dev/hdb6       132905808   156344579    11719386   83  Linux

Disk /dev/sda: 400.0 GB, 400088457216 bytes
16 heads, 63 sectors/track, 775221 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        1008   781422767   390710880    f  W95 Ext'd (LBA)
/dev/sda5            1071   781422767   390710848+   7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    36885239    18442588+   7  HPFS/NTFS
/dev/sdb2        36885240   234436544    98775652+   f  W95 Ext'd (LBA)
/dev/sdb5        36885303   234436544    98775621    7  HPFS/NTFS
alain@VAMPIRE666:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=edf52180-dae7-4e4d-aa86-7093e732798b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=quiet splash locale=it_IT

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
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=edf52180-dae7-4e4d-aa86-7093e732798b ro quiet splash locale=it_IT
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=edf52180-dae7-4e4d-aa86-7093e732798b ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows NT/2000/XP (loader)
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

alain@VAMPIRE666:~$ 

```

> Just as I thought...Even though your windows disk (#3) is first in the Bios hard disk boot order, the grub 'find' command still returns '(hd0,1)' for root (disk 1) because it privileges IDE ahead of SATA. I sure hope Grub2 addresses this issue.
So I can't solve the problem? 

Thanks to you both for your support!

EDIT: I was thinking....can't I use the Windows boot loader and insert uBuntu i the boot entries (but if it can be done...I don't know how to).

---

### Post by logos34 on 2007-09-13
> **vampire666eng said:**
> So I can't solve the problem?

Yes. I was just referring to the order in which the grub shell sees the drives.

try '(hd1,0)':

gksudo gedit /boot/grub/menu.lst

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows NT/2000/XP (loader)
root            (hd1,0)    -->or 'rootnoverify'
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


You may also have to edit /boot/grub/device.map.

---

### Post by Pumalite on 2007-09-13
There you go. I hope it works.

---

### Post by logos34 on 2007-09-13
> **vampire666eng said:**
> EDIT: I was thinking....can't I use the Windows boot loader and insert uBuntu i the boot entries (but if it can be done...I don't know how to).

Grub is the preferred way...Windows ntldr should be a last resort, but there is a way.

---

### Post by Pumalite on 2007-09-13
Grub is the best boot loader around, period.

---

### Post by vampire666eng on 2007-09-13
A BIG THANK YOU and a friendly hug to you both!
It works perfectly now! Yey!

Thank you - thank you - thank you - thank you!

> **logos34 said:**
> Grub is the preferred way...Windows ntldr should be a last resort, but there is a way.> **Pumalite said:**
> Grub is the best boot loader around, period.
:guitar::popcorn:

---

### Post by logos34 on 2007-09-13
Ok, enjoy!

---

### Post by Pumalite on 2007-09-13
Happy Ubunting!!

---

### Post by vampire666eng on 2007-09-14
Thanks! :)

---

### Post by von Stalhein on 2007-09-14
Sorry to hijack, I'm having the same problem, but I'm ubern00b.

I loaded Ubuntu onto a separate HDD. I changed the boot sequence in the BIOS, but XP comes up without any appearance of GRUB.

From reading the above, I think I need to get it to boot from my G: drive (the Ubuntu OS) rather than the C: or F: which have Windows files - am I on the right track here?

TIA

---

### Post by wolfger on 2007-09-14
> **von Stalhein said:**
> From reading the above, I think I need to get it to boot from my G: drive (the Ubuntu OS) rather than the C: or F: which have Windows files - am I on the right track here?
Maybe. Your Ubuntu partitions shouldn't have a drive letter like "G:", that's a Windows thing. Note also that a single physical hard drive can have many Windows "drives" (what Linux more appropriately calls partitions). You will need to boot from the physical drive that contains Grub. Is there any possibility you can provide a screenshot of your drive partitioning like vampire666eng did? That might help.

---

### Post by Pumalite on 2007-09-14
Can you get in Ubuntu right now or it has disappeared from the radar screen?

---

### Post by von Stalhein on 2007-09-14
Thanks guys.

I re-installed.

If the boot sequence in the BIOS is set to the HDD first, GRUB goes to start but is halted by error #17.

If I boot with the CD first in the sequence, I do get a menu with a couple of flavours of Ubuntu, as well as the option to start XP. I have been in Ubuntu for long enough to get 180 meg of updates, but it still reports the error on reboot.

It's a bit of a nuisance to have to leave the disk in to boot.

From some Googling, it looks like an MBR issue, but I haven't gotten my head around how to fix it yet. I think I need to be in Ubuntu, open a command line and edit the location of the drive with Ubuntu on it or something? 

 I have 3 physical drives, XP Home on 1 & 2, and Ubuntu on 3. The 3rd physical drive has been partitioned by Ubuntu into 2 parts, one about 5 gg, the other the balance of the 160 G HDD.

---

### Post by Pumalite on 2007-09-14
You have to be in Ubuntu ,get to the Terminal and post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by von Stalhein on 2007-09-15
I booted into Ubuntu, and did the Terminal thing.
I put sudo fdisk -lu and hit enter, and was asked for a  password, which I duly entered. The following was the result.
I couldn't work out how to get the rest of the command you stipulated in - obviously I missed the sequence somewhere.

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   300415499   150207718+  83  Linux
/dev/sda2       300415500   312576704     6080602+   f  W95 Ext'd (LBA)
/dev/sda5       300415563   312576704     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16065   234436544   117210240    f  W95 Ext'd (LBA)
/dev/sdc5           16128   234436544   117210208+   7  HPFS/NTFS


---

### Post by meierfra on 2007-09-15
>  I couldn't work out how to get the rest of the command you stipulated in - obviously I missed the sequence somewhere.

Just do copy and paste.

---

### Post by Pumalite on 2007-09-15
You have Ubuntu in sda1. We have to make sure that Ubuntu entry in your menu.lst points to the right partition: root (hd0,0), Also need to know where is pointing Windows.

---

### Post by von Stalhein on 2007-09-16
Hello again,
Sorry for taking so long to get back - RL keeps interfering :-( and I think we may be in different hemispheres!!
I pasted the command into Terminal as suggested, and the following is the result :- 


> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   234436544   117210240    f  W95 Ext'd (LBA)
/dev/sdb5           16128   234436544   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   300415499   150207718+  83  Linux
/dev/sdc2       300415500   312576704     6080602+   f  W95 Ext'd (LBA)
/dev/sdc5       300415563   312576704     6080571   82  Linux swap / Solaris
stephen@stephen-Ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


I hope that contains the info you need?

---

### Post by meierfra on 2007-09-16
You already gave us that information. Post the output of

```
cat /boot/grub/menu.lst
```

---

### Post by von Stalhein on 2007-09-16
Sorry to muck you about. n00b > me

OK, this is the output from that command: -
> 
stephen@stephen-Ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by meierfra on 2007-09-16
The data is a little bit confusing, so I need to ask some questions:

You posted the output of  "sudo fdisk -l"  twice. But the results differ:
In the earlier output ubuntu is on sda and windows is  on sdb
In the later output  ubuntu is on sdc and windows on sda.

Did you do anything different the second time? (Use the live cd? Reinstalled again?  Changed the boot order in the Bios? ... )

Is any of your hard drives an external drive?

In the  Bios, can you choose which hard drive to boot  from?

---

### Post by von Stalhein on 2007-09-16
> **meierfra said:**
> The data is a little bit confusing, so I need to ask some questions:

You posted the output of  "sudo fdisk -l"  twice. But the results differ:
In the earlier output ubuntu is on sda and windows is  on sdb
In the later output  ubuntu is on sdc and windows on sda.

Did you do anything different the second time? (Use the live cd? Reinstalled again?  Changed the boot order in the Bios? ... )

Is any of your hard drives an external drive?

In the  Bios, can you choose which hard drive to boot  from?

I did reinstall with the CD. The first time, when the process finished, and regardless of whether I modified the boot order, the machine hgave me no menu, it just booted to XP.

To use XP I have to boot from from the CD. A menu comes up, the last choice is to boot from the first hard drive. Then, I presume the GRUB menu appears with the choices of the Ubuntu in various guiese, and then XP at the bottom.

In the BIOS, I can't tell it to boot from a specific HDD, the drive Ubuntu is on is internal.

The first time I used Terminal, I could only enter   "sudo fdisk -lu" before a prompt came up requesting a password. That was the first output. The next time I pasted in the "cat /boot/grub/menu.lst " and the output from that was in my last post.
I'll try it again., and put it in the next post.
Thanks for your patience.

---

### Post by von Stalhein on 2007-09-16
Terminal will only let me do that command in two parts. 
It processes the "sudo fdisk -lu" command, and then the "cat /boot/grub/menu.lst"

Output follows :-
> stephen@stephen-Ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   234436544   117218241    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   234436544   117210240    f  W95 Ext'd (LBA)
/dev/sdb5           16128   234436544   117210208+   7  HPFS/NTFS

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   300415499   150207718+  83  Linux
/dev/sdc2       300415500   312576704     6080602+   f  W95 Ext'd (LBA)
/dev/sdc5       300415563   312576704     6080571   82  Linux swap / Solaris
stephen@stephen-Ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd2,0)

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

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd2,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=22f44470-d94b-4a71-b68c-f50feb08c547 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd2,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Pumalite on 2007-09-16
It seems you have not resolved your issue, but you have been switching hard drives around and re-installing the system. It's very hard to follow you. What's your present status?

---

### Post by von Stalhein on 2007-09-16
> **Pumalite said:**
> It seems you have not resolved your issue, but you have been switching hard drives around and re-installing the system. It's very hard to follow you. What's your present status?

The situation is as detailed above.

When I didn't get a GRUB menu after the first install (machine just booted to XP), I reinstalled over the top (no uninstall).

 Since that process, if I boot the machine without the CD in the drive (designated as the 1st boot device in the BIOS), I get the #17 error. If I boot with the CD in the drive, I get the Ubuntu CD menu, and can pick the" boot from 1st hard drive" option.

That puts me into another menu, which contains various Ubuntus and an option to boot into XP.

I have not consciously changed any HDDs around - there are 3 physical disks.
Disk 1 has the XP OS & files, Disk 2 XP files, and Disk 3 Ubuntu.

---

### Post by Pumalite on 2007-09-16
Try re-installing Grub: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by von Stalhein on 2007-09-16
OK, thanks, that looks logical.
I'll try it later today and report back.

---

### Post by Pumalite on 2007-09-16
OK. Good luck.

---

### Post by von Stalhein on 2007-09-18
I followed that process, and I thought I was winning, as the GRUB menu reported success.
It found (hd2,0) and setup on (hd0).

However, the error message then was that "cannot mount selected partition" for either Ubuntu or XP choices in the GRUB menu.

I changed boot sequence in the BIOS and persisted, and even ran the recommended GRUB sequence from a command line after accidentally hitting the escape key. Again the same issue. There was some sphincter tightening going on when I couldn't get into either OS :-)

Anyway, I've done the fixmbr operation, and I am now back to 3 physical drives, all on the NTFS file system - having formatted the #3 drive that contained Ubuntu.

I'm keen to have another crack at making this a dual boot system - any recommendations before I try again?

---

### Post by Pumalite on 2007-09-18
Keep trying. The recipe is the same.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287)

---

### Post by von Stalhein on 2007-09-20
I think I am starting to move from n00b to ubergeek.

Having had trouble as detailed above, I fixmbr'ed and reloaded Ubuntu. On reboot, straight into XP - which I expected, but I had to check.

I used SuperGrub to change the config from (hd,0) to (hd,2), and then reset the boot sequence so that the thing booted from the drive containing Ubuntu (the new 160G HDD). Eureka! The GRUB menu appears, and it's all good.

I built this machine about 2 years ago, and the only things I hadn't done was replace a power supply (the new HDD tipped the system over in respect of amps required) and loading a Linux OS.

Thank to to all who gave me advice. I've done a heap of reading, and I'm looking forward to discovering more about the OS.

---

### Post by Pumalite on 2007-09-20
Good for you. As you will find out Linux is a lot of fun, but it takes dedication and perseverance. You seem to have them.

---

### Post by wolfger on 2007-09-20
FWIW, there's a lot fewer grub problems if you just ditch Windows entirely. :guitar:

---

### Post by von Stalhein on 2007-09-20
> **wolfger said:**
> FWIW, there's a lot fewer grub problems if you just ditch Windows entirely. :guitar:

I'm sure that's true, but I like to hasten slowly :-)

---

