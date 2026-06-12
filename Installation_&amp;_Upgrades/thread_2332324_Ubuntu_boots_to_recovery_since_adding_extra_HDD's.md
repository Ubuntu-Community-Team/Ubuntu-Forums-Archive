---
title: "Ubuntu boots to recovery since adding extra HDD's"
date: 2016-07-30
forum: Installation &amp; Upgrades
---

### Post by extrobe on 2016-07-30
Hi, still pretty new to Ubuntu, so please go easy on me :)

I've setup a NAS server on Ubuntu 16.x in my HP Microserver

Everything working well, until I added a couple of extra drives to the 4 bays

Now, it boots into recovery mode, saying it can't find an ext4 partition on sdc

From what I can determine, Grub is expecting the install to exist on sdc, but where I've added the extra drives, by boot drive has been relegated to sde
(If I take the new drives out, I can boot to the install no problem)

From what I've read, I think that I need to 'install' grub to sde - but first need to get recovery to boot to the system (as of course sde doesn't exist when I take the drives out)

So, within Recovery, I've install grub, and I'm following some 'recovery' steps...
```
grub> set root=(hd4,1)
grub> set prefix=(hd4,1)/boot/grub
grub> insmod normal
grub> normal

```
But not sure if I'm on the right track or if I'm at risk of nuking my install.
Currently, I'm 'running' the first command above, and it's been on 'Probing Devices to guess BIOS drives.' for a good 1.5hr, so not sure if it's actually progressing or if I should cancel / if that'll make things worse. (It does say it will take a long time, but not sure how long is too long!)

Hope that all makes sense!

---

### Post by Bashing-om on 2016-07-30
extrobe;  Humm ...

Sounds to me like you would be better served to use UUIds to identify what partitions the system is to mount. I bet you are using the block device ID ( sdXY ) .

In any event, show us what is now set to be mounted at startup:
```

cat /etc/fstab

```
And now to identify the related UUIDs:
show us :
```

sudo blkid -c /dev/null -o list

```

With the thought that if we use UUIDs, grub will then be happy .. and the system will correctly identify what is where .

[INDENT][INDENT]it could be a
[INDENT][INDENT][INDENT]a good thought
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by extrobe on 2016-07-30
Yes, I was reading about UUIDs - and they certainly sounds like what I should be using!

here are my outputs...

/etc/fstab:
```

/dev/mapper/BAST--vg-root     /     ext4     errors=remount-ro     0     1
UUID=4a014538-3b03-4aa8-a72d-507d96dd0476     /boot     ext2     defaults     0
 # /boot was on /dev/sdb1 during installation
/dev/mapper/BAST--vg--swap_1     none     wsap     sw     0     0
/dev/sda1     /datamounts/personal     ext3     defaults     0     2
/dev/sdb1     /datamounts/media     ext3     defaults     0     2
```

blkid -c /dev/null -o list
```

/dev/sda1                       (not mounted)
/dev/sdb1                       (not mounted)
/dev/sdc1     ext3              (not mounted)       c3d26dcd-1ba1-4bbd-aa79-9135a8330fc0
/dev/sdd1     ext3              (not mounted)       21342c32-2b65-4d98-9864-039e4ae3d5de
/dev/sde1     ext2              /boot               4a014538-3b03-4aa8-a72d-507d96dd0476
/dev/sde5     LVM2_member       (in use)            mDpq2H-yF4u-oGag-bjzu-XnBH-cVFY-ymo34


/dev/mapper/BAST--vg-root       ext4     /          954adde0-3c74-40dc-b77b-dffe79e0d8ed
/dev/mapper/BAST--vg-swap_1     swap     [SWAP]     f4f31080-6657-4b58-9838-1fed6915ca4f
```

---

### Post by Bashing-om on 2016-07-30
extrobe; Welp. yeah .....

We are on the right path ...The block IDs (sdXY) can change depending on when the system recogizes the devise(s) and assigns the identifiers .

Look, I know nothing about LVM .. so I am very hesitant here to offer any further advise .. than what I have as my fstab file as a reference to what you "may" want to set up;
```

sysop@1404mini:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=29a6fc4f-ff12-4cac-8eb1-e98e50f1107f /home           ext4    defaults        0       2
# /var was on /dev/sda8 during installation
UUID=136af805-5758-4880-acc4-0e1d35e2c266 /var            ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=192a4783-56fa-4fd0-a62f-c45a14c08482 none            swap    sw              0       0
#/moving /tmp to ram 27may13
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0

sysop@1404mini:

```

See also now what :
```

sudo blkid

```
reveals about the unmounted partitions that you do want to mount .

Here is why grub is screaming ,, and dropping to recovery :
> 
UUID=4a014538-3b03-4aa8-a72d-507d96dd0476

that UUID belongs to the /boot partition, and NOT root .
We need to get the root partition identified and mounted .. that too is where many boot files are located .
verify what " /dev/mapper/BAST--vg-root " is ..

As said I know Nothing about LVM .. can not help here much .

[INDENT][INDENT]if I know better
[INDENT][INDENT][INDENT]I would do better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by extrobe on 2016-07-30
Bugger - I seem to have made things worse!

From what I'd read elsewhere, I thought I could mount sde1, then install did grub-install /dev/sde, but not get an error saying it can't mount the partition - so can't get in at all :(

I'm trying out some of the recovery options on install disk - but hasn't got me anywhere so far :(

---

### Post by Bashing-om on 2016-07-30
extrobe; Hey ...

I do feel for you ...
If this were a standard install ..one could mount the root partition form the live environment in a straight forward manner .. and edit any file one needed to , I am sure there is also a way in your LVM case .. But I do not know the howto .

Hang in here .. wait for someone else who has the experience to advise on mounting the installed /root partition and making the edits .

[INDENT]keep on mind
[INDENT][INDENT][INDENT]this is linux
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by extrobe on 2016-07-30
Thanks - I don't think I've done anything 'special' with the install - disks 1-4 are on a SAS controller + 1 disk on AHCI controller (this is the drive I'm trying to boot from)

Other than that, it should be a pretty standard setup

I think the LVM partition showing up is just the recovery partition rather than an actual part of my system - but as you'll have gathered, I'm not expert!

---

### Post by Bashing-om on 2016-07-30
extrobe; Well ....

As a thought .. show us what we are working with ,, so we do know what we are working toward.

From the live installer .. post back the outputs of terminal commands:
```

sudo parted -l
sudo fdisk -lu

```

Be aware:
> 
/dev/mapper/BAST--vg-root     /     ext4     errors=remount-ro     0     1

says this is not a standard install . I do look forward to anything that adds to my store of knowledge.

[INDENT][INDENT]this too
[INDENT][INDENT][INDENT]can be a real learning experience
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by extrobe on 2016-07-30
Ok, here goes (parted first - sda in the install usb)

```

Model: Sandisk Cruzer
Disk /dev/sda: 4005MB
Partition Table: msdos
Number    Start    End    Size    Type    File system    Flags 
1    1049kb    4005MB    4003MB    primary    fat32        boot, bla


Model: ATA ST3000 (scsi)
Disk /dev/sdb: 3001GB
Partition Table: msdos
Number    Start    End    Size    Type    File system    Flags
1    32.8kb    375GB    375GB    primary            boot


Model: ATA ST3000 (scsi)
Disk /dev/sdc: 3001GB
Partition Table: msdos
Number    Start    End    Size    Type    File system    Flags
1    32.8kb    375GB    375GB    primary            boot


Model: ST2000 (scsi)
Disk /dev/sdd: 2000GB
Partition Table: gpt
Partition Table: msdos
Number    Start    End    Size    File system    Flags
1    1049kb    2000GB    2000GB    ext3


Model: ATA WDC (scsi)
Disk /dev/sde: 8002GB
Partition Table: gpt
Number    Start    End    Size    Type    File system    Flags
1    1048k    8002GB    8002GB    ext3            msftdata


Model: ATA Sandisk (scsi)
Disk /dev/sdf: 128GB
Partition Table: msdos
Number    Start    End    Size    Type    File system    Flags
1    1049kb    512MB    511MB    primary    ext2        boot
2    513MB    128GB    128GB    extended
5    523MB    128MB    logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/BAST--vg-swap_1: 4257MB
Partition Table: loop
Number    Start    End    Size    Type    File system    Flags
1    0.00    4257MB    4257MB        linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/BAST--vg-root: 123GB
Partition Table: loop
Number    Start    End    Size    Type    File system    Flags
1    0.00    123GB    123GB    ext4

```

for fdisk - are there any specific pieces to pull out? it's 100's of lines to type out :)

---

### Post by Bashing-om on 2016-07-30
extrobe; Curiouser and curiouser ....

Alla the time:
> 

Model: ST2000 (scsi)
Disk /dev/sdd: 2000GB
Partition Table: gpt
Partition Table: msdos
Number    Start    End    Size    File system    Flags
1    1049kb    2000GB    2000GB    ext3


How do we wind up with 2 partition tables ?? and would they not conflict ? Is this even doable ???

as to fdisk:
> 
for fdisk - are there any specific pieces to pull out? it's 100's of lines to type out

Let's try and pipe the output to a pastebin site:
```

sudo fdisk -lu | nc termbin.com 9999

```
where the result is a URL back in terminal .. pass that complete link back here and we will access that file.

I still can not make out what is supposed to be the booting device.
We poke at it 

[INDENT][INDENT]some more
[/INDENT][/INDENT]

---

### Post by extrobe on 2016-07-30
> **Bashing-om said:**
> 

How do we wind up with 2 partition tables ?? and would they not conflict ? Is this even doable ???



Almost certainly a copy&paste error - just going to check to be sure though!

---

### Post by extrobe on 2016-07-30
That's affirmative on the copy & paste error - it's gpt, not msdos AND gpt

> **Bashing-om said:**
> 
Let's try and pipe the output to a pastebin site:
```

sudo fdisk -lu | nc termbin.com 9999

```
where the result is a URL back in terminal .. pass that complete link back here and we will access that file.[INDENT][INDENT]
[/INDENT]
[/INDENT]


Nice trick!!

fdisk output
[http://termbin.com/yx0n](http://termbin.com/yx0n)

If it makes things easier, happy to pull out the 'other' disks not required - once I'm up & running I can switch to UUID and then re-add them - no real data on them yet anyway.

---

### Post by Bashing-om on 2016-07-30
extrobe; Hey !

I am beginning to get an idea here of what is not going on ...

What we have here from the fdisk output .. is that ONLY 2 of the drives are linux file systems.
In mounting the other drives, will have to declare the file system type .. and in the mounting within fstab give the explicit authorizations.

And once more .. running into that wall of my ignorance . I do not do Windows anymore, will be for me a hunt and peck operation to determine the mount options to satisfy your use needs. We best have others best advise here too .

So yeah .. we pull all the drives leaving only what is needed for the system to boot . And once booted, we take it up from there .

[INDENT][INDENT]small steps
[INDENT][INDENT][INDENT]even on a long journey
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by extrobe on 2016-07-31
After many attempts at trying to fix, I conceded and did a full reinstall - I didn't have any data to lose, and I'd made 5 pages of notes getting everything setup, so was fairly quick (hours rather than days it took me first time round!) to get going.

Funnily enough, when I reinstalled, the default option was something like 'Use entire partition with LVM' - this time I changed it to 'Use entire partition'

Obviously, I want to try and prevent this happening again by ensuring I'm using UUID's


I've checked menu.lst file, and get this...

```

title           Ubuntu 16.04.1 LTS, kernel 4.4.0-31-generic
root            (hd0)
kernel          /boot/vmlinuz-4.4.0-31-generic root=UUID=0e14e0bf-ca92-4d4a-b03$
initrd          /boot/initrd.img-4.4.0-31-generic


title           Ubuntu 16.04.1 LTS, kernel 4.4.0-31-generic (recovery mode)
root            (hd0)
kernel          /boot/vmlinuz-4.4.0-31-generic root=UUID=0e14e0bf-ca92-4d4a-b03$
initrd          /boot/initrd.img-4.4.0-31-generic

```
 given it says root-UUID=xxxxx , does that mean it is already set to boot from UUID? Is there something else I should check as well?

Thanks for the help - it's appreciated!

---

### Post by Bashing-om on 2016-07-31
extrobe; Ho Kay ....

Let's take a look at what is now - after the re-install - set for mounting. That action is controlled in the /etc/fstab ( File System TABle ) file.
```

cat /etc/fstab

```

And now we consider what we want to add for mounting the devices at boottime . OR if you want, just to mount the devices as on-demand. 

And a warning:
> 
I've checked menu.lst file, and get

the term "menu.lst" indicates you are following some real old guide. That file has not been around for many years now as when the initiate system changed to upstart .. and in 16.04 that initiate system is now systemd.

As your additional drives are NTFS -non linux -, will be worth your while to have some idea of how you may want to mount them:
[http://ubuntuforums.org/showthread.php?t=2329830](http://ubuntuforums.org/showthread.php?t=2329830) <- examples of how to mount NTFS

This ain't no step for a stepper
[INDENT][INDENT]together we can
[/INDENT][/INDENT]

---

