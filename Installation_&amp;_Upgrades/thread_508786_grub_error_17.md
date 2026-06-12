---
title: "grub error 17"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by stijngysemans on 2007-07-24
After installing Ubuntu on this pc, in dual boot with XP, it shows the following error: grub error 17. I already looked on the forum for a solution but nothing came up. hereby i give you the following information:

sudo fdisk -l

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2612    20980858+   7  HPFS/NTFS
/dev/hda2            4482       24792   163148107+   f  W95 Ext'd (LBA)
/dev/hda3            2613        4481    15012742+  83  Linux
/dev/hda5            4570       24792   162441216    7  HPFS/NTFS
/dev/hda6            4482        4569      706797   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 250 MB, 250609664 bytes
64 heads, 32 sectors/track, 239 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb4   *           1         239      244720    6  FAT16


```

and my menu.lst
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
# kopt=root=UUID=d42ddd95-4069-4ed8-896c-56171adb4bf3 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d42ddd95-4069-4ed8-896c-56171adb4bf3 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=d42ddd95-4069-4ed8-896c-56171adb4bf3 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

and my device map
```

(hd0)	/dev/hda
(hd1)	/dev/hdb

```

who can help me. thank you!!

---

### Post by Pumalite on 2007-07-24
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
If you scan down the page; there is a list of Grub errors with their possible fixes. Error 17 is one of them. I think ( not sure) it means 'File System not Found. If that'sthe case download the iso burn it as image to a CD and use it to find your system and fix your Grub

---

### Post by reckless2k2 on 2007-07-24
not sure but you might've kinda goofed up the location of the grub install. not sure. try to changing the boot partition to hda3 in fdisk. might work. won't hurt though either way. you can always change it back. other solution is to fixmbr windows and edit the boot.ini to add ubuntu. you can create the file from ubuntu and save it to the fat32 share.

---

### Post by meierfra on 2007-07-25
I would change all appearances of 

root (hd0,1) 

in the file menu.lst   to

root (hd0,2)

(According to your  fdisk information, your linux root partition seems to be hda3. This corresponds to (hd0,2).)

---

### Post by MQMike on 2007-07-25
Yep, what meierfra said.

We are assuming XP is on your hda1 (hd0, 0)
And Ubuntu is on hda3 (hd0, 2).

---

### Post by stijngysemans on 2007-07-26
The thing is, after the problem showed up, i changed it from hd0,2 to hd0,1 to see if that could solve the problem but it didn't.
to summerize: hd0,2 doesn't work either!

> 
try to changing the boot partition to hda3 in fdisk.

how do I do that? In general: the boot partition must be the one where grub is installed on? How can I see on wich partition grub is installed?

---

### Post by Gen2ly on 2007-07-26
no, Instead of stating UUID just try specifying your device ( i.e. /dev/hda3) in the kernel line.

---

### Post by Gremlinzzz on 2007-07-27
Error17 : "Invalid device requested"
This error is returned if a device string is recognizable but does not fall under the other device errors.

---

### Post by Pumalite on 2007-07-27
From Super Grub:

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by MQMike on 2007-07-27
XP was there first.
Then you installed Ubuntu.
It *should be just fine -- this is standard *
But, not, so:
Sounds like you did not have the installer put GRUB in the MBR?

Maybe you could try re-installing GRUB (in any case).

Ubuntu is on (hd0, 2), right?

In Ubuntu (Live CD if necessary),
Get a GRUB prompt byt typing at a Terminal,
sudo grub
Then at the grub> prompt, type each of these, pressing Enter after each one:

root (hd0, 2)
setup (hd0)
quit
$exit

close out all windows
re-boot to test it

---

### Post by MQMike on 2007-07-27
just fyi,

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

Bigpond, GRUB:   [http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

---

### Post by stijngysemans on 2007-08-02
> **MQMike said:**
> XP was there first.
Then you installed Ubuntu.
It *should be just fine -- this is standard *
But, not, so:
Sounds like you did not have the installer put GRUB in the MBR?

Maybe you could try re-installing GRUB (in any case).

Ubuntu is on (hd0, 2), right?

In Ubuntu (Live CD if necessary),
Get a GRUB prompt byt typing at a Terminal,
sudo grub
Then at the grub> prompt, type each of these, pressing Enter after each one:

root (hd0, 2)
setup (hd0)
quit
$exit

close out all windows
re-boot to test it

i tried it and i just keeps giving me the grub error 17!

---

### Post by MQMike on 2007-08-02
Confusing.

I notice from fdisk –l that you have two HDs?  Are you sure Linux is on the first HD, hd0?

In any case, let’s find out where those GRUB files are that we need:

Get a GRUB prompt (from a Live CD, sudo grub, as before), and type

grub>  find /boot/grub/stage1

That will return the location (hdx, y) of the GRUB files.  It is that value, (hdx, y), that you want put into the  root command:
grub>  root (hdx, y)
grub> setup (hd0)
grub> quit
$ exit

re-boot to test it.

And it is true that your menu.lst says Ubuntu is in (hd0, 1), but sudo fdisk –lu says (hd0, 2) ???
The find command may shed some light on all this.  The menu.lst should also use the same value (hdx, y) for Ubuntu that we get from find.

---

### Post by MQMike on 2007-08-02
thinking out loud . . .

I don't know much about partitioning, except I thought you only used an extended partition when you run out of primary partitions; that is, you can only have 4 primary partitions on a HD.  When you get 3 of them, then you make an extended partition, which counts as a primary, and withing the extended you can make logical partitions.  Etc.
But your sudo fdisk -lu is saying you have an extended partition as the second partition?
Anybody catch anything wrong on that?

---

### Post by merlinus on 2007-08-02
PMFJI, but...

sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2612    20980858+   7  HPFS/NTFS
/dev/hda2            4482       24792   163148107+   f  W95 Ext'd (LBA)
/dev/hda3            2613        4481    15012742+  83  Linux
/dev/hda5            4570       24792   162441216    7  HPFS/NTFS
/dev/hda6            4482        4569      706797   82  Linux swap / Solaris

Partition table entries are not in disk order

Something is incorrect here, because if hda2 is an extended
partition, then numbering afterwards would start at 5 and not at 3.

And looking at the block starts and ends, it would definitely
seem that linux is on the second partition, yet it is
listed as hda3.

-merlin

---

### Post by MQMike on 2007-08-02
merlinus, Yes.

If true, what can he do now?
Re-do the partitioning using GParted Live CD, wiping out everything from hda2 on out BUT being real careful not to touch Windows on hda1 -- do not reformat the Windows partition!

What do you think, any ideas for an Rx?

---

### Post by MQMike on 2007-08-02
sorry -- 

posting the obvious now:  GRUB may be getting confused by that parititioning scheme ( ? ).

---

### Post by merlinus on 2007-08-02
Post output of:

```

df -h
mount

```

-merlin

---

### Post by stijngysemans on 2007-08-02
first of all, the second "hard drive" is just an old zip drive

---

### Post by merlinus on 2007-08-02
OK.  What about those two commands?

-merlin

---

### Post by stijngysemans on 2007-08-02
the output of sudo grub -> find /boot/grub/stage1 is (hd0,2)

this is the output of 'df -h'
```

Filesystem            Size  Used Avail Use% Mounted on

tmpfs                 126M   33M   93M  27% /lib/modules/2.6.20-15-generic/volatile

tmpfs                 126M   33M   93M  27% /lib/modules/2.6.20-15-generic/volatile

varrun                126M  100K  125M   1% /var/run

varlock               126M     0  126M   0% /var/lock

udev                  126M  104K  125M   1% /dev

devshm                126M     0  126M   0% /dev/shm

tmpfs                 126M   12K  126M   1% /tmp

```

this is the output of 'mount'
```

proc on /proc type proc (rw)

sysfs on /sys type sysfs (rw)

tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)

tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)

/dev/bus/usb on /proc/bus/usb type none (rw,bind)

fusectl on /sys/fs/fuse/connections type fusectl (rw)

varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)

varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)

udev on /dev type tmpfs (rw,mode=0755)

devshm on /dev/shm type tmpfs (rw)

devpts on /dev/pts type devpts (rw,gid=5,mode=620)

tmpfs on /tmp type tmpfs (rw,nosuid,nodev)

binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

```

---

### Post by stijngysemans on 2007-08-02
My friend whose computer shows the error 17 told me the following:
at first, the computer had 2 partitions equally large in size: one with xp, one for data. because of lack of knowledge of the terminology, the data partition was formatted as extended.



a little try to represent that visually:

[________________xp________________|(________________data________________)] *the brackets show the "extendedness" of the second partition



some time ago, i wanted to enlarge the data partition, because 100 GB was way too much, even for xp. using partitionmagic, i shrinked the xp partition to 50 GB, thus creating a 150 GB data partition. no changes were made to the file systems, except from their size.



another attempt to visualize that:

[_______xp_______|(__________________________data________________________)]



a few weeks later xp started to act weird, so i decided to add ubuntu to the mix. i shrinked the 50 GB partition even more, and installed ubuntu on the freed space.



last visualisation:

[__xp___|ubuntu|s|(__________________________data________________________)] *s = linux swap





the result of this: the aforementioned grub error 17...

---

### Post by merlinus on 2007-08-02
Not those.  These:

```

df -h
mount

```

-merlin

---

### Post by meierfra on 2007-08-02
When do you get error 17? Booting into windows xp? ubuntu? both? Before the grub menu appears?

---

### Post by stijngysemans on 2007-08-03
> **merlinus said:**
> Not those.  These:

```

df -h
mount

```

-merlin
i've posted the output of those commands on the top of this page.

> **meierfra said:**
> When do you get error 17? Booting into windows xp? ubuntu? both? Before the grub menu appears?
When booting you should normally get a grub menu, we get this error.

---

### Post by stijngysemans on 2007-08-13
bump

---

### Post by MQMike on 2007-08-13
Not sure.  And I’m leaving all that partition output for the other guys here.

Did you do what meierfra recommended (Post #4)?  I.e.,
I would change all appearances of 
root (hd0,1) 
in the file menu.lst to
root (hd0,2)

(ie., edit, as root, /boot/grub/men.lst to do that, then File-Save, File-Quit.)

Then back to my Post #10:
Do it again:

In Ubuntu (Live CD if necessary),
Get a GRUB prompt byt typing at a Terminal,
sudo grub
Then at the grub> prompt, type each of these, pressing Enter after each one:

root (hd0, 2)
setup (hd0)
quit
$exit

close out all windows
re-boot to test it


Your Windows boot entry in /boot/grub/menu.lst looks ok, but if you wish to try rootnoverify (hd0,0) instead of root (hd0,0), you can.

It won't take long to do these things so we can rule them out.

Also, if you had a Super Grub Disk Live CD, it would be interesting to see if you could get Ubuntu to boot using ANY method.  But, first, please try this post here.

---

### Post by meierfra on 2007-08-13
Do this again 


> at the grub> prompt, type each of these, pressing  Enter after each one:

root (hd0, 2)
setup (hd0)
quit
exit


and post all the  output.

---

### Post by meierfra on 2007-08-13
Did you check out 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")
as suggested earlier? In particular,  did you try  change your bio settings:

[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

Sorry for all the questions, but its is tough to come up with solutions if we don't know what all you have tried.

---

### Post by stijngysemans on 2007-08-18
The problem was: the harddrive was too large to be correctly recognized by the bios. so grub didn't get loaded correctly. The exact error message, prompetd by Super Grub will I post later!
Thx for all the help. My friend is now working back on his windows. He says he's "sick of this ubuntu-story". :( In the future I can maybe guide him step by step through an ubuntu installation on his new laptop or desktop computer.

---

