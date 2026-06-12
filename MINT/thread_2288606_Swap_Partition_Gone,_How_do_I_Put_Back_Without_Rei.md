---
title: "Swap Partition Gone, How do I Put Back Without Reinstall?"
date: 2015-07-28
forum: MINT
---

### Post by tomasrey88 on 2015-07-28
Hi,

I recently used the installation disc to install a full install linux mint OS on a USB flash memory. However, during the install, it forced me to reformat the swap partition on my hard drive in addition to the reformat of the USB flash. Now, I have no more swap partition. How do I add it back without having to reinstall? I don't want to reinstall and lose all my installed programs and settings. 

I am afraid to use GParted without proper direction from you guys from fear of further messing up my system. 

Thanks,
Ever Greatful. 

This is how i Determined that I have no swap: 
[IMG]http://i15.photobucket.com/albums/a371/MINGMAY/Screenshot%20from%202015-07-28%20102641.png[/IMG]

---

### Post by Bucky Ball on 2015-07-28
*Thread moved to **MINT**.*

Please post another screenshot. That one is too small to see. Thanks. :)

You can 'Adv Reply' and use the paperclip icon to attach a larger shot. Don't insert it in the body of the post, please.

PS: Yes, best not to twiddle with Gparted if you're not sure what you're up to as you could lose data. :|

PPS: If you have a decent amount of RAM don't panic too much about running without a /swap. Don't hammer the resources, either, though! :)

---

### Post by howefield on 2015-07-28
With that much memory I doubt you'll ever need swap, however it is best to have it. :)

You have probably changed the UUID of the swap partition which is now different to what's in your fstab. 

What's the output of the following three commands

```
sudo fdisk -l
```
```
sudo blkid
```
```
cat /etc/fstab
```

---

### Post by Bucky Ball on 2015-07-28
Ah, yea. I put my glasses on and blew the screen right up and can make out some detail. Lot of RAM, no /swap, but as howefield mentions, best to have one.

---

### Post by tomasrey88 on 2015-07-28
**MyComputer ~ $ sudo fdisk -l**

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x83e6d949

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20482874    10241406   27  Hidden NTFS WinRE
/dev/sda2   *    20484096   821265345   400390625    7  HPFS/NTFS/exFAT
/dev/sda3       821266432  1015885823    97309696    b  W95 FAT32
/dev/sda4      1015887870  1250263039   117187585    5  Extended
/dev/sda5      1015887872  1020768255     2440192   83  Linux
/dev/sda6      1020770304  1059829759    19529728   83  Linux
/dev/sda7      1059831808  1242449919    91309056   83  Linux
/dev/sda8      1242451968  1250263039     3905536   82  Linux swap / Solaris


**MyComputer ~ $ sudo blkid**
[sudo] password for MyComputer: PleaseHelpMeThanks
/dev/sda1: LABEL="PQSERVICE" UUID="C66C141D6C140AB7" TYPE="ntfs" 
/dev/sda2: UUID="DA4A9D964A9D6FCD" TYPE="ntfs" 
/dev/sda3: UUID="6AA8-E62B" TYPE="vfat" 
/dev/sda5: UUID="7ca8e14c-dc89-4aaa-87f9-6e07fe0488f1" TYPE="ext4" 
/dev/sda6: UUID="20d14369-41e6-4b98-b357-fd46ed4ad760" TYPE="ext4" 
/dev/sda7: UUID="1fa36636-1317-4e02-9fc5-21d7e449a230" TYPE="ext4" 
[B]
MyComputer ~ $ cat /etc/fstab[/B]
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=20d14369-41e6-4b98-b357-fd46ed4ad760 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=1fa36636-1317-4e02-9fc5-21d7e449a230 /home           ext4    defaults        0       2
# swap was on /dev/sda8 during installation
UUID=263957c3-9f46-482f-82b4-c74ab5ee5b2c none            swap    sw              0       0

**Thanks. I want swap back but not at the expense of accidentally deleting my hard drive by mucking about blind with GParted. Please advise. Much appreciation. **

---

### Post by flocculant on 2015-07-28
You apparently have no UUID for sda8 - which is the swap partition. Try generating a new one for it and then edit fstab to suit

```
uuidgen
```

will give you a new UUID

set the swap partition with the new number

```
sudo tune2fs /dev/sda8 newUUID
```

Edit fstab after backing it up

```
sudo cp /etc/fstab /etc/fstab.2807

gksudo gedit /etc/fstab
```

Change the last line 

>  UUID=263957c3-9f46-482f-82b4-c74ab5ee5b2c none swap sw 0 0

to the new UUID

```
UUID=newUUID none swap sw 0 0
```

Close gedit and then turn swap on

```
sudo swapon -a
```

Check it is running with ```
free -m
```

If you get any problems you can restore the backed up fstab

```
sudo mv /etc/fstab.2807 /etc/fstab
```

Edit - if you want to use gparted. Start that - right click on the swap partition - it has the option to New UUID. After that you will still need to backup and edit fstab with the new UUID and then swapon.

---

### Post by tomasrey88 on 2015-08-09
**Your suggestion didn't quite work. What went wrong? Copy and paste of my terminal is below. Thanks. **

mycomputer ~ $ uuidgen
f15c81d4-35dc-4c85-9a90-c0e6cdda48c4
mycomputer ~ $ sudo tune2fs /dev/sda8 f15c81d4-35dc-4c85-9a90-c0e6cdda48c4
[sudo] password for me: 
tune2fs 1.42.9 (4-Feb-2014)
Usage: tune2fs [-c max_mounts_count] [-e errors_behavior] [-g group]
    [-i interval[d|m|w]] [-j] [-J journal_options] [-l]
    [-m reserved_blocks_percent] [-o [^]mount_options[,...]] [-p mmp_update_interval]
    [-r reserved_blocks_count] [-u user] [-C mount_count] [-L volume_label]
    [-M last_mounted_dir] [-O [^]feature[,...]]
    [-Q quota_options]
    [-E extended-option[,...]] [-T last_check_time] [-U UUID]
    [ -I new_inode_size ] device
mycomputer ~ $ sudo cp /etc/fstab /etc/fstab.2807
mycomputer ~ $ gksudo gedit /etc/fstab

(gedit:3460): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3460): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NXFZ2X': No such file or directory

(gedit:3460): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3460): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.S49W2X': No such file or directory

(gedit:3460): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

**I CHANGED THE LAST LINE OF /etc/fstab TO: UUID=f15c81d4-35dc-4c85-9a90-c0e6cdda48c4 none            swap    sw              0       0**

[B]mycomputer ~ $ sudo swapon -a
swapon: cannot find the device for UUID=f15c81d4-35dc-4c85-9a90-c0e6cdda48c4[/B]
mycomputer ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:         12016       1892      10124         14        104        782
-/+ buffers/cache:       1005      11011
Swap:            0          0          0

> **flocculant said:**
> You apparently have no UUID for sda8 - which is the swap partition. Try generating a new one for it and then edit fstab to suit

```
uuidgen
```

will give you a new UUID

set the swap partition with the new number

```
sudo tune2fs /dev/sda8 newUUID
```

Edit fstab after backing it up

```
sudo cp /etc/fstab /etc/fstab.2807

gksudo gedit /etc/fstab
```

Change the last line 



to the new UUID

```
UUID=newUUID none swap sw 0 0
```

Close gedit and then turn swap on

```
sudo swapon -a
```

Check it is running with ```
free -m
```

If you get any problems you can restore the backed up fstab

```
sudo mv /etc/fstab.2807 /etc/fstab
```

Edit - if you want to use gparted. Start that - right click on the swap partition - it has the option to New UUID. After that you will still need to backup and edit fstab with the new UUID and then swapon.

---

### Post by tomasrey88 on 2015-08-09
**Sometimes changes to these files don't take hold unless you reboot first, so I rebooted and then tried the following in the console, but it still didn't work. **

mycomputer ~ $ sudo swapon -a
swapon: cannot find the device for UUID=f15c81d4-35dc-4c85-9a90-c0e6cdda48c4
mycomputer ~ $ free -m
             total       used       free     shared    buffers     cached
Mem:         12016       1729      10287         14         73        727
-/+ buffers/cache:        928      11087
Swap:            0          0          0

> **flocculant said:**
> You apparently have no UUID for sda8 - which is the swap partition. Try generating a new one for it and then edit fstab to suit



---

### Post by Bucky Ball on 2015-08-10
Please use code tags for terminal output. See the last link in my signature. Thanks. :)

---

### Post by flocculant on 2015-08-10
> **tomasrey88 said:**
> ...

My bad.

try using mkswap

sudo mkswap /dev/sda8

That'll remake swap and give it a UUID, use that UUID in fstab.

---

### Post by tomasrey88 on 2015-08-12
Thanks, I think that worked :0)

---

### Post by tomasrey88 on 2015-08-12
Bucky Ball, how do I type [SOLVED] in to the subject like I see on some of the other posts on the forum? Thanks.

---

### Post by flocculant on 2015-08-12
> **tomasrey88 said:**
> Bucky Ball, how do I type [SOLVED] in to the subject like I see on some of the other posts on the forum? Thanks.

Thread Tools at the top of the thread.

---

