---
title: "Windows 8.1 disappeared from grub loader"
date: 2015-03-30
forum: Installation &amp; Upgrades
---

### Post by HappyPrime on 2015-03-30
Little bit of background: My desktop has two hard drives in it, one of which was completely taken over by Windows 8, the other which I installed ubuntu onto half of it some time ago. I switch between the two a lot. Today I had a shot at installing the new SteamOS on the remaining space on the second hard drive. All seemed to install well, however upon rebooting the Windows 8 option for the loader was missing.

Updating grub does nothing. Completely purging and reinstalling grub does nothing.

output of fdisk -l

```
[code]WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.




Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x0006a911


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   961136639   480567296   83  Linux
/dev/sdb2       961138686  1953523711   496192513    5  Extended
Partition 2 does not start on a physical sector boundary.
/dev/sdb5       961138688   976760831     7811072   82  Linux swap / Solaris
/dev/sdb6       976762880   996761599     9999360   83  Linux
/dev/sdb7       996763648  1016762367     9999360   83  Linux
/dev/sdb8      1016764416  1036763135     9999360   82  Linux swap / Solaris
/dev/sdb9      1036765184  1953523711   458379264   83  Linux
```
[/CODE]

----Windows should be on the sda partition

If I run gparted it shows only sda1 through 5, and an error on each one. For sda1 it says

```
[code]<i>Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          ece8e839-bd76-4600-baeb-f15871f531ad
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize
Filesystem flags:         signed_directory_hash 
Default mount options:    user_xattr acl
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              625856
Block count:              2499840
Reserved block count:     124992
Free blocks:              2422288
Free inodes:              625845
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      610
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         8128
Inode blocks per group:   508
Flex block group size:    16
Filesystem created:       Mon Mar 30 21:15:46 2015
Last mount time:          Mon Mar 30 21:15:55 2015
Last write time:          Mon Mar 30 21:15:55 2015
Mount count:              1
Maximum mount count:      -1
Last checked:             Mon Mar 30 21:15:46 2015
Check interval:           0 (<none>)
Lifetime writes:          131 MB
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:              256
Required extra isize:     28
Desired extra isize:      28
Journal inode:            8
Default directory hash:   half_md4
Directory Hash Seed:      5ed56b29-2381-46a8-af02-f5f9778c7fd1
Journal backup:           inode blocks</i>


<i>dumpe2fs 1.42.9 (4-Feb-2014)
dumpe2fs: Invalid argument while reading journal super block</i>


<i>Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package.
The following list of software packages is required for ext4 file system support: e2fsprogs v1.41+.</i>

```

for sda2 through 5 its says;

```
Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda2 is missing

```[/CODE]

Help would be appreciated. 
Keep in mind that though I am familiar using ubuntu, it has never been for very heavy stuff. I will probably need walkthroughs for most instructions.


EDIT:
Just noticed that a 511MB volume, corresponding to sda1, shows up in file explorer. Trying to open it gives me this error:

```
Error mounting /dev/sda1 at /media/<user>/ece8e839-bd76-4600-baeb-f15871f531ad: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/<user>/ece8e839-bd76-4600-baeb-f15871f531ad"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Don't know if thats helpful at all, but before all this I could see and open a volume from file explorer, and could navigate to all the files in my windows hard drive. I kept my music in there.

EDIT:
The file path I used to go through was: /media/<user>/F81A88611A881EAE/Users/...


I'm working on getting boot-repair going, but from what I understand it only affects linux partitions, so it may not be helpful? Will edit again when I've got that,

---

### Post by oldfred on 2015-03-30
Please use code tags. Easy to add in advanced editor with # icon.

Please post link to summary report from Boot-Repair. 
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

It cannot fix Windows specific issues as grub only boots a Working Windows.

But your entire configuration does not look correct. Windows with gpt partitioning on sda must be booting in UEFI mode. 
Also fdisk does not work on gpt partitioned drives. Use parted or gdisk.
But your sdb drive is MBR(msdos). Normally from MBR only systems installed in BIOS boot or CSM from UEFI will boot. But we have seen a few systems with Ubuntu on sdb with MBR, but a UEFI grub installed to the efi partition on sda. Summary report will show configuration.

If you then installed another system but in BIOS only boot, grub will not be able to boot any UEFI installs. UEFI & BIOS are not compatible and you have to dual boot by going into UEFI boot menu. And some system require you to turn on/off UEFI or CSM mode to match how system is installed.

---

### Post by HappyPrime on 2015-03-30
So I can't get a boot repair going, because I can't get a live ubuntu usb to load. The only thing that I am able to read as it is booting is " fast calibration failel" or somesuch, and then it goes to a blank screen.
And Ubuntu has disappeared from the loader, though I was able to get into it using recovery mode, and then restore the option.

I read somewhere that using a Windows 8 iso to run the autorepair might help, but though running apparently fine, that changed nothing. 

Have I completely screwed myself?

---

### Post by HappyPrime on 2015-03-30
So far from an ideal, but I was running out of time and I needed a working windows computer.
I just reinstalled everything from scratch.

I don't really want to mark this as solved though...it wasn't really a solution.

---

### Post by oldfred on 2015-03-30
If starting over be sure to partition the sdb drive as gpt and install in UEFI mode. Best to manually add your own efi partition first as Ubuntu wants to use the efi partition on sda with all installs. You can copy files to sdb after install.

These are older versions of Ubuntu, but procedure is the same.
 **Two Drive UEFI installs**
[http://ubuntuforums.org/showthread.php?t=2192378](http://ubuntuforums.org/showthread.php?t=2192378)
HP Envy 2 drive install i7 & 2 1TB drives
[http://ubuntuforums.org/showthread.php?t=2175877](http://ubuntuforums.org/showthread.php?t=2175877)
Samsung Series 7 laptop - Ubuntu UEFI install to sdc (ignore CSM sidetrack)
[http://ubuntuforums.org/showthread.php?t=2135459](http://ubuntuforums.org/showthread.php?t=2135459)
Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)

You must use Something Else to have options on partitions and locations.
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by HappyPrime on 2015-03-31
Thanks I will make sure to do so. Don't really know why it didn't last time, I was sure I had done that.

---

