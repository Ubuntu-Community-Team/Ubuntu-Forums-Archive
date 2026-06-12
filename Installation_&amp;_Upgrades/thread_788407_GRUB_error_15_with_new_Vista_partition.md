---
title: "GRUB error 15 with new Vista partition"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by r0t on 2008-05-09
Hello, I just installed Windows Vista and Ubuntu on my Dell XPS M1330, following a step by step guide on the web. Everything worked very nicely, until the next day when I tried to create a new partition in Vista to be used as a shared media drive. After that I'm stuck with a GRUB error 15-message at boot.

I am a Linux newbie, but I've been looking around the web, and found some of the relevant files on my harddrive using the Ubuntu Live CD.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        7839    62918572+   7  HPFS/NTFS
/dev/sda3            7840       30401   181229265    f  W95 Ext'd (LBA)
/dev/sda5            7840       11486    29294464+  83  Linux
/dev/sda6           11487       14525    24410736   83  Linux
/dev/sda7           14526       14890     2931831   82  Linux swap / Solaris
/dev/sda8           14891       30139   122485760    7  HPFS/NTFS
/dev/sda9           30140       30401     2104483+  dd  Unknown


And here is from my menu.lst:
default		0
timeout		10
color cyan/blue white/blue
### BEGIN AUTOMAGIC KERNELS LIST
## ## Start Default Options ##
# kopt=root=UUID=2515d410-5368-4877-a516-d6192e46ef95 ro
# crashdump=0
# groot=(hd0,5)
# alternative=false
# lockalternative=false
# defoptions=quiet splash
# lockold=false
# xenhopt=
# xenkopt=console=tty0
# altoptions=(recovery mode) single
# howmany=all
# memtest86=false
# updatedefaultentry=false
# savedefault=false
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2515d410-5368-4877-a516-d6192e46ef95 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Microsoft Windows XP Embedded
root		(hd0,4)
savedefault
makeactive
chainloader	+1

Any suggestions? Anything else I would need to post?

Thanks for any help!

---

### Post by Pumalite on 2008-05-09
This might help:
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)
According to your fdisk; sda5 is dedicated to Linux , not Windows.

---

### Post by r0t on 2008-05-09
No help, I'm afraid.

One thing occurred to me now: the only partition with a star in the boot-column is a windows-partition. Shouldn't there be a bootable linux-partition as well (the root-partition where the boot-directory is, I guess?)

And also, there's a strange Windows partition overlapping all of the Linux partition. Should that be there?

---

### Post by Pumalite on 2008-05-09
Post a screenshot of gparted.

---

### Post by r0t on 2008-05-09
[http://ubuntuforums.org/attachment.php?attachmentid=69406&stc=1&d=1210373609](http://ubuntuforums.org/attachment.php?attachmentid=69406&stc=1&d=1210373609)

Windows on sda2, Dell Mediadirect on sda9, ubuntu root on 5 and users home dir on 6. sda8 is the new partition that caused the problem.

---

### Post by r0t on 2008-05-09
So the numbers in menu.lst correspond somehow to sda1..9 I guess, and they are not correct not. What number for e.g. sda5 be then? (hd0,3) as in third item? (hd0,4) as in 5-1?

---

### Post by Pumalite on 2008-05-09
It might be that you use the Vista partitioner to create your new partition inside of an extended partition. I'd start over. Install Vista to the whole drive. 'Shrink' it with the Vista partitioner. Then use Gparted Live CD to partition your new unallocated space.Then install Ubuntu.

---

### Post by unutbu on 2008-05-09
According to [http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting](http://www.gnu.org/software/grub/manual/grub.html#Troubleshooting),
GRUB error 15 means
```
File not found
    This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.
```

It sounds like adding a new partition shifted the numbering, so I think your problem may be fixable by finding the the right pairs of numbers (x,y) to map "(hd0,x)" in menu.lst to the right partitions /dev/sday.

I don't know the right numbers because I'm not sure what number GRUB assigns to extended partitions, but here is a way you can find out for yourself:

(See [http://www.gnu.org/software/grub/manual/grub.html#Naming-convention](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention))

From the LiveCD, open a terminal and as root, run

```
grub
```

At the grub prompt type

```
root (<TAB><TAB>
```

GRUB uses TAB-completion. It will offer suggestions on how to finish the line you just typed. It will tell you which number corresponds to which filesystem type. Using this info, you should be able to find out what the correct x and y numbers are that map (hd0,x) to /dev/sday.

Quit grub. Now edit menu.lst, changing (hd0,x) as appropriate. Reboot.

---

### Post by r0t on 2008-05-09
.

---

### Post by r0t on 2008-05-10
Thanks for advicing. I'll be looking into this after the weekend!

---

### Post by r0t on 2008-05-12
I have now tried erasing both Vista and Dell MediaDirect OS, only leaving this:

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=2515d410-5368-4877-a516-d6192e46ef95 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet


I've tried substituting (hd0,5) for every other value, still getting the same error 15. (Using grub > root tab-tab gave no output at all, so that didn't help)

Is there anything else I could try, except for installing everything over again?

---

### Post by unutbu on 2008-05-12
At the grub prompt, did you type
```

root (<TAB><TAB>
```

with the parenthesis?

---

### Post by r0t on 2008-05-12
Sorry, just discovered that I had to do it as root. Now I get the following:

   Partition num: 0,  Filesystem type unknown, partition type 0xde
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 6,  Filesystem type unknown, partition type 0x82
   Partition num: 7,  Filesystem type unknown, partition type 0x7
   Partition num: 8,  Filesystem type unknown, partition type 0xdd

---

### Post by unutbu on 2008-05-12
The linux partitions are probably formatted with filesystem type ext3, but grub reports them as ext2fs. Don't worry -- that's normal. Since your first linux partition is the root partition, the root partition in grub's notation, looks to be (hd0,4).

```
Partition num: 0, Filesystem type unknown, partition type 0xde
Partition num: 1, Filesystem type unknown, partition type 0x7
Partition num: **4**, Filesystem **type is ext2fs**, partition type 0x83
Partition num: 5, Filesystem type is ext2fs, partition type 0x83
Partition num: 6, Filesystem type unknown, partition type 0x82
Partition num: 7, Filesystem type unknown, partition type 0x7
Partition num: 8, Filesystem type unknown, partition type 0xdd 
```

Boot the LiveCD. Open a terminal. (You might not need to prefix the commands with 'sudo' below, but I've included them just in case.)

```

sudo mkdir /media/disk
sudo mount /dev/sda5 /media/disk
gksudo gedit /media/disk/boot/grub/menu.lst
```

Above, the first command creates a directory -- a mount point -- for your hard drive. Note that when you boot the LiveCD, it creates its own little world which is in no way connected with your hard drive. You have to mount your hard drive partitions yourself if you want to access them. That's what the second command (`mount`) does.

Edit the boot stanza to:

```
title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,**4**)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=2515d410-5368-4877-a516-d6192e46ef95 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet
```

---

