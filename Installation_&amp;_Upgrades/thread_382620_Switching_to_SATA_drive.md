---
title: "Switching to SATA drive"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by freakzilla on 2007-03-12
I'd like to switch out my EIDE hard drive for a new SATA drive.

My system now is dual booting.  Both XP and Ubuntu are on the regular EIDE drive.  I also have a second EIDE for storage that i'm just leaving alone.  

At this point i've copied the EIDE drive to the SATA drive using a windows program HDClone.
I tried just unhooking the old drive but only XP boots.

With all drives connected "sudo fdisk -l" gives me:

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6350    51006343+   7  HPFS/NTFS
/dev/sda2            6351        6531     1453882+   f  W95 Ext'd (LBA)
/dev/sda3            6532        7596     8554612+  83  Linux
/dev/sda4            7597       14593    56203402+  83  Linux
/dev/sda5            6351        6531     1453851   82  Linux swap / Solaris

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6350    51006343+   7  HPFS/NTFS
/dev/hda2            6351        6531     1453882+   f  W95 Ext'd (LBA)
/dev/hda3            6532        7596     8554612+  83  Linux
/dev/hda4            7597       14593    56203402+  83  Linux
/dev/hda5            6351        6531     1453851   82  Linux swap / Solaris

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
16 heads, 63 sectors/track, 387621 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2      387621   195360480    f  W95 Ext'd (LBA)
/dev/hdb5               2      387621   195360448+   b  W95 FAT32

And my /etc/fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=985b83b2-2a8d-47c1-975f-2fa183a2cb1c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda4
UUID=ebc02610-433a-42ab-8f44-595a640a9431 /home           ext3    defaults        0       2
# /dev/hdb5
UUID=43E2-57DB  /media/storage  vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=70E0695FE0692C92 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=bc4dde1b-9ff9-4a5b-a60b-3f6b1164db4d none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

Please help me with what i thought would be a simple move

---

### Post by El_Matthews on 2007-03-12
Your new disk is called sda and in your fstab file you are still booting from the old hda. the problem is that you have to find the id first. get your UUID by running 'blkid'. modify the fstab file and reboot.

to modify the fstab file you can boot from the ubuntu cd.

---

### Post by dannyboy79 on 2007-03-12
is grub appearing? you need to change your fstab entries so that they no longer refer to hda but refer to sda. so make your fstab look like this. also, please show me what you device.map looks like which is contained within your /boot/grub folder. it probably only has the 1 or 2 drives mapped like this if you had the hdb drive there when you installed ubuntu.
hda = hd0
hdb = hd1

/dev/sda3 / ext3 defaults,errors=remount-ro 0 1
/dev/sda4 /home ext3 defaults 0 2
/dev/hdb5 /media/storage vfat defaults,utf8,umask=007,gid=46 0 1
/dev/sda1 /media/windows ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5 none swap sw 0 0

leave the proc entry and your cdrom entry the way they are. NOTE: it is ok to use either the UUID or the /dev/ entries and since i know what your dev entries are, we'll use that. otherwise you can find out what your new sata partitions UUID's are but I can't explain  it easily. then you'll want to add your hda drive back in later after you get your sda drive all set up. you can reformat it for storage space. are you sure hdclone works with ext3 partitions? also, did you rehook your system or program your bios so that sda is now the 1st hard drive to be booted? because this may also affect the root line within your menu.lst as well. please post that also, it's located next to your device.map file. i can help once you provide that info.

---

### Post by dannyboy79 on 2007-03-12
> **El_Matthews said:**
> Your new disk is called sda and in your fstab file you are still booting from the old hda. the problem is that you have to find the id first. get your UUID by running 'blkid'. modify the fstab file and reboot.

to modify the fstab file you can boot from the ubuntu cd.
you don't need to know the uuid, just use the dev location, it's a lot easier. but you can do what you like, you can read the man page on fstab, both will work just fine!

---

### Post by El_Matthews on 2007-03-12
> **dannyboy79 said:**
> you don't need to know the uuid, just use the dev location, it's a lot easier. but you can do what you like, you can read the man page on fstab, both will work just fine!


indeed, I checked it and it doesn't seem to be necessary, sorry. Just use /dev/sda, much easier.

---

### Post by freakzilla on 2007-03-12
Man you guys are fast at answering stuff.

My device.map reads:
(hd0)	/dev/hda
(hd1)	/dev/hdb

I tried resetting the boot order in bios to use the SATA drive,  I can get xp going but ubuntu kicks me into a command prompt after tying to load.

HDclone worked fine on the ext3 file system.

---

### Post by dannyboy79 on 2007-03-12
ok, well I am not sure what you mean by Ubuntu kicks you into a command prompt. You mean ubuntu does boot up but with no X-server? You need to be more specifc. You didn't post your menu.lst, how do you expect people to help you when you don't help them help you. I am being honest here, this is one of the most frustrating things, questions would be answered so much faster if people would just read the post, and ANSWER all the questions asked so that the helper can help them instead of having to re-ask stuff over and over. Now I know this is the only the 2nd time I am asking but I need to see your menu.lst to  help you. Please post the output of cat /boot/grub/menu.lst. thank you. OR if you don't want to do that, then simply change your device.map so that hda is changed to sda. so that it would be (hd0) /dev/sda. I am guessing your menu.lst calls out (hd0,0) for your kernel location as well as your root line, so this should fix it but if this doesn't than post everything that I am asking for and I can help.

---

### Post by freakzilla on 2007-03-12
Easy killer,  just missed the part about the menu.lst.  Your help is appreciated.  This stuff might be clear to you but it's over my head.  

The menu.lst reads:

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

By kicking me to a command prompt i meant that during my first attempt at copying the drive I cloned it to the sata and just unplugged the original EIDE drive.  If i try to boot to ubuntu and got this message:

/bin/sh: can't access tty; job control turn off
(initramfs)

---

### Post by dannyboy79 on 2007-03-12
ok, 1st things 1st.
with your sda drive and your hdb drive plugged in and your bios has the sda drive being the 1st hard drive it will boot to, does grub appear with a list of os's? we need to figure out first if your sda drive has grub loaded into it's mbr or not. i am not sure if hdclone copied the mbr of your old hda drive.  if grub appears and you're saying that when you pick the windows entry it boots but ubuntu doesn't then we need to change the entries in menu.lst as well as your device.map. every place in your menu.lst you see hda3, change it so that it says sda3. also change your device.map so that hda is changed to sda. so that it would be (hd0) /dev/sda. also, do the fstab changes I asked for above and let's try to boot ubuntu only after you do everything I have suggested. if it doesn't work, please let me know exactly what hard drives you had hooked up, what your bios setup is, what your device.map looks like, what your menu.lst looks like, and what your fstab looks like and most importantly, what was the error that showed up or did the grub menu not show up, etc etc.

---

### Post by freakzilla on 2007-03-12
Replaced all hda3 with sda3 in device.map and menu.lst.  Changed the fstab as recommeded and Bam, happy computer time.  Thanks for the help.  \\:D/

---

### Post by dannyboy79 on 2007-03-12
another one solved, i love it!!! i am glad to have helped you.

---

### Post by jonas99 on 2007-03-14
I'm having a related issue, with the dreaded "/bin/sh: Can't access tty; Job control turned off" message on boot.

I tried both a fresh install of Ubuntu and have moved a partition image from my previously functional IDE drive to my SATA drive (which is the ultimate goal) with the same result. BTW, I'm running an Asus P5WD2 Premium motherboard if that matters. I could really use some help with this if anyone has any ideas.

Output of 'fdisk -l':
```
Disk /dev/hde: 20.4 GB, 20490559488 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        2491    20008926    7  HPFS/NTFS

Disk /dev/sda: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4462    35840983+  83  Linux
/dev/sda2            4463       36481   257192617+   5  Extended
/dev/sda5            4463       35695   250879041   83  Linux
/dev/sda6           35696       36481     6313513+  82  Linux swap / Solaris
```

output of blkid:
```
/dev/hde1: TYPE="ntfs" 
/dev/sda1: UUID="2a2514d1-881b-424c-aa45-ea4748f448a0" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="e3d361c5-1da4-4894-95ec-b09b194f1926" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="f49890ef-97b4-4cea-935a-c380be890beb" TYPE="swap" 
```

contents of /etc/fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#/dev/sda1
UUID=2a2514d1-881b-424c-aa45-ea4748f448a0  /  ext3  defaults,error=remount-ro  0
 1
#/dev/sda5
UUID=e3d361c5-1da4-4894-95ec-b09b194f1926  /video   ext3   defaults,error=remoun
t-ro 0 2
#/dev/sda6
UUID=f49890ef-97b4-4cea-935a-c380be890beb  none  swap   sw 0 0
/dev/hdg         /media/cdrom0   udf,iso9660 user,noauto 0 0
/dev/hde1        /mnt/windows    ntfs   defaults,nls=utf8,umask=007,gid=46 0 1

```

contents of /boot/grub/menu.lst:
```

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=2a2514d1-881b-424c-aa45-ea4748f448a0 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=2a2514d1-881b-424c-aa45-ea4748f448a0 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=2a2514d1-881b-424c-aa45-ea4748f448a0 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=UUID=2a2514d1-881b-424c-aa45-ea4748f448a0 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by jonas99 on 2007-03-14
Oh, btw, switching to Ctl-Alt-F1 after arriving at the initramfs prompt shows the following message:
```
Starting up ...
ALERT! /dev/disk/by-uuid/2a2514d1-881b-424c-aa45-ea4748f448a0 does not exist. Dropping to a shell!
```

---

### Post by confused57 on 2007-03-14
I don't know if this will work or not, but you might be able to use the live cd to determine the new UUID's of your partitions:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
sudo vol_id -u /media/ubuntu
```

or you could change your kernel root entries & fstab to reflect root as /dev/sda1, instead of using UUID numbers.

```
kernel   /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
```

```
/dev/sda1 /  ext3  defaults,error=remount-ro  0  1
```

This site has some info you might find useful:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

