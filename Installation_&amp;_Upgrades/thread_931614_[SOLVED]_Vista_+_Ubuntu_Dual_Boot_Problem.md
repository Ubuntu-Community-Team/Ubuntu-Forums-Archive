---
title: "[SOLVED] Vista + Ubuntu Dual Boot Problem"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by lyoshenka on 2008-09-27
Hey,

I had Windows Vista 64-bit installed on my computer and wanted to add Ubuntu (dual-boot setup). Unfortunately, I didn't read about Vista's issues before I repartitioned things, so I just used Gparted to resize and move everything around. I did not defragment Vista or use it's built-in resize tool. I didn't get any errors during installation and everything seemed to go well. Ubuntu now works fine. However, when I choose Vista from the GRUB menu, the computer promptly restarts. I have no idea why this happens? I think it has something to do with GRUB trying to load the windows bootloader and failing somehow. Does anyone get the same error and is there any way to fix this without reinstalling Vista (Vista was preinstalled on my comp. I erased the recovery partition and I don't have any Vista CDs. I did back up the old MBR and the recovery partition, but I'm hoping it doesn't come to trying to restore all that. I'm not even sure it's possible or how to do it).

I know the Windows files are still there because I can mount the NTFS partition in Ubuntu and use the files perfectly. I also don't think its an issue with my GRUB configuration (this seems to be the problem addressed in most Vista+Ubuntu dual boot threads) but I could be wrong.



Possibly helpful information:

/dev/sda2 : windows partition
/dev/sda3 : ubuntu partition
/dev/sda4 : currently empty. I was planning to use this for general data storage

```

$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5521f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38392       38913     4192965   82  Linux swap / Solaris
/dev/sda2   *           1       12814   102928423+   7  HPFS/NTFS
/dev/sda3           12815       15364    20482875   83  Linux
/dev/sda4           15365       38391   184964377+   7  HPFS/NTFS

```

```

$ sudo parted
GNU Parted 1.7.1
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 2      32.3kB  105GB  105GB   primary  ntfs         boot 
 3      105GB   126GB  21.0GB  primary  ext3              
 4      126GB   316GB  189GB   primary  ntfs              
 1      316GB   320GB  4294MB  primary  linux-swap  

```

```

$ cat /boot/grub/menu.lst

...

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d619af3a-d7d5-473d-ab91-f63107589ad1 ro splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=d619af3a-d7d5-473d-ab91-f63107589ad1 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
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

```

---

### Post by WWSmith36 on 2008-09-27
> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

You might want to change to
rootnoverify    (hd0,1)

---

### Post by caljohnsmith on 2008-09-27
Sounds like you're going to need a Vista Recovery CD, and since you don't have one, you can download one from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). Once you boot from that, try doing the "Vista Repair" option, and that most likely be all it takes to get Vista going again. If not, let me know what errors you get when you boot Vista from Grub after doing the repair.

---

### Post by lyoshenka on 2008-09-28
@ WWSmith36: Nope, that didn't change anything.

@ caljohnsmith: I'll try that tomorrow and hopefully it will work.

---

### Post by Mark Phelps on 2008-09-29
The only "tool" known to be able to resize a Vista OS partition without damaging it is the resize option inside Vista.  Gparted MIGHT be able to do that, but all too often, results in a corrupt NTFS partition in the process.

You will need to boot into Vista, using the recovery medium already linked in a previous post, and do a startup recovery.  

If that doesn't work, your only option will be to restore Vista to its original state, and repeat the process, this time, using the resize option in Vista to make room for Linux.

---

### Post by lyoshenka on 2008-09-29
In that case I must have gotten lucky. caljohnsmith's solution worked perfectly and both OSes work fine now.

Thanks everyone.

---

