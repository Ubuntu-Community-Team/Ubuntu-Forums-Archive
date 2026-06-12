---
title: "Attempted dual boot install, now loads directly to ubuntu, no sign of xp"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by Frijole on 2008-03-20
I installed Ubuntu on my drive that already contained XP. I defragged beforehand and there seemed to be enough space. I then went through the ubuntu install and created 2 new partitions, a swap and ext3 for the root ubuntu filesystem. Everything in Ubuntu is working but My computer boots directly to ubuntu without any sign of XP? Where did I go wrong? And, more importantly, how can I fix it? Any ideas would be greatly appreciated.

---

### Post by Touch.Code on 2008-03-20
This is like me however, I installed Linux on a seperate harddrive, now I cannot access Linux, only Windows :/

---

### Post by Rome.konig on 2008-03-20
check your grub menu.lst

that can be found in /boot/grub/menu.lst

and please post what it says, then we can go further and maybe solve this thread.

---

### Post by Rome.konig on 2008-03-20
@touch-code

what HD did you install Linux in?

you can go into your bios and boot that HD first to access linux, with linux booting first, grub should give you an option to select which OS to boot first.

hope this works for ya :)

---

### Post by forestpixie on 2008-03-20
Frijole - you'll need to know the correct partition as well
```
cat /boot/grub/menu.lst
sudo fdisk -l
```

TouchCode - you'll need to know fdisk result as well - if you can't boot buntu - boot the livecd and do it from there, if you just need to install grub it can be done from there

---

### Post by Frijole on 2008-03-20
ok, my problem is taht windows isn't showing up though. Ubuntu boots ok.

---

### Post by forestpixie on 2008-03-20
so do what I said, open a terminal and paste commands in one by one - paste results here for us and we can help - but without info we'll be guessing :)

---

### Post by Touch.Code on 2008-03-20
Everyone, I did run fdisk. I posted the output in my topic :)

---

### Post by forestpixie on 2008-03-20
> Everyone, I did run fdisk. I posted the output in my topic

not sure what you mean by that - there's not fdisk in your post

Edit - your thread - you'll need to post the supergrub error there

---

### Post by Frijole on 2008-03-20
here is the output I get from cat:
```
frijole@theBean:~$ cat /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=fef3a792-0766-4514-acff-3539529159c4 ro

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fef3a792-0766-4514-acff-3539529159c4 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=fef3a792-0766-4514-acff-3539529159c4 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```


and this is the fdisk output:

```
Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6f2c6f2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1           14536       14593      465885   82  Linux swap / Solaris
/dev/hdc2   *       13320       14535     9767520   83  Linux

```

---

### Post by Frijole on 2008-03-20
can anyone help me out with this? Im lost.

---

### Post by forestpixie on 2008-03-21
what sort of hdd's have you got in your pc? - I'm a bit confused I can see that the linux partitions start halfway through the hdd - but there is no reference to the preceding partitions.

Can you do this from a terminal and post the complete output

```
ls /media
sudo fdisk -l
```

---

### Post by Frijole on 2008-03-21
thanks for your help.

```
frijole@theBean:~$ ls /media
cdrom  cdrom0  floppy  floppy0
frijole@theBean:~$ sudo fdisk -l
[sudo] password for frijole:

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6f2c6f2

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1           14536       14593      465885   82  Linux swap / Solaris
/dev/hdc2   *       13320       14535     9767520   83  Linux

Partition table entries are not in disk order

```

---

### Post by forestpixie on 2008-03-21
Ok - I've no idea why it's reporting the partitions like that - can you load the livecd and when you get there - use the same command to see what' reported from there.

It appears to be missing sda and sdb - which would presumably be the xp partitions - so it looks like they are there - but not in buntu.

---

### Post by Herman on 2008-03-21
Take a look with GParted Partition Editor, it looks to me as if Windows Xp has been deleted.
In the Ubuntu Live CD, 'System'-->'Administration'--'Partition Editor'.

If it really has been deleted you can probably get it back again with TestDisk, [TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html"), or maybe with Parted. **[[B]Parted** User's Manual]("http://www.gnu.org/software/parted/manual/html_mono/parted.html") [/B](Look up the 'rescue' command). 2.4.12 rescue It works, I have used it a few times, once just yesterday.

Regards, Herman :)

---

### Post by kushykush on 2008-03-21
The problem is not GRUB but Windows MBR especially Windows Vista which has a new BCD.

You can edit GRUB list menu and sure it will start pointing you to all the Operating Systems installed on your hard drives. However, GRUB cannot make XP or "longhorn" (vista), boot properly. Because GRUB cannot fix the Windows boot.

The problem is Windows, especially Vista, will not share its MBR (or whatever makes it boot) with any other system, such as GRUB.

Before offering "solutions" people who are not familiar with Windows and especially the new VISTA BCD should stop and think.

There ought to be a common sense free solution to all this.  But I have not found one.  Please point to me if I am amiss.  The only viable "solution" is to buy commercially available software such as Acronis.  However, if Acronis can do it then why can't the brilliant Ubuntu/Linux community?

Problem: How to properly install GRUB without messing up the Windows MBR so that all systems will not only show up in the GRUB start out list, but will also properly boot.

Solutions found by me:  NONE

Suggestions:  The auto install GRUB program in Ubuntu needs to be revised so as to accomodate pre-installed Windows OSs (especially Vista).  GRUB should also be rewritten to accomodate post-install OSs.  For example, what happens if you install Vista on your computer where a Linux based Operating System(s) are installed?

Right now as things stand:  If you install Ubuntu (which will install GRUB), it messes up your other installs (especially Windows).  If you install Windows (Vista, especially) on a computer where a Linux bases Operating System(s) are installed, GRUB gets zapped.  

HOW CAN WINDOWS (VISTA) BE TAUGHT TO COEXIST?

---

### Post by Herman on 2008-03-21
:confused:  Lots of people boot Vista just fine with GRUB.
I don't have Vista myself, but there are lots of tutorials for installing Ubuntu with Vista just the same as with XP, nothing specail seems to be needed.

Regards, Herman :)

---

### Post by Herman on 2008-03-21
Well, you can use [EasyBCD]("http://neosmart.net/dl.php?id=1") if you want.

---

### Post by Herman on 2008-03-21
There is no such thing as a 'Windows MBR', Windows has a 'boot sector', but not a MBR.
MBR stands for 'Master Boot Record', and it belongs to the hard disk and it is quite seperate from any partition and therefore from any operating system. There is only one Master Boot Record per hard disk, but there can be many partition boot records, or boot sectors.

---

### Post by Frijole on 2008-03-24
I ended up re-installing Windows but this time I did not use the whole disk. I installed XP on the first 80GB of my 120GB drive. I would like to put Ubuntu on the rest of the disk. I heard that it is easiest to dual boot when the drive is partitioned when windows is loaded. Does anyone know the best way to finish setting up the dual boot?

---

### Post by forestpixie on 2008-03-24
If the free 40Gb is unformatted - I would do so before you start the install, there is a partition editor in system >admin of the livecd - start that 

use it to make 2 partitions - 1 for the installation, format it to ext3, the other for swap and format it as swap.

Start the installation, when you get to partitioning choose manual.
Select the ext3 partition you have previously made - edit partition - button near bottom of window. Once in the partition edit window - select the mountpoint dropdown menu and choose / . Close that window and continue with the installation.

---

### Post by Frijole on 2008-03-24
If I do all of that then XP and windows will show up in the GRUB list? Also, I heard about using a FAT32 partition to be able to swap files between  the two systems, do you know anything about that?

---

### Post by forestpixie on 2008-03-24
Linux will see  ntfs files by default and will write to them by default in gutsy, so I wouldn't be looking at fat32 at all - yes xp should show up in grub list.

Leave files you want to share on the ntfs partition and you'll be able to access them from within buntu.

---

### Post by Frijole on 2008-03-24
nice, thanks for the help. I will try it out tonight.

---

### Post by waspbr on 2008-03-24
[LIST]
[*]just pop a live CD into you PC,
[*]Run it
[*]click on the install icon
[*]select the language, location and all that
[*]choose manual install, select the empty space
[*]out of that make a swap partition , rule of the thumb is twice the amount of RAM you have, mount type = swap
[*]make another partition with the remaining space, ext3, mount type "/"
[*]Fill in your use details
[*]say ok to what ever pops up
[*]open a cold beer and drink it 
[*]you should be done
[/LIST]

---

### Post by Frijole on 2008-03-24
sounds pretty straightforward, and I'll take any excuse for a cold beer. thanks.

---

