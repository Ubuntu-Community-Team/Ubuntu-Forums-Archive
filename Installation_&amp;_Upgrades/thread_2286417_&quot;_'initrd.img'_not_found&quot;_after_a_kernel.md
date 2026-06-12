---
title: "&quot; 'initrd.img' not found&quot; after a kernel upgrade hang (&amp; a re-boot)"
date: 2015-07-12
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2015-07-12
So a few days ago I hit the software updater from my [COLOR=#ff0000]drive #2[/COLOR] (running Precise), and some kernel files were set to be upgraded, I think to 3.13.0-58.  

Then an Adobe Flash installer started to upgrade, but hung.  

And hung, and hung.  There seemed to be no way to exit gracefully from the software updater, or to get out of it at all.

***So I re-booted***.  But it seems ***the kernel upgrade process hadn't completed***, so when I next tried to log in, I selected my [COLOR=#ff0000]#2 drive[/COLOR] from the GRUB2 menu, and saw this:

```
error: file '/initrd.img' not found. Press any key to continue
```

Upon pressing any key, big BIOS-type lettering threw out a bunch of stuff, including:

```
kernel panic - not syncing: VFS: unable to mount root fs on unknown-block (0,0)

CPU: 1 PID: 1: Comm: swapper/0 Not tainted 3.13.0.57-generic #95~precise1-Ubuntu

Call Trace: dump_stack+0x46/0x58

panic+ [COLOR=#800000][numbers][/COLOR]
mount_block_root [COLOR=#800000][numbers][/COLOR]
mount_root[COLOR=#800000] [nos][/COLOR]
prepare_namespace [COLOR=#800000][nos][/COLOR]
kernel_init [COLOR=#800000][nos][/COLOR]
ret_from_fork [COLOR=#800000][nos][/COLOR]
rest_init [COLOR=#800000][nos][/COLOR] 
```

I have 3 drives.  [COLOR=#800080]Drive #1[/COLOR] runs Ubuntu-MATE 14.04;[COLOR=#ff0000] drive #2[/COLOR] runs Precise; and [COLOR=#800080]drive #3[/COLOR] is for storage.  I have BIOS booting, not EFI.

From drive #1, I can mount [COLOR=#ff0000]drive #2 [/COLOR]and access all of [COLOR=#ff0000]drive #2[/COLOR]'s files with no problems.   

[B][I]But I cannot now boot into drive #2.  
[/I][/B]
When I look in the root dir of my good drive (drive #1), I see this file:
```
initrd.img      19.2 MB Link to Raw disk image      application/x-raw-disk-image
```But when I look in the root dir of my "problem" drive ([COLOR=#ff0000]drive #2[/COLOR]), I see this:```
initrd.img      33 bytes link (broken)      inode/symlink
```[I][B]  My question:  How can I repair this to return to normal booting from my Precise drive (drive #2)?
[/B][/I]
Some command output:  ```
***[COLOR=#0000ff]sudo blkid[/COLOR]*** 
/dev/sda1: LABEL="UbuntuMATE-14.04" UUID="1742aa67-b8ce-45d2-94ca-05e3579f7e2f" TYPE="ext4" 
/dev/sda2: UUID="a88c33fd-88b5-43b2-92f6-457430d206fd" TYPE="swap" 
/dev/sdb1: LABEL="Ubuntu-12.04.5" UUID="4d4f7665-f633-4409-82f9-af43d0143823" TYPE="ext4" 
/dev/sdb2: UUID="106dae89-e837-4063-9f9c-bcdeae4b2d5a" TYPE="swap" 
/dev/sdc1: LABEL="WeirdBeard" UUID="c801726e-7a01-4963-989a-38482e6658cf" TYPE="ext4"
------------------------------------------------------------------------------------------

[COLOR=#0000cd]***sudo fdisk -l***[/COLOR]
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3aec6e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1932552191   966275072   83  Linux
/dev/sda2      1932552192  1953525167    10486488   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b03b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1932554239   966276096   83  Linux
/dev/sdb2      1932554240  1953525167    10485464   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41031e20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1953523711   976760832   83  Linux
---------------------------------------------------------------------------------


[COLOR=#0000ff]***sudo xxd -l 2 -p /dev/sda        ***[/COLOR]<-- Replacing "sda" with "sdb" here (& just below) gives the same output. 
eb63

[COLOR=#0000ff]***sudo xxd -s 1049 -l 2 -p /dev/sda***[/COLOR] 
ffff

```

Boot Info Script output is here:[URL="http://paste.ubuntu.com/11865186/plain/"]
[/URL][http://paste.ubuntu.com/11865226/](http://paste.ubuntu.com/11865226/)

Thanks loads for any help.

---

### Post by dino99 on 2015-07-12
if you have at least two kernels installed, boot with the working one, otherwise goto the 'recovery' process, then fix that Adobe trouble:

[http://askubuntu.com/questions/603295/how-to-fix-dpkg-error-2](http://askubuntu.com/questions/603295/how-to-fix-dpkg-error-2)

---

### Post by watchpocket on 2015-07-12
> if you have at least two kernels installed, boot with the working one

Well, I need to be able to boot from both drives.

***Would it be a mistake to simply copy the initrd.img file from my Trusty root directory (on drive #1) to my Precise root dir (on drive #2), where it appears there is no working initrd.img file?***

> goto the 'recovery' process

I did boot into recovery mode on drive 2, if that's what you mean. That returned roughly the same "BIOS"-looking big-print info I quoted above.

Also I ran these three commands from the Trusty disk:
```
sudo fsck /media/rj/Ubuntu-12.04.5
sudo e2fsck -b 8193 /media/rj/Ubuntu-12.04.5
sudo e2fsck -b 32768 /media/rj/Ubuntu-12.04.5
```

All three returned this:
```
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Is a directory while trying to open /media/rj/Ubuntu-12.04.5

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

I've forgotten how to run fsck on drive 2 if that drive isn't mounted.   Can that only be done from a USB stick?

---

### Post by watchpocket on 2015-07-12
Can an initrd.img file be copied from one OS to a previous one?  Is this a bad idea? Are they specific to the OS?  

My Trusty has kernal version 3.13.0-58.  My precise has -57.


> then fix that Adobe trouble

To do that I can just go into synaptic and remove flashplugin-installer and re-install it, no?

---

### Post by watchpocket on 2015-07-13
For anyone else having **problems with a corrupted or broken initrd.img**, the most **useful info** I've found so far is here:

[http://www.thegeekstuff.com/2009/07/how-to-view-modify-and-recreate-initrd-img/](http://www.thegeekstuff.com/2009/07/how-to-view-modify-and-recreate-initrd-img/)

---

