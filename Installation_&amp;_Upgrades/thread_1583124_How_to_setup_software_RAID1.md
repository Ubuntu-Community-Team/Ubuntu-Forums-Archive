---
title: "How to setup software RAID1?"
date: 2010-09-27
forum: Installation &amp; Upgrades
---

### Post by tsunamikitsune on 2010-09-27
I recently set up an old desktop computer on my home network for use as a file server. I installed Ubuntu 10.04 Server on it and I'm slowly learning how to make it do what I want (I'm used to the GUI, so this is a bit of a jump for me).

My plans are to put two 1.5TB hard drives in the computer (there's already a 160GB with the OS installed) and put them in a RAID1 configuration. This, as I understand it, will write all data to both drives, creating two identical drives. I'll only have 1.5TB total space for backup, but if one of the hard drives die, I can replace it without losing any data.

Hopefully I understand all that correctly. Now, my questions are how to actually set a RAID configuration up. I don't have a controller or anything, assuming I could do it off the two SATA ports in the motherboard (the 160GB is IDE) in software RAID.

Once I have the two hard drives set up in RAID1, how do I allow the house to access the file storage? We're all on Windows 7 computers.

If one of the hard drives fail, how will I know? Can I set it up so I receive some sort of notification? Also, how does the replacement process work; can I just pop the broken drive out and put a similar one in? Do I need to readjust any settings after replacing one?

Sorry for all the questions and complete lack of having any idea what I'm doing, but I'm hoping I can make this work out the way I want it to and give my housemates a reliable method of file storage.

---

### Post by Fafler on 2010-09-27
Theres a command line program in Linux called mdadm that does just that. Or you could do it using the Disk Utility wizard. But basically, you just add the drives, make partitions, add them to a RAID, format it and mount it. If you choose the terminal way, i can guide you, but yo need to get the drives first.

Software RAID under Linux works very good and is in many cases faster than hardware RAID. And it's great for home use.

Once you have the RAID running, you'll install the samba server. A filesharing server for Linux.

The Linux software RAID is able to notify you by email or you could look in /proc/mdstat on a regular basis. I'll might write a notify-applet for gnome at some point, since i just had trouble with an array without knowing it. Afte a failure, you just add a new drive and tell the software to use it.

---

### Post by tsunamikitsune on 2010-09-27
Cool, thanks for the info. I actually just received both 1.5TB drives today (Newegg was crazy fast this time) and I'll probably attempt to set all this up when I get back from my class coming up in a half hour.

Since I'm on Ubuntu Server, the CLI is my only choice, so if you could give me a tutorial on how to do it that way, it would be greatly appreciated. :D

---

### Post by Fafler on 2010-09-27
Connect the drives. SATA is hotswap, so you can do that if you like.
```
dmesg | grep sd
```to get devicenames
```
sudo fdisk /dev/devicename
```Make a partition with n and just set it to maximum size. Press t and set type to fd and finally w to write the changes to disk. Repeat for both drives.

Now, use
```
blkid /dev/devicename
```to get the UUID of each partition. They are unique identifiers of that specific partition and i find them a good tool when using RAID because devicenames tend to change from time to time.
To create the array, do
```
mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/disk/by-uuid/replace-with-very-long-uuid /dev/disk/by-uuid/and-again-here
```
```
cat /proc/mdstat
```
To make sure it's rebuilding the array. A RAID 1 array should do that on creation.

Now i guess you should do
```
mdadm --describe --brief /dev/md0 > /etc/mdadm.conf
```
but i don't use mdadm.conf on my system, so it might be a bit different. Anyway, make a mount point where you want it and add a line to your fstab to mount it.
```
mkdir /mnt/raid
sudo nano /etc/fstab
```
The line you add should look like
```

/dev/md0 /mnt/raid ext4 defaults 0 0
```
Save and exit.
Make the filesystem and mount it with
```
mkfs.ext4 /dev/md0 -m 0
mount /mnt/raid
```

... and that should pretty much be it. Ask if you need anything.

---

### Post by tsunamikitsune on 2010-09-27
> **Fafler said:**
> Connect the drives. SATA is hotswap, so you can do that if you like.
```
dmesg | grep sd
```to get devicenames


Alright, hard drives are installed. When I run that command, I get this:

```

kit@WATCHSERVER:~$ dmesg | grep sd
[    0.739272] sd 0:0:1:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    0.739277] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.739644] sd 2:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    0.739684] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    0.739744] sd 2:0:0:0: [sdb] Write Protect is off
[    0.739750] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.739811] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.740077] sd 3:0:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    0.740105] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    0.740173] sd 3:0:0:0: [sdc] Write Protect is off
[    0.740180] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    0.740188] sd 0:0:1:0: [sda] Write Protect is off
[    0.740195] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[    0.740244] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.740260] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.740571]  sdc:
[    0.740676]  sda:
[    0.740806]  sdb: unknown partition table
[    0.750572] sd 2:0:0:0: [sdb] Attached SCSI disk
[    0.752596]  sda1 sda2 < unknown partition table
[    0.755974] sd 3:0:0:0: [sdc] Attached SCSI disk
[    0.773048]  sda5 >
[    0.773405] sd 0:0:1:0: [sda] Attached SCSI disk
[    1.137801] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.137808] EXT4-fs (sda1): write access will be enabled during recovery
[    3.478150] EXT4-fs (sda1): orphan cleanup on readonly fs
[    3.478163] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 3014809
[    3.478313] EXT4-fs (sda1): 1 orphan inode deleted
[    3.478319] EXT4-fs (sda1): recovery complete
[    3.990077] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.913530] Adding 1466360k swap on /dev/sda5.  Priority:-1 extents:1 across:1466360k
kit@WATCHSERVER:~$

```

> 
```
sudo fdisk /dev/devicename
```Make a partition with n and just set it to maximum size. Press t and set type to fd and finally w to write the changes to disk. Repeat for both drives.


From what I gathered from the first command, my two new drives are sdb and sdc. So, this is what I do next:

```


kit@WATCHSERVER:~$ sudo fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x3b1b8fe1.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)

```

Do I want an extended or primary partition?

---

### Post by Fafler on 2010-09-28
Primary. Forgot about that ;-)

---

### Post by tsunamikitsune on 2010-09-28
Cool beans. Moving right along then:

> 
Now, use
```
blkid /dev/devicename
```to get the UUID of each partition. They are unique identifiers of that specific partition and i find them a good tool when using RAID because devicenames tend to change from time to time.


Uh, this one doesn't seem to give me any output. I tried adding sudo in front, but that doesn't help either. The only way I get anything to pop up from the "blkid" command is to type it in solo:

```

kit@WATCHSERVER:~$ blkid
/dev/sda1: UUID="871b9d39-9b42-4d3a-9fea-eec0e9303896" TYPE="ext4"
/dev/sda5: UUID="9d57bd3b-8957-422e-af6b-ca8df515509d" TYPE="swap"

```

No sdb or sdc here. Should I be concerned?

---

### Post by Fafler on 2010-09-28
The UUID might be created with the filesystem instead of the partition. Actually not sure. Anyway, no just use sdb1 and sdc1.

---

### Post by tsunamikitsune on 2010-09-28
Okay, things seem to be going smoothly, as far as I can tell:

```

kit@WATCHSERVER:~$ sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1  /dev/sdc1
mdadm: array /dev/md0 started.
kit@WATCHSERVER:~$ cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sdc1[1] sdb1[0]
      1465135936 blocks [2/2] [UU]
      [>....................]  resync =  0.0% (1450752/1465135936) finish=285.8min speed=85338K/sec

unused devices: <none>

```

Until this part:

```

kit@WATCHSERVER:~$ sudo mdadm --describe --brief /dev/md0 > /etc/mdadm.conf
-bash: /etc/mdadm.conf: Permission denied

```

---

### Post by Fafler on 2010-09-28
Old debian habit (sudo vs. su). In Ubuntu that would be

sudo mdadm --describe --brief /dev/md0 | sudo tee /etc/mdadm.conf

---

### Post by tsunamikitsune on 2010-09-28
> **Fafler said:**
> Old debian habit (sudo vs. su). In Ubuntu that would be

sudo mdadm --describe --brief /dev/md0 | sudo tee /etc/mdadm.conf

It says --describe isn't a valid option, but I get this without it:

```

kit@WATCHSERVER:~$ sudo mdadm --brief /dev/md0 | sudo tee /etc/mdadm.conf
/dev/md0: 1397.26GiB raid1 2 devices, 0 spares. Use mdadm --detail for more detail.

```

Everything look okay? Or was --describe an important part of that?

---

### Post by Fafler on 2010-09-28
No, it's not right. mdadm should give out info on how the array is constructed and save it to mdadm.conf.

Try this instead:

```
sudo mdadm -Es | grep md0 | sudo tee /etc/mdadm.conf
sudo ln -s /etc/mdadm.conf /etc/mdadm/mdadm.conf

```

If it tells the folder /etc/mdadm does not exist, don't worry. It's not needed in that case.

---

### Post by tsunamikitsune on 2010-09-28
Awesome. I finished the last few steps without a hitch. Thank you for all of your help. :D

One last question before I'm all finished, though. How do I set the partition to be accessed by the rest of the network? I know I need to install Samba, but what kind of configuration does that require?

---

### Post by Fafler on 2010-09-28
Have you formatted and mounted the array? Does it automount on reboot?

What shares do you want and what permissions should they have?

---

### Post by tsunamikitsune on 2010-09-28
After rebooting, I get something odd coming up:

```

fsck from util-linux-ng 2.17.2
/dev/sda1: clean, 51560/9682944 files, 995289/38705408 blocks

```

From here, I can only press Esc (to switch to a Ubuntu 10.04 loading screen) and Ctrl+Alt+Del (to reboot). I can't access the OS anymore. D:

---

### Post by tsunamikitsune on 2010-09-28
Bump? What did I do wrong to make this message pop up?

---

### Post by Fafler on 2010-09-29
Well, if anyone did something wrong, it's me. Just can't figure out what.

Does it say anything else?

Try to reboot and just as it starts to load Ubuntu (and maybe a second before) press shift or esc to enter the bootloader. Now, press E to edit boot parameters. Move down to the line starting with linux and replace the last two words, "quiet splash" with "1" and press ctrl + x to boot. It will get a menu where you can choose several actions to fix the system. Select root, press enter and login with your password.

Now you have a root shell.

Edit your /etc/fstab and comment out the line used to mount the array. Also, check if you made any other alterations in there by mistake.

Reboot and hopefully it boots without any problems.

Just for good measure, post your fstab and mdadm.conf

---

### Post by tsunamikitsune on 2010-10-03
I'm having trouble even getting to the root shell. When I edit the parameters, I change the word "quiet" (there's no "splash") to "1" and hit ctrl+x and it gives me the same message.

---

