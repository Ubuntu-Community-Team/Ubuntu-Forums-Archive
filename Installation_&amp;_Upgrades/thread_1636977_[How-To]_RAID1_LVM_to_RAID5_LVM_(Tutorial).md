---
title: "[How-To] RAID1 LVM to RAID5 LVM (Tutorial)"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by SaturnusDJ on 2010-12-03
Information from [http://ubuntuforums.org/showthread.php?t=990045](http://ubuntuforums.org/showthread.php?t=990045) that uses information from [http://scottwallace.posterous.com/tag/mdadm](http://scottwallace.posterous.com/tag/mdadm) that uses information from [http://www.n8gray.org/blog/2006/09/05/stupid-raid-tricks-with-evms-and-mdadm/](http://www.n8gray.org/blog/2006/09/05/stupid-raid-tricks-with-evms-and-mdadm/) is used for this tutorial. :p
But...I did not like the steps saying '*to destroy all configurationfiles and building new*' so I find out a solution.

This worked twice for me with Ubuntu 10.04 setups.

**Before proceeding:**
- Don't be stupid, backup important data first.
- Don't kill commands used in this tutorial.
- Do not proceed with this tutorial if you can't prevent /boot from becoming RAID5 also. This may kill GRUB.
- Try to understand what you are doing. Preventing and fixing mistakes is much easier than.
- Run all commands as superuser/root.
- Everything shown in code boxes are commands, no output information will be there.
- Use the "cat /proc/mdstat" command any moment to see the RAID status.

[SIZE=4]**RAID1 with LVM --> RAID5 with LVM**[/SIZE]

_In this tutorial:_
RAID1 array: "/dev/mdx," containing: "/dev/sda" and "/dev/sdb."
We will add "/dev/sdc" to create a RAID5 setup.

[SIZE=3]**Part 1 - Converting the RAID1 array to a RAID5 array**[/SIZE]
_Step 1_
Copy partition structures from the current disks to the new disk:
```
dd if=/dev/sda of=/dev/sdc count=1 bs=512
sfdisk -d /dev/sda > sda.sf
sfdisk --force /dev/sdc < sda.sf
```
Reload the disk.
```
partprobe /dev/sdc
```
Check if the partition structure is the same as on the disk in the RAID1 setup. For example, compare these two outputs:
```
fdisk -l /dev/sda
fdisk -l /dev/sdc
```

_Step 2_
Switch to Live CD. Preferable the same version of the same distro you have installed. (Unless, you know how to stop an array being used or your array isn't in use*. Tn that case skip this step).
Install mdadm.
```
apt-get install mdadm
```
Find arrays.
```
partprobe
```
_Step 3_
Stop the RAID1 array.
```
mdadm --stop /dev/mdx
```

Overwrite meta data and combine one old disk with the new disk, starting with the old one.
```
mdadm --create /dev/mdx --level=5 -n 2 /dev/sda /dev/sdc
```
Recovery will start, wait until it is finished. 

Check the process.
```
cat /proc/mdstat
```
Afterwards you should have a degraded RAID5 setup.
'(UU_)' is indicating this.

Add the third disk. (This is the second one of the old RAID1 setup.)
```
mdadm --add /dev/mdx /dev/sdb
```

Tell the array to not use it as spare.
```
mdadm --grow /dev/mdx --raid-disks=3 --backup-file=/mnt/tmp/raid1-5.backup.file
```
Reshaping will start. This takes more time than recovery. (The backup argument apparently is a option in case grow fails.)
Wait until it is done.

[SIZE=3]**Part 2 - Editing the configuration data**[/SIZE]
_Step 4_
The LVM part. Now we've got a RAID5 setup but the OS inside the LVM does not know this. We will get inside LVM. (If you do not use the Live CD method, skip this step.)
Install LVM2.**
```
apt-get install lvm2
partprobe
```

Find LVM stuff.
```
vgscan
```

Activate the Volume Group(s).
```
vgchange -ay
```

Now you also know where they are. Mount the one containing the operating system.
```
mount /dev/mapper/OS-LV /mnt/OS
```

_Step 5_
Get the new array information.
```
mdadm --detail --scan
```
Only catch the lines that talk about the array we are working with.
It looks something like this:
> ARRAY /dev/mdx level=raid5 num-devices=3 metadata=00.90 UUID=a5241471:51b928ef:92045851:c654ebbf

Put this into the /etc/mdadm/mdadm.conf of the operating system. This would be /mnt/OS/etc/mdadm/mdadm.conf in this tutorial when using the Live CD method.
Be sure to replace the correct old information talking about a raid1 array and save.

This actually means nothing yet. The info needs to go into the boot image.

_Step 6_
(Non Live CD method users want to skip this step also.)
Chroot to the LV.
```
chroot /mnt/OS
```
Specific commands that have kind of relative paths in it will now work like as if you are booted into the OS-LV we mounted earlier.

_Step 7_
Update the boot image.
```
update-initramfs -u
```

Reboot to OS.

You should get into the OS like it was the case with the raid1 array.

Check if everything is fine.
```
cat /proc/mdstat
```
You should have a double amount of blocks now.

[SIZE=3]**Part 3 - Assigning the new bits**[/SIZE]
_Step 8_
Give the new space to the physical volume.
```
pvresize /dev/mdx
```
This won't take much time.

Check if it is there.
```
vgdisplay
```
Look at the line saying '*Free PE / Size*.'

Give it to members of the group, for this tutorial let's say /home is in a group called 'home-dirs' and needs to get extended with 500GB.
```
lvextend -L+500G /dev/mapper/home-dirs
```
[SIZE="1"]See manuals for other kinds of extend commands.[/SIZE]
This could take some time.

Check if they got it.
```
lvdisplay
```
Look at the line saying '*LV Size*.'

Finally, resize the filesystem so the space becomes useable
```
resize2fs /dev/mapper/home-dirs
```
This takes some time also but less than the previous operation.

Check out your new space.
```
df -h
```

Done! :)

____________________________________________________________________________________________________


[SIZE=1]
*My array broke right at this moment (this must have been coincidence) so I continued in the OS itself. However, the first successful attempt took place using a Live CD.
**I don't know for sure whether this 'partprobe' command is needed now. It won't harm anyways...
[/SIZE]

---

### Post by SaturnusDJ on 2013-01-30
Critical update, just before part 2:

```
mdadm --grow /dev/mdx --raid-disks=3 --backup-file=/mnt/raid1-5.backup.file
```

The location of the backup-file should be a place somewhere save. Placing the file at the array itself is not a good idea (however it worked for me).

Place the backup-file at an usb drive or hard disk. (Remember when using a live cd, saving in that environment just saves it to ram, if a power outage happens, it's gone.)

---

