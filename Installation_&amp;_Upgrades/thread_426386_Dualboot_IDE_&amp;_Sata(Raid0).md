---
title: "Dualboot IDE &amp; Sata(Raid0)"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by acidreign on 2007-04-28
Hello, linux community! This is my first post.

I am having an issue booting into windows from grub, ubuntu boots just fine.

I have windows installed on two Sata drives in Raid 0 partitioned into one drive for the OS and one for files. I unplugged those drives and installed feisty on an ide drive.

My bios is set to boot from ide then sata which works fine. If I want to get into windows I can just change the bios boot order and windows will boot up perfectly. But my goal here is the illusive dual boot!

Oh yea, the problem... so I boot up and Grub gives me my OS options. If I choose WinXP it says "Starting up..." and just hangs, nothing happens. If i choose Ubuntu it boots up into linux with no problems.

Here is the end of my menu.lst
```
title           Kubuntu 7.07 Feisty Fawn
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=f0b14ccb-71b8-44cd-9ed6-c906ff969e51 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Microsoft Windows XP Professional
rootnoverify    (hd1,0)
map             (hd0,0) (hd1,0)
map             (hd1,0) (hd0,0)
savedefault
makeactive
chainloader     +1
```

I have tried changing "rootnoverify" to just "root" with no difference.

Here is the output from fdisk -l
```
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x43ad of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       77825   573930157+   f  W95 Ext'd (LBA)
/dev/sda5   ?      194956       14497   697946110+  14  Hidden FAT16 <32M

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9352    75119908+  83  Linux
/dev/hda2            9353        9729     3028252+   5  Extended
/dev/hda5            9353        9729     3028221   82  Linux swap / Solaris
```

And here is the contents of my fstab file.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f0b14ccb-71b8-44cd-9ed6-c906ff969e51 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=2f72fd91-c60a-4972-8474-0148610401b4 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

I noticed there is no mention of my Sata drives in this file. Maybe that is part of my problem? I don't see why this should matter on boot though, Maybe I just dont know enough about how linux boots. 

I have wasted countless hours trying to get this to work. If someone could please help me figure out what is wrong I would be grateful.

---

### Post by acidreign on 2007-04-28
No one has WinXP in a raid configuration on SATA with Ubuntu on IDE??? Come on... someone help me out here!

---

### Post by bulldog on 2007-04-28
Hmmm,I know nothing about raid configs.
Your sata hdd's are not listed in fstab,because you disabled them when you installed ubuntu:) 
This has nothing to do with the boot procedure,however,fstab is used to mount partitions when you use ubuntu.

But as far as I know raid0 is all about speed,it writes your files on two disk at the same time.
GRUB only points to a partition and then it ends his work.
So the fault should be on the windows boot loader,because windows start to boot and stops loading for some reason.
It should be GRUB if you get any error message about not finding a partition,but that's not happening.

So I should take a look at the boot.ini file in the windows folder.

---

### Post by acidreign on 2007-04-28
Thanks for the reply! :) 

Here are the contents of my boot.ini file
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by bulldog on 2007-04-28
It's quite the same as mine :)  and I don't have a raid config.
It should be okay,because if you boot the sata hdd,it boots fine into windows.
So there should be something in the MBR of the windows disk which enables the raid,which is not seen if you use the grub menu.

But as mentioned before,this are just wild guesses,because I never used a raid config myself.

If you do a search on the forums 'raid 0 configuration' or something like that,I think you should find something useful,because I have not the knowledge to help you with this.:(

---

### Post by osxdude on 2007-04-28
Hey, I'm trying to do the same thing! The HDD  is currently copying it's contents to my comp's first HDD. The BIOS, however, does not support adding 2 HDDs to the boot list! Gaaaaaahhhh!

Sorry. Just had to. :)

---

### Post by chmod530 on 2007-04-28
I had a similiar problem, I found by booting from a windows cd, going into the repair console and doing fixboot and fixmbr solved the issue.  Think it killed grub, not sure, it was a while ago, but it worked and I could boot windows just fine.

---

### Post by acidreign on 2007-05-01
I can boot windows ok. There is no possible way that grub overwrote my MBR because my windows drive was disconnected during the Ubuntu install. 
They both boot fine when I select either drive as the boot drive from my bios. I just cant boot from the IDE(ubuntu) to the SATA(windows) using grub for some reason. 
The only thing I have left to try is modifying NTLDR to boot linux.

---

### Post by l0c0m0c0 on 2007-05-09
I'm in the same boat here.  I have XP on a sata raid0 config and ubuntu on a ide channel.  I can boot either one if i change it in bios but cannot get a good grub setup.

---

### Post by kjaggu on 2007-05-13
My friend is also facing a similar problem with two hard drives. He is now looking for a fresh install of both WinXP as well as Ubuntu 7.04.

Please help.

---

### Post by Sayonara on 2007-07-28
I am also having this problem.

The standard reply for "I want Ubuntu on IDE and Windows on SATA" seems to be that the GRUB entry for WinXP should be something like:

```
title	Microsoft Windows XP Professional
root	(hd1,0)
map	(hd1,hd0)
map	(hd0,hd1)
chainloader +1
```

I don't have a clue what it should be for SATA Raid0 though.

---

### Post by Sayonara on 2007-07-28
I have set mine as follows, and it works fine:

```
title	Microsoft Windows XP Professional 64-Bit Edition
map	(hd0) (hd1)
map	(hd1) (hd0)
rootnoverify (hd1,0)
chainloader +1
```

---

### Post by Jerubaal on 2007-07-30
I've had problems with exactly the same thing! I wondered whether the **map **lines should come before the **root **line, so I will try that and see what happens. 

My GRUB code is the 'standard reply' code & I have also tried the rootnoverify to no avail.  I have probably tried the makeactive line, but don't think that helped.

My error message is:
```
root (hd1,0)
filesystem type unknown, partition type 0x7
map (hd0, hd1)
```

Do I need *ntfs-3g* installed, or is that just for booting from the Windows bootloader?

---

