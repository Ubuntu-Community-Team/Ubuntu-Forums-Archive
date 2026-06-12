---
title: "An error occured while mounting /."
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by duronjoshua on 2014-03-03
I've read through related threads but a lot of the suggestions seemed  somewhat vague and unhelpful.  I re-installed ubuntu 13.10 yesterday after running into some problems.  I set it up to where / was on my 32gb ssd and the /home and swap  partitions were on my 500gb hdd. I ran into an issue with grub, so I  started Ubuntu with a boot disk and ran boot-repair, restarted and  everything seemed to be working fine. However, a few hours later I  rebooted and was greeted with the "An error occurred while mounting /."  and "An error occurred while mounting /home" messages. I pressed to try  to fix them both but it did nothing. Any help would be greatly  appreciated, preferably in the form of detailed and deliberate  instruction. Thank you

Here is the ouput of "blkid"
```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6c42b421-8288-499b-b0dc-bd8fd555c1b9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="656d5dd0-09be-4c20-8bac-6656e2af9184" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="E203-B14A" TYPE="vfat"
```

I am currently running```
fsck.ext3 -cDfty -C 0 /dev/sd**
``` on both disks. Will post results (if any)

---

### Post by ajgreeny on 2014-03-03
Can we also see the output of **cat /etc/fstab** when your fsck finishes, please.

---

### Post by duronjoshua on 2014-03-03
I rebooted after blkid, Ubuntu ran another disk check and everthing seemed to boot up fine. I rebooted again to make sure it would work consistently and was greeted with the same mounting error as before. 
(I'm using a boot disk currently) 
The result of cat/etc/fstab is
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=656d5dd0-09be-4c20-8bac-6656e2af9184 /               ext3    noatime,nodiratime,discard,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=6c42b421-8288-499b-b0dc-bd8fd555c1b9 /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
#UUID=244e84f0-75cd-4c3e-8bb6-265dc6f106f2 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
tmpfs /tmp tmpfs defaults,noatime,size=512M,mode=1777 0 0
tmpfs /var/spool tmpfs defaults,noatime,size=512M,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,size=512M,mode=1777 0 0


```

---

### Post by duronjoshua on 2014-03-03
I tried and was able to boot into my system by running 

```
mount -o remount, rw /
dpkg -- configure -a
mount -o remount, ro / 
sync
reboot 
```

But I have to do it every time in order to log in. Is there anything I can do once on my normal installation to fix this permenantly?

---

### Post by ajgreeny on 2014-03-04
Are you running those last 5 command as root in a user terminal, or using recovery mode, or have you enabled the root account on the machine?

The second command would tend to give the impression that some of the packages are not configured properly, or not configured at all after installation, so more info needed before a solution comes to mind.

---

