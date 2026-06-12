---
title: "Windows won't boot after 8.04 install"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Platybuntu on 2008-04-25
Installed 8.04 Desktop (64 bit) Ubuntu a couple of hours ago using the (downloadable iso) 8.04 disk on a system with existing Windows MCE (2004) installation. Opted for dual boot installation with resizing of single 500 GB windows partition to accommodate Ubuntu (40%) and Windows (60%). Installation went without a hitch. Grub menu shows Windows MCE entry as last on GRUB list. Will boot to Ubuntu fine but not to Windows:
"A disk read error occurred. Press ctrl-alt-Del to restart". It has conitnued to do this after 3 consecutive attempts. Not sure where the conflict is. I have looked at a couple of similar threads and thought that printing extracts from the Grub Boot menu and the "fdisk -l" might be helpful. Results below. Any help would be greatly appreciated:


sudo fdisk -l

Disk identifier: 0x7648667a



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1       36308   291643978+   7  HPFS/NTFS

/dev/sda2           36309       60801   196740022+   5  Extended

/dev/sda5           36309       59803   188723556   83  Linux

/dev/sda6           59804       60801     8016403+  82  Linux swap / Solaris



Disk /dev/sdb: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xa40f2b38



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       60801   488384001    7  HPFS/NTFS



Disk /dev/sdc: 4089 MB, 4089445376 bytes

33 heads, 63 sectors/track, 3841 cylinders

Units = cylinders of 2079 * 512 = 1064448 bytes

Disk identifier: 0x00000000


sudo gedit/boot/grub/menu.lst

## default num

# Set the default entry to the entry number NUM. Numbering starts from 0, and

# the entry number 0 is the default default		4
if the command is not used.

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



## ## End Default Options ##



title		Ubuntu 8.04, kernel 2.6.24-16-generic

root		(hd0,4)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ca3170b-6708-4fa8-88ec-0dd1c088b6f5 ro quiet splash

initrd		/boot/initrd.img-2.6.24-16-generic

quiet



title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)

root		(hd0,4)

kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8ca3170b-6708-4fa8-88ec-0dd1c088b6f5 ro single

initrd		/boot/initrd.img-2.6.24-16-generic



title		Ubuntu 8.04, memtest86+

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

title		Windows XP Media Center Edition

root		(hd0,0)

savedefault

makeactive

chainloader	+1

---

### Post by forkd on 2008-04-25
I've had a similar issue in the past and, while it isn't all linux based, this is how I resolved the issue.

boot with the windows disk and fixmbr from a command prompt.  This will overwrite your mbr.  Now your machine should boot to windows only.  Now boot to the linux disk and reinstall grub which should auto-detect the settings.  

Hope this helps.

---

### Post by jedimasterk on 2008-04-25
This version needs to be pulled from the mirrors!!. To many problems, especially since it's a LTS version!!.

---

### Post by Bubba64 on 2008-04-25
> **jedimasterk said:**
> This version needs to be pulled from the mirrors!!. To many problems, especially since it's a LTS version!!.

You are more likely to see the problems posted here on on other forums, that is what their for. The majority of people have no problems so why would they post.

---

### Post by Platybuntu on 2008-04-25
Thanks forkd,

I appreciate your response. I'll give it a go and let you know how I get on. Must confess to being a bit new to the whole forum thing so took me the better part of a day after the even to even find these responses (to my original thread). As a result I've re-formatted/installed MCE (what a chore) to at least maintain an operative HTPC. I will however try the same thing using a 3 year old Acer laptop, using the 32 bit installation of 8.04 and Win XP. Once I gain some confidence that this dual boots succesfully will have another go on main PC but will take added precaution of using a different HDD.

Cheers & Thanks again

---

### Post by tetsuo-shima on 2008-04-29
> **Bubba64 said:**
> You are more likely to see the problems posted here on on other forums, that is what their for. The majority of people have no problems so why would they post.

I understand that this is a place where problems are more likely to appear. However, if you look at the number of page views of postings referring to GRUB problems and kernel problems on Hardy in the forums right now, that may be a difficult argument to make.

---

### Post by Slim Odds on 2008-04-29
> **jedimasterk said:**
> This version needs to be pulled from the mirrors!!. To many problems, especially since it's a LTS version!!.

Stability and "LONG TERM SUPPORT" have nothing to do with each other.

I get very tired of this particular comment.

Some people have issues. It's the same with every release.

---

