---
title: "[SOLVED] Grub error 22"
date: 2008-11-20
forum: Installation &amp; Upgrades
---

### Post by ep3w on 2008-11-20
I recently had to format the XP partition on my notebook which I was previously dual booting with 8.10. I knew this would over write grub, which is no problem.  Problem is when I boot a live CD to try to install grub here is what I get
```
grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub>
```
Here is my fdisk -l

```
omitting empty partition (5)

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8390    67392643+   7  HPFS/NTFS
/dev/sda2            8391        8772     3068415    b  W95 FAT32
/dev/sda3            8773        9729     7687102+   5  Extended
/dev/sda4            9603        9729     1020127+  82  Linux swap / Solaris
/dev/sda5            8773        9602     6666912   83  Linux

Disk /dev/sdb: 1021 MB, 1021312512 bytes
129 heads, 16 sectors/track, 966 cylinders
Units = cylinders of 2064 * 512 = 1056768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         967      997367+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(972, 128, 16) logical=(966, 57, 15)


```

Thanks for any help!

---

### Post by iponeverything on 2008-11-21
I think that there is an offset -- I don't know why grub is telling you 5.

Try using 4.

```
root (hd0,4)

```

---

### Post by ep3w on 2008-11-21
root (hd0,4) just give the error 17: cannot mount selected partition.

---

### Post by iponeverything on 2008-11-21
what's in your /boot/grub/menu.lst?

---

### Post by ep3w on 2008-11-21
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
# kopt=root=UUID=47ff67cd-5356-4d8a-90df-9b02b91710ed ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=47ff67cd-5356-4d8a-90df-9b02b91710ed

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
# defoptions=splash vga=795

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		47ff67cd-5356-4d8a-90df-9b02b91710ed
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=47ff67cd-5356-4d8a-90df-9b02b91710ed ro splash vga=795 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		47ff67cd-5356-4d8a-90df-9b02b91710ed
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=47ff67cd-5356-4d8a-90df-9b02b91710ed ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		47ff67cd-5356-4d8a-90df-9b02b91710ed
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

It was working fine before the format, I am not sure what got changed that it wont let me reinstall.

---

### Post by iponeverything on 2008-11-21
That is truly strange. There appears is something funky with your partition table -- for grub to be so mixed up.  I would tread lightly in trying to resolve this.

---

### Post by caljohnsmith on 2008-11-21
> **ep3w said:**
> 
Here is my fdisk -l
```

[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8390    67392643+   7  HPFS/NTFS
/dev/sda2            8391        8772     3068415    b  W95 FAT32
/dev/sda3            8773        9729     7687102+   5  Extended
[COLOR="Red"]/dev/sda4            9603        9729     1020127+  82  Linux swap / Solaris[/COLOR]
/dev/sda5            8773        9602     6666912   83  Linux


```

That empty partition error above, along with the fact that sda4 is inside your extended partition when it is labeled as a primary partition, unfortunately means your HDD has a corrupt partition table; the fact that Grub chokes even when using the correct partition also reaffirms that. But the good news is that most likely you can use "testdisk" to fix your partition table, so from your Live CD, first make sure the Ubuntu Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
**If you are using Version 6.8:**
After starting testdisk with the above command, choose "no log", select HDD and "Proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "Proceed", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Search!" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partition table.
[B]
If you are using Version 6.9:[/B]
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "quick search", Y/N depending on if you have any Vista partitions, hit enter to continue, and select "Deeper Search" so it does a deeper search, which could take a while. Post the output of the screen that has the deep search results if you would like help recovering your partition table.

---

### Post by ep3w on 2008-11-21
I used Gparted to setup my partitions and have not touched them in a long time. I do know that for some reason, it would not allocate a small space to either partition, about 8mb or something like that.  When it would expand the partition, it would just leave it out.  I would assume that is the empty partition.  I am not sure this is what you were describing as the one partition inside the other, but I do think that the linux partition and swap are inside an extended partition.  I was going to try to post a screenshot of this in gparted but it looks like now when I boot the CD, it shows the whole disk unallocated.  I know this isn't right since I can still boot windows fine.  I will run testdisk now and post the results.Thanks!

---

### Post by ep3w on 2008-11-21
Here is the results of testdisk
Analyza:
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  8389 254 63  134785287
 2 P FAT32                 8390   0  1  8771 254 63    6136830 [NO NAME]
 3 E extended              8772   0  1  9728 254 63   15374205
 4 P Linux Swap            9602   0  1  9728 254 63    2040255
Space conflict between the following two partitions
 3 E extended              8772   0  1  9728 254 63   15374205
 4 P Linux Swap            9602   0  1  9728 254 63    2040255
   X extended              8772   0  2  9601 254 63   13333949
 5 L Linux                 8772   2  1  9601 254 63   13333824





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition





```

Search:
I am not sure if this is correct, I was away from the computer when it finished
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  8389 254 63  134785287
D FAT32 LBA             8390   0  1  8771 254 63    6136830 [NO NAME]
D Linux                 8565   2  1  9521 254 63   15374079
D Linux                 8772   2  1  9601 254 63   13333824
P Linux Swap            9602   0  1  9728 254 63    2040255








Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
NTFS, 69 GB / 64 GiB





```

---

### Post by caljohnsmith on 2008-11-21
> **ep3w said:**
> Here is the results of testdisk
Analyza:
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS              0   1  1  8389 254 63  134785287
 2 P FAT32                 8390   0  1  8771 254 63    6136830 [NO NAME]
 3 E extended              8772   0  1  9728 254 63   15374205
 4 P Linux Swap            9602   0  1  9728 254 63    2040255
[COLOR="Red"]Space conflict between the following two partitions[/COLOR]
 3 E extended              8772   0  1  9728 254 63   15374205
 4 P Linux Swap            9602   0  1  9728 254 63    2040255
   X extended              8772   0  2  9601 254 63   13333949
 5 L Linux                 8772   2  1  9601 254 63   13333824

```
The above error basically confirms that your swap partition is labeled as a primary partition and yet it resides inside of your extended partition, so there is a space conflict or overlapping partitions.
> **ep3w said:**
> 
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]*[/COLOR] HPFS - NTFS              0   1  1  8389 254 63  134785287
[COLOR="Red"]P[/COLOR] FAT32 LBA             8390   0  1  8771 254 63    6136830 [NO NAME]
[COLOR="Red"]D[/COLOR] Linux                 8565   2  1  9521 254 63   15374079
[COLOR="Red"]L[/COLOR] Linux                 8772   2  1  9601 254 63   13333824
[COLOR="Red"]P[/COLOR] Linux Swap            9602   0  1  9728 254 63    2040255


```
OK, on the screen showing the results of your deep scan as shown above, I would recommend marking your partitions as they are highlighted in red. Also, when you select the second linux partition above, press "P" to list the files in its root directory; if it shows a listing of your Ubuntu root directory without giving you an error, then that should be your true Ubuntu partition (not the one above it). That's just a helpful confirmation that you have the correct partition.

Once you have all the partitions marked as shown above, proceed to the next screen and choose "write". Then reboot, and please post the output of:
```
sudo fdisk -l
sudo parted /dev/sda print
```
If neither of those commands return an error, then you should be able to do the Grub commands that you have in your first post; the "find" command should return (hd0,4) this time. Let me know how it goes or if you run into problems. :)

---

### Post by ep3w on 2008-11-21
Thanks that worked perfectly! So just for my understanding, what happened was somehow the types of partitions got changed so grub wouldn't read it, or just read it offset? And changing the letters in testdisk just changed the type to primary, for example and this helped grub to read it in the correct way? Thanks again for the help!

---

### Post by caljohnsmith on 2008-11-21
> **ep3w said:**
> Thanks that worked perfectly! So just for my understanding, what happened was somehow the types of partitions got changed so grub wouldn't read it, or just read it offset? And changing the letters in testdisk just changed the type to primary, for example and this helped grub to read it in the correct way? Thanks again for the help!
That's great news it worked. I don't know what caused your partition table to become corrupted, but as you can see, testdisk can usually sort things out (thankfully). Somehow your extended partition swallowed your primary swap partition, so the swap partition was inside of your extended partition when it shouldn't have been. Testdisk just rebuilt your partition table to correctly show that the primary swap partition is outside of the extended partition like it should be. Anyway, cheers and have fun with Ubuntu. :)

---

