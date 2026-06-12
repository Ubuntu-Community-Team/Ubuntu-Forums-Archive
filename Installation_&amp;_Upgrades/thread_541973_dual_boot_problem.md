---
title: "dual boot problem"
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by muski on 2007-09-03
hi i am new to linux ... installed 3 days back.
I had two windows installed on my comp in C drive and D drive resp.
I installed ubuntu 7.04 on the C drive and formatted C drive(while doing so).
what i wanted was to keep windows which i have in D drive along with the Ubuntu now installed in C drive.After installation however grub is not recognizing the original windows.(which was in D).
i went to menu.list and made these changes 
(my windows is in hda5,and i dont have sata harddisk)
title           Microsoft Windows XP Professional
root            (hd0,5)
savedefault
makeactive
chainloader     +1

it didnt work and said parsec error

later i changed it to
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,4)
savedefault
makeactive
chainloader     +1
( someone told me that you need to put n-1 hence (hd0,4) )

it still said parsec error

note:- the drive in which i have windows is NTFS

what is the way to solve the problem?
thankyou

---

### Post by thelocust on 2007-09-03
Try this:

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Change the hdd info first.

---

### Post by muski on 2007-09-03
hdd info ... ?? what should i change ... i am sorry i am new and i dont get it
can you please explain it ?

---

### Post by thelocust on 2007-09-03
Sorry first make a back up of your menu.list by entering the following in terminal.
```

sudo cp /boot/grub/menu.list /boot/grub/menu.list.bak
```

That way if you mess anything up you'll be safe.

---

### Post by thelocust on 2007-09-03
then open your menu.list and scroll down to see what hdd your booting linux on. It should look something like this:

```
title        Kubuntu Feisty
root        (hd0,0)
kernel        /vmlinuz-2.6.20-16-generic root=UUID=f27ad5b3-644a-41d0-96db-9b29566eaf2a ro quiet splash
initrd        /initrd.img-2.6.20-16-generic
quiet
savedefault
```Except the title will be different something with Ubuntu in it. Then post what your root is (hd0,0)

---

### Post by muski on 2007-09-03
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
# kopt=root=UUID=f7aa2ef3-4c11-4776-b4dd-903cd83b70b3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,7)

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

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f7aa2ef3-4c11-4776-b4dd-903cd83b70b3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=f7aa2ef3-4c11-4776-b4dd-903cd83b70b3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,7)
kernel		/boot/memtest86+.bin
quiet






### END DEBIAN AUTOMAGIC KERNELS LIST
# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

i changed the menu.lst as above ... however on restart it still gave error and said no such disk found

---

### Post by thelocust on 2007-09-03
can you post the output when you enter "sudo fdisk -l" into terminal.

---

### Post by muski on 2007-09-03
the output is

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2               1        9728    78140128+   f  W95 Ext'd (LBA)
/dev/hda5            1913        5736    30716248+   7  HPFS/NTFS
/dev/hda6            5737        7648    15358108+   7  HPFS/NTFS
/dev/hda7            7649        9728    16707568+   7  HPFS/NTFS
/dev/hda8               1        1824    14651185+  83  Linux
/dev/hda9            1825        1912      706828+  82  Linux swap / Solaris

---

### Post by thelocust on 2007-09-03
This says your only using one 80 Gig HDD. In your first post you said you had to harddrives so I think you have bigger problems than just duel booting. Can anyone else help with this?

---

### Post by merlinus on 2007-09-03
From your last posting of /boot/grub/menu.lst, the entry for windows is incorrect.  As you said at first, it should be (hd0,4).

Change that entry, restart, and then try reinstalling grub this way:

```

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

```Substitute results from find for (hdx,y) and setup (hdx).

Restart and see what happens.

-merlin

---

### Post by muski on 2007-09-03
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

i changed it to

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP
root (hd0,4)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

as you said  ... then i restarted but now what am i supposed to do ?
the code which you gave

sudo grub
find /boot/grub/stage1
root (hdx,y)
setup (hdx)
quit

am i supposed to run it one line atfter the other in the terminal ?

PS:- 

after restart when i try to log in the windows it says
error 12 ... invalid device requested

---

### Post by merlinus on 2007-09-03
> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows XP
root (hd0,4)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
Since you have only one hdd, get rid of the two map lines. 

And yes, run the grub commands one at a time in a terminal.  And restart.

-merlin

---

### Post by muski on 2007-09-03
well i did that just as you said 

sudo grub

find /boot/grub/stage1
it showed (hd0,7)

root (hd0,7)

setup (hd0)

quit

after the restart when i tried logging into my windows it still said 

error 12 invalid device requested :(

---

### Post by merlinus on 2007-09-03
Did you remove the two map lines from /boot/grub/menu.lst?

-merlin

---

### Post by muski on 2007-09-03
yes i did the same ... typed wrong before

and i removed the lines as well

---

### Post by merlinus on 2007-09-03
What does this show:

```

cat /boot/grub/device.map

```

-merlin

---

### Post by merlinus on 2007-09-03
Also, set a boot flag on your windows partition using gparted.

-merlin

---

### Post by muski on 2007-09-03
:~$ cat /boot/grub/device.map
      (hd0)   /dev/hda

and how am i supposed to set the boot flag ?
should i install gparted ? 
i havent heard of it before


installed gparted but when i run it it prompts me to login as root as gparted can be 
"weapon of mass destruction" :D
hence i shall wait for you to tell me exactly what to do with it

---

### Post by merlinus on 2007-09-03
Open gparted, right-click on your windows partition, select manage flags, and tick the boot box.  

-merlin

---

### Post by muski on 2007-09-03
did that
restarted
tried to log in to windows 

still
error 12 invalid device requested.

as you said i had changed menu.lst as below ...
> 
title           Other operating systems:
root
title              Windows XP
root               (hd0,4)
savedefault
makeactive
chainloader        +1


---

### Post by meierfra on 2007-09-03
Windows  need to be installed  on a primary partition  in order to boot ( that is  a partition which is not inside an extended partition). I don't see any good way to fix that problem other than  reinstalling windows on a new primary partition. But maybe somebody else has a good idea.

---

### Post by merlinus on 2007-09-03
Yes, meierfra, I was afraid of that too, but tried everything I could to save muski from having to re-partition and re-install.

At this point, though, it looks like the only option.

-merlin

---

### Post by muski on 2007-09-03
oh all right then ... i'll go ahead and reinstall ..
by the way
as i have 3 NTFS drives on my hard disk (one having the old windows) ... 
if i reformat the drive which had windows ... install fresh windows on that drive ... will i be able to access the other two drives using windows ... i have some important stuff in one of the drives ..

anyway 
thanks a lot guys

---

### Post by merlinus on 2007-09-04
Are you talking about partitions or hdds?

In any event, you will have to re-partition before installing xp.  My suggestion is to back up data before doing anything.

-merlin

---

### Post by muski on 2007-09-04
> **merlinus said:**
> Are you talking about partitions or hdds?

In any event, you will have to re-partition before installing xp.  My suggestion is to back up data before doing anything.

-merlin


just partitions on a single hard disk 
anyway as you suggested i will first create backup
thanks

---

### Post by muski on 2007-09-04
also 

as meierfra said 
> Windows need to be installed on a primary partition in order to boot ( that is a partition which is not inside an extended partition). I don't see any good way to fix that problem other than reinstalling windows on a new primary partition. But maybe somebody else has a good idea.

since my hd0 is now linux (primary partition)
i should install windows on the partition i have linux on adn then reinstall ubuntu or
i can install windows on some other partition and while formatting change that partition to hd0.
if the latter is possible please tell me how to do so .
thanks

---

### Post by meierfra on 2007-09-04
You don't   need to reinstall ubuntu.  Indeed, you should not install windows on the current ubuntu partition, since that is still inside the extended partition.  Do this with gparted:

Delete the windows partition hda5.
Shrink the extended partition hda2, leaving the unallocated space before  hda2.

Then use your windows disk to reinstall Windows on the unallocated space.
After you did this you should be able to boot into windows, but not into ubuntu.
To  be able to boot into ubuntu again, you will have to reinstall Grub and edit menu.lst.  If you need help with that, come back here after you reinstalled windows.

---

